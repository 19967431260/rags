# 客户端日志路径汇总

本文档整理了 Skill Market 项目中各个客户端/服务的日志存储路径，便于问题排查时快速定位日志文件。

---

## 1. ClawHive (Electron 桌面端)

ClawHive 使用 `electron-log` 进行日志记录，日志按日期分文件存储。

### 日志配置

| 配置项 | 值 | 说明 |
|--------|-----|------|
| 日志级别 | `info` | 文件日志级别 |
| 单文件大小限制 | 10MB | 超出后自动归档 |
| 文件命名格式 | `yyyy-mm-dd.log` | 按日期分割 |
| 归档命名格式 | `yyyy-mm-dd.{index}.log` | 同日多次滚动 |

### 日志路径

#### macOS
```
~/Library/Logs/clawhive/
~/Library/Logs/ClawHive/
~/Library/Logs/ClawHive助手/
```

#### Windows
```
%APPDATA%\clawhive\logs\
%APPDATA%\ClawHive\logs\
%APPDATA%\ClawHive助手\logs\
%LOCALAPPDATA%\clawhive\logs\
%LOCALAPPDATA%\ClawHive\logs\
%LOCALAPPDATA%\ClawHive助手\logs\
```

#### Linux
```
~/.config/clawhive/logs/
~/.config/ClawHive/logs/
~/.config/ClawHive助手/logs/
```

### 日志内容说明

| 日志标签 | 说明 |
|----------|------|
| `[main]` | 主进程生命周期事件（启动、窗口创建、关闭等） |
| `[tray]` | 系统托盘相关事件 |
| `[ipc]` | 渲染进程与主进程通信 |
| `[logger]` | 日志系统初始化信息 |
| `[feedback]` | 用户反馈提交流程 |
| `[renderer:console]` | 渲染进程 console 输出转发 |

**源码参考**: `clawHive/src/main/logger.ts:12-45`

---

## 2. WEClawHelper (Go Agent 客户端)

WEClawHelper 是部署在用户机器上的 Agent 服务，使用 `logrus` + `file-rotatelogs` 进行日志记录。

### 日志配置

| 配置项 | 默认值 | 命令行参数 | 说明 |
|--------|--------|------------|------|
| 日志级别 | `info` | `--log-level` | 支持 debug/info/warn/error |
| 写入文件 | `true` | `--log-to-file` | 是否输出到文件 |
| 文件数量 | 4 | `--log-file-count` | 保留的日志文件数 |
| 单文件大小 | 25MB | `--log-file-size` | 单个日志文件大小限制 |
| 日志目录 | 见下方 | `--log-file-path` | 自定义日志目录 |

### 日志路径

#### macOS / Linux
```
~/.weclawhelper/logs/
```

#### Windows
```
%USERPROFILE%\.weclawhelper\logs\
```

### 日志文件命名
```
weclawhelper-yyyy-mm-dd.log
```

### 日志内容说明

| 日志字段 | 说明 |
|----------|------|
| `agentID` | Agent 唯一标识 |
| `remote` | 远程连接地址 |
| `status` | HTTP 响应状态码 |
| WebSocket 相关 | 连接建立、心跳、消息收发 |
| Host 信息同步 | IP 地址变更检测 |
| Claw 检测 | 定期健康检查结果 |
| Metrics 上报 | OpenClaw 使用指标 |

**源码参考**: 
- `agent-manager-core/cmd/weclawhelper/main.go:142-151`
- `agent-manager-core/pkg/utils/logutil/log.go:9-31`

---

## 3. Agent Server (Go 服务端)

Agent Server 是中心化的 Agent 管理服务，日志配置与 WEClawHelper 类似。

### 日志配置

| 配置项 | 默认值 | 命令行参数 |
|--------|--------|------------|
| 日志级别 | `info` | `--log-level` |
| 写入文件 | `true` | `--log-to-file` |
| 日志目录 | `./logs` | `--log-file-path` |
| 文件数量 | 默认 | `--log-file-count` |
| 单文件大小 | 默认 | `--log-file-size` |

### 日志路径
```
./logs/server-yyyy-mm-dd.log
```

### 日志内容说明

| 日志类型 | 说明 |
|----------|------|
| WebSocket 会话管理 | Agent 注册、心跳、断开 |
| 代理请求转发 | API 请求代理到 Agent |
| 认证相关 | HMAC-SHA256 验证 |
| 本地注册表（测试用） | AgentID 分配 |

**源码参考**: `agent-manager-core/cmd/server/main.go:97-101`

---

## 4. Backend (NestJS API 服务)

Backend 使用 NestJS 内置 Logger，输出到 stdout/stderr。

### 日志配置

| 配置项 | 环境变量 | 默认值 | 说明 |
|--------|----------|--------|------|
| 日志级别 | `LOG_LEVEL` | `log,warn,error` | 逗号分隔的级别列表 |
| 数据库日志 | `DB_LOGGING` | `false` | 是否打印 SQL |

### 日志路径

Backend **不写入本地文件**，日志输出到 stdout，由容器/进程管理器（如 PM2、Docker）收集：

```bash
# Docker 容器日志
docker logs <container-id>

# PM2 日志
~/.pm2/logs/backend-out.log
~/.pm2/logs/backend-error.log

# 直接运行时
stdout / stderr
```

### 日志内容说明

| Logger 名称 | 说明 |
|-------------|------|
| `HTTP` | HTTP 请求响应日志，包含 requestId、耗时 |
| `AuditLogService` | 平台审计日志（写入数据库） |
| 各 Service 名 | 业务模块日志，如 `TenantsService`、`SkillsService` |

### 审计日志（数据库）

敏感操作记录到 `platform_audit_logs` 表：

| 字段 | 说明 |
|------|------|
| `operator_id` | 操作人 ID |
| `action` | 操作类型 |
| `resource_type` | 资源类型 |
| `resource_id` | 资源 ID |
| `details` | 操作详情 JSON |
| `created_at` | 操作时间 |

**源码参考**: 
- `backend/src/main.ts:20-56`
- `backend/src/common/interceptors/logging.interceptor.ts:11-44`

---

## 5. Frontend (Next.js Web 端)

Frontend 是纯前端应用，日志主要在浏览器 DevTools 中查看。

### 日志路径

| 环境 | 位置 |
|------|------|
| 开发环境 | 浏览器 DevTools Console |
| 生产环境 | 无持久化日志 |
| SSR 日志 | Node.js stdout（如有 SSR） |

### 说明

前端使用标准 `console.log/warn/error`，无独立日志文件。如需前端错误追踪，建议接入 Sentry 等 APM 服务。

---

## 6. 反馈日志收集

ClawHive 反馈功能会自动收集以下日志目录：

| 标签 | 路径 | 说明 |
|------|------|------|
| `weclawhelper` | `~/.weclawhelper/logs/` | Agent 日志 |
| `clawhive` | 见 ClawHive 日志路径 | 桌面端日志 |

收集的日志会打包成 ZIP 上传到 NOS，文件名格式：
```
clawhive-feedback-{runId}.zip
```

**源码参考**: `clawHive/src/main/feedback-paths.ts:84-99`

---

## 7. OpenClaw / LobsterAI (被管理的 Claw 客户端)

OpenClaw 和 有道龙虾 (LobsterAI) 是实际执行 AI 任务的客户端应用，由 WEClawHelper 管理和检测。

### 客户端类型

| 类型标识 | 说明 |
|----------|------|
| `openclaw` | OpenClaw 客户端 |
| `有道龙虾` | 有道龙虾 (LobsterAI) 客户端 |

### OpenClaw 日志路径

#### Sandbox 沙箱日志
```
~/.openclaw/sandbox.log
```

**说明**: 记录沙箱虚拟机 (start_vm / qemu) 的启动、运行、崩溃信息。由 WEClawHelper 的 Watchdog 组件写入。

**源码参考**: `agent-manager-core/pkg/sandbox/watchdog.go:35-54`

### OpenClaw 工作目录

#### macOS / Linux
```
~/openclaw/
```

**说明**: OpenClaw 运行时目录，包含：
- `weclaw-config.json` - Claw 配置文件（由 ClawHive 同步）
- `openclaw_qemu` - QEMU 密钥文件

**源码参考**: `clawHive/src/main/weclawhelper.ts:372-411`

### 检测脚本路径

| 平台 | 路径 | 说明 |
|------|------|------|
| macOS/Linux | `~/.weclawhelper/scripts/check-client.sh` | Claw 客户端检测脚本 |
| Windows | `%USERPROFILE%\.weclawhelper\scripts\check-client.ps1` | Claw 客户端检测脚本 |

**作用**: 定期执行检测当前安装的 Claw 客户端类型、版本、状态，返回 JSON 格式结果。

**返回字段**:
| 字段 | 说明 |
|------|------|
| `type` | 客户端类型 (`openclaw` / `有道龙虾`) |
| `version` | 客户端版本号 |
| `status` | 状态 (`ok` / `error`) |
| `message` | 错误信息（如有） |
| `installDir` | 安装目录 |

**源码参考**: `agent-manager-core/pkg/host/claw.go:20-98`

### OpenClaw Metrics 脚本

| 平台 | 路径 |
|------|------|
| macOS/Linux | `~/.weclawhelper/scripts/openclaw-stats.py` |

**作用**: 收集 OpenClaw 使用指标（如调用次数、耗时等），定期上报到后端。

**源码参考**: `agent-manager-core/pkg/host/metrics.go:18-77`

---

## 8. 行为安全策略配置 (NEAgentGuard)

行为安全模块的策略配置文件，由 WEClawHelper 从服务端同步并写入本地。

### 配置文件路径

| 文件 | 路径 | 说明 |
|------|------|------|
| 规则配置 | `~/.neagentguard/clawtrace/policy/rules.json` | 文件/域名/命令访问规则 |
| 运行时配置 | `~/.neagentguard/clawtrace/policy/runtime-config.json` | 沙箱开关、Nonce TTL 等 |

### rules.json 结构

```json
{
  "version": 1,
  "adminGlobal": { "file": [], "domain": [], "command": [] },
  "adminLocal": { "file": [], "domain": [], "command": [] },
  "user": { "file": [], "domain": [], "command": [] },
  "defaultFileAction": "allow",
  "defaultDomainOutboundAction": "deny",
  "defaultDomainInboundAction": "deny",
  "defaultCommandAction": "allow"
}
```

### runtime-config.json 结构

```json
{
  "version": 1,
  "enableSandbox": false,
  "sandboxNonceTTLMinutes": 10
}
```

**源码参考**: `agent-manager-core/pkg/behaviorsecurity/apply.go:101-145`

---

## 9. JSON 配置文件汇总

### WEClawHelper 配置

| 文件 | 路径 | 说明 |
|------|------|------|
| 主配置 | `~/.weclawhelper/config.json` | Agent 启动参数持久化 |
| Agent ID | `~/.weclawhelper/agent_id` | 注册后分配的唯一 ID |

#### config.json 结构

```json
{
  "bindCode": "ABC123",
  "registryURL": "wss://...",
  "agentServer": "https://...",
  "authSecret": "...",
  "machineType": "local",
  "account": "user@example.com",
  "logLevel": "info",
  "logToFile": true,
  "logFilePath": "",
  "noSandbox": false,
  "sandboxScript": "",
  "shellDir": "",
  "insecure": false,
  "clawHiveManaged": true,
  "clawHiveHeartbeatFile": "",
  "clawHiveAppPath": ""
}
```

**源码参考**: `agent-manager-core/pkg/host/config.go:10-71`

### Windows 遗留配置路径

| 文件 | 路径 | 说明 |
|------|------|------|
| 旧配置 | `C:\ProgramData\WEClawHelper\config.json` | 旧版配置（已迁移） |
| 旧 Agent ID | `C:\ProgramData\WEClawHelper\agent_id` | 旧版 ID（已迁移） |

**说明**: Windows 平台已从 ProgramData 迁移到用户目录 `%USERPROFILE%\.weclawhelper\`

**源码参考**: `clawHive/src/main/weclawhelper.ts:514-516`

### ClawHive 心跳文件

| 平台 | 路径 | 说明 |
|------|------|------|
| macOS | `~/.weclawhelper/clawhive.heartbeat` | ClawHive 存活心跳 |

**作用**: macOS 平台上 WEClawHelper 通过监控此文件判断 ClawHive 是否存活，用于自动退出机制。

**源码参考**: `clawHive/src/main/weclawhelper.ts:143-168`

### Claw 配置文件

| 文件 | 路径 | 说明 |
|------|------|------|
| weclaw-config.json | `~/openclaw/weclaw-config.json` | Claw 运行配置 |
| weclaw-config.json | `~/.weclawhelper/scripts/weclaw-config.json` | 备份位置 |

**作用**: 由 ClawHive 从内置资源同步到用户目录，供 OpenClaw 读取。

**源码参考**: `clawHive/src/main/weclawhelper.ts:380-390`

---

## 快速排查指南

### 场景 1: ClawHive 桌面端无法启动
1. 检查 `~/Library/Logs/clawhive/` (macOS) 或 `%APPDATA%\clawhive\logs\` (Windows)
2. 查看最新的 `yyyy-mm-dd.log` 文件
3. 搜索 `[main]` 标签定位启动错误

### 场景 2: Agent 无法连接服务端
1. 检查 `~/.weclawhelper/logs/weclawhelper-*.log`
2. 搜索 `registry` 或 `websocket` 关键词
3. 查看 `agentID` 和连接状态

### 场景 3: Backend API 异常
1. 查看容器/PM2 日志
2. 根据 `X-Request-Id` 响应头追踪完整请求链路
3. 检查 `platform_audit_logs` 表查看敏感操作记录

### 场景 4: 用户提交反馈
1. 通过 ClawHive 内置反馈功能自动收集日志
2. 日志 ZIP 包会上传到 NOS
3. 包含 ClawHive + WEClawHelper 双端日志

### 场景 5: OpenClaw 沙箱崩溃
1. 检查 `~/.openclaw/sandbox.log`
2. 搜索 `start_vm` 或 `qemu` 相关错误
3. 查看 WEClawHelper 日志中的 `sandbox:` 标签

### 场景 6: Claw 客户端未检测到
1. 检查 `~/.weclawhelper/scripts/check-client.sh` 是否存在
2. 手动执行脚本查看输出: `bash ~/.weclawhelper/scripts/check-client.sh`
3. 查看 WEClawHelper 日志中的 `claw check` 相关记录

### 场景 7: 行为安全策略不生效
1. 检查 `~/.neagentguard/clawtrace/policy/rules.json` 是否存在
2. 验证 JSON 格式是否正确
3. 查看 WEClawHelper 日志中的 `behaviorsecurity` 或 `configsync` 相关记录

---

## 日志级别说明

| 级别 | 适用场景 |
|------|----------|
| `debug` | 开发调试，详细输出 |
| `info` | 生产默认，关键流程记录 |
| `warn` | 潜在问题，不影响功能 |
| `error` | 明确错误，需要关注 |

---

*文档生成时间: 2026-04-23*
*基于源码版本: skill-market/develop*
