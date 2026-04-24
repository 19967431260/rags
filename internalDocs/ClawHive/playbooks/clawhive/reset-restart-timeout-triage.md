# 排障：Web 端重启本地蟹蟹失败（Gateway 无法就绪）

> **适用产品：** 蟹蟹（OpenClaw Gateway / macOS）  
> **适用场景：** 用户在 Web 端点击「重启本地蟹蟹」后，操作长时间无响应或返回重启失败  
> **文档类型：** 单问题排障手册（Playbook）  
> **面向对象：** TSE（技术支持工程师）

---

## 一、现象

用户在 Web 端蟹蟹管理界面点击「重启」按钮后，页面持续 loading，最终提示重启失败或超时。

用户侧无报错弹窗，或仅显示通用错误提示。进一步引导用户查看 Gateway 日志时，可见以下特征之一：

- `[✗] 重启超时，请检查日志：tail -f /tmp/openclaw/*.log`（若用户通过 Agent 脚本触发）
- 日志中无任何新条目（进程未启动）
- 日志中有报错但进程反复退出（崩溃循环）

---

## 二、功能流程说明（代码调用链）

Web 端重启操作的完整代码调用链如下：

```
[Web 前端] 用户点击「重启」
  │
  ▼
[前端] POST /api/hosts/:agentId/restart-claw
  │
  ▼
[后端 hosts.service → restartClaw()]
  写库：agent_hosts.claw_status = 'restarting'
  │
  ▼
[后端 → WEClawHelper Agent RPC]
  下发 reset-client 指令（含 clientType=openclaw）
  │
  ▼
[WEClawHelper Agent → reset-openclaw 执行器]
  ├── 重置 workspace（解压默认配置）
  └── 调用 openclaw service restart（等价于 launchctl bootout + bootstrap）
        │
        ▼
      [macOS LaunchAgent：ai.openclaw.gateway]
        launchctl 拉起 openclaw gateway 进程
        │
        ▼
      [openclaw gateway 启动序列（Node.js 进程）]
        ├── 加载 workspace 配置（~/.openclaw/workspace/config.json 等）
        ├── 绑定本地 HTTP 端口（默认 25555）
        ├── 启动 mDNS/Bonjour 广播（@homebridge/ciao，MDNSServer）
        │     依赖：本地网卡 IPv4 地址
        └── 初始化 Channel 连接（飞书 WS、其他外部 Channel）
              依赖：网络可达性
  │
  ▼
[WEClawHelper] 轮询健康检查端点：GET http://localhost:25555/health
  │
  ├── 超时时限内返回 {"status":"ok"} ──────────────────→ 上报后端：claw_status = 'running'
  │                                                       前端显示：重启成功
  │
  └── 超时未响应 ──────────────────────────────────────→ 上报后端：claw_status = 'error'
                                                          前端显示：重启失败
```

**健康检查就绪的判定条件（源码层）：**

Gateway HTTP Server 在以下所有条件同时满足后，才将 `/health` 接口的 `status` 置为 `ok`：

1. `subsystem-CJEvHE2o.js`：所有子系统（mDNS、Channel、Cron）完成 `init()` 调用
2. `gateway-cli-6Ksv5U_O.js`：Bonjour 广播进入 `announcing` 状态（非 `probing`）
3. HTTP Server 成功监听 `25555` 端口

任一条件未满足，`/health` 持续返回非 ok 状态或无响应，导致超时。

---

## 三、可能原因

| # | 原因 | 涉及模块 / 代码位置 | 判断依据 |
|---|------|-------------------|---------|
| 1 | **LaunchAgent 拉起失败，Node 进程未启动** | `ai.openclaw.gateway.plist` / launchctl | `launchctl list` PID 为 `-`；日志无任何输出 |
| 2 | **openclaw 二进制不在 PATH，LaunchAgent 的 EnvironmentVariables 缺失** | `gateway.plist → EnvironmentVariables.PATH` | 进程退出码 `127`（command not found） |
| 3 | **本地 HTTP 端口 25555 被占用，Server 监听失败** | `gateway-cli-6Ksv5U_O.js` HTTP Server bind | 日志含 `EADDRINUSE :25555` |
| 4 | **启动时网卡无 IPv4，mDNS 模块初始化卡住** | `@homebridge/ciao → MDNSServer.ts → NetworkManager` | 日志含 `no IPv4 address available on en0` |
| 5 | **网卡 IP 状态从 `undefined` 变为有值，触发 MDNSServer 断言崩溃（已知 Bug，≤ v2026.4.1）** | `MDNSServer.handleUpdatedNetworkInterfaces()` → `NetworkManager.checkForNewInterfaces()` | 日志含 `AssertionError: Reached illegal state! IPv4 address changed from undefined to defined` |
| 6 | **外部 Channel（飞书）WebSocket 连接失败，子系统 init() 阻塞** | `subsystem-CJEvHE2o.js` → `gateway/channels/feishu` | 日志含 `ENOTFOUND open.feishu.cn` 或 `unable to connect after trying N times` |
| 7 | **workspace 配置文件损坏，Gateway 启动时解析失败崩溃** | `gateway-cli-6Ksv5U_O.js` 配置加载阶段 | 日志含 `ENOENT` 或 `SyntaxError` + 配置文件路径 |
| 8 | **openclaw 版本过旧，存在其他已知启动 Bug** | 全局 | 日志含 `update available`；版本 ≤ v2026.4.1 |

---

## 四、快速恢复（优先执行，不阻塞用户）

> 以下三步覆盖绝大多数重启失败场景，全程约 3 分钟，**先让用户操作，无需等待深度排查结论**。

### 4.1 第一步：确认网络状态，在 Web 端再次点击「重启」

mDNS 初始化和 Channel 连接均依赖网络就绪。让用户确认：

```bash
# 确认主网卡已有 IP（en0 为 Wi-Fi 接口）
ipconfig getifaddr en0

# 若使用飞书 Channel，确认域名可达
curl -s --max-time 5 https://open.feishu.cn -o /dev/null -w "%{http_code}\n"
```

- `en0` 有 IP 输出，curl 返回非 `000` → 网络正常，**直接在 Web 端再次点击「重启」**
- `en0` 无输出 → 引导用户重连 Wi-Fi，待网络就绪后再重启

---

### 4.2 第二步：若 Web 端重启仍失败，引导用户手动拉起 Gateway 进程

绕过 Web 端流程，直接通过 `launchctl` 操作 Gateway 的 LaunchAgent：

```bash
# 停止
launchctl bootout gui/$(id -u) ~/Library/LaunchAgents/ai.openclaw.gateway.plist 2>/dev/null || true
sleep 2

# 重新拉起
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/ai.openclaw.gateway.plist

# 验证健康状态
sleep 8 && curl -s --max-time 5 http://localhost:25555/health
```

---

### 4.3 第三步：若健康检查仍不通过，检查版本并升级

```bash
openclaw --version
```

若版本 ≤ `v2026.4.1`，存在 mDNS 接口变更崩溃的已知 Bug（见三、原因 #5），升级可修复：

```bash
openclaw update
openclaw service restart
```

---

### 4.4 快速恢复流程图

```
Web 端重启失败
  │
  ▼
① 确认网络（ipconfig getifaddr en0）→ Web 端再次点击「重启」
  │
  ├── 成功 ───────────────────────────────────────────── ✅ 解决
  │
  └── 仍失败
        │
        ▼
      ② 手动 launchctl bootout + bootstrap，验证 /health
        │
        ├── 成功 ──────────────────────────────────────── ✅ 解决
        │
        └── 仍失败
              │
              ▼
            ③ openclaw update + service restart
              │
              ├── 成功 ──────────────────────────────── ✅ 解决
              │
              └── 仍失败 ──────────────────────────────── ⚠️ 进入深度排查（第五章）
```

---

## 五、深度排查步骤

### Step 1 — 确认 Gateway 进程状态

```bash
launchctl list | grep openclaw
pgrep -la node | grep openclaw
```

| 结果 | 说明 | 下一步 |
|------|------|-------|
| 有条目且 PID 不为 `-` | 进程运行中，但 `/health` 不响应 | Step 2 查日志，定位卡住的子系统 |
| PID 为 `-` | 进程注册后立即崩溃退出（退出码可在 `launchctl list` 最后一列查看） | Step 2 查崩溃原因 |
| 无条目 | LaunchAgent 未注册 | Step 4 检查 plist |

---

### Step 2 — 查看 Gateway 日志，定位具体模块失败

```bash
# 实时跟踪
tail -f /tmp/openclaw/*.log

# 筛选 ERROR / WARN（JSON 日志格式）
grep -h '"logLevelName":"ERROR"\|"logLevelName":"WARN"' \
  /tmp/openclaw/openclaw-$(date +%Y-%m-%d).log | tail -30

# 快速命中已知关键字
grep -Ei \
  'ENOTFOUND|AssertionError|Unhandled|no IPv4|ENOENT|SyntaxError|EADDRINUSE|update available' \
  /tmp/openclaw/openclaw-$(date +%Y-%m-%d).log
```

**关键日志速查表（含源码位置）：**

| 日志关键字 | 源码模块 | 含义 | 处理方向 |
|-----------|---------|------|---------|
| `no IPv4 address available on en0` | `subsystem-CJEvHE2o.js` | 网卡无 IP，mDNS 初始化挂起 | 等网络就绪后重启 |
| `ENOTFOUND open.feishu.cn` | `gateway/channels/feishu`（openclaw-lark 插件） | 飞书域名 DNS 解析失败，Channel init() 阻塞 | 检查 DNS / 防火墙 |
| `Reached illegal state! IPv4 address changed from undefined to defined` | `@homebridge/ciao → MDNSServer.handleUpdatedNetworkInterfaces()` | 网卡 IP 变化时 mDNS 断言崩溃，进程退出（已知 Bug） | 升级 openclaw |
| `Unhandled promise rejection: AssertionError` | Node.js 全局 uncaughtRejection | 进程因未捕获异常即将退出 | 配合上条处理 |
| `unable to connect after trying N times` | `subsystem-CJEvHE2o.js → [ws]` | WS 连接多次重试均失败 | 检查防火墙/VPN |
| `EADDRINUSE :25555` | `gateway-cli-6Ksv5U_O.js` HTTP Server | 端口被占用，Server 无法监听 | `lsof -i :25555`，杀掉占用进程 |
| `ENOENT` / `SyntaxError` + 配置路径 | `gateway-cli-6Ksv5U_O.js` 配置加载 | workspace 配置文件缺失或损坏 | 重置 workspace 后重启 |
| `update available (latest): vX` | `subsystem-CJEvHE2o.js → gateway/update-check` | 存在新版本，当前版本有已知 Bug | `openclaw update` |

---

### Step 3 — 排查 mDNS 崩溃与网络状态（Case：原因 #4 / #5）

> **特征日志：** `no IPv4 address available on en0` + `Reached illegal state! IPv4 address changed from undefined to defined`
>
> **代码根因：** `@homebridge/ciao` 的 `MDNSServer.handleUpdatedNetworkInterfaces()` 在处理网卡 IP 从 `undefined` 变为有值时，触发了 `ERR_ASSERTION` 断言，属 **v2026.4.1 及以下版本的已知 Bug**，新版本已修复。

```bash
# 确认网卡 IP 是否已稳定
ifconfig en0 | grep 'inet '

# 确认飞书域名可达性
nslookup open.feishu.cn
curl -v --max-time 10 https://open.feishu.cn/open-apis/bot/v1/openclaw_bot/ping
```

| 排查结果 | 处理 |
|---------|------|
| en0 无 IPv4 | 重连 Wi-Fi，待 IP 稳定后再重启 Gateway |
| DNS 解析失败 | 切换 DNS 至 `8.8.8.8`，或联系网络管理员修复 |
| DNS 正常但 curl 超时 | VPN 或防火墙阻断，将 `*.feishu.cn` 加入直连白名单 |
| 日志有 `Reached illegal state` | 版本 ≤ v2026.4.1 的已知 Bug，执行 `openclaw update` |

---

### Step 4 — 排查 LaunchAgent 配置（Case：原因 #1 / #2）

```bash
# 查看 plist 配置
cat ~/Library/LaunchAgents/ai.openclaw.gateway.plist

# 验证 openclaw 二进制路径
which openclaw
file $(which openclaw 2>/dev/null || echo '/opt/homebrew/bin/openclaw')
```

重点检查 plist 中：
- `ProgramArguments[0]` 的 openclaw 路径是否真实存在
- `EnvironmentVariables.PATH` 是否包含 `/opt/homebrew/bin`（Apple Silicon Homebrew 路径）

若 plist 异常，重新生成：
```bash
openclaw service install
```

---

### Step 5 — 排查端口占用（Case：原因 #3）

```bash
lsof -i :25555
```

若有其他进程占用：
```bash
# 杀掉占用进程
kill -9 <PID>
# 重新拉起 Gateway
launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/ai.openclaw.gateway.plist
```

---

### Step 6 — 排查 workspace 配置损坏（Case：原因 #7）

```bash
# 检查关键配置文件是否存在且格式正常
cat ~/.openclaw/workspace/config.json | python3 -m json.tool > /dev/null && echo "JSON 格式正常" || echo "JSON 解析失败"
ls ~/.openclaw/workspace/
```

若配置文件损坏或缺失，通过 Web 端「重置 workspace」功能恢复，或手动执行：
```bash
# 还原默认 workspace（由 WEClawHelper 脚本提供）
bash ~/.weclawhelper/scripts/reset-openclaw.sh --workspace-only
```

---

## 六、所需日志清单

| 日志 | 位置 | 关键内容 |
|------|------|---------|
| Gateway 运行日志 | `/tmp/openclaw/openclaw-YYYY-MM-DD.log` | ERROR / WARN，含模块路径 |
| Gateway 启动日志 | `~/.openclaw/logs/gateway.log` | 进程启动阶段输出 |
| LaunchAgent 状态 | 命令输出 | `launchctl list \| grep openclaw`（含退出码） |

**一键收集命令（让用户粘贴执行，将输出发给 TSE）：**

```bash
echo "=== openclaw 版本 ===" && openclaw --version 2>/dev/null || echo "命令不存在"
echo "=== LaunchAgent 状态（含退出码）===" && launchctl list | grep openclaw
echo "=== 网络状态 ===" && ipconfig getifaddr en0
echo "=== 端口 25555 占用 ===" && lsof -i :25555
echo "=== ERROR/WARN 日志（最近 30 条）===" && \
  grep -h '"logLevelName":"ERROR"\|"logLevelName":"WARN"' /tmp/openclaw/*.log 2>/dev/null | tail -30
```

---

## 七、解决方案汇总

| 根因 | 涉及模块 | 解决方式 |
|------|---------|---------|
| 网络未就绪 / en0 无 IPv4 | `MDNSServer` / Channel init | 等待网络就绪后在 Web 端重新触发重启 |
| 飞书域名不可达 | `openclaw-lark` 插件 WS 连接 | 修复 DNS；或将 `*.feishu.cn` 加入 VPN 直连白名单 |
| mDNS 网卡 IP 变更崩溃（≤ v2026.4.1 已知 Bug） | `@homebridge/ciao → MDNSServer` | `openclaw update` 升级至 v2026.4.22+ |
| 端口 25555 被占用 | Gateway HTTP Server bind | `kill -9` 占用进程后重启 |
| LaunchAgent plist 损坏 / PATH 缺失 | `ai.openclaw.gateway.plist` | `openclaw service install` 重新生成 |
| workspace 配置文件损坏 | 配置加载模块 | Web 端「重置 workspace」或 `reset-openclaw.sh --workspace-only` |
| openclaw 命令不在 PATH | LaunchAgent 环境变量 | 补充 plist 中 `EnvironmentVariables.PATH` |

---

## 八、相关文档

- [ClawHive 安装与启动问题排障总览](./installation-triage.md)
- [Web 端安装 Claw 运行时报错"安装未启动"](./install-not-started-triage.md)
- [WEClawHelper 连接/注册/心跳排障](../weclawhelper/connection-triage.md)
- [ClawHive 错误码参考](../../error-codes/clawhive-errors.md)