# 客户端日志路径汇总

本文档整理了 ClawHive 项目中各端的日志存储路径，便于问题排查时快速定位日志文件。

---

## 1. ClawHive（Electron 桌面端）

ClawHive 使用 `electron-log` 进行日志记录，日志路径由 `app.getPath('logs')` 决定，按日期分文件存储。

### 日志配置

| 配置项 | 值 | 说明 |
|--------|-----|------|
| 日志级别（文件） | `info` | 生产环境固定 info |
| 日志级别（控制台） | `info`（开发）/ 关闭（打包后） | 打包后 console 日志关闭 |
| 单文件大小限制 | 10 MB | 超出后自动归档 |
| 当前文件命名 | `yyyy-mm-dd.log` | 按日期 |
| 归档文件命名 | `yyyy-mm-dd.{index}.log` | 同日多次滚动，index 从 1 递增 |

### 日志路径

应用名候选列表（按代码中 `CLAWHIVE_LOG_DIR_CANDIDATES` 定义顺序）：
```
clawhive / ClawHive / ClawHive助手
```

#### macOS
```
~/Library/Logs/clawhive/
~/Library/Logs/ClawHive/
~/Library/Logs/ClawHive助手/
```
> 优先检查 `~/Library/Logs/clawhive/`（首选目录）

#### Windows
```
%APPDATA%\clawhive\logs\
%APPDATA%\ClawHive\logs\
%APPDATA%\ClawHive助手\logs\
%LOCALAPPDATA%\clawhive\logs\
%LOCALAPPDATA%\ClawHive\logs\
%LOCALAPPDATA%\ClawHive助手\logs\
```
> `%APPDATA%` 通常为 `C:\Users\{用户名}\AppData\Roaming`  
> `%LOCALAPPDATA%` 通常为 `C:\Users\{用户名}\AppData\Local`

#### Linux
```
~/.config/clawhive/logs/
~/.config/ClawHive/logs/
~/.config/ClawHive助手/logs/
```

### 常见日志标签

| 标签 | 含义 |
|------|------|
| `[logger]` | 日志系统初始化，含实际 logsPath |
| `[main]` | 主进程生命周期（启动、窗口、关闭） |
| `[tray]` | 系统托盘事件 |
| `[ipc]` | 渲染进程与主进程通信 |
| `[feedback]` | 用户反馈提交流程 |
| `[renderer:console]` | 渲染进程 console 输出转发 |
| `[weclawhelper]` | WEClawHelper 安装/启动/状态轮询 |
| `[upgrade]` | 应用自动更新相关 |

> 不确定日志实际落地路径时，搜索 `[logger] configured` 一行，其中包含 `logsPath` 字段的实际值。

**源码参考**：`clawHive/src/main/logger.ts`、`clawHive/src/main/feedback-paths.ts`、`clawHive/src/shared/app-brand.ts`

---

## 2. WEClawHelper（Go 后台服务）

WEClawHelper 是 ClawHive 启动的本地 Go 服务，日志目录固定在 `DataDir()/logs/`。

### DataDir 定义

| 平台 | DataDir |
|------|---------|
| macOS / Linux | `~/.weclawhelper/` |
| Windows | `%USERPROFILE%\.weclawhelper\`（等价于 `C:\Users\{用户名}\.weclawhelper\`） |

> Windows 已完全迁移到用户目录，不再使用 `C:\ProgramData\WEClawHelper`（旧版遗留）。

### 日志路径

| 平台 | 路径 |
|------|------|
| macOS / Linux | `~/.weclawhelper/logs/` |
| Windows | `%USERPROFILE%\.weclawhelper\logs\` |

### 日志文件格式

```
weclawhelper-command-yyyy-mm-dd.log   ← 命令审计日志
```

> 也可通过 `--command-log-path` 启动参数指定自定义目录。

### 其他关键目录

| 目录 | 说明 |
|------|------|
| `~/.weclawhelper/scripts/` | WEClawHelper 运行脚本（含 `weclaw-config.json`） |
| `~/.weclawhelper/skills/` | 已安装的 Skill 包 |
| `~/.weclawhelper/plugins/` | 插件目录 |
| `~/.weclawhelper/sandbox/` | 沙箱工作区 |
| `~/.weclawhelper/runtime/` | 运行时状态文件（含 `weclawtrace-bootstrap.json`） |
| `~/.weclawhelper/bin/` | 内置二进制文件 |
| `~/.weclawhelper/clawhive.heartbeat` | ClawHive 存活心跳文件（macOS，WEClawHelper 监控） |

**源码参考**：`agent-manager-core/pkg/host/paths_unix.go`、`agent-manager-core/pkg/host/paths_windows.go`、`agent-manager-core/cmd/weclawhelper/main.go`

---

## 3. 后端（NestJS）

后端日志通过 PM2 / 容器标准输出收集，无独立日志文件路径。

排查时查看：
- PM2：`pm2 logs skill-market-backend`
- 容器：`docker logs <container_id>`
- 数据库审计：`platform_audit_logs` 表（敏感操作记录）

---

## 快速排查指南

### 场景 1：ClawHive 桌面端无法启动
1. macOS：`~/Library/Logs/clawhive/` → 最新 `yyyy-mm-dd.log`
2. Windows：`%APPDATA%\clawhive\logs\` → 最新 `yyyy-mm-dd.log`
3. 搜索 `[main]` 标签定位启动错误，搜索 `[logger] configured` 确认日志路径

### 场景 2：WEClawHelper 无法连接 / Agent 离线
1. macOS/Linux：`~/.weclawhelper/logs/weclawhelper-command-*.log`
2. Windows：`%USERPROFILE%\.weclawhelper\logs\weclawhelper-command-*.log`
3. 搜索 `registry`、`websocket`、`agentID` 关键词

### 场景 3：用户提交反馈（自动收集）
1. ClawHive 内置反馈功能自动打包日志上传 NOS
2. 包含 ClawHive + WEClawHelper 双端日志
3. 临时打包目录：系统 temp 目录下 `clawhive-feedback-{runId}/`

### 场景 4：不确定日志路径
1. 在 ClawHive 日志中搜索 `[logger] configured`，查看 `logsPath` 字段实际值
2. WEClawHelper 日志固定在 `DataDir()/logs/`，DataDir 见上表

---

## 日志级别说明

| 级别 | 含义 |
|------|------|
| `debug` | 详细调试，默认不输出到文件 |
| `info` | 关键流程，生产默认级别 |
| `warn` | 潜在问题，不影响功能 |
| `error` | 明确错误，需关注 |

---

*基于源码版本：commit 7148d195*
*更新时间：2026-04-23*