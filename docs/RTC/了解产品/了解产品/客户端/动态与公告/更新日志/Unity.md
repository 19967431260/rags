本文介绍了网易云信音视频通话（NERTC）为 Unity 引擎提供的 SDK 的更新日志，后续简称 NERTC Unity SDK。具体功能请前往 [下载 SDK 体验](https://doc.yunxin.163.com/nertc/resource?platform=unity) 和 [查看 API 文档](https://doc.yunxin.163.com/nertc/client-apis/jM5Nzg1NDA?platform=unity)。

## 纯音频

### V5.4.128 (2024-09-26)

V5.4.128 版本为纯音频版本，相较上一个纯音频版本 5.4.124，主要变更为：

- 引入语音消息审核功能，增强内容管理。
- 扩展平台兼容性，新增 XBox 与 HarmonyOS 设备支持。如有需求，可 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。
- 提升系统性能，优化用户体验。

### V5.4.124 (2024-05-24)

V5.4.124 版本为纯音频版本，相较上一个纯音频版本 5.4.109，主要变更为：

- 新增 [语音消息](https://doc.yunxin.163.com/nertc/guide/zk4NDY0NjI?platform=unity)。

### V5.4.109 (2023-10-12)

V5.4.109 版本为纯音频 SDK 版本，主要新增特性如下：

- 新增 API

    <div style="width:200px">API</div> | 说明 |
    --- | --- |
    [`PauseAudio`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/classnertc_1_1_i_rtc_engine.html#afea75f4f5a8ae1130924120d043509fb) | 当应用退至后台时，您可以调用该接口暂停音频输入和输出 |
    [`ResumeAudio`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/classnertc_1_1_i_rtc_engine.html#a0705453775b23977723d88034ee353e7) | 当应用退至前台时，恢复音频输入和输出
    [`IsInChannel`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/classnertc_1_1_i_rtc_engine.html#a592588214a911698ac1e0ce4f35ec9ae) | 检查用户是否已经在房间内

- API 变更

    <div style="width:200px">API</div> | 说明 |
    --- | --- |
    [`JoinChannel`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/classnertc_1_1_i_rtc_engine.html#ac2389c30485d409489442caf4268b246) | `channelOptions` 参数中新增 `teamID`、`mode` 和 `audibleDistance` 参数，用于设置范围语音的小队 ID、范围语音的语音模式和语音接收范围。 |
    [`SwitchChannel`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/classnertc_1_1_i_rtc_engine.html#aecc20656761a5c86188dca6aa8f1c433) | `channelOptions` 参数中新增 `teamID`、`mode` 和 `audibleDistance` 参数。<br>移除 `SwitchChannelEx` 接口。

- 改进优化
    - 优化非中国大陆地区的用户体验
    - 优化音频体验
    - 提升稳定性

### V5.4.105 (2023-08-16)

V5.4.105 版本为纯音频 SDK 版本，主要新增特性如下：

- 新增特性
    序号 | 新增特性 | 特性描述 | 相关文档
    ---- | ---- | ---- | ----
    1 | 范围语音 | 在一个 RTC 房间内，用户可以与一定距离内的其他用户进./行实时语音通话，支持 **仅小队** 或 **所有人** 的语音模式。它可以让玩家在游戏中实时交流，从而更好地协调战术和策略。 | [范围语音](https://doc.yunxin.163.com/nertc/guide/jA2MzkzOTk?platform=unity) |
    2 | 设置混音文件的音调 | 支持调整伴音和音效的音调。在 K 歌场景中，为了使歌曲更适合主播的声线音域，可以升高或降低伴奏的音阶。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/TY2MzU0ODc?platform=unity) |
    3 | 音频裸流传输 | 支持音频裸流传输，您可以向 NERTC SDK 提供自定义格式的音频编码数据，并由 NERTC SDK 进行推流。 | <a href="https://doc.yunxin.163.com/nertc/guide/Tk5NjM4MjI?platform=unity" target="_blank">音频裸流传输</a> |
    4 | 设置音频订阅优先级 | 支持优先订阅远端某用户发布的音频流。在 ASL 策略下，即在服务器线路上选择最清晰的三条音频流传输给本地用户时，本地用户设置优先订阅一个成员的音频流后，即使该成员的说话音量较低或不够清晰，本地用户仍能接收到该指定成员的音频流。 | [设置音频订阅优先级](https://doc.yunxin.163.com/nertc/guide/jE4MjY0MDE?platform=unity) |
    5 | 音频循环缓存录制 | 在原有的支持实时写文件基础上，支持设置仅录制最近一段时间内的音频数据，最高为 15 分钟。 | [客户端音频录制](/https://doc.yunxin.163.com/nertc/guide/DIyNDE2ODk?platformId=50002) |
    6 | 云代理 | 支持使用云代理服务穿透防火墙限制，使用固定 IP 连接到网易云信服务器。 | [云代理](https://doc.yunxin.163.com/nertc/guide/zU5NTIzMDc?platform=unity2) |
    7 | 音频辅流 | 支持通过辅流输入伴音文件或自定义音频源。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/TY2MzU0ODc?platform=unity)

- 新增 API

    V5.4.105 版本新增的接口请参考 [Unity SDK API 参考（纯音频）](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/audioOnly/html/index.html)。

- 升级必看

    如果需要从历史 v3 或 v4 版本升级至 V5.4.105 版本，请先联系网易云信技术支持工程师进行评估。直接升级可能引发非预期的错误。

### V3.9.902 (2022-07-11)

- 问题修复

    1. 修复空间音效距离衰减的异常增益问题。
    2. 修复空间音效 3D 方位信息更新的问题。
    3. 修复已知崩溃。

- API 变更

    <div style="width:200px">API</div> | 说明 |
    --- | --- |
    [`enableSpatializer`](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/html/interface_n_e_r_t_c_1_1_i_rtc_engine.html#a24c81174b2b6e9dc9889be7698ae28b7) | 废弃 `applyToTeam` 参数。默认不开启空间音效。 |

### V3.9.901 (2021-11-15)

- 新增空间音效的功能，可以实现 720 度 3D 场景下的空间语音效果。
- 同时支持范围语音的功能，支持有效范围内的音量衰减以及超出范围彻底静音。

### V3.9.900 (2021-09-18)

NERTC Unity SDK 正式发布。

搭建基于跨平台底层的 Unity 框架。支持标准的多人音频功能，包括音频的发送、订阅、质量数据透明。

## 音视频

### V5.4.13 (2023-10-20)

V5.4.13 版本为音视频 SDK 版本，相较于上一个音视频 SDK 版本 V5.4.5，主要变更如下：

**问题修复**

修复自定义视频输入时出现的绿屏问题。

### V5.4.5 (2023-09-06)

V5.4.5 版本为音视频 SDK 版本，相较于上一个音视频 SDK 版本 V4.5.907，主要新增如下特性：

- 新增特性

    序号 | 新增特性 | 特性描述 | 相关文档
    ---- | ---- | ---- | ----
    1 | 高级 Token 鉴权 | 若您的应用中存在对安全性要求较高的语音或视频通话场景，或者对观众上麦有权限控制的场景，建议您选择高级 Token 鉴权模式，以有效避免客户端遭遇破解攻击的问题。 | [高级 Token 鉴权](https://doc.yunxin.163.com/nertc/guide/zc3NDI2NTU?platform=unity)
    2 | 设置混音文件的音调 | 支持调整伴音和音效的音调。在 K 歌场景中，为了使歌曲更适合主播的声线音域，可以升高或降低伴奏的音阶。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/TY2MzU0ODc?platform=unity) |
    3 | 音频裸流传输 | 支持音频裸流传输，您可以向 NERTC SDK 提供自定义格式的音频编码数据，并由 NERTC SDK 进行推流。 | <a href="https://doc.yunxin.163.com/nertc/guide/Tk5NjM4MjI?platform=unity" target="_blank">音频裸流传输</a> |
    4 | 设置音频订阅优先级 | 支持优先订阅远端某用户发布的音频流。在 ASL 策略下，即在服务器线路上选择最清晰的三条音频流传输给本地用户时，本地用户设置优先订阅一个成员的音频流后，即使该成员的说话音量较低或不够清晰，本地用户仍能接收到该指定成员的音频流。 | [设置音频订阅优先级](https://doc.yunxin.163.com/nertc/guide/jE4MjY0MDE?platform=unity) |
    5 | 音频循环缓存录制 | 在原有的支持实时写文件基础上，支持设置仅录制最近一段时间内的音频数据，最高为 15 分钟。 | [客户端音频录制](/https://doc.yunxin.163.com/nertc/guide/DIyNDE2ODk?platformId=50002) |
    6 | 云代理 | 支持使用云代理服务穿透防火墙限制，使用固定 IP 连接到网易云信服务器。 | [云代理](https://doc.yunxin.163.com/nertc/guide/zU5NTIzMDc?platform=unity2) |
    7 | 音频辅流 | 支持通过辅流输入伴音文件或自定义音频源。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/TY2MzU0ODc?platform=unity)
    8 | 水印 | 出于信息安全、版权声明、防伪、宣传等目的，您可以为视频流画面添加编码水印，例如添加公司名称、标语等文字水印、录制时间等时间戳水印、以及 logo 等图片水印。 | [水印](https://doc.yunxin.163.com/nertc/guide/zA1ODY1NTI?platform=unity) |
    9 | 视频图像畸变矫正 | 在线美术或音乐教学场景中，用户会使用摄像头拍摄画板上的内容或录制师生的弹琴动作，但由于拍摄角度、镜头光学特性等原因，摄像头拍摄的画面相比原画可能有变形。NERTC SDK 支持通过提供畸变控制算法还原真实画面和场景。 | [视频图像畸变矫正](https://doc.yunxin.163.com/nertc/guide/zk3NTE1NDM?platform=unity)
    10 | 虚拟背景 | 支持通过自动识别用户人像，虚化用户周围的真实环境，或者以指定颜色的图片或自定义图像替代真实背景。 | [虚拟背景](https://doc.yunxin.163.com/nertc/guide/TAyNjAwNjY?platform=unity)
    11 | 云信美颜 | 云信自研的基础美颜和高级美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。 | [云信美颜](https://doc.yunxin.163.com/nertc/guide/DAzMDM0OTk?platform=unity)

- 新增 API

    V5.4.5 版本新增的接口请参考 [Unity SDK API 参考（音视频）](https://doc.yunxin.163.com/nertc/api-refer/unity/doxygen/Latest/zh/html/index.html)。

- 升级必看
    如果需要从历史 v4 版本升级至 V5.4.5 版本，请先联系网易云信技术支持进行评估。直接升级可能引发非预期的错误。

### V4.5.907 (2022-10-21)

NERTC Unity SDK（音视频版本）正式发布。

支持标准的多人音视频功能，包括音视频的发送、订阅。同时支持屏幕共享、音频录制、美声变声、自定义音视频采集等功能。