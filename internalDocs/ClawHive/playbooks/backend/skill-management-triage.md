# Skill 管理问题排障手册

## 概述

本手册用于排查 Skill 市场后端服务中与 Skill 管理相关的常见问题，包括 Skill 创建、更新、审核、发布等环节的故障。

---

## 1. Skill 创建失败

### 现象
- 用户点击创建 Skill 后提示失败
- 接口返回 400/500 错误

### 排查步骤

1. **检查请求参数**
   ```bash
   # 查看后端日志
   cd /path/to/backend
   tail -f logs/app.log | grep "skill"
   ```
   - 确认 `name`、`description` 等必填字段是否为空
   - 检查 `skillType` 是否在允许范围内（`mcp`、`prompt`）

2. **检查用户权限**
   - 确认用户是否有 `skill:create` 权限
   - 检查用户的租户归属是否正确
   ```sql
   SELECT u.*, t.name as tenant_name 
   FROM users u 
   LEFT JOIN tenants t ON u.tenant_id = t.id 
   WHERE u.id = '<user_id>';
   ```

3. **检查数据库约束**
   - Skill 名称是否在同一租户内重复
   ```sql
   SELECT * FROM skills WHERE name = '<skill_name>' AND tenant_id = '<tenant_id>';
   ```

### 常见原因
| 错误信息 | 原因 | 解决方案 |
|---------|------|---------|
| `Skill name already exists` | 同租户下名称重复 | 修改 Skill 名称 |
| `Invalid skill type` | skillType 不在枚举范围 | 使用 `mcp` 或 `prompt` |
| `Forbidden` | 用户无创建权限 | 联系租户管理员分配权限 |

---

## 2. Skill 更新后数据不一致

### 现象
- 更新 Skill 后，前端显示的数据与实际不符
- 部分字段更新成功，部分失败

### 排查步骤

1. **检查前端缓存**
   - 前端使用 React Query 缓存，更新后应触发 invalidate
   - 检查浏览器 Network 面板，确认请求是否发出

2. **检查后端日志**
   ```bash
   grep "skill update" logs/app.log | tail -20
   ```

3. **检查数据库实际值**
   ```sql
   SELECT * FROM skills WHERE id = '<skill_id>';
   SELECT * FROM skill_versions WHERE skill_id = '<skill_id>' ORDER BY created_at DESC LIMIT 5;
   ```

4. **检查版本关联**
   - Skill 更新会创建新版本，检查版本链是否正确
   - 确认 `current_version_id` 是否指向最新版本

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 前端显示旧数据 | React Query 缓存未失效 | 硬刷新页面或检查 mutation 的 onSuccess |
| 部分字段未更新 | DTO 校验过滤了字段 | 检查 UpdateSkillDto 定义 |
| 版本号未递增 | 版本创建逻辑异常 | 检查 skill-versions.service.ts |

---

## 3. Skill 审核流程异常

### 现象
- Skill 提交审核后状态未变化
- 审核通过/拒绝后状态卡住
- 审核历史记录缺失

### 排查步骤

1. **检查状态机合法性**
   
   Skill 状态流转规则：
   ```
   draft -> pending_review -> approved/rejected
   approved -> published
   published -> deprecated
   rejected -> draft (可重新编辑)
   ```
   
   检查当前状态是否允许目标转换：
   ```sql
   SELECT id, name, status, review_status FROM skills WHERE id = '<skill_id>';
   ```

2. **检查审核记录**
   ```sql
   SELECT * FROM skill_reviews 
   WHERE skill_id = '<skill_id>' 
   ORDER BY created_at DESC;
   ```

3. **检查用户审核权限**
   - 确认操作用户是否有 `skill:review` 权限
   - 运营人员角色（`operator`）应具有此权限

4. **检查事务完整性**
   - 审核操作涉及多表更新，检查是否有事务回滚
   ```bash
   grep "transaction" logs/app.log | grep "skill"
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 状态未变化 | 状态机转换不合法 | 确认当前状态是否允许目标操作 |
| 缺少审核记录 | 事务回滚 | 检查数据库连接和事务日志 |
| 权限拒绝 | 用户角色不足 | 分配 operator 或更高角色 |

---

## 4. Skill 发布失败

### 现象
- Skill 审核通过后无法发布
- 发布后在市场中不可见

### 排查步骤

1. **检查发布前提条件**
   - Skill 必须处于 `approved` 状态
   - 必须有至少一个有效版本
   ```sql
   SELECT s.*, sv.version 
   FROM skills s 
   JOIN skill_versions sv ON s.current_version_id = sv.id 
   WHERE s.id = '<skill_id>';
   ```

2. **检查市场可见性设置**
   ```sql
   SELECT is_public, visibility_scope FROM skills WHERE id = '<skill_id>';
   ```

3. **检查租户发布配额**
   ```sql
   SELECT 
     t.name,
     t.skill_publish_quota,
     (SELECT COUNT(*) FROM skills WHERE tenant_id = t.id AND status = 'published') as published_count
   FROM tenants t 
   WHERE t.id = '<tenant_id>';
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 发布按钮不可用 | 状态非 approved | 完成审核流程 |
| 市场不可见 | is_public = false | 修改可见性设置 |
| 配额已满 | 超出租户发布限制 | 联系平台管理员提升配额 |

---

## 5. Skill 绑定/解绑龙虾失败

### 现象
- 龙虾安装 Skill 失败
- Skill 从龙虾卸载后仍显示已安装

### 排查步骤

1. **检查龙虾状态**
   ```sql
   SELECT * FROM lobster_instances WHERE id = '<instance_id>';
   ```
   - 确认龙虾实例处于 `online` 状态

2. **检查绑定关系表**
   ```sql
   SELECT * FROM lobster_skill_bindings 
   WHERE lobster_instance_id = '<instance_id>' 
   AND skill_id = '<skill_id>';
   ```

3. **检查 Agent 心跳**
   - 龙虾通过 WEClawHelper 与后端通信
   - 检查最近心跳时间
   ```sql
   SELECT id, last_heartbeat_at FROM lobster_instances WHERE id = '<instance_id>';
   ```

4. **检查 Agent 日志**
   - 登录目标机器查看 WEClawHelper 日志
   ```bash
   # macOS
   cat ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log
   
   # Windows
   type %APPDATA%\WEClawHelper\logs\weclaw-helper.log
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 安装超时 | Agent 离线 | 检查 WEClawHelper 进程和网络 |
| 状态不一致 | 数据库与 Agent 不同步 | 触发全量同步或重启 Agent |
| 权限不足 | 用户无该龙虾操作权限 | 检查用户-龙虾权限绑定 |

---

## 6. 批量操作性能问题

### 现象
- 批量更新/删除 Skill 时响应很慢
- 数据库连接池耗尽

### 排查步骤

1. **检查慢查询**
   ```sql
   -- MySQL 慢查询日志
   SHOW VARIABLES LIKE 'slow_query_log%';
   
   -- 查看当前运行的查询
   SHOW PROCESSLIST;
   ```

2. **检查连接池状态**
   ```bash
   # 查看后端日志中的连接池警告
   grep "connection pool" logs/app.log
   ```

3. **检查索引使用**
   ```sql
   EXPLAIN SELECT * FROM skills WHERE tenant_id = '<tenant_id>' AND status = 'published';
   ```

### 优化建议
- 批量操作使用分页处理，每批不超过 100 条
- 确保 `tenant_id`、`status` 等常用查询字段有索引
- 考虑使用读写分离减轻主库压力

---

## 相关文档

- [Skill 状态机设计](/docs/guides/skill-status-machine.md)
- [RBAC 权限设计](/docs/guides/rbac-design.md)
- [服务架构说明](/docs/guides/dev-architecture.md)
- [错误码参考](/internalDocs/error-codes/backend-errors.md)
