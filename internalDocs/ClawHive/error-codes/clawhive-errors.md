# ClawHive 客户端错误码参考

## 概述

本文档整理了 ClawHive 桌面客户端（Electron 应用）中的错误码和错误消息，包括主进程、渲染进程、IPC 通信等模块。

---

## 1. 应用启动错误

### 主进程错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `AppInitError` | `Failed to initialize application` | 应用初始化失败 | 查看 main.log 详细日志 |
| `ConfigLoadError` | `Failed to load configuration` | 配置加载失败 | 检查配置文件完整性 |
| `SingleInstanceError` | `Another instance is already running` | 已有实例运行 | 关闭其他实例 |
| `PortInUseError` | `Local service port is in use` | 端口被占用 | 释放端口 15234 |

### 窗口创建错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `WindowCreateError` | `Failed to create main window` | 窗口创建失败 | 检查系统图形驱动 |
| `PreloadScriptError` | `Failed to load preload script` | 预加载脚本失败 | 检查应用完整性 |
| `RendererCrashError` | `Renderer process crashed` | 渲染进程崩溃 | 检查 renderer.log |

---

## 2. 认证相关错误

### 登录错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `LoginTimeoutError` | `Login request timed out` | 登录超时 | 检查网络连接 |
| `InvalidCredentialsError` | `Invalid username or password` | 凭证错误 | 确认账号密码 |
| `AccountDisabledError` | `Account has been disabled` | 账号被禁用 | 联系管理员 |
| `OAuthError` | `OAuth authentication failed` | OAuth 失败 | 检查 OAuth 配置 |
| `NetworkError` | `Network request failed` | 网络请求失败 | 检查网络和代理 |

### Token 错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `TokenExpiredError` | `Session has expired` | Token 过期 | 重新登录 |
| `TokenInvalidError` | `Invalid authentication token` | Token 无效 | 重新登录 |
| `RefreshTokenError` | `Failed to refresh token` | 刷新 Token 失败 | 重新登录 |

---

## 3. Agent 通信错误

### IPC 通信错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `IPCTimeoutError` | `IPC request timed out` | IPC 请求超时 | 重启应用 |
| `IPCChannelError` | `IPC channel not established` | 通道未建立 | 检查 Agent 状态 |
| `IPCSerializationError` | `Failed to serialize IPC message` | 序列化失败 | 检查数据格式 |

### Agent 状态错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `AgentOfflineError` | `Agent is offline` | Agent 离线 | 检查 WEClawHelper |
| `AgentNotFoundError` | `Agent process not found` | Agent 进程不存在 | 重启应用 |
| `AgentStartError` | `Failed to start agent` | Agent 启动失败 | 查看 Agent 日志 |
| `AgentCommunicationError` | `Failed to communicate with agent` | 通信失败 | 检查本地服务 |

---

## 4. Skill 相关错误

### Skill 加载错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `SkillLoadError` | `Failed to load skill` | Skill 加载失败 | 检查 Skill 文件 |
| `SkillNotFoundError` | `Skill not found` | Skill 不存在 | 同步 Skill 列表 |
| `SkillParseError` | `Failed to parse skill manifest` | manifest 解析失败 | 检查 Skill 格式 |
| `SkillVersionError` | `Incompatible skill version` | 版本不兼容 | 更新 Skill 或客户端 |

### Skill 执行错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `SkillExecutionError` | `Skill execution failed` | 执行失败 | 查看执行日志 |
| `SkillTimeoutError` | `Skill execution timed out` | 执行超时 | 检查 Skill 逻辑 |
| `SkillRuntimeError` | `Skill runtime error` | 运行时错误 | 查看详细错误 |
| `SkillDependencyError` | `Missing skill dependency` | 依赖缺失 | 安装所需依赖 |

### Skill 同步错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `SkillSyncError` | `Failed to sync skills` | 同步失败 | 检查网络 |
| `SkillDownloadError` | `Failed to download skill` | 下载失败 | 重试下载 |
| `SkillInstallError` | `Failed to install skill` | 安装失败 | 检查存储空间 |
| `SkillUninstallError` | `Failed to uninstall skill` | 卸载失败 | 检查文件权限 |

---

## 5. 反馈相关错误

### 日志收集错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `FeedbackArchiveError` | `Failed to create log archive` | 压缩日志失败 | 检查磁盘空间 |
| `FeedbackUploadError` | `Failed to upload feedback` | 上传反馈失败 | 检查网络 |
| `FeedbackFileSizeError` | `Log file exceeds size limit` | 日志文件过大 | 分割或压缩日志 |

### ServiceState 错误

| 错误类型 | 描述 |
|---------|------|
| `ServiceState.IDLE` | 服务空闲 |
| `ServiceState.COLLECTING` | 正在收集日志 |
| `ServiceState.UPLOADING` | 正在上传 |
| `ServiceState.ERROR` | 发生错误 |
| `ServiceState.COMPLETE` | 完成 |

---

## 6. 更新相关错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `UpdateCheckError` | `Failed to check for updates` | 检查更新失败 | 检查网络 |
| `UpdateDownloadError` | `Failed to download update` | 下载更新失败 | 检查网络和空间 |
| `UpdateInstallError` | `Failed to install update` | 安装更新失败 | 使用管理员权限 |
| `UpdateSignatureError` | `Update signature verification failed` | 签名验证失败 | 重新下载 |

---

## 7. 存储相关错误

### 本地存储错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `StorageReadError` | `Failed to read from storage` | 读取失败 | 检查文件权限 |
| `StorageWriteError` | `Failed to write to storage` | 写入失败 | 检查磁盘空间 |
| `StorageCorruptError` | `Storage data is corrupted` | 数据损坏 | 清理并重新初始化 |
| `StorageQuotaError` | `Storage quota exceeded` | 存储配额超限 | 清理缓存 |

### 缓存错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `CacheReadError` | `Failed to read cache` | 缓存读取失败 | 清理缓存 |
| `CacheWriteError` | `Failed to write cache` | 缓存写入失败 | 检查权限和空间 |
| `CacheExpiredError` | `Cache has expired` | 缓存过期 | 正常情况，会自动刷新 |

---

## 8. 网络相关错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `NetworkOfflineError` | `No network connection` | 无网络连接 | 检查网络 |
| `NetworkTimeoutError` | `Network request timed out` | 请求超时 | 检查网络质量 |
| `CertificateError` | `SSL certificate error` | 证书错误 | 导入信任证书 |
| `ProxyError` | `Proxy connection failed` | 代理连接失败 | 检查代理配置 |
| `DNSError` | `DNS resolution failed` | DNS 解析失败 | 检查 DNS 设置 |
| `CORSError` | `CORS policy blocked` | CORS 策略阻止 | 联系管理员配置 |

---

## 9. 前端 UI 错误

### React 错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `RenderError` | `Component render error` | 组件渲染错误 | 查看控制台日志 |
| `StateError` | `Invalid state update` | 状态更新错误 | 检查组件逻辑 |
| `HydrationError` | `Hydration mismatch` | 水合不匹配 | 检查 SSR 逻辑 |

### React Query 错误

| 错误类型 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `QueryError` | 查询失败 | 检查 API 和网络 |
| `MutationError` | 变更失败 | 检查请求参数 |
| `CacheError` | 缓存错误 | 清理 Query 缓存 |

---

## 10. 系统相关错误

### 权限错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `FileAccessError` | `Permission denied` | 文件访问被拒 | 检查文件权限 |
| `AdminPrivilegeError` | `Requires administrator privileges` | 需要管理员权限 | 使用管理员运行 |
| `SystemIntegrationError` | `System integration failed` | 系统集成失败 | 检查系统设置 |

### 资源错误

| 错误类型 | 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|---------|
| `MemoryError` | `Out of memory` | 内存不足 | 关闭其他应用 |
| `DiskSpaceError` | `Insufficient disk space` | 磁盘空间不足 | 清理磁盘 |
| `CPUOverloadError` | `CPU usage too high` | CPU 过载 | 检查资源占用 |

---

## 错误代码汇总表

### 数字错误码映射

| 错误码 | 类别 | 描述 |
|-------|------|------|
| 1xxx | 认证 | 登录、Token 相关 |
| 2xxx | Agent | Agent 通信相关 |
| 3xxx | Skill | Skill 操作相关 |
| 4xxx | 网络 | 网络请求相关 |
| 5xxx | 存储 | 本地存储相关 |
| 6xxx | 更新 | 自动更新相关 |
| 7xxx | 系统 | 系统资源相关 |
| 8xxx | UI | 界面渲染相关 |
| 9xxx | 其他 | 其他错误 |

### 常见错误码

| 错误码 | 名称 | 描述 |
|-------|------|------|
| 1001 | `AUTH_TIMEOUT` | 登录超时 |
| 1002 | `AUTH_INVALID` | 凭证无效 |
| 1003 | `TOKEN_EXPIRED` | Token 过期 |
| 2001 | `AGENT_OFFLINE` | Agent 离线 |
| 2002 | `AGENT_START_FAILED` | Agent 启动失败 |
| 3001 | `SKILL_NOT_FOUND` | Skill 不存在 |
| 3002 | `SKILL_LOAD_FAILED` | Skill 加载失败 |
| 3003 | `SKILL_EXEC_TIMEOUT` | Skill 执行超时 |
| 4001 | `NETWORK_OFFLINE` | 网络离线 |
| 4002 | `NETWORK_TIMEOUT` | 网络超时 |
| 5001 | `STORAGE_FULL` | 存储已满 |
| 6001 | `UPDATE_FAILED` | 更新失败 |

---

## 日志中的错误格式

### 主进程日志格式

```
[2024-01-15 10:30:00.123] [ERROR] [main] Error message
  at Function.createError (path/to/file.js:123)
  Error details...
```

### 渲染进程日志格式

```
[2024-01-15 10:30:00.123] [ERROR] [renderer] Component error: message
  Stack trace...
```

### 常用日志搜索

```bash
# macOS
grep -i "error" ~/Library/Logs/ClawHive/main.log | tail -50

# 按时间范围
grep "2024-01-15 10:" ~/Library/Logs/ClawHive/main.log

# 按错误类型
grep "SkillExecutionError" ~/Library/Logs/ClawHive/renderer.log
```

---

## 快速排查指南

### 根据错误类别定位

```
认证问题 → 1xxx 错误 → 检查登录和 Token
Agent 问题 → 2xxx 错误 → 检查 WEClawHelper
Skill 问题 → 3xxx 错误 → 检查 Skill 配置和依赖
网络问题 → 4xxx 错误 → 检查网络和代理
存储问题 → 5xxx 错误 → 检查磁盘空间和权限
```

### 常见问题处理流程

1. **应用无法启动**：检查 main.log → 查找 AppInitError
2. **无法登录**：检查网络 → 检查 Token → 查看 1xxx 错误
3. **Agent 离线**：检查 WEClawHelper 进程 → 查看 2xxx 错误
4. **Skill 执行失败**：检查 skill-execution.log → 查看 3xxx 错误

---

## 相关文档

- [ClawHive 安装排障](/internalDocs/playbooks/clawhive/installation-triage.md)
- [WEClawHelper 排障](/internalDocs/playbooks/weclawhelper/connection-triage.md)
- [日志路径汇总](/docs/guides/client-log-paths.md)
