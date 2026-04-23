# 后端常见问题排障手册

## 概述

本手册用于排查 skill-market 后端服务（NestJS）的常见问题，包括服务启动、数据库、认证、性能等方面。

---

## 1. 服务启动失败

### 现象
- `npm run start:dev` 报错退出
- 服务启动后立即崩溃
- 端口绑定失败

### 排查步骤

1. **检查 Node.js 版本**
   ```bash
   node --version  # 要求 >= 18.0.0
   npm --version   # 要求 >= 9.0.0
   ```

2. **检查依赖安装**
   ```bash
   cd backend
   rm -rf node_modules package-lock.json
   npm install
   ```

3. **检查环境变量**
   ```bash
   # 确认 .env 文件存在
   ls -la .env
   
   # 检查必需变量
   grep -E "^(DB_|JWT_|REDIS_)" .env
   ```

4. **检查端口占用**
   ```bash
   lsof -i :3001
   # 如果被占用，杀死进程或更改端口
   ```

5. **检查数据库连接**
   ```bash
   # 测试 MySQL 连接
   mysql -h localhost -u root -p skill_market -e "SELECT 1"
   ```

6. **查看详细启动日志**
   ```bash
   npm run start:dev 2>&1 | tee startup.log
   ```

### 常见原因
| 错误信息 | 原因 | 解决方案 |
|---------|------|---------|
| `EADDRINUSE` | 端口被占用 | 杀死占用进程 |
| `ER_ACCESS_DENIED` | 数据库认证失败 | 检查 DB_PASSWORD |
| `MODULE_NOT_FOUND` | 依赖缺失 | 重新 npm install |
| `ECONNREFUSED` | 数据库/Redis 未启动 | 启动依赖服务 |

---

## 2. 数据库相关问题

### 2.1 连接失败

**排查步骤：**
```bash
# 检查 MySQL 服务状态
systemctl status mysql  # Linux
brew services list | grep mysql  # macOS

# 检查连接配置
cat .env | grep DB_

# 手动测试连接
mysql -h $DB_HOST -P $DB_PORT -u $DB_USER -p$DB_PASSWORD $DB_NAME
```

### 2.2 迁移失败

**排查步骤：**
```bash
# 查看待执行迁移
ls -la database/migrations/

# 检查迁移历史
mysql -e "SELECT * FROM migrations ORDER BY timestamp DESC LIMIT 10"

# 手动执行迁移
npm run migration:run
```

**常见问题：**
| 错误 | 原因 | 解决方案 |
|-----|------|---------|
| `ER_DUP_ENTRY` | 数据重复 | 检查唯一约束 |
| `ER_NO_SUCH_TABLE` | 表不存在 | 执行前置迁移 |
| `ER_LOCK_WAIT_TIMEOUT` | 锁等待超时 | 检查并发操作 |

### 2.3 查询性能问题

**排查步骤：**
```bash
# 开启慢查询日志
mysql -e "SET GLOBAL slow_query_log = 'ON'"
mysql -e "SET GLOBAL long_query_time = 1"

# 查看慢查询
mysql -e "SELECT * FROM mysql.slow_log ORDER BY start_time DESC LIMIT 10"

# 分析查询计划
mysql -e "EXPLAIN SELECT * FROM skills WHERE tenant_id = 'xxx'"
```

---

## 3. 认证与授权问题

### 3.1 JWT Token 问题

**排查步骤：**

1. **检查 Token 格式**
   ```bash
   # 解码 JWT（不验证签名）
   echo "eyJhbGci..." | cut -d. -f2 | base64 -d 2>/dev/null | jq .
   ```

2. **检查 Token 过期**
   - 默认过期时间：7 天
   - 检查 `JWT_EXPIRES_IN` 配置

3. **验证签名**
   ```bash
   # 检查 JWT_SECRET 是否一致
   grep JWT_SECRET .env
   ```

### 3.2 权限不足

**排查步骤：**

1. **检查用户角色**
   ```sql
   SELECT u.id, u.email, r.name as role_name 
   FROM users u 
   JOIN user_roles ur ON u.id = ur.user_id 
   JOIN roles r ON ur.role_id = r.id 
   WHERE u.id = '<user_id>';
   ```

2. **检查角色权限**
   ```sql
   SELECT r.name as role, p.resource, p.action 
   FROM roles r 
   JOIN role_permissions rp ON r.id = rp.role_id 
   JOIN permissions p ON rp.permission_id = p.id 
   WHERE r.name = '<role_name>';
   ```

3. **检查 Guard 日志**
   ```bash
   grep "RbacGuard\|PermissionGuard" logs/app.log
   ```

### 常见错误码
| 状态码 | 含义 | 排查方向 |
|-------|------|---------|
| 401 | 未认证 | 检查 Token 有效性 |
| 403 | 无权限 | 检查角色和权限绑定 |
| 419 | Token 过期 | 刷新 Token |

---

## 4. API 请求问题

### 4.1 请求超时

**排查步骤：**

1. **检查请求日志**
   ```bash
   grep "timeout\|ETIMEDOUT" logs/app.log
   ```

2. **检查外部依赖**
   ```bash
   # 测试外部服务连通性
   curl -v -m 10 https://external-service.com/api
   ```

3. **检查数据库慢查询**
   ```bash
   grep "query time" logs/app.log | sort -t: -k4 -rn | head -10
   ```

### 4.2 请求参数校验失败

**排查步骤：**

1. **检查 DTO 定义**
   ```typescript
   // 查看对应的 DTO 类
   // backend/src/<module>/dto/<operation>.dto.ts
   ```

2. **查看校验错误详情**
   ```bash
   grep "ValidationPipe\|BadRequestException" logs/app.log
   ```

3. **常见校验问题**
   | 错误 | 原因 | 解决方案 |
   |-----|------|---------|
   | `must be a string` | 类型不匹配 | 检查传参类型 |
   | `should not be empty` | 必填字段为空 | 补充必填字段 |
   | `must be an enum value` | 枚举值不合法 | 使用允许的枚举值 |

### 4.3 CORS 问题

**排查步骤：**

1. **检查 CORS 配置**
   ```bash
   grep -A 10 "cors" src/main.ts
   ```

2. **检查请求头**
   - 确认 `Origin` 头在允许列表中
   - 检查 `Access-Control-Allow-*` 响应头

3. **配置示例**
   ```typescript
   app.enableCors({
     origin: ['https://skill-market.example.com'],
     methods: ['GET', 'POST', 'PUT', 'DELETE', 'PATCH'],
     credentials: true,
   });
   ```

---

## 5. 性能问题

### 5.1 响应慢

**排查步骤：**

1. **检查 API 响应时间**
   ```bash
   # 从日志提取响应时间
   grep "Response time" logs/app.log | awk '{print $NF}' | sort -rn | head -20
   ```

2. **检查数据库性能**
   ```sql
   SHOW PROCESSLIST;
   SHOW STATUS LIKE 'Threads_connected';
   ```

3. **检查 Redis 性能**
   ```bash
   redis-cli INFO stats | grep -E "instantaneous_ops|used_memory"
   ```

4. **检查系统资源**
   ```bash
   top -l 1 | head -10
   free -m
   df -h
   ```

### 5.2 内存泄漏

**排查步骤：**

1. **监控内存使用**
   ```bash
   # 持续监控 Node.js 进程
   while true; do ps aux | grep "node.*nest" | awk '{print $6}'; sleep 60; done
   ```

2. **生成堆快照**
   ```bash
   kill -USR2 <pid>  # 触发 heapdump（需要配置）
   ```

3. **检查常见泄漏点**
   - 未清理的事件监听器
   - 未释放的数据库连接
   - 累积的定时器

### 5.3 连接池耗尽

**排查步骤：**

1. **检查数据库连接数**
   ```sql
   SHOW STATUS LIKE 'Threads_connected';
   SHOW VARIABLES LIKE 'max_connections';
   ```

2. **检查连接池配置**
   ```typescript
   // ormconfig.ts
   {
     extra: {
       connectionLimit: 10,  // 检查此值
     }
   }
   ```

3. **检查 Redis 连接**
   ```bash
   redis-cli CLIENT LIST | wc -l
   ```

---

## 6. 日志与监控

### 日志位置
- 开发环境：控制台输出
- 生产环境：`/var/log/skill-market/` 或 Docker 日志

### 日志级别
```bash
# 设置环境变量
LOG_LEVEL=debug npm run start:dev
```

### 常用日志查询

```bash
# 错误统计
grep -c "ERROR" logs/app.log

# 按时间查询
grep "2024-01-15 10:" logs/app.log

# 按模块查询
grep "\[SkillsService\]" logs/app.log

# 按请求 ID 追踪
grep "req-12345" logs/app.log
```

### 健康检查

```bash
# API 健康检查
curl http://localhost:3001/api/health

# 数据库健康检查
curl http://localhost:3001/api/health/db

# Redis 健康检查
curl http://localhost:3001/api/health/redis
```

---

## 7. 常见 Bug 模式速查

基于历史 Bug 分析，以下是常见问题模式：

| 模式 | 描述 | 排查要点 |
|-----|------|---------|
| 数据类型处理 | 前端传 string，后端期望 number | 检查 DTO 类型注解 |
| 字段名不匹配 | 前后端字段名不一致 | 对比 API 文档和实现 |
| 状态机转换 | 状态流转路径缺失 | 检查状态机定义 |
| SQL JOIN 膨胀 | 多对多 JOIN 导致数据翻倍 | 使用子查询或去重 |
| 前端状态同步 | 更新后缓存未失效 | 检查 React Query invalidate |
| 路由冲突 | 路由定义顺序问题 | 调整路由顺序 |
| 硬编码值 | 环境相关值被硬编码 | 改用环境变量 |

---

## 相关文档

- [服务架构说明](/docs/guides/dev-architecture.md)
- [RBAC 权限设计](/docs/guides/rbac-design.md)
- [数据库迁移指南](/docs/guides/database-migrations.md)
- [Skill 管理排障](/internalDocs/playbooks/backend/skill-management-triage.md)
- [错误码参考](/internalDocs/error-codes/backend-errors.md)
