# Skill Market 技术支持知识库

## 概述

本文档是 Skill Market 平台技术支持知识库的索引入口，用于帮助技术支持人员快速定位和解决客户问题。

---

## 知识库结构

```
internalDocs/
├── INDEX.md                    # 本文件 - 知识库入口
├── playbooks/                  # 排障手册
│   ├── backend/
│   │   ├── skill-management-triage.md    # Skill 管理问题排障
│   │   └── common-issues-triage.md       # 后端常见问题排障
│   ├── clawhive/
│   │   └── installation-triage.md        # ClawHive 安装启动排障
│   └── weclawhelper/
│       └── connection-triage.md          # Agent 连接通信排障
├── error-codes/                # 错误码参考
│   ├── backend-errors.md       # 后端服务错误码
│   ├── agent-errors.md         # Agent 服务错误码
│   └── clawhive-errors.md      # 客户端错误码
├── best-practices/             # 最佳实践
│   ├── skill-development.md    # Skill 开发最佳实践
│   └── operations.md           # 运维操作最佳实践
└── background/                 # 技术背景
    ├── architecture.md         # 系统架构说明
    ├── rbac.md                 # 权限体系说明
    └── client-log-paths.md     # 日志路径汇总
```

---

## 快速检索指南

### 按问题类型检索

| 问题类型 | 参考文档 |
|---------|---------|
| Skill 创建/更新/审核/发布问题 | [Skill 管理排障](playbooks/backend/skill-management-triage.md) |
| 后端服务启动/连接/性能问题 | [后端常见问题排障](playbooks/backend/common-issues-triage.md) |
| ClawHive 安装/启动/登录问题 | [ClawHive 安装排障](playbooks/clawhive/installation-triage.md) |
| Agent 离线/注册/任务执行问题 | [Agent 连接排障](playbooks/weclawhelper/connection-triage.md) |
| 后端 API 报错 | [后端错误码](error-codes/backend-errors.md) |
| Agent 日志报错 | [Agent 错误码](error-codes/agent-errors.md) |
| 客户端界面报错 | [客户端错误码](error-codes/clawhive-errors.md) |
| 权限不足问题 | [RBAC 权限体系](background/rbac.md) |
| 系统架构理解 | [系统架构](background/architecture.md) |
| 日志路径查询 | [日志路径汇总](background/client-log-paths.md) |

### 按组件检索

| 组件 | 相关文档 |
|-----|---------|
| **前端 (Next.js)** | [架构说明](background/architecture.md) |
| **后端 (NestJS)** | [后端排障](playbooks/backend/common-issues-triage.md), [错误码](error-codes/backend-errors.md) |
| **Agent Manager (Go)** | [Agent 错误码](error-codes/agent-errors.md) |
| **ClawHive (Electron)** | [安装排障](playbooks/clawhive/installation-triage.md), [错误码](error-codes/clawhive-errors.md) |
| **WEClawHelper (Go)** | [连接排障](playbooks/weclawhelper/connection-triage.md), [错误码](error-codes/agent-errors.md) |

### 按错误码检索

| 错误码范围 | 模块 | 文档 |
|-----------|------|------|
| HTTP 4xx/5xx | 后端 API | [后端错误码](error-codes/backend-errors.md) |
| REG_xxx | Agent 注册 | [Agent 错误码](error-codes/agent-errors.md) |
| HB_xxx | Agent 心跳 | [Agent 错误码](error-codes/agent-errors.md) |
| EXEC_xxx | 任务执行 | [Agent 错误码](error-codes/agent-errors.md) |
| 1xxx | 客户端认证 | [客户端错误码](error-codes/clawhive-errors.md) |
| 2xxx | Agent 通信 | [客户端错误码](error-codes/clawhive-errors.md) |
| 3xxx | Skill 操作 | [客户端错误码](error-codes/clawhive-errors.md) |

---

## 常见问题速查

### 1. Skill 相关

**Q: Skill 创建失败，提示名称已存在**
- 原因：同一租户下 Skill 名称重复
- 解决：修改 Skill 名称
- 详见：[Skill 管理排障](playbooks/backend/skill-management-triage.md#1-skill-创建失败)

**Q: Skill 审核提交后状态未变化**
- 原因：状态机转换不合法或事务回滚
- 解决：检查当前状态和审核权限
- 详见：[Skill 管理排障](playbooks/backend/skill-management-triage.md#3-skill-审核流程异常)

**Q: Skill 发布后在市场不可见**
- 原因：可见性设置或租户配额问题
- 解决：检查 is_public 设置和发布配额
- 详见：[Skill 管理排障](playbooks/backend/skill-management-triage.md#4-skill-发布失败)

### 2. 登录认证相关

**Q: 登录失败，提示凭证无效**
- 原因：用户名密码错误或账号状态异常
- 解决：确认账号密码，检查账号状态
- 详见：[后端错误码](error-codes/backend-errors.md#2-用户模块-users)

**Q: Token 过期后无法自动刷新**
- 原因：Refresh Token 也已过期
- 解决：重新登录
- 详见：[后端错误码](error-codes/backend-errors.md#token-相关)

### 3. Agent 相关

**Q: Agent 显示离线**
- 原因：进程未运行、网络问题、心跳超时
- 解决：检查 Agent 进程和网络连接
- 详见：[Agent 连接排障](playbooks/weclawhelper/connection-triage.md#3-心跳异常)

**Q: Agent 注册失败，签名验证不通过**
- 原因：系统时间不同步
- 解决：同步 NTP 时间
- 详见：[Agent 连接排障](playbooks/weclawhelper/connection-triage.md#2-注册失败)

**Q: Skill 执行超时**
- 原因：Skill 逻辑耗时、资源限制、MCP Server 问题
- 解决：检查 Skill 日志和 MCP 服务状态
- 详见：[Agent 连接排障](playbooks/weclawhelper/connection-triage.md#4-任务执行失败)

### 4. 客户端相关

**Q: ClawHive 无法启动**
- 原因：进程残留、配置损坏、端口占用
- 解决：杀死残留进程、清理缓存
- 详见：[ClawHive 排障](playbooks/clawhive/installation-triage.md#2-启动失败)

**Q: ClawHive 更新失败**
- 原因：网络问题、磁盘空间、权限不足
- 解决：检查网络和磁盘空间
- 详见：[ClawHive 排障](playbooks/clawhive/installation-triage.md#7-自动更新问题)

### 5. 权限相关

**Q: 操作返回 403 Forbidden**
- 原因：用户角色无对应权限
- 解决：检查用户角色和所需权限
- 详见：[RBAC 权限体系](background/rbac.md#8-排障指南)

---

## 日志收集位置

### 各组件日志路径

| 组件 | macOS | Windows |
|-----|-------|---------|
| ClawHive | `~/Library/Logs/ClawHive/` | `%USERPROFILE%\AppData\Roaming\ClawHive\logs\` |
| WEClawHelper | `~/Library/Application Support/WEClawHelper/logs/` | `%APPDATA%\WEClawHelper\logs\` |
| 后端服务 | `backend/logs/` 或 `/var/log/skill-market/` | - |

### 关键日志文件

| 文件 | 内容 |
|-----|------|
| `main.log` | ClawHive 主进程日志 |
| `renderer.log` | ClawHive 渲染进程日志 |
| `weclaw-helper.log` | Agent 日志 |
| `skill-execution.log` | Skill 执行日志 |
| `app.log` | 后端应用日志 |

---

## 外部参考文档

以下是项目中其他相关文档的位置：

| 文档 | 路径 | 说明 |
|-----|------|------|
| 服务架构 | `/docs/guides/dev-architecture.md` | 开发架构指南 |
| RBAC 设计 | `/docs/guides/rbac-design.md` | v3.3 权限设计文档 |
| Skill 状态机 | `/docs/guides/skill-status-machine.md` | Skill 状态流转规则 |
| 服务目录 | `/docs/guides/services-catalog.md` | 服务清单 |
| Bug 分析 | `/docs/bugfix/` | 历史 Bug 分析文档 |

---

## 使用说明

### 技术支持工作流

1. **问题收集**：获取用户问题描述、错误截图、日志文件
2. **问题分类**：根据问题类型定位到对应的排障手册
3. **排查定位**：按手册步骤逐步排查
4. **查阅错误码**：如有具体错误码，查阅错误码参考文档
5. **解决问题**：根据排查结果给出解决方案
6. **记录反馈**：将典型问题补充到知识库

### 知识库更新规范

- 新发现的问题模式应补充到对应的排障手册
- 新增的错误码应更新到错误码参考文档
- 架构变更应同步更新技术背景文档
- 遵循 Markdown 格式规范，保持文档结构一致

---

## 版本历史

| 版本 | 日期 | 变更说明 |
|-----|------|---------|
| 1.0.0 | 2024-01-15 | 初始版本，包含基础排障手册和错误码参考 |
