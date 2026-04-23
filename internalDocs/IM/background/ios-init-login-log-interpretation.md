# Evidence Card: iOS 初始化与登录日志解读

## 定位
这是 **iOS IM 初始化/登录链路的日志阅读地图**。核心价值不是告诉排障人员“下一步一定怎么修”，而是帮助把日志现象定位到具体流程阶段，并据此提出更准确的下一轮追问或归因方向。

## 适用场景
- iOS 端登录失败、自动登录异常、频繁重连、切网后状态异常。
- 想判断问题是出在 SDK 初始化、长连接建立、登录请求、同步阶段还是网络切换。
- 想区分“自动登录会持续重试”的错误与“会立即回调业务层失败”的错误。

## 流程证据地图

### 1. 初始化阶段
文档列出的初始化锚点包括：
- `SDK init begin` / `SDK init end`
- 私有化 `serverSetting` 读取
- 日志清理 `clean log cache begin max days`
- `SDK started`
- 打印 appkey、device id、session id、server setting、sdk config、root sdk attributes
- `queryLbs`
- 设备信息/APM/APNS token 上报

**可证明什么**
- SDK 是否正常启动。
- 是否加载了私有化配置、数据目录、版本信息。
- 是否进入 LBS 和设备信息上报阶段。

**主 skill 可据此追问**
- 是否使用了私有化部署/`nim_server.conf`。
- 是否初始化时就报错，还是初始化成功后登录失败。

### 2. 手动登录与自动登录的差异
文档明确区分：
- **手动登录**：设置 60 秒超时 -> 建链成功 -> 发起登录 -> 登录成功 -> 创建 manager -> 打开数据库。
- **自动登录**：检查本地账号密码 -> 建链 -> 登录成功；若失败，部分错误会自动重试。

**重要语义**
- 首次安装或切换账号时更适合手动登录。
- 日常启动更适合自动登录。
- `logout` 会销毁 manager 并关闭数据库。

### 3. 建链成功的证据
典型锚点：
- `try to connect link ...`
- `begin to connect`
- `check available link: ... result:1`
- `Begin to Connect Link Server ...`
- `set login step: 2`（LinkOK）

**可证明什么**
- 如果连这些都没有或始终建链失败，优先判断为 **网络/App Link/链路连通性问题**，而不是账号密码问题。

### 4. 登录请求与成功证据
典型锚点：
- `im tags ...`
- `set login step: 4`
- `raise login task id ... via WIFI`
- `Send Packet : SID 1 CID 1 ...`
- `login success + accid`
- `receive login callback ... code 200`
- `login ok`
- `set login step: 5`

**可证明什么**
- 已经从“仅建链”进入“真正登录”。
- 出现 `login success + accid` 基本可判定服务端登录成功。

### 5. 登录后的同步阶段
典型锚点：
- `begin to sync:`
- 一系列 `tag/value`
- `Send Packet : SID 5 CID 1 SER 2`
- `sync completed 200`

**可证明什么**
- 登录成功后是否卡在同步。
- 若用户说“能登录但会话/群资料不全”，这里是关键观察点。

### 6. 失败与自动重试语义
文档明确指出自动登录失败后会自动重试的错误包括：
- 415 网络连接错误
- 408 请求超时
- 999 打包错误
- 998 解包错误
- 398 需要重新尝试登录
- 5xx

**可证明什么**
- 某些错误即使当下失败，也不代表流程结束；SDK 可能继续自动重连重登。
- 若设置了 `maxAutoLoginRetryTimes`，超过上限后才真正向业务层报失败。

### 7. 重复调用登录的风险
文档特别提醒：短时间内未等上一次登录返回结果就再次登录，SDK 可能先断开再重连，并重新触发缓存的 API 调用，进而造成：
- 连接反复断开/重建
- 调用错乱
- 参数异常

**这条对主 skill 很有价值**
- 当日志出现反复 `connect -> disconnect -> connect`，不能机械判定为纯网络问题；还要问业务层是否重复触发登录。

### 8. 网络切换与心跳
网络切换日志：
- `net device changed: Cellular state connected`
- `net device changed: No Connection state connected`
- `set login step: 10`

心跳与长连接异常：
- `Socket Read Idle (App Link)`
- `Socket Write Idle (App Link)`
- 心跳超时后关闭连接并重连

**可证明什么**
- 切网触发的重连是预期行为。
- 若长时间无读写后开始心跳，再关闭连接重连，更偏网络质量/App Link 层问题。

## 建议给主 skill 的使用方式
1. 先把日志归到下列阶段之一：
   - 初始化未完成
   - 建链失败
   - 建链成功但登录失败
   - 登录成功但同步异常
   - 自动重试中
   - 网络切换/心跳触发重连
2. 根据阶段决定追问：
   - 是否首次安装/切账号
   - 是否手动登录还是自动登录
   - 是否短时间重复点登录
   - 故障发生时是否切网/断网
   - 是否拿到 `onAutoLoginFailed` 回调及错误码
3. 这张卡最适合和真实日志片段一起用；脱离日志单独使用时，只能提供一般性方向。

## 局限与注意事项
- 文中大量细节绑定旧版实现与内部 tag 文档，需防止把历史行为当成当前版本铁律。
- 它更像“诊断路线图”，不是面向客户的最终答复模板。
