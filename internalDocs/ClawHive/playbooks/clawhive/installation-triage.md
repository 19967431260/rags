# ClawHive（帝王蟹）安装与问题排查指导

> **文档类型：** 安装架构说明 + TSE 排障手册  
> **源码基准：** `agent-manager-core/scripts/claw/mac/`  
> **适用平台：** macOS（Intel / Apple Silicon）  
> **参考版本：** OpenClaw 默认安装版本 `2026.4.9`（源自 `weclaw-config.json`）  
> **重要约定：** 所有结论均以源码为依据；无源码支撑之处明确标注「**源码中未确认**」

---

## 一、系统架构与组件职责

### 1.1 组件全景

安装完成后，用户机器上运行以下组件（均来源于安装脚本的操作行为）：

```
用户机器
  ├── WEClawHelper Agent          （Go 二进制，常驻进程）
  │     职责：接收服务端指令、下发脚本、上报状态、生命周期管理
  │     安装位置：源码中未确认（二进制路径由 clawHive/scripts/ 打包决定）
  │     运行方式：macOS LaunchAgent 常驻（plist 名称源码中未确认）
  │     配置文件：~/.weclawhelper/config.json
  │     运行时目录：~/.weclawhelper/runtime/
  │
  ├── OpenClaw Gateway             （Node.js 进程，npm 全局安装）
  │     职责：本地 AI 网关，处理 Skill 执行、Channel 连接（飞书/企微/钉钉/POPO）、mDNS 广播
  │     安装位置：由 nvm 管理，路径为 $NVM_DIR/versions/node/<ver>/bin/openclaw
  │     运行方式：macOS LaunchAgent（ai.openclaw.gateway）
  │     plist 位置：~/Library/LaunchAgents/ai.openclaw.gateway.plist
  │     存活检测端口：18789（源自 restart.sh：GW_PORT=18789）
  │     工作目录：~/.openclaw/
  │
  ├── OpenClaw Extensions          （插件目录）
  │     安装位置：~/.openclaw/extensions/
  │     已知插件（来自安装脚本）：
  │       moltbot-popo-*.tar.gz       → ~/.openclaw/extensions/（POPO 插件）
  │       dingtalk-connector-*.tar.gz → ~/.openclaw/extensions/（钉钉插件）
  │       wecom-openclaw-plugin-*.tar.gz → ~/.openclaw/extensions/（企微插件）
  │       clawhive_plugins_v1.0.0.tar.gz → ~/.openclaw/extensions/（ClawHive 内置插件）
  │       weclawtrace-1.1.2.tgz       → ~/.openclaw/extensions/weclawtrace/（追踪插件）
  │
  ├── OpenClaw Workspace           （AI 上下文工作空间）
  │     位置：~/.openclaw/workspace/
  │     初始化来源：~/.weclawhelper/init-resource/workspace-default.tar.gz
  │     默认文件：IDENTITY.md / HEARTBEAT.md / MEMORY.md / BOOTSTRAP.md /
  │               USER.md / SOUL.md / AGENTS.md / TOOLS.md
  │
  └── OpenClaw SDK 软链接          （插件依赖）
        位置：~/.openclaw/node_modules/openclaw → <npm 全局 openclaw 包目录>
        作用：供 DingTalk / WeCom 等插件引用 openclaw SDK
```

### 1.2 依赖关系

```
WEClawHelper Agent
  └── 依赖 ~/.weclawhelper/config.json（clientType 配置）
  └── 依赖 ~/.weclawhelper/scripts/（所有运维脚本）
  └── 依赖 ~/.weclawhelper/plugins/（插件安装包）
  └── 依赖 ~/.weclawhelper/init-resource/（workspace 初始包）
  └── 依赖 ~/.weclawhelper/runtime/（运行时状态/锁文件）

OpenClaw Gateway
  └── 依赖 nvm（Node.js 版本管理）
  └── 依赖 Node.js ≥ v24（MIN_NODE_MAJOR=24，源自 install-openclaw.sh）
  └── 依赖 ~/.openclaw/workspace/（AI 上下文，启动时加载）
  └── 依赖 ~/.openclaw/extensions/（插件，启动时扫描）
  └── 依赖 ~/.openclaw/node_modules/openclaw（插件 SDK 软链接）
  └── 依赖 ~/Library/LaunchAgents/ai.openclaw.gateway.plist（开机自启）
  └── 依赖网络（Channel 连接：飞书/企微/钉钉域名）

nvm
  └── 安装路径：$HOME/.nvm/
  └── 初始化脚本：$HOME/.nvm/nvm.sh
  └── Node 24 路径：$HOME/.nvm/versions/node/<v24.x.x>/bin/
```

### 1.3 启动顺序

```
系统开机 / 用户登录
  │
  ▼
1. macOS LaunchAgent 拉起 WEClawHelper Agent
  │
  ▼
2. macOS LaunchAgent 拉起 OpenClaw Gateway（ai.openclaw.gateway）
      ├── 加载 workspace 配置
      ├── 扫描 extensions/ 目录并加载插件
      ├── 启动 mDNS/Bonjour 广播（依赖本地网卡 IPv4）
      ├── 绑定本地端口 18789（存活检测端口）
      └── 初始化 Channel 连接（飞书/企微/钉钉等，依赖网络）
  │
  ▼
3. WEClawHelper 轮询 check-openclaw.sh：
      通过 nc -z 127.0.0.1 18789 + pgrep -f 'openclaw.*gateway' 判定存活
      （源自 check-openclaw.sh 第 151–154 行）
  │
  ▼
4. WEClawHelper 上报 Gateway 状态至服务端
```

---

## 二、安装流程详解

### 2.1 安装触发路径

| 触发方式 | 入口 |
|---------|------|
| Web 端蟹蟹安装向导 | 后端下发 `install-client.sh` → 判断 `CLIENT_TYPE` → 执行 `install-openclaw.sh` 或 `install-lobsterai.sh` |
| WEClawHelper Agent | RPC 接收服务端 install 指令后调用安装脚本 |

### 2.2 安装脚本入口

**主安装脚本：** `~/.weclawhelper/scripts/install-openclaw.sh`  
（部署来源：`agent-manager-core/scripts/claw/mac/install-openclaw.sh`）

### 2.3 安装步骤全流程

```
[Step 1] 环境检查（CURRENT_STEP=env_check，进度 5%）
  ├── 检查是否为 macOS（非 Darwin 直接 fail）
  ├── 检查磁盘空间（df -g $HOME，< 10GB 则 fail）
  └── 检查 / 安装 Xcode CLT（xcode-select -p）
        失败判定：softwareupdate 找不到 CLT label → fail

[Step 2] nvm 检测与安装（CURRENT_STEP=nvm_check，进度 20%）
  ├── 检测 nvm 是否由 root 安装（stat -f '%Su' $NVM_DIR/nvm.sh）
  │     root 安装 → 弹框请求 sudo 密码，卸载 root nvm，清理 ~/.npmrc prefix/globalconfig
  ├── 检测 Node.js 来源：nvm / brew / other / none
  ├── 检测 Node.js 版本（要求 major ≥ 24）
  │     不满足 → nvm install 24；满足但非 nvm → 重新用 nvm 安装（强制隔离）
  └── 写入 nvm 初始化到 ~/.zshrc（标记行：# Load nvm if available）

[Step 3] 安装 OpenClaw（CURRENT_STEP=install_openclaw，进度 70%）
  ├── 默认模式：npm install -g openclaw@<version>
  │     版本来源：weclaw-config.json → defaultOpenclawVersion → 当前值 "2026.4.9"
  │     fallback：硬编码 "2026.4.9"（install-openclaw.sh 第 47 行）
  ├── 可选官方模式（--use-official-install-script）：
  │     curl -fsSL https://openclaw.ai/install.sh | bash
  ├── 安装前置依赖：npm install -g node-addon-api node-gyp
  └── 安装成功判定：command -v openclaw 有输出 + openclaw --version 正常返回

[Step 4] 配置开机自启（CURRENT_STEP=autostart，进度 85%）
  ├── openclaw gateway install（注册 LaunchAgent plist）
  └── openclaw gateway status（验证注册结果）

[Step 4.1] 安装后自检（CURRENT_STEP=postcheck，进度 90%）
  ├── command -v openclaw（必须通过，否则 fail）
  ├── openclaw --version
  ├── openclaw status
  └── openclaw health --json

[Step 5] 安装插件（进度 95%）
  ├── POPO 插件：~/.weclawhelper/plugins/moltbot-popo-*.tar.gz → ~/.openclaw/extensions/
  ├── DingTalk 插件：~/.weclawhelper/plugins/dingtalk-connector-*.tar.gz → ~/.openclaw/extensions/
  ├── WeCom 插件：~/.weclawhelper/plugins/wecom-openclaw-plugin-*.tar.gz → ~/.openclaw/extensions/
  └── ClawHive 内置插件：~/.weclawhelper/plugins/clawhive_plugins_v1.0.0.tar.gz → ~/.openclaw/extensions/
        注意：插件找不到时仅 warn，不 fail，不阻塞安装

[Step 6] 修复 OpenClaw SDK 依赖（CURRENT_STEP=repair_openclaw_sdk，进度 97%）
  └── 创建软链接：~/.openclaw/node_modules/openclaw → <npm 全局 openclaw 包>
        失败时仅 warn："DingTalk/WeCom 插件可能启动失败"

[Step 7] 初始化 workspace（进度 97%）
  └── tar -xzf ~/.weclawhelper/init-resource/workspace-default.tar.gz → ~/.openclaw/workspace/

[Step 7.1] 初始化预置 Skills
  └── unzip ~/.weclawhelper/skills/*.zip → ~/.openclaw/workspace/skills/

[Step 7.2] 安装 weclawtrace（CURRENT_STEP=install_clawtrace，进度 98%）
  └── ~/ .weclawhelper/plugins/weclawtrace-1.1.2.tgz → ~/.openclaw/extensions/weclawtrace/

[完成] _on_exit 回调
  └── status=success → status.json: {"status":"success","progress":100}
  └── status=fail    → status.json: {"status":"fail","stderr":"<last 2000 chars>"}
```

### 2.4 关键配置文件

| 配置文件 | 位置 | 来源 | 关键字段 |
|---------|------|------|---------|
| WEClawHelper 配置 | `~/.weclawhelper/config.json` | WEClawHelper 首次启动写入 | `clientType`（openclaw/lobsterai） |
| OpenClaw 版本配置 | `~/.weclawhelper/scripts/weclaw-config.json` | 随脚本下发 | `defaultOpenclawVersion`（当前值 `"2026.4.9"`） |
| nvm 初始化 | `~/.zshrc` | install-openclaw.sh 写入 | `# Load nvm if available` |
| LaunchAgent plist | `~/Library/LaunchAgents/ai.openclaw.gateway.plist` | `openclaw gateway install` 写入 | 源码中未确认 plist 完整内容，由 openclaw 命令生成 |
| env-init.sh | `~/.weclawhelper/scripts/env-init.sh` | 随脚本下发 | nvm 加载、Node 24 切换、`CLIENT_CONTROL_*` 变量、`WECLAWHELPER_*` 变量 |

### 2.5 成功 / 失败判断点

| 步骤 | 成功标志 | 失败标志 |
|------|---------|---------|
| 环境检查 | `macOS ✓`；磁盘 ≥ 10GB；xcode-select -p 有输出 | `fail "此脚本仅支持 macOS"` / `fail "磁盘空间不足"` |
| nvm 安装 | `command -v nvm` 有输出 | `fail "nvm 安装失败"` |
| Node.js 安装 | `node -v` major ≥ 24 | `fail "Node.js 不满足要求 (≥24)"` |
| OpenClaw 安装 | `command -v openclaw` 有输出 | `fail "npm install -g ${NPM_SPEC} 失败"` |
| 开机自启 | `openclaw gateway install` 返回 0 | `warn "配置开机自启动失败"` |
| 安装后自检 | `command -v openclaw` 有输出 | `fail "安装后自检失败：openclaw 命令不可用"` |
| 插件安装 | tar/unzip 解压成功 | `warn` 但不 fail（不阻塞） |
| SDK 软链接 | ln -s 成功 | `warn` 但不 fail |
| 整体完成 | `status.json: {"status":"success","progress":100}` | `status.json: {"status":"fail","stderr":"..."}` |

---

## 三、日志目录与归属

### 3.1 日志文件清单（有源码依据）

| 日志文件 | 归属组件 | 内容 | 源码依据 |
|---------|---------|------|---------|
| `/tmp/openclaw-install/progress.jsonl` | 安装脚本 | 安装全过程逐步骤事件（JSONL，每行一个事件） | `install-openclaw.sh:88` |
| `/tmp/openclaw-install/status.json` | 安装脚本 | 当前安装状态快照（最新一步，原子写入） | `install-openclaw.sh:89` |
| `/tmp/openclaw-install/install.pid` | 安装脚本 | 安装进程 PID（用于判断是否在运行） | `install-openclaw.sh:90` |
| `/tmp/openclaw-install/current-session.json` | 安装脚本 | 安装会话 ID（sessionId、clientType、pid） | `install-openclaw.sh:91` |
| `~/.weclawhelper/runtime/client-control-trace.log` | WEClawHelper Agent | 操作锁的获取/释放/冲突事件 | `env-init.sh:52-53` |
| `~/.weclawhelper/runtime/client-control-conflicts.log` | WEClawHelper Agent | 并发操作冲突记录 | `env-init.sh:52` |
| `/tmp/openclaw/*.log` | OpenClaw Gateway | Gateway 运行日志（JSON 格式，按日期分文件） | `restart.sh:37` 中的提示信息 |

> **注意：** LobsterAI 安装时使用 `/tmp/lobsterai-install/` 目录（源自 `install-progress.sh:25`）。

### 3.2 优先排查顺序

```
1. /tmp/openclaw-install/status.json        ← 安装失败时首先查看，含 stderr 字段
2. /tmp/openclaw-install/progress.jsonl     ← 逐步骤完整事件，定位失败 step
3. /tmp/openclaw/*.log                      ← Gateway 无法启动时查看
4. ~/.weclawhelper/runtime/client-control-trace.log  ← 操作冲突/锁问题时查看
5. launchctl list | grep openclaw           ← 进程状态、退出码
```

---

## 四、常见安装 / 启动 / 访问异常排查

---

### 异常 1：安装卡住或长时间无进度

**现象**  
Web 端安装向导进度条停止，后端持续返回 `status=running` 但 progress 不变。

**可能原因**  
- nvm 安装时网络超时（从 `raw.githubusercontent.com` 下载 nvm install.sh）
- `npm install -g openclaw` 下载超时（npm registry 不可达）
- root npm 修复时弹出 osascript 密码框，用户未响应

**检查项**  

```bash
# 查看当前安装步骤和进度
cat /tmp/openclaw-install/status.json

# 查看完整事件日志
cat /tmp/openclaw-install/progress.jsonl

# 确认安装进程是否仍存活
cat /tmp/openclaw-install/install.pid
kill -0 $(cat /tmp/openclaw-install/install.pid 2>/dev/null) && echo "进程存活" || echo "进程已退出"
```

**关键日志字段**  

| 字段 | 含义 |
|------|------|
| `step` | 当前所处安装步骤（`env_check` / `nvm_check` / `install_openclaw` 等） |
| `progress` | 当前百分比（0–100） |
| `status` | `running` / `success` / `fail` |
| `stderr` | 失败时含最后 2000 字节的 stderr 内容 |

**判断标准**  
- `step=nvm_check` 且 progress 停在 20% 超过 5 分钟 → 网络问题（nvm 下载超时）
- `step=install_openclaw` 且 progress 停在 70% 超过 10 分钟 → npm 下载超时

**处理建议**  
1. 确认网络可访问 `raw.githubusercontent.com` 和 `registry.npmjs.org`
2. 如因密码弹框未响应：引导用户在终端执行 `bash ~/.weclawhelper/scripts/install-openclaw.sh` 手动完成安装
3. 已完成部分安装时（nvm 已装、Node 已装），可加 `--version <ver>` 直接跳到 Step 3

**升级/研发边界**  
当前 nvm 固定从 `https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh` 下载（`install-openclaw.sh:637`），网络受限环境无镜像源 fallback——属产品问题，需升级脚本支持国内镜像源。

---

### 异常 2：安装失败，status=fail，stderr 含 npm 权限错误

**现象**  
`status.json` 中 `status=fail`，`stderr` 含 `EACCES` 或 `permission denied`。

**可能原因**  
- npm 由 root 安装（`stat -f '%Su' $(which npm)` 返回 `root`）
- `~/.npm` 缓存目录属于 root
- `~/.npmrc` 中有 `prefix` 或 `globalconfig` 配置干扰 nvm

**检查项**  

```bash
# 检查 npm 所有者
stat -f '%Su' $(which npm 2>/dev/null)

# 检查 ~/.npm 所有者
stat -f '%Su' ~/.npm 2>/dev/null

# 检查 ~/.npmrc 中的冲突配置
grep -E '^(prefix|globalconfig)' ~/.npmrc 2>/dev/null

# 查看 stderr 详情
cat /tmp/openclaw-install/status.json | python3 -c "import sys,json; d=json.load(sys.stdin); print(d.get('stderr',''))"
```

**日志**  
`/tmp/openclaw-install/status.json` → `stderr` 字段  
`/tmp/openclaw-install/progress.jsonl` → `step=install_openclaw` 附近的 `fail` 事件

**判断标准**  
- `stat` 返回 `root` + `stderr` 含 `EACCES` → 确认是 root npm 问题
- `~/.npmrc` 含 `prefix=` 行 + nvm 报 exit 11 → 确认是 npmrc 冲突

**处理建议**  
1. 引导用户手动修复：
   ```bash
   # 修复 ~/.npm 所有权
   sudo chown -R $(id -u):$(id -g) ~/.npm
   # 清除 npmrc 冲突配置
   sed -i.bak '/^prefix[[:space:]]*=/d; /^globalconfig[[:space:]]*=/d' ~/.npmrc
   ```
2. 修复后重新触发安装

**升级/研发边界**  
脚本的自动修复逻辑（`_check_root_npm`）依赖 `osascript` 弹框获取密码，在无图形界面的环境（如 SSH）无法工作——属已知局限，无需升级，需 TSE 协助手动修复。

---

### 异常 3：安装成功但 Gateway 无法启动（check-openclaw 返回 stopped）

**现象**  
`check-openclaw.sh` 返回 `{"status":"stopped",...}`。

**可能原因**  
1. LaunchAgent plist 中 `openclaw` 路径不在 PATH（`EnvironmentVariables.PATH` 缺少 nvm bin 目录）
2. 端口 18789 被占用，Gateway bind 失败
3. Gateway 启动时 workspace 配置解析报错（ENOENT / SyntaxError）
4. 启动时网卡无 IPv4，mDNS 初始化卡住

**检查项**  

```bash
# 1. 确认 openclaw 命令存在
which openclaw
openclaw --version

# 2. 查看 LaunchAgent 状态（含退出码）
launchctl list | grep openclaw

# 3. 检查端口占用
nc -z 127.0.0.1 18789 && echo "端口已被占用" || echo "端口空闲"

# 4. 查看 Gateway 日志
tail -50 /tmp/openclaw/*.log

# 5. 检查 workspace 配置文件
ls ~/.openclaw/workspace/
cat ~/.openclaw/workspace/config.json 2>/dev/null | python3 -m json.tool > /dev/null && echo "JSON 正常" || echo "JSON 异常"
```

**关键日志**  
- `/tmp/openclaw/*.log`：Gateway 运行日志（JSON 格式）
- `launchctl list` 输出的 `LastExitStatus` 字段（check-openclaw.sh 第 163 行读取此字段）

**存活判定逻辑（源自 check-openclaw.sh:151–154）**  
```
端口检测：nc -z 127.0.0.1 18789
进程检测：pgrep -f 'openclaw.*gateway'
两者同时满足 → status=running
否则          → status=stopped
```

**处理建议**  

| 根因 | 处理 |
|------|------|
| openclaw 不在 PATH | 检查 plist `EnvironmentVariables.PATH` 是否含 nvm bin 目录；执行 `openclaw service install` 重新生成 plist |
| 端口 18789 被占用 | `lsof -i :18789`，kill 占用进程后重启 Gateway |
| workspace 配置损坏 | Web 端「重置 workspace」或手动执行 `reset-openclaw.sh` |
| mDNS 初始化卡住（网络未就绪） | 等待网络就绪（`ipconfig getifaddr en0` 有输出）后重启 |

**升级/研发边界**  
check-openclaw.sh 使用 `nc -z` 代替 `lsof` 做端口探测（`check-openclaw.sh:151` 注释说明：lsof 在 macOS 扫描全量 fd 可能耗时数秒）——当前实现合理。Gateway 日志路径 `/tmp/openclaw/` 在重启后可能被系统清理（`/tmp` 为临时目录）——属已知局限，建议研发考虑持久化日志路径。

---

### 异常 4：Gateway 重启超时（reset-openclaw.sh 输出 `[✗] 重启超时`）

**现象**  
执行 `reset-openclaw.sh` 或 Web 端重启后，终端或日志出现：  
`[✗] 重启超时，请检查日志: tail -f /tmp/openclaw/*.log`

**可能原因**  
（参见 `restart.sh:37`，超时时限为 15 秒，每秒检测一次）  
1. Gateway 进程未被 LaunchAgent 拉起（plist 问题）
2. 端口 18789 未监听（启动后崩溃，或端口被占用）
3. mDNS 组件崩溃（已知 Bug，≤ v2026.4.1）：`AssertionError: Reached illegal state! IPv4 address changed from undefined to defined`

**检查项**  

```bash
# restart.sh 中的就绪判定逻辑（源自 restart.sh:25–28）：
# port_pid=$(lsof -nP -iTCP:18789 -sTCP:LISTEN)
# pgrep_pid=$(pgrep -f 'openclaw.*gateway')
# 两者均有值 → 就绪

# 手动复现判定
lsof -nP -iTCP:18789 -sTCP:LISTEN 2>/dev/null
pgrep -f 'openclaw.*gateway'

# 查看 Gateway 启动日志
tail -f /tmp/openclaw/*.log
grep -Ei 'ENOTFOUND|AssertionError|Unhandled|no IPv4|EADDRINUSE' /tmp/openclaw/*.log 2>/dev/null
```

**日志关键字速查**  

| 关键字 | 含义 |
|--------|------|
| `no IPv4 address available on en0` | 网卡无 IP，mDNS 初始化挂起 |
| `ENOTFOUND open.feishu.cn` | 飞书域名不可达，Channel init 阻塞 |
| `Reached illegal state! IPv4 address changed from undefined to defined` | mDNS 崩溃，已知 Bug（≤ v2026.4.1） |
| `EADDRINUSE :18789` | 端口被占用 |

**处理建议**  
1. 网络未就绪 → 等待网络就绪（`ipconfig getifaddr en0` 有输出）后重试
2. mDNS 崩溃（≤ v2026.4.1）→ `openclaw update` 升级
3. 端口占用 → `lsof -i :18789`，kill 后重启

**升级/研发边界**  
restart.sh 超时时限硬编码为 15 秒（`seq 1 15`，源自 `restart.sh:24`），对于性能较弱的机器可能不足——属已知局限，建议研发支持通过环境变量自定义超时时限。

---

### 异常 5：安装进度查询返回 `status=not_started`

**现象**  
Web 端安装向导弹出：`安装失败：安装未启动，请先执行 install-openclaw.sh 或 install-lobsterai.sh`

**可能原因**  
（源自 `install-progress.sh:237–251`）  
1. `STATUS_FILE` 不存在：安装脚本从未启动（指令下发失败）
2. sessionId 不匹配：`status.json` 中 sessionId ≠ `current-session.json` 中 sessionId（旧会话遗留）
3. TTL 过期：`status.json` 修改时间距今超过 900 秒（`INSTALL_PROGRESS_SESSION_TTL_SECONDS=900`，`install-progress.sh:26`）

**检查项**  

```bash
# 检查进度文件是否存在
ls -la /tmp/openclaw-install/
cat /tmp/openclaw-install/status.json
cat /tmp/openclaw-install/current-session.json

# 检查 sessionId 是否一致
status_session=$(cat /tmp/openclaw-install/status.json 2>/dev/null | grep -o '"sessionId":"[^"]*"' | cut -d'"' -f4)
current_session=$(cat /tmp/openclaw-install/current-session.json 2>/dev/null | grep -o '"sessionId":"[^"]*"' | cut -d'"' -f4)
echo "status sessionId: $status_session"
echo "current sessionId: $current_session"

# 检查 status.json 文件年龄
echo "文件年龄（秒）: $(($(date +%s) - $(stat -f '%m' /tmp/openclaw-install/status.json 2>/dev/null || echo 0)))"
```

**判断标准**  
- 文件不存在 → 安装脚本未执行，排查 WEClawHelper Agent 连接
- sessionId 不一致 → 旧会话遗留，清理后重新安装
- 文件年龄 > 900 秒 → TTL 过期，重新安装

**处理建议**  
```bash
# 清理进度目录后在 Web 端重新触发安装
rm -rf /tmp/openclaw-install/
```

---

### 异常 6：插件无法使用（Channel 连接失败）

**现象**  
OpenClaw Gateway 运行中，但飞书/企微/钉钉/POPO 等 Channel 无法收发消息。

**可能原因**  
1. SDK 软链接未创建（`~/.openclaw/node_modules/openclaw` 不存在或指向错误）
2. 插件 tar 包未解压（安装时仅 warn）
3. 外部 Channel 域名不可达（网络/防火墙）

**检查项**  

```bash
# 检查 SDK 软链接
ls -la ~/.openclaw/node_modules/openclaw
# 应为软链接，指向 npm 全局 openclaw 包目录

# 检查插件目录
ls -la ~/.openclaw/extensions/

# 检查 Gateway 日志中的 Channel 连接错误
grep -i 'ENOTFOUND\|connect\|channel\|plugin\|extension' /tmp/openclaw/*.log 2>/dev/null | tail -20
```

**处理建议**  

| 根因 | 处理 |
|------|------|
| SDK 软链接缺失 | 手动执行安装脚本中的 `ensure_openclaw_sdk_link` 逻辑：`ln -s $(npm root -g)/openclaw ~/.openclaw/node_modules/openclaw` |
| 插件目录为空 | 确认 `~/.weclawhelper/plugins/` 下有对应 tar 包，手动解压：`tar -xzf ~/.weclawhelper/plugins/<plugin>.tar.gz -C ~/.openclaw/extensions/` |
| 外部 Channel 不可达 | 检查防火墙，放行对应 Channel 域名 |

**升级/研发边界**  
插件安装失败时仅 warn 不 fail（`install-openclaw.sh:1030-1033`），用户安装完成后才发现插件缺失——建议研发在安装完成报告中明确列出各插件安装状态。

---

## 五、运维快速命令

```bash
# 查看当前安装状态
cat /tmp/openclaw-install/status.json

# 实时跟踪安装进度
bash ~/.weclawhelper/scripts/install-progress.sh --watch

# 检查 OpenClaw 存活状态
bash ~/.weclawhelper/scripts/check-openclaw.sh

# 重启 Gateway
bash ~/.weclawhelper/scripts/restart.sh

# 重置 workspace 并重启（reset-openclaw.sh 源码流程：清空→解压→调用 restart.sh）
bash ~/.weclawhelper/scripts/reset-openclaw.sh

# 检查 LaunchAgent 状态（含退出码）
launchctl list | grep openclaw

# 查看 Gateway 实时日志
tail -f /tmp/openclaw/*.log

# 一键收集诊断信息（让用户执行后提供输出）
echo "=== openclaw 版本 ===" && openclaw --version 2>/dev/null || echo "命令不存在"
echo "=== node 版本 ===" && node -v 2>/dev/null || echo "node 不存在"
echo "=== nvm 状态 ===" && source ~/.nvm/nvm.sh 2>/dev/null && nvm current || echo "nvm 未加载"
echo "=== LaunchAgent ===" && launchctl list | grep openclaw
echo "=== 端口 18789 ===" && nc -z 127.0.0.1 18789 && echo "监听中" || echo "未监听"
echo "=== 安装状态 ===" && cat /tmp/openclaw-install/status.json 2>/dev/null || echo "无安装记录"
echo "=== Gateway 错误日志 ===" && grep -h '"logLevelName":"ERROR"' /tmp/openclaw/*.log 2>/dev/null | tail -10 || echo "无日志"
```

---

## 六、源码依据索引

| 结论 | 源码文件 | 行号 |
|------|---------|------|
| 最低 Node.js 版本要求 v24 | `mac/install-openclaw.sh` | 34 |
| 磁盘空间要求 ≥ 10GB | `mac/install-openclaw.sh` | 490–492 |
| 进度文件目录 `/tmp/openclaw-install/` | `mac/install-openclaw.sh` | 86–91 |
| 安装 TTL 默认 900 秒 | `mac/install-progress.sh` | 26 |
| `not_started` 返回逻辑（SessionId 校验） | `mac/install-progress.sh` | 196–225 |
| `not_started` 消息文案 | `mac/install-progress.sh` | 237 |
| OpenClaw 默认安装版本 `2026.4.9` | `mac/weclaw-config.json` | 2 |
| 版本配置读取逻辑（fallback）| `mac/install-openclaw.sh` | 37–52 |
| nvm 版本固定 `v0.40.1` | `mac/install-openclaw.sh` | 637 |
| root npm 检测与修复逻辑 | `mac/install-openclaw.sh` | 414–464 |
| node-addon-api / node-gyp 前置安装 | `mac/install-openclaw.sh` | 915–926 |
| 插件安装目录 `~/.openclaw/extensions/` | `mac/install-openclaw.sh` | 1027, 1052, 1076, 1099 |
| SDK 软链接路径 `~/.openclaw/node_modules/openclaw` | `mac/install-openclaw.sh` | 359 |
| workspace 路径 `~/.openclaw/workspace/` | `mac/install-openclaw.sh` | 1124 |
| workspace 默认包路径 | `mac/reset-openclaw.sh` | 28 |
| OpenClaw 存活检测端口 `18789` | `mac/restart.sh` | 13；`mac/check-openclaw.sh` | 151 |
| 存活判定：nc + pgrep 双重检测 | `mac/check-openclaw.sh` | 151–156 |
| LaunchAgent 搜索路径顺序 | `mac/check-openclaw.sh` | 113–118 |
| launchctl PID 判定逻辑 | `mac/check-openclaw.sh` | 162–168 |
| restart.sh 超时时限 15 秒 | `mac/restart.sh` | 24 |
| 重启就绪判定：lsof + pgrep | `mac/restart.sh` | 25–28 |
| nvm 初始化写入标记行 | `mac/install-openclaw.sh` | 597 |
| env-init.sh 中 CLIENT_CONTROL_* 变量定义 | `mac/env-init.sh` | 50–53 |
| client_control 锁目录路径 | `mac/env-init.sh` | 50 |
| WEClawHelper config 路径 | `mac/env-init.sh` | 48 |
