# 排障：Web 端安装 Claw 运行时报错"安装未启动"

> **适用产品：** 蟹蟹（Web 端安装向导）  
> **适用场景：** 安装客户端 → 步骤「下载并部署 Claw 运行时」出现报错弹窗  
> **文档类型：** 单问题排障手册（Playbook）  
> **面向对象：** TSE（技术支持工程师）

---

## 一、现象

用户在 Web 端蟹蟹安装向导的「下载并部署 Claw 运行时」步骤中，安装进度页面弹出以下提示：

> 安装失败：安装未启动，请先执行 install-openclaw.sh 或 install-lobsterai.sh。是否清空当前配置，从第一步重新开始安装？

页面同时提供"重新安装"和"清空配置，从头开始"两个操作选项。

---

## 二、功能流程说明

理解此问题需要先掌握安装链路的完整流程：

```
用户点击"开始安装"
  │
  ▼
[前端] POST /api/hosts/:agentId/trigger-install
  │   携带参数：agentId、clientType（openclaw 或 lobsterai）
  │
  ▼
[后端 hosts.service] 写库：
  agent_hosts.claw_status  = 'installing'
  agent_hosts.claw_message = '安装准备中'
  │
  ▼
[后端] 通过 WEClawHelper Agent 异步下发 install-client 脚本
  │   macOS 实际执行：bash ~/.weclawhelper/scripts/install-client.sh
  │   环境变量传入：CLIENT_TYPE、DOWNLOAD_URL、DOWNLOAD_SHA256
  │
  ▼
[用户机器] 安装脚本后台执行，实时写入进度文件：
  ┌─────────────────────────────────────────────────────────┐
  │  OpenClaw:                                              │
  │    状态快照: /tmp/openclaw-install/status.json          │
  │    事件详情: /tmp/openclaw-install/progress.jsonl       │
  │  LobsterAI:                                             │
  │    状态快照: /tmp/lobsterai-install/status.json         │
  │    事件详情: /tmp/lobsterai-install/progress.jsonl      │
  └─────────────────────────────────────────────────────────┘
  │
  ▼
[前端] 每隔数秒轮询后端 GET /api/hosts/:agentId/local-install-status
  │
  ▼
[后端] 调用 install-progress.sh 查询进度
  │
  ├── STATUS_FILE 不存在 ──────────────────────────────────→ 返回：
  │                                                            status = "not_started"
  │                                                            message = "安装未启动，请先执行
  │                                                             install-openclaw.sh 或
  │                                                             install-lobsterai.sh"
  ├── sessionId 不匹配 / TTL 过期 ─────────────────────────→ 同上，返回 not_started
  │
  └── 文件存在且有效 ────────────────────────────────────────→ 正常返回进度
  │
  ▼
[前端] 检测到 phase=installing + clawMessage 包含"安装未启动"
  → 自动重试触发安装，最多 3 次（每次间隔 30 秒）
  → 超过重试上限 → 展示"安装失败"弹窗（即用户看到的报错）
```

---

## 三、可能原因

| # | 原因 | 判断依据 |
|---|------|---------|
| 1 | **Agent 离线，install-client 脚本未被下发** | `agent_hosts.last_heartbeat_at` 超时；Agent 日志无 install-client 记录 |
| 2 | **安装包 URL 未配置，脚本无法下载安装包** | 后端日志含 `hasDownloadUrl=no` |
| 3 | **安装策略拦截，指令未下发** | 后端日志含 `[triggerInstall] blocked` |
| 4 | **脚本不存在或无执行权限，启动后立即退出** | `~/.weclawhelper/scripts/install-client.sh` 不存在或无 `x` 权限 |
| 5 | **进度文件被系统 /tmp 清理机制清空** | `/tmp/openclaw-install/` 或 `/tmp/lobsterai-install/` 目录不存在 |
| 6 | **sessionId 不一致（旧会话遗留）** | `status.json` 存在但 sessionId 与当前安装会话不匹配 |
| 7 | **进度状态文件超过 TTL（默认 900 秒）** | `status.json` 文件修改时间距今超过 900 秒 |
| 8 | **CLIENT_TYPE 变量传递错误，读取了错误目录** | 后端下发的 clientType 与 install-progress.sh 实际读取的目录不一致 |

---

## 四、快速恢复（优先执行，不阻塞用户）

> 在深入排查之前，先按以下顺序引导用户尝试。**大多数情况（进度文件丢失 / TTL 过期 / 旧会话遗留）通过前两步即可解决，全程约 2 分钟。**

### 4.1 第一步：直接点击页面上的"重新安装"

弹窗出现后，页面提供了两个选项：

- ✅ **推荐先点"重新安装"**（不清空配置）  
  系统会自动重新触发 `install-client` 脚本，重建进度文件，安装流程从头开始。  
  适用于：进度文件被清理、网络抖动导致脚本启动失败等偶发性问题。

- ⚠️ 仅当"重新安装"连续失败 2 次以上时，才考虑点"清空配置，从第一步重新开始"。

---

### 4.2 第二步：若"重新安装"仍报同样错误，清理进度目录后重试

引导用户打开终端（macOS）或 PowerShell（Windows），执行以下命令：

**macOS / Linux：**
```bash
# 根据安装类型选择一条执行
rm -rf /tmp/openclaw-install/
rm -rf /tmp/lobsterai-install/
```

**Windows（PowerShell）：**
```powershell
# 根据安装类型选择一条执行
Remove-Item -Recurse -Force "$env:TEMP\openclaw-install" -ErrorAction SilentlyContinue
Remove-Item -Recurse -Force "$env:TEMP\lobsterai-install" -ErrorAction SilentlyContinue
```

清理后，**回到页面点击"重新安装"**，等待进度条正常推进。

> **原理：** 报错本质是 `install-progress.sh` 找不到有效的进度状态文件。清空旧目录后重新触发安装，脚本会重新创建文件并写入进度。

---

### 4.3 第三步：若仍失败，重启 WEClawHelper 后重试

WEClawHelper 是负责在用户机器上执行安装脚本的 Agent。若 Agent 进程异常，脚本无法被触发。

**macOS：**
```bash
# 查看 WEClawHelper 是否在运行
pgrep -l weclawhelper

# 若没有输出（未运行），手动启动
open -a WEClawHelper 2>/dev/null || open ~/.weclawhelper/weclawhelper 2>/dev/null || true
```

**Windows（PowerShell）：**
```powershell
# 查看进程
Get-Process | Where-Object { $_.Name -like "*weclawhelper*" }

# 若未运行，手动启动（路径因安装方式而异）
Start-Process "$env:USERPROFILE\.weclawhelper\weclawhelper.exe" -ErrorAction SilentlyContinue
```

WEClawHelper 启动后，**回到页面点击"重新安装"**。

---

### 4.4 快速恢复流程图

```
报错"安装未启动"
  │
  ▼
① 点击页面"重新安装"
  │
  ├── 成功（进度条推进）──────────────────────────── ✅ 解决
  │
  └── 仍报同样错误
        │
        ▼
      ② 清理进度目录（rm -rf /tmp/openclaw-install/ 等）
         回到页面点"重新安装"
        │
        ├── 成功 ───────────────────────────────────── ✅ 解决
        │
        └── 仍失败
              │
              ▼
            ③ 重启 WEClawHelper，再点"重新安装"
              │
              ├── 成功 ──────────────────────────────── ✅ 解决
              │
              └── 仍失败 ──────────────────────────────── ⚠️ 进入深度排查（第五章）
```

---

## 五、深度排查步骤

### Step 1 — 确认 Agent 在线，安装指令已下发

**① 查库确认 Agent 心跳：**
```sql
SELECT id, os, arch, claw_status, claw_message, claw_last_reported_at, last_heartbeat_at
FROM agent_hosts
WHERE id = <agentId>;
```
- `last_heartbeat_at` 距当前时间 > 60 秒 → Agent 离线  
  → **转 Agent 连接排障**（`connection-triage.md`），解决后重新触发安装。

**② 搜索后端日志（关键字 `[triggerInstall]`）：**

| 日志内容 | 含义 | 处理 |
|---------|------|------|
| `[triggerInstall] start agentId=N clientType=openclaw hasDownloadUrl=yes` | 正常触发 | 继续看下一步 |
| `hasDownloadUrl=no` | 安装包地址未配置 | 联系运营在后台配置安装包 URL 和 sha256 |
| `[triggerInstall] blocked reason=local_disabled` | 租户关闭了本地安装 | 联系租户管理员开启 |
| `[triggerInstall] blocked reason=client_not_allowed` | 租户未开放该 clientType | 联系租户管理员授权 |
| `[triggerInstall] blocked reason=os_client_not_allowed` | 该 OS 下不支持所选客户端 | 引导用户返回上一步重新选择客户端类型 |

**③ 查看 WEClawHelper Agent 日志，确认脚本是否执行：**
- macOS/Linux：`~/.weclawhelper/logs/weclaw-helper.log`
- Windows：`%USERPROFILE%\.weclawhelper\logs\weclaw-helper.log`

搜索关键字 `install-client`，确认是否有执行记录及返回码。

---

### Step 2 — 检查用户机器上的进度文件

**让用户执行以下命令（根据系统和 clientType）：**

**macOS / Linux：**
```bash
# OpenClaw
ls -la /tmp/openclaw-install/ && cat /tmp/openclaw-install/status.json

# LobsterAI
ls -la /tmp/lobsterai-install/ && cat /tmp/lobsterai-install/status.json
```

**Windows（PowerShell）：**
```powershell
# OpenClaw
Get-Item "$env:TEMP\openclaw-install" -ErrorAction SilentlyContinue
Get-Content "$env:TEMP\openclaw-install\status.json" -ErrorAction SilentlyContinue

# LobsterAI
Get-Item "$env:TEMP\lobsterai-install" -ErrorAction SilentlyContinue
Get-Content "$env:TEMP\lobsterai-install\status.json" -ErrorAction SilentlyContinue
```

**判断结果：**

| 结果 | 说明 | 下一步 |
|------|------|-------|
| 目录不存在 / status.json 不存在 | 安装脚本从未写入进度 → 脚本未启动 | 继续 Step 3 |
| status.json 存在，status=running | 安装正在进行，前端轮询异常 | 手动运行 install-progress.sh（Step 5）验证 |
| status.json 存在，status=success/fail | 旧会话遗留，TTL 或 sessionId 问题 | 进入 Step 4 |

---

### Step 3 — 检查安装脚本是否存在且有执行权限

```bash
# macOS：检查脚本是否存在
ls -la ~/.weclawhelper/scripts/install-client.sh
ls -la ~/.weclawhelper/scripts/install-openclaw.sh
ls -la ~/.weclawhelper/scripts/install-lobsterai.sh
ls -la ~/.weclawhelper/scripts/install-progress.sh
```

- **脚本不存在** → WEClawHelper 脚本未同步  
  解决：重启 WEClawHelper 触发脚本自动同步，或重装 WEClawHelper。

- **脚本存在但无执行权限**（`-rw-r--r--` 而非 `-rwxr-xr-x`）  
  解决：
  ```bash
  chmod +x ~/.weclawhelper/scripts/*.sh
  ```
  然后在页面点击"重新安装"重新触发。

---

### Step 4 — 排查 sessionId 不一致 / TTL 过期

```bash
# 查看 status.json 中的 sessionId 和时间戳
cat /tmp/openclaw-install/status.json   # 或 lobsterai-install
```

典型 `status.json` 内容：
```json
{
  "ts": "2026-04-24T08:00:00Z",
  "step": "done",
  "status": "success",
  "message": "安装完成",
  "progress": 100,
  "pid": 12345,
  "sessionId": "abc123"
}
```

检查项：
1. **`ts` 时间距当前是否超过 900 秒（15 分钟）**  
   → 超过则 TTL 过期，`install-progress.sh` 视为旧会话返回 `not_started`。
2. **`sessionId` 是否与当前安装会话一致**  
   → 不一致则同样返回 `not_started`。

**处理：** 清空进度目录，然后在页面点击"重新安装"：
```bash
rm -rf /tmp/openclaw-install/
# 或
rm -rf /tmp/lobsterai-install/
```

---

### Step 5 — 手动运行 install-progress.sh 验证进度查询

在用户机器上直接运行脚本，复现后端实际收到的返回值：

```bash
# OpenClaw
CLIENT_TYPE=openclaw bash ~/.weclawhelper/scripts/install-progress.sh

# LobsterAI
CLIENT_TYPE=lobsterai bash ~/.weclawhelper/scripts/install-progress.sh
```

**预期正常返回（安装进行中）：**
```json
{
  "ts": "2026-04-24T10:00:00Z",
  "step": "install_openclaw",
  "status": "running",
  "message": "正在安装 OpenClaw",
  "progress": 42,
  "running": true
}
```

**异常返回（触发报错的根因）：**
```json
{"ts":"...","status":"not_started","message":"安装未启动，请先执行 install-openclaw.sh 或 install-lobsterai.sh"}
```

---

## 六、所需日志清单

| 日志 | 位置 | 查找内容 |
|------|------|---------|
| 后端服务日志 | 服务端容器 stdout / 日志采集 | `[triggerInstall]`、`hasDownloadUrl`、`blocked` |
| WEClawHelper Agent 日志 | macOS: `~/.weclawhelper/logs/weclaw-helper.log`<br>Windows: `%USERPROFILE%\.weclawhelper\logs\weclaw-helper.log` | `install-client`、`exit code` |
| 安装进度状态文件 | `/tmp/openclaw-install/status.json`<br>`/tmp/lobsterai-install/status.json` | `status`、`sessionId`、`ts` |
| 安装完整事件日志 | `/tmp/openclaw-install/progress.jsonl`<br>`/tmp/lobsterai-install/progress.jsonl` | 逐步骤事件，`status=fail` 行 |

---

## 七、解决方案汇总

| 根因 | 解决方式 |
|------|---------|
| Agent 离线 | 排查并恢复 WEClawHelper 连接后，重新触发安装 |
| 安装包 URL 未配置 | 后台管理员配置对应 clientType 的 `DOWNLOAD_URL` 和 `DOWNLOAD_SHA256` |
| 安装策略拦截（租户限制） | 租户管理员在蟹蟹管理后台开放对应客户端类型或操作系统 |
| 脚本不存在 | 重启 WEClawHelper 触发脚本同步；或手动重装 WEClawHelper |
| 脚本无执行权限 | `chmod +x ~/.weclawhelper/scripts/*.sh` 后重新触发安装 |
| 进度目录被清理 | 页面点击"重新安装"即可（会重新触发 install-client） |
| sessionId 不一致 / TTL 过期 | `rm -rf /tmp/openclaw-install/`（或 lobsterai-install），再点击"重新安装" |
| CLIENT_TYPE 传递错误 | 排查后端 `[triggerInstall]` 日志中 `clientType` 字段，确认与用户实际选择一致 |

---

## 八、相关文档

- [ClawHive 安装与启动问题排障总览](./installation-triage.md)
- [WEClawHelper 连接/注册/心跳排障](../weclawhelper/connection-triage.md)
- [ClawHive 错误码参考](../../error-codes/clawhive-errors.md)
- [日志路径汇总](../../background/client-log-paths.md)
