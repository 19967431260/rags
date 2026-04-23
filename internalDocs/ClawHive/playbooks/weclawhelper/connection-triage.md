# WEClawHelper 连接与通信问题排障手册

## 概述

WEClawHelper 是运行在用户机器上的 Go Agent，负责与后端服务通信、执行 Skill、上报心跳等。本手册用于排查 Agent 的连接、注册、心跳和任务执行问题。

---

## 1. Agent 无法启动

### 现象
- WEClawHelper 进程未运行
- ClawHive 显示 Agent 离线
- 启动后立即退出

### 排查步骤

1. **检查进程状态**
   ```bash
   # macOS
   ps aux | grep -i weclawhelper
   pgrep -l WEClawHelper
   
   # Windows (PowerShell)
   Get-Process | Where-Object {$_.Name -like "*WEClawHelper*"}
   ```

2. **检查启动日志**
   ```bash
   # macOS
   cat ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log | head -100
   
   # Windows
   type "%APPDATA%\WEClawHelper\logs\weclaw-helper.log" | more
   ```

3. **检查配置文件**
   ```bash
   # macOS
   cat ~/Library/Application\ Support/WEClawHelper/config.json
   ```
   
   配置文件示例：
   ```json
   {
     "server_url": "https://skill-market.example.com",
     "agent_id": "agt_xxxx",
     "machine_id": "mac_xxxx",
     "log_level": "info"
   }
   ```

4. **检查端口占用**
   ```bash
   # Agent 本地服务端口
   lsof -i :15235
   netstat -an | grep 15235
   ```

5. **手动启动调试**
   ```bash
   # macOS - 找到二进制文件路径
   /Applications/ClawHive.app/Contents/Resources/WEClawHelper --debug
   
   # Windows
   "%LOCALAPPDATA%\ClawHive\WEClawHelper.exe" --debug
   ```

### 常见原因
| 错误日志 | 原因 | 解决方案 |
|---------|------|---------|
| `config file not found` | 配置文件缺失 | 重新安装或从 ClawHive 触发初始化 |
| `address already in use` | 端口被占用 | 杀死占用进程或更改端口 |
| `permission denied` | 权限不足 | 检查文件/目录权限 |

---

## 2. 注册失败

### 现象
- Agent 启动后无法注册到后端
- 日志中显示 registration failed
- 后端数据库无此 Agent 记录

### 排查步骤

1. **检查网络连通性**
   ```bash
   # 测试后端可达性
   curl -v https://skill-market.example.com/api/health
   
   # 测试 Agent 注册接口
   curl -v https://skill-market.example.com/api/v1/agents/register
   ```

2. **检查 Agent 日志**
   ```bash
   grep -i "register" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log
   ```

3. **检查签名验证**
   - Agent 注册需要通过签名验证
   - 检查系统时间是否同步（时间偏差会导致签名失败）
   ```bash
   # 检查系统时间
   date
   
   # 同步时间（macOS）
   sudo sntp -sS time.apple.com
   ```

4. **检查证书问题**
   ```bash
   # 验证 SSL 证书
   openssl s_client -connect skill-market.example.com:443
   ```

5. **检查后端日志**
   ```bash
   # 在后端服务器
   grep "agent register" /path/to/backend/logs/app.log
   ```

### 常见原因
| 错误信息 | 原因 | 解决方案 |
|---------|------|---------|
| `signature verification failed` | 签名不匹配 | 检查系统时间，重新生成 agent_id |
| `connection refused` | 后端服务不可达 | 检查网络和防火墙 |
| `certificate verify failed` | SSL 证书问题 | 导入信任的 CA 证书 |
| `agent already registered` | 重复注册 | 清理旧配置后重试 |

---

## 3. 心跳异常

### 现象
- Agent 显示在线但后端显示离线
- 心跳间歇性失败
- 后端 last_heartbeat_at 长时间未更新

### 排查步骤

1. **检查心跳日志**
   ```bash
   grep -i "heartbeat" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log | tail -50
   ```

2. **检查后端心跳记录**
   ```sql
   SELECT id, agent_id, last_heartbeat_at, status 
   FROM agents 
   WHERE agent_id = '<agent_id>';
   ```

3. **检查网络稳定性**
   ```bash
   # 持续 ping 测试
   ping -c 100 skill-market.example.com
   
   # 检查丢包率
   mtr skill-market.example.com
   ```

4. **检查心跳间隔配置**
   ```bash
   # 查看 Agent 配置中的心跳间隔
   cat ~/Library/Application\ Support/WEClawHelper/config.json | grep heartbeat
   ```
   
   默认心跳间隔：30 秒

5. **检查后端心跳超时配置**
   - 后端默认 90 秒无心跳判定离线
   - 检查 `backend/.env` 中的 `AGENT_HEARTBEAT_TIMEOUT`

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 间歇性离线 | 网络不稳定 | 检查网络质量 |
| 持续离线 | 心跳请求被拦截 | 检查防火墙/代理 |
| 时间偏差导致 | 系统时间不同步 | 同步 NTP 时间 |

---

## 4. 任务执行失败

### 现象
- Skill 执行超时
- 执行结果未上报
- 任务卡在 pending 状态

### 排查步骤

1. **检查任务日志**
   ```bash
   grep -i "task\|execute" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log | tail -100
   ```

2. **检查 Skill 文件**
   ```bash
   # 查看已下载的 Skill
   ls -la ~/Library/Application\ Support/WEClawHelper/skills/
   
   # 检查 Skill manifest
   cat ~/Library/Application\ Support/WEClawHelper/skills/<skill_id>/manifest.json
   ```

3. **检查执行环境**
   - MCP 类型 Skill 需要对应运行时
   - Prompt 类型 Skill 需要 LLM 配置
   ```bash
   # 检查 Node.js（如果 Skill 依赖）
   node --version
   
   # 检查 Python（如果 Skill 依赖）
   python3 --version
   ```

4. **检查资源限制**
   ```bash
   # 检查内存使用
   ps aux | grep WEClawHelper
   
   # 检查磁盘空间
   df -h
   ```

5. **检查后端任务状态**
   ```sql
   SELECT * FROM tasks 
   WHERE agent_id = '<agent_id>' 
   ORDER BY created_at DESC 
   LIMIT 10;
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 执行超时 | Skill 逻辑耗时过长 | 优化 Skill 或增加超时时间 |
| 依赖缺失 | 运行环境不完整 | 安装所需依赖 |
| 内存溢出 | Skill 资源消耗过大 | 限制 Skill 资源使用 |

---

## 5. 配置同步问题

### 现象
- Agent 配置与后端不一致
- Skill 列表未更新
- 权限变更未生效

### 排查步骤

1. **触发手动同步**
   - 在 ClawHive 中点击"同步配置"
   - 或重启 Agent

2. **检查同步日志**
   ```bash
   grep -i "sync\|config" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log
   ```

3. **对比本地与远程配置**
   ```bash
   # 本地配置
   cat ~/Library/Application\ Support/WEClawHelper/config.json
   
   # 远程配置（通过 API）
   curl -H "Authorization: Bearer <token>" \
     https://skill-market.example.com/api/v1/agents/<agent_id>/config
   ```

4. **清理本地缓存**
   ```bash
   rm ~/Library/Application\ Support/WEClawHelper/cache/*
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 配置不同步 | 缓存未刷新 | 清理缓存并重启 |
| Skill 缺失 | 下载失败 | 检查网络并重新同步 |
| 权限未生效 | Token 未刷新 | 重新登录获取新 Token |

---

## 6. 日志与调试

### 日志文件位置

| 平台 | 路径 |
|-----|------|
| macOS | `~/Library/Application Support/WEClawHelper/logs/` |
| Windows | `%APPDATA%\WEClawHelper\logs\` |
| Linux | `~/.config/WEClawHelper/logs/` |

### 日志级别调整

编辑 `config.json`：
```json
{
  "log_level": "debug"  // 可选: debug, info, warn, error
}
```

然后重启 Agent 生效。

### 常用调试命令

```bash
# 实时查看日志
tail -f ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log

# 搜索错误
grep -i "error\|fail" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log

# 统计错误类型
grep -i "error" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log | sort | uniq -c | sort -rn

# 检查 API 调用
grep -i "api\|http" ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log
```

### 获取诊断信息

```bash
# 系统信息
uname -a
sw_vers  # macOS 版本

# Agent 版本
cat ~/Library/Application\ Support/WEClawHelper/version

# 网络信息
ifconfig | grep inet
netstat -an | grep ESTABLISHED | grep skill-market
```

---

## 7. 安全相关

### 现象
- Agent 被安全软件拦截
- 网络请求被防火墙阻断
- 证书验证失败

### 排查步骤

1. **检查杀毒软件日志**
   - 将 WEClawHelper 添加到白名单

2. **检查防火墙规则**
   ```bash
   # macOS
   sudo /usr/libexec/ApplicationFirewall/socketfilterfw --listapps
   
   # 允许 WEClawHelper
   sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add /path/to/WEClawHelper
   ```

3. **检查企业代理**
   ```bash
   # 查看系统代理设置
   scutil --proxy
   
   # 设置 Agent 代理（在 config.json）
   {
     "proxy": "http://proxy.company.com:8080"
   }
   ```

4. **检查证书链**
   ```bash
   # 导出服务器证书
   openssl s_client -showcerts -connect skill-market.example.com:443 </dev/null 2>/dev/null | openssl x509 -outform PEM > server.crt
   
   # 验证证书
   openssl verify server.crt
   ```

---

## 相关文档

- [日志路径汇总](/docs/guides/client-log-paths.md)
- [ClawHive 安装排障](/internalDocs/playbooks/clawhive/installation-triage.md)
- [Agent 错误码](/internalDocs/error-codes/agent-errors.md)
- [服务架构说明](/docs/guides/dev-architecture.md)
