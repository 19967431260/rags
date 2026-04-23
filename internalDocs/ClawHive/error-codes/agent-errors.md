# Agent 服务错误码参考

## 概述

本文档整理了 WEClawHelper (Go Agent) 和 agent-manager-core 服务中的错误码和错误消息，便于排查 Agent 相关问题。

---

## 1. Agent 注册错误

### 注册流程错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `REG_001` | `registration failed: invalid machine id` | 机器 ID 格式错误 | 检查机器 ID 生成逻辑 |
| `REG_002` | `registration failed: signature verification failed` | 签名验证失败 | 检查系统时间同步 |
| `REG_003` | `registration failed: agent already exists` | Agent 已注册 | 清理旧配置后重试 |
| `REG_004` | `registration failed: tenant not found` | 租户不存在 | 检查租户配置 |
| `REG_005` | `registration failed: quota exceeded` | Agent 配额已满 | 联系管理员提升配额 |

### 签名相关错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `invalid signature format` | 签名格式错误 | 检查签名算法实现 |
| `signature timestamp expired` | 签名时间戳过期 | 同步系统时间 |
| `signature nonce reused` | 随机数重复使用 | 检查 nonce 生成逻辑 |

---

## 2. 心跳相关错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `HB_001` | `heartbeat failed: agent not registered` | Agent 未注册 | 执行注册流程 |
| `HB_002` | `heartbeat failed: invalid token` | Token 无效 | 重新获取 Token |
| `HB_003` | `heartbeat failed: network timeout` | 网络超时 | 检查网络连接 |
| `HB_004` | `heartbeat failed: server unavailable` | 服务器不可用 | 检查后端服务状态 |

---

## 3. 任务执行错误

### 任务获取错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `TASK_001` | `task fetch failed: unauthorized` | 认证失败 | 检查 Token |
| `TASK_002` | `task fetch failed: no pending tasks` | 无待执行任务 | 正常情况，无需处理 |
| `TASK_003` | `task not found` | 任务不存在 | 任务可能已被取消 |

### 任务执行错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `EXEC_001` | `execution failed: skill not found` | Skill 不存在 | 同步 Skill 列表 |
| `EXEC_002` | `execution failed: skill load error` | Skill 加载失败 | 检查 Skill 文件完整性 |
| `EXEC_003` | `execution failed: timeout` | 执行超时 | 检查 Skill 逻辑或增加超时 |
| `EXEC_004` | `execution failed: resource limit` | 资源超限 | 检查内存/CPU 限制 |
| `EXEC_005` | `execution failed: runtime error` | 运行时错误 | 查看详细错误日志 |

### 结果上报错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `REPORT_001` | `result report failed: network error` | 网络错误 | 检查网络连接 |
| `REPORT_002` | `result report failed: invalid format` | 结果格式错误 | 检查结果序列化 |
| `REPORT_003` | `result report failed: task expired` | 任务已过期 | 任务超时被取消 |

---

## 4. Skill 同步错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `SYNC_001` | `skill sync failed: download error` | 下载失败 | 检查网络和存储空间 |
| `SYNC_002` | `skill sync failed: checksum mismatch` | 校验和不匹配 | 重新下载 |
| `SYNC_003` | `skill sync failed: extraction error` | 解压失败 | 检查文件完整性 |
| `SYNC_004` | `skill sync failed: manifest invalid` | manifest 无效 | 检查 Skill 包格式 |

---

## 5. 配置相关错误

| 错误码 | 错误消息 | 触发场景 | 解决方案 |
|-------|---------|---------|---------|
| `CFG_001` | `config load failed: file not found` | 配置文件不存在 | 重新初始化配置 |
| `CFG_002` | `config load failed: parse error` | 配置解析失败 | 检查 JSON 格式 |
| `CFG_003` | `config load failed: invalid field` | 配置字段无效 | 检查配置项名称 |
| `CFG_004` | `config save failed: permission denied` | 无写权限 | 检查目录权限 |

### 配置文件结构

```json
{
  "server_url": "https://skill-market.example.com",
  "agent_id": "agt_xxxxxxxxxxxx",
  "machine_id": "mac_xxxxxxxxxxxx",
  "tenant_id": "tnt_xxxxxxxxxxxx",
  "log_level": "info",
  "heartbeat_interval": 30,
  "task_timeout": 300,
  "proxy": ""
}
```

---

## 6. 网络相关错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `connection refused` | 目标服务未启动 | 检查后端服务 |
| `connection timeout` | 连接超时 | 检查网络和防火墙 |
| `certificate verify failed` | SSL 证书问题 | 导入 CA 证书 |
| `proxy connection failed` | 代理连接失败 | 检查代理配置 |
| `dns lookup failed` | DNS 解析失败 | 检查 DNS 配置 |

---

## 7. MCP Server 错误

### MCP 启动错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `mcp server start failed: port in use` | 端口被占用 | 释放端口或更换端口 |
| `mcp server start failed: binary not found` | MCP 二进制不存在 | 检查安装完整性 |
| `mcp server start failed: permission denied` | 无执行权限 | 添加执行权限 |

### MCP 通信错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `mcp call failed: server not running` | MCP 服务未运行 | 启动 MCP 服务 |
| `mcp call failed: invalid request` | 请求格式错误 | 检查 MCP 协议 |
| `mcp call failed: method not found` | 方法不存在 | 检查 Skill 定义 |
| `mcp call failed: timeout` | 调用超时 | 增加超时或优化 Skill |

---

## 8. 文件系统错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `no space left on device` | 磁盘空间不足 | 清理磁盘空间 |
| `permission denied` | 无读写权限 | 检查目录权限 |
| `file already exists` | 文件已存在 | 删除或重命名 |
| `directory not empty` | 目录非空 | 清空目录后重试 |
| `too many open files` | 文件描述符耗尽 | 增加 ulimit |

---

## 9. agent-manager-core API 错误

### 健康检查接口 `/health`

| 响应 | 含义 |
|-----|------|
| `{"status": "ok"}` | 服务正常 |
| `{"status": "degraded", "reason": "..."}` | 服务降级 |
| `{"status": "unhealthy", "reason": "..."}` | 服务异常 |

### 注册接口 `/api/v1/agents/register`

| HTTP 状态码 | 错误体示例 | 说明 |
|------------|----------|------|
| 400 | `{"error": "invalid_request", "message": "..."}` | 请求参数错误 |
| 401 | `{"error": "unauthorized", "message": "..."}` | 认证失败 |
| 409 | `{"error": "conflict", "message": "agent already exists"}` | Agent 已存在 |
| 500 | `{"error": "internal_error", "message": "..."}` | 内部错误 |

### 心跳接口 `/api/v1/agents/heartbeat`

| HTTP 状态码 | 错误体示例 | 说明 |
|------------|----------|------|
| 400 | `{"error": "invalid_request"}` | 请求格式错误 |
| 401 | `{"error": "unauthorized"}` | Token 无效 |
| 404 | `{"error": "agent_not_found"}` | Agent 未注册 |

---

## 10. 日志中的错误格式

### 标准日志格式

```
2024-01-15T10:30:00Z ERROR [component] message key=value key2=value2
```

### 常见日志关键字

| 关键字 | 含义 | 排查方向 |
|-------|------|---------|
| `[register]` | 注册相关 | 检查注册流程 |
| `[heartbeat]` | 心跳相关 | 检查网络连接 |
| `[task]` | 任务相关 | 检查任务执行 |
| `[skill]` | Skill 相关 | 检查 Skill 同步 |
| `[mcp]` | MCP 相关 | 检查 MCP Server |
| `[config]` | 配置相关 | 检查配置文件 |

### 日志搜索示例

```bash
# 查找所有错误
grep "ERROR" weclaw-helper.log

# 查找注册相关错误
grep "ERROR.*register" weclaw-helper.log

# 查找特定时间段错误
grep "2024-01-15T10:" weclaw-helper.log | grep "ERROR"

# 统计错误类型
grep "ERROR" weclaw-helper.log | awk '{print $3}' | sort | uniq -c | sort -rn
```

---

## 快速排查指南

### 根据错误码前缀定位

| 前缀 | 模块 | 排查文档 |
|-----|------|---------|
| `REG_` | 注册 | 检查签名、网络、配置 |
| `HB_` | 心跳 | 检查网络、Token |
| `TASK_` | 任务获取 | 检查认证、服务状态 |
| `EXEC_` | 任务执行 | 检查 Skill、资源限制 |
| `REPORT_` | 结果上报 | 检查网络、任务状态 |
| `SYNC_` | Skill 同步 | 检查网络、存储 |
| `CFG_` | 配置 | 检查配置文件 |

### 常见问题快速定位

```
Agent 无法启动 → CFG_* 错误 → 检查配置文件
Agent 离线 → HB_* 错误 → 检查网络和心跳
任务不执行 → EXEC_* 错误 → 检查 Skill 和资源
Skill 缺失 → SYNC_* 错误 → 检查同步和下载
```

---

## 相关文档

- [WEClawHelper 排障手册](/internalDocs/playbooks/weclawhelper/connection-triage.md)
- [日志路径汇总](/docs/guides/client-log-paths.md)
- [服务架构说明](/docs/guides/dev-architecture.md)
