本文介绍网易云信音视频通话 NERTC SDK Linux 端的版本更新日志。具体功能请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=linux) 和 查看 [API 文档](https://doc.yunxin.163.com/nertc/client-apis?platform=linux)。

<style>
table th:first-of-type {width: 35%;}
</style>

## 5.9.15 (2025-12-18)

**新增功能**

- **AI 降噪增强**：音频 AI 降噪场景下利用声纹人声增强技术，显著提升背景人声降噪效果。
- **编码前马赛克功能**：支持外部调用设置编码前马赛克，提供马赛克和区域马赛克两种处理能力。
- **视频暗光增强**：新增暗光增强功能，可在光线亮度偏低和亮度不均匀环境下，自适应调整视频画面亮度值，恢复并凸显图像细节信息，全面提升视频图像视觉效果。
- **Player 点播支持**：Player 组件新增点播功能支持。
- **会中设备检测**：支持会中的音视频设备检测功能。
- **批注合流功能**：屏幕共享支持和外部输入的批注合流。

## 5.9.10 (2025-09-24)

**新增功能**

- **屏幕共享增强**：支持配置色彩空间配置选项，提升共享内容的色彩还原度和观看体验。
- **音频缓冲配置优化**：支持普通耳返缓冲区大小的配置，有效降低音频延迟，提升实时互动体验。
- **视频调试工具增强**：支持不同类型的视频数据导出，便于开发调试和问题排查，相关接口请参考 [`setVideoDump`](https://doc.yunxin.163.com/nertc/references/windows/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a43a025a2cdf282ab7ca33f466eea1d70)。
- **音频调试功能增强**：音频数据导出支持分级生成不同类型的文件，并可配置生成带时间戳的文件名。

**功能优化**

- **KTV 场景优化**：调整默认音效参数配置，提升 KTV 模式下人声表现力和音质体验。
- **背景音乐保护**：改进噪声门限和 AI 语音检测算法，避免对小音量背景音乐的误判，保证音乐流畅播放。

**问题修复**

修复 Linux 部分机型设备对 OpenGL 版本兼容问题。

## 5.9.5 (2025-08-14)

- 辅流音频音质增强，支持配置码率、采样频率、声道模式（单声道/双声道）、音频编码模式等参数。
- 共享声音降噪优化。
- 修复已知问题，提升用户体验。

## 5.9.0 (2025-07-02)

**新增功能**

- **新增视频色彩空间功能**：支持多种色彩标准（如 BT.709）和色彩范围（Limited/Full Range），适用于高质量视频直播、影视制作及专业视频会议场景，提升视频画质表现力。
    - 支持在自采集模式下设置色彩空间参数，通过 `NERtcVideoFrame` 中的 [`color_space_range`](https://doc.yunxin.163.com/nertc/references/windows/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_frame.html#afb19a34d84b7b0c07743e330e0590c26)（色彩范围）和 [`color_space_matrix`](https://doc.yunxin.163.com/nertc/references/windows/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_frame.html#a3da9962b3693d3a2dd20e8d1cde3bb28)（色彩矩阵标准）相关枚举选项。
    - 支持画面渲染和自渲染时的色彩空间处理。
    - 支持截图功能和视频算法（美颜、人脸检测、视频增强等）兼容各种色彩空间。

- **RTMP 拉流播放功能**：拉流时无需加入房间<!--，与 RTMP 推流功能互斥（当前版本暂不支持 B 帧及多路流拉取） -->，适用于直播观看和直播连麦场景，实现更灵活的内容分发。

- **字幕翻译增强**：支持多源语言和多目标语言的实时翻译，具体通过 [dst_languages](https://doc.yunxin.163.com/nertc/references/windows/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_a_s_r_caption_config.html#a10877a31fdebf03c8840872b17ad593d) 和 [src_languages](https://doc.yunxin.163.com/nertc/references/windows/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_a_s_r_caption_config.html#a90ce57d3c22ed9a1f29f98f07e4d7b5a) 字段指定语言。

- **虚拟背景能力上报**：在用户加入房间事件时，上报设备支持的虚拟背景能力级别信息，适用于需要根据设备性能动态调整虚拟背景效果的场景。

**功能优化**

- 优化音频处理系统，提升 AEC 回声消除效果，音质效果优化。
- 提升多核服务器环境下的性能表现，适用于高负载场景。
- 改进多种 Linux 发行版的兼容性，支持最新版本的 Ubuntu 22.04 和 CentOS 8。
- 改进 OpenGL 图形渲染性能，降低 GPU 资源占用。

**缺陷修复**

- 修复多种音频处理相关问题，提升通话稳定性。
- 解决服务器环境下长时间运行可能出现的系统资源问题。
- 修复在无图形界面环境下使用虚拟背景功能可能引起的异常。

## 5.8.20 (2025-05-30)

**新增功能**

- **自定义重连时长配置**：支持开发者根据业务需求自定义网络重连时长，可设置重连间隔和最大重连次数。适用于网络环境不稳定的远程会议、在线客服、医疗问诊等场景，确保通话连续性。

- **远端视频数据回调**：新增远端视频数据回调接口（[`addRemoteVideoFrameObserver`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1ce2b0280b18b63fcdccda2b46d14b47)），支持获取远端用户的视频帧数据进行自定义处理。适用于需要实时美颜、虚拟背景、AI 分析或录制存档的视频会议、直播连麦、在线教育场景。

**功能优化**

- **网络连接性能提升**：媒体连接建立过程优化，支持 IPv4 和 IPv6 并发连接，自动选择最优网络路径，显著提升首次连接速度和连接成功率。适用于跨国视频会议、复杂网络环境下的移动办公场景。

- **AI 降噪功能优化**：AI 降噪模块体积减少，降低应用包大小的同时保持卓越降噪效果，有效消除键盘声、环境噪音等干扰。

## 5.8.15 (2025-04-29)

- 媒体传输层现支持 IPv4 和 IPv6 网络协议的同时连接，大幅提高了网络适应性。
- 针对视频中流处理机制，优化了多人视频会议中的资源分配和传输控制。
- 修复了多项潜在问题。

## 5.8.10 (2025-04-01)

AI 降噪升级到 4.0 版本。AI 降噪新增音效增强模式，可精准消除背景人声，提升语音清晰度，优化通话体验。

## 5.8.5 (2025-03-20)

**新增特性**

- 新增支持 IPv6 网络解析与接入，提升全球网络兼容性。
- 新增音频的 AI 降噪与啸叫检测功能开关，开发者可一键启用或关闭。
- 新增支持 AI 服务相关操作的数据回调（[`onAiData`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a751d63d82944233eb1077ebce7c586eb)）。
- 新增支持虚拟背景功能。
- 新增支持添加视频水印。

**功能优化**

- 优化屏幕共享功能使用。

## 5.8.0 (2025-02-26)

- 支持 Simulcast（Simultaneous Multistream，多流传输）视频编码和传输技术，同时发送三个不同分辨率和码率的视频流，提高音视频的网络条件和设备性能适应性。相关 API 请调用 [`setVideoStreamLayerCount`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6c1b03c4209db6287f409e85798f34ae)。
- 其他已知问题优化修复。

## 5.7.0 (2025-01-20)

- 支持通过加密的 WSS（WebSocket Secure）协议通道传输实时通信中的信令数据。
- 将实时视频流推流到直播服务器时，支持超时检测，提升直播的稳定性。
- 修复已知问题，提升用户体验。

## 5.6.50 (2024-12-27)

- 支持配置了统信系统、麒麟系统、海光芯片、飞腾芯片的硬件设备。

- AI 任务支持实时字幕、AI 打断功能。相关接口请参考 [`startASRCaption`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1689a0bdcf317353d05e806bcb4140d7)。使用示例请参考 <a href="https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client">基于 RTC SDK 实现与 AI 数字人音视频互动</a>。

- 本地录制支持纯音频录制。相关接口请参考 [`addLocalRecorderStreamForTask`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1689a0bdcf317353d05e806bcb4140d7)，使用示例请参考 [本地录制](https://doc.yunxin.163.com/nertc/guide/jE4MTM3NzE?platform=macOS)。

- 本地录制支持对录制文件进行 MP4 转码。相关接口请参考 [`stopLocalRecorderRemuxMp4`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a115e5599310219d54897737b12feafe7)。

- 本地录制支持录制音频共享声音。

## 5.4.10 (2023-12-15)

本次升级改动较大，请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/jY0ODc2OTI?platform=linux)。

**新增特性**

| <div style="width:60px;">新增特性</div> | <div style="width:300px;">特性描述</div> | <div style="width:100px;">相关文档</div> |
| --- | --- | --- |
| 屏幕共享 | 支持 X11 显示协议和 Wayland 显示协议的 Linux 系统进行屏幕共享。 | [屏幕共享](https://doc.yunxin.163.com/nertc/guide/Dk2MTEwNjQ?platform=linux) |
| 音乐文件播放及混音(伴音) | 在房间中播放本地或者在线音乐文件，作为通话或直播时的背景声音，同时让房间内的其他人听到此音乐。NERTC 播放伴音方法可以用来播放比较长的背景音，例如伴奏音乐、环境白噪声、背景音乐等等。<br>NERTC 支持在麦克风关闭的状态下，发送伴音。在娱乐社交、在线教育等场景中，即使用户不想要开启麦克风进行语音聊天，也能在房间内播放背景音乐。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/Tk2ODIyMDQ?platform=linux) |
| 音效文件播放管理 | 支持在通话或直播中播放短时音频文件，一般用于渲染房间气氛，例如游戏音效、掌声、口哨、欢呼声、笑声的短时音效。支持多个音效叠加播放。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/Tk2ODIyMDQ?platform=linux) |
| 美声变声与混响 | NERTC SDK 支持设置多种预设的美声与变声音效，您也可以通过设置本地语音音效均衡或混响来达到自定义的人声效果，增加场景气氛。 | [美声变声与混响](https://doc.yunxin.163.com/nertc/guide/jE1MzE5NzM?platform=linux) |
| 多房间管理 | 在娱乐社交与在线教育场景中，App 用户往往需要同时加入多个房间，接收多个房间的音视频流。网易云信 NERTC SDK 提供多房间管理功能，隔离多个房间的消息和回调，在跨房间连麦场景和超级小班课场景都可以实现更灵活的房间管理业务。 | [多房间管理](https://doc.yunxin.163.com/nertc/guide/DAxNjA1NjM?platform=linux) |
| 旁路推流 | NERTC SDK 支持云端音视频混流和 RTMP 旁路推流，可以将实时音视频流转为标准直播流，并将其从网易云信实时音视频云推送到第三方 CDN（Content Delivery Network）或网易云信直播服务。 | [旁路推流](https://doc.yunxin.163.com/nertc/guide/TI2ODQxOTU?platform=server) |
| 跨房间流媒体转发 | 在 NERTC 直播场景的音视频房间中，跨房间媒体流转发功能可实现主播角色跨房间与其他主播实时交流互动，在娱乐场景下可实现跨直播间连麦效果。 | [跨房间流媒体转发](https://doc.yunxin.163.com/nertc/guide/DcyNjA0NzA?platform=linux) |
| 视频截图 | NERTC SDK 支持针对实时视频流进行截图，包括本地主流和辅流画面、远端主流和辅流画面。在在线教育以及主播直播等场景中，通过视频截图功能截取实时视频流画面，以便后续的存档分析、事件备忘、证据留存等。 | [视频截图](https://doc.yunxin.163.com/nertc/guide/jIwOTg1NDY?platform=linux) |
| 云代理 | 网易云信云代理可穿透防火墙限制，使用固定 IP 连接到网易云信服务器。云代理方案可满足多种在公有云、混合云、私有云等有防火墙或者其他网络限制的环境下，内外网进行音视频通话的场景。 | [云代理](https://doc.yunxin.163.com/nertc/guide/DE2NzUxMTY?platform=linux) |
| 音频共享 | NERTC 提供了音频共享功能，帮助您在共享屏幕的同时也能播放本地背景音，或者共享本地视频文件或音乐文件的声音，为您规避播放在线音乐文件可能会遇到的版权问题。 | [音频共享](https://doc.yunxin.163.com/nertc/guide/jcwNDA2Nzk?platform=linux) |
| 视频大小流 | 大流对应高清画质，小流对应低清画质。用户可以选择上传一大一小两个视频流，接收方可以根据需要进行选择。 | [`enableDualStreamMode`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac83f9db30c5754efe06ca8f06eab1a05) |
| 音视频流回退 | 网络不理想的环境下，音视频的质量都会下降。为提升用户体验，您可以通过指定接口设置视频流回退选项。在网络条件差、无法同时保证音频和视频质量的情况下，SDK 会自动将视频流从大流切换为小流，或将媒体流回退为音频流，从而提高音视频质量。 | [`setLocalPublishFallbackOption`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0b38d4712494802a96e53e41150c2260) |
| 音频裸流传输 | NERTC SDK 支持音频裸流传输，您可以向 NERTC SDK 提供自定义的 OPUS 等格式的音频编码数据，并由 NERTC SDK 进行推流。适用于需要与硬件配合的应用场景中，例如使用教室硬件设备进行线上教学，在利用硬件自身能力进行音频采集、编码的基础上，还需要良好的抗弱网传输能力。 | [音频裸流传输](https://doc.yunxin.163.com/nertc/guide/zU4NTg0NTI?platform=linux) |
| 视频裸流传输 | NERTC SDK 支持视频裸流传输，您可以向 NERTC SDK 提供自定义的 H.264 等格式的视频编码数据，并由 NERTC SDK 进行推流。适用于需要与硬件配合的应用场景中，例如使用教室硬件设备进行线上教学，在利用硬件自身能力进行视频采集、编码的基础上，还需要良好的抗弱网传输能力。 | [视频裸流传输](https://doc.yunxin.163.com/nertc/guide/TYwMjYwOTQ?platform=linux) |

**新增 API**

<div class="full_width_table">

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`setScreenCaptureSource`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a39f8b8e9b6aa1c428ce225beacb8896d) | 设置屏幕共享参数，该方法在屏幕共享过程中调用，用来快速切换采集源 |
| [`getScreenCaptureSources`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a10585dd4a762ccebd06addbb7c57c096) | 获得一个可以共享的屏幕和窗口的列表 |
| [`NERtcScreenCaptureParameters`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_screen_capture_parameters.html) | 支持屏幕共享高亮框配置 |
| [`playEffect`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9c4a27db0bc0e1c946c4cef1cb42e6f8) | 播放指定音效文件 |
| [`stopEffect`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a3c0ec8800dcde86d8e771c6fb41c89b5) | 停止播放指定音效文件 |
| [`pauseEffect`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a788d9820256804a992ce45cffffe8921) | 暂停播放指定音效文件 |
| [`resumeEffect`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a382f3f9f19b47780a77c627eb868acd2) | 恢复播放指定音效文件 |
| [`stopAllEffects`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ade0e7594f87942d55574b1b21aa76d22) | 停止播放所有音效文件 |
| [`pauseAllEffects`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aff814b90dee7c16180b0a3dc597f9d95) | 暂停播放所有音效文件 |
| [`resumeAllEffects`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a80af18aff1638a72449b58094f7121aa) | 恢复播放所有音效文件 |
| [`setEffcetSendVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a35a638341c80c885a80a0ce26e6d2e6d) | 设置音效文件的发送音量 |
| [`setEffcetPlaybackVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8239d173a4210a5e97bbb02d2bb22408) | 设置音效文件的播放音量 |
| [`setEffectPitch`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#adf1ee5f8e1d8c27ebd3608e8dc928f2c) | 设置音效文件音调 |
| [`getEffectSendVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a59cc8aa6c47a1655d9e88017150f7838) | 获取音效文件的发送音量 |
| [`getEffcetPlaybackVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ad8ff276a90e9796c432c4251f8b0854f) | 获取音效文件的播放音量 |
| [`getEffectPitch`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ad5656d4f957583c12f10fe32a8b87b58) | 获取音效文件音调 |
| [`setEffectPosition`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a03da333ef3bb1f6e456807a173d550fd) | 设置音效文件的播放位置 |
| [`getEffectDuration`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a2c4336d60890815ee035ff63f15296fd) | 获取音效文件时长 |
| [`getEffectCurrentPosition`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a26843fa093085650d7fa915e65bbf0e1) | 获取音效文件当前播放进度 |
| [`startAudioMixing`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5246f41018a7cbcddafd58b54f2aa790) | 开始播放伴音 |
| [`enableLocalSubStreamAudio`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#acb645a5a1cb5afecce680b434dd4c365) | 开启音频辅流 |
| [`stopAudioMixing`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a87846b81505c568c3bc33a2ca8c01e1d) | 停止播放伴音 |
| [`pauseAudioMixing`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a75e28550a5e4c816d95998ab513de7db) | 暂停播放伴音 |
| [`resumeAudioMixing`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a895dd671d9f27e0c06c575bd3a985c3b) | 恢复播放伴音 |
| [`setAudioMixingPlaybackVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1a35486533d4269b41ec550688fe994e) | 设置伴音播放音量 |
| [`setAudioMixingSendVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8b913ee33655ae5153405fcaedfcc4a5) | 设置伴音的发送音量 |
| [`setAudioMixingPitch`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afc49fa103c6806f5e17aafb41eb3ac4b) | 设置伴音的音调 |
| [`getAudioMixingPlaybackVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a979d8ba9ba9f22d33853f40ad080c43a) | 获取伴音的播放音量 |
| [`getAudioMixingSendVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a132b17b724d75391af26cfef884bbef0) | 获取伴音的发送音量 |
| [`getAudioMixingPitch`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4104afcb0fe83b4c4c0edd63f1021280) | 获取伴音的音调 |
| [`getAudioMixingDuration`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afe9db02f579f3decb969100a2725e069) | 获取伴音的总长度 |
| [`setAudioMixingPosition`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#abca6b5d01e08b6dc4893e90153e9fd01) | 设置伴音的播放进度 |
| [`getAudioMixingCurrentPosition`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a70383f0fb54ef8310c18c96383b92a4d) | 获取伴音当前播放进度 |
| [`onAudioMixingStateChanged`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a39351279a586979bc1ef25d10433894b) | 伴音播放状态改变回调 |
| [`onAudioMixingTimestampUpdate`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ad259b5769a5ba48b58643480faca79bc) | 伴音播放进度回调 |
| [`onAudioEffectFinished`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a69ce2bfa8f0cec24dfabae2751cbf3d8) | 本地音效文件播放已结束回调 |
| [`onAudioEffectTimestampUpdate`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a98d0770e5d6981422560185899cd63fd) | 本地音效文件播放进度信息回调 |
| [`setVoiceBeautifierPreset`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a81b7ea061c4b61a518689ab3bf83e17a) | 设置预设的美声效果 |
| [`setAudioEffectPreset`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#af1d4e68e36c0e30d7bed6e5e00fc51d8) | 设置预设的变声效果 |
| [`setLocalVoicePitch`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ab1ff742d724ab296826a3128b98c60d9) | 设置本地语音音调 |
| [`setLocalVoiceEqualization`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#adf31aa3cfb4fa6cec57fbac46b47595d) | 设置本地语音音效均衡 |
| [`setLocalVoiceReverbParam`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a201700a4ea2b2368436b77f14e8067cf) | 设置本地语音混响 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c64c195919c2fb4c98ad32f1057afc6" target="_blank">`takeLocalSnapshot`</a> | 截取本地视频流画面 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a28966129e4f879209bf06e01617fa50a" target="_blank">`takeRemoteSnapshot`</a> | 截取远端视频流画面 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_n_e_rtc_take_snapshot_callback.html#ad4cb868ec2fbd8bd35efc3101f343687" target="_blank">`onTakeSnapshotResult`</a> | 截图结果 block 回调 |
| [`setCloudProxy`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ade9d3ad8490b2b17492b150773041948) | 开通云代理设置 |
| [`enableDualStreamMode`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac83f9db30c5754efe06ca8f06eab1a05) | 设置是否开启视频大小流模式 |
| [`setLocalPublishFallbackOption`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0b38d4712494802a96e53e41150c2260) | 设置弱网条件下发布的音视频流回退选项 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5a20869b06cde0cd1f27b30a8b59fc7f" target="_blank">`setExternalSubStreamAudioSource`</a> | 开启外部音频辅流输入 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c5aaaa9c1b8d58b1e3ad1f4d7dcdb5c" target="_blank">`pushExternalAudioEncodedFrame`</a> | 推送外部音频主流编码帧 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a30426676dc38d4de6d5f7634e58fd870" target="_blank">`pushExternalSubStreamAudioFrame`</a> | 推送外部音频辅流编码帧 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6bf490923f8a8ebbdfdcaa76578dc5cd" target="_blank">`setPreDecodeObserver`</a> | 注册解码前媒体数据观测器 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_pre_decode_observer.html#ac6012e89321a7678e3c1f192c26a0b89" target="_blank">`onFrame`</a> | 解码前媒体数据回调 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ab7845fc73174ed9983e27676c747602b" target="_blank">`pushExternalVideoEncodedFrame`</a> | 推送外部视频主流或辅流编码帧 |
| [`setVideoEncoderQosObserver`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a39a436beee4d9f4df98b95853d7160c4) | 注册视频编码 QoS 信息监听器 |
| <a href="https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a39a436beee4d9f4df98b95853d7160c4" target="_blank">`setPreDecodeObserver`</a> | 注册解码前媒体数据观测器 |
| [`onRequestSendKeyFrame`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#aa8c5f0e420db19a085d580f188a09cc2) | I 帧请求事件回调 |
| [`onVideoCodecUpdated`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#ad186cc362106a2935556b3c16ec643b5) | 视频编码器类型信息回调 |
| [`onBitrateUpdated`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#a6f810bbc3dd564a1ce49a82a98cdbae8) | 视频码率信息回调 |
| [`enableLoopbackRecording`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a44ea82286265381d1a2348fbe5c591b7) | 开启声卡采集 |
| [`adjustLoopbackRecordingSignalVolume`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5b1891d6b398f0fb755541edc993beb1) | 调节声卡采集信号音量 |
| [`startChannelMediaRelay`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a3c217fa914aad57cd006caa26b12ffe3) | 开启跨直播间媒体流转发 |
| [`updateChannelMediaRelay`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4a1a35c122cd0bba634b312fd00399eb) | 更新媒体流转发 |
| [`stopChannelMediaRelay`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a55348f3e72af97ef6b9eabb8adfec11b) | 停止跨直播间媒体流转发 |
| [`onMediaRelayStateChanged`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ab8c4d3c3a2d3f695200694ab3805dd62) | 跨房间媒体流转发状态发生改变回调 |
| [`onMediaRelayEvent`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a4e6ab72395627936258caa5a176654f9) | 媒体流相关转发事件回调 |
| [`addLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae53d9d69d13da31179e98c467b3788d5) | 添加房间推流任务 |
| [`updateLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#abba8d7c5094509960589e9b6e56c0ef6) | 更新修改房间推流任务 |
| [`removeLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae2764a62d1c421d4bec3e626eb6c3f83) | 删除房间推流任务 |
| [`onAddLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ac87b9ec9ac76cec6583abb9bf8b121b2) | 通知添加直播任务结果 |
| [`onUpdateLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a51e871e3eb8f884f77e8f72001b0c6dd) | 通知更新直播任务结果 |
| [`onRemoveLiveStreamTask`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a373a0d2e896ea07a4a727c7f9899f160) | 通知删除直播任务结果 |
| [`onLiveStreamState`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#aba53fc5c94b82af9f477b463584c6f2f) | 通知直播推流状态 |
| [`createChannel`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aaad999ec7dae22a41ae1d083b3612c89) | 创建并获取一个 NERtcChannel 对象。通过创建多个对象，用户可以同时加入多个频道
| [`IRtcChannel`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html) | 该类提供在指定频道内实现实时音视频功能的方法 |
| [`IRtcChannelEventHandler`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel_event_handler.html) | 该类提供监听指定频道事件和数据的回调 |
</div>

## 4.4.9 (2022-06-15)

网易云信于 2022 年 6 月 15 日发布了 NERTC SDK 最新版本 V4.4.9。

**新增特性**

| <div style="width:60px">新增特性</div> | <div style="width:300px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- |
| 屏幕共享 | 支持在视频通话或互动直播过程中实现屏幕共享，主播或连麦者可以将自己的屏幕内容，以视频的方式分享给远端参会者或在线观众观看，从而提升沟通效率，一般适用于多人视频聊天、在线会议以及在线教育场景。 | [屏幕共享](/https://doc.yunxin.163.com/nertc/guide/DQ0OTEwNjU?platformId=50002) |
| 原始音频数据 | 支持对采集到的音视频原始数据进行自定义的前处理和后处理，获取想要的播放效果。适用于非标设备接入、自定义音频效果、语音处理、语音识别等场景。 | [原始音频数据](/https://doc.yunxin.163.com/nertc/guide/TM4Nzk4Mzc) |
| 自定义音频采集与渲染 | 支持用户使用自定义音频源，NERTC SDK 为用户提供传输通道，并进行编码推流。 | [自定义音频采集与渲染](/https://doc.yunxin.163.com/nertc/guide/jA2ODgzMDg) |

**改进优化**

- 集成 Linux SDK 时无 GLIBCXX 或 gcc/g++ 的版本限制。
- 支持静态编译 openssl。
- 音频依赖优化：若无相关音频服务及系统库，音频依赖会从 PulseAudio 自动降级到 Dummy Audio。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`startScreenCaptureByScreenRect`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1c10c8522dc6715388ffe62f165beed7) | 开启屏幕共享，共享范围为指定屏幕的指定区域。 |
| [`startScreenCaptureByWindowId`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8eab357982a5fa500e4e5d5eadb42923) | 开启屏幕共享，共享范围为指定窗口的指定区域。 |
| [`updateScreenCaptureRegion`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a53d4152c3770a262e244752dfaf19801) | 更新屏幕共享区域。 |
| [`pauseScreenCapture`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a797d351e31ec5eecbe434564b7f4d326) | 暂停屏幕共享。 |
| [`resumeScreenCapture`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a7323b3f9e0eee581a0dc67354df4e092) | 恢复屏幕共享。 |
| [`stopScreenCapture`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a722c1bb960536c104fd3560479f86d72) | 停止屏幕共享。 |
| [`setupLocalSubStreamVideoCanvas`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9abf36ee67a86d2c14d38fbea19764bf) | 设置本端的辅流视频回放画布。 |
| [`setupRemoteSubStreamVideoCanvas`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a72a28c34a25ae241c75045dc83e84388) | 设置远端的辅流视频回放画布。 |
| [`subscribeRemoteVideoSubStream`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a210b788405ba94697dfefdd501bac078) | 订阅或取消订阅远端的屏幕共享辅流视频，订阅之后才能接收远端的辅流视频数据。 |
| [`onUserSubStreamVideoStart`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a48f88b74beb1db6d8ccbca5f079912ee) | 远端用户开启屏幕共享辅流通道的回调。 |
| [`onUserSubStreamVideoStop`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#abf09442bb44e42d300bcae8a1b21aaa3) | 远端用户停止屏幕共享辅流通道的回调。 |
| [`onScreenCaptureStatus`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a7649a71ffa815cecde17836facd0834a) | 屏幕共享状态变化回调。 |
| [`setExternalAudioSource`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a32505c00824e8f85443a9e5e7a8c04f3) | 启用外部自定义音频数据输入功能，并设置采集参数。 |
| [`pushExternalAudioFrame`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0e9b283dd7b1d3d5beb39760fb2fd4fb) | 将外部音频数据帧推送给内部引擎。 |
| [`setExternalAudioRender`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a37efd1ec3002171e754fadd46663867d) | 设置外部音频渲染。 |
| [`pullExternalAudioFrame`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a22f7611bf3d9462c03d3bf77f1e5fdb4) | 拉取外部音频数据。 |
| [`setAudioFrameObserver`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a7649a71ffa815cecde17836facd0834a) | 注册语音观测器对象。 |
| [`setRecordingAudioFrameParameters`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae3f5b17aade8c9fe8ff5a6fef6383d9e) | 设置录制的声音格式。 |
| [`setPlaybackAudioFrameParameters`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a7649a71ffa815cecde17836facd0834a) | 设置播放的声音格式。 |
| [`setMixedAudioFrameParameters`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a83e4fbdea5fff4015275bdc31095a2ad) | 设置采集和播放后的混合后的采样率。 |
| [`onAudioFrameDidRecord`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a32505c00824e8f85443a9e5e7a8c04f3) | 采集音频数据回调。 |
| [`onAudioFrameWillPlayback`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0e9b283dd7b1d3d5beb39760fb2fd4fb) | 播放音频数据回调。 |
| [`onMixedAudioFrame`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a37efd1ec3002171e754fadd46663867d) | 音频采集与播放混合后数据帧回调。 |
| [`onPlaybackAudioFrameBeforeMixing`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a22f7611bf3d9462c03d3bf77f1e5fdb4) | 某一远端用户的原始音频帧回调。 |

**变更 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`onLocalAudioStats`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_media_stats_observer.html#ad4343447be03b1477ff3ee5487865d09) | [NERtcAudioSendStats](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_audio_send_stats.html) 结构体新增 `audio_layers_count` 字段表示音频流总条数，新增 `audio_layers_list` 字段表示每条音频主流或辅流的统计数据，包括丢包率、采集音量等。 |
| [`onRemoteAudioStats`](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_media_stats_observer.html#a1e3f116bd1e9c9a20e7e33b4deadbd4b) | [NERtcAudioRecvStats](https://doc.yunxin.163.com/docs/interface/nertc/linux/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_audio_recv_stats.html) 结构体新增 `audio_layers_count` 字段表示音频流总条数，新增 `audio_layers_list` 字段表示每条音频主流或辅流的统计数据，包括丢包率、采集音量等。 |

## 4.4.8 (2021-12-20)

网易云信于 2021 年 12 月 20 日发布了 Linux NERTC SDK 初始版本 V4.4.8。

**支持平台**

- x86_64 架构
- ARM64(aarch64) 架构

**支持功能**

<!-- <style>
table th:first-of-type {
    width: 40%;
}
table th:nth-of-type(2) {
    width: 60%;
}
</style> -->

| 新增特性 | 特性描述 |
| --- | --- |
| 多人音视频通话 | NERTC SDK 为您提供稳定流畅、高品质、全平台的点对点和多人实时音视频通话服务。 |
| 房间管理及房间事件通知 | 支持快速加入或退出房间，并在本地或远端用户的相应状态改变时提供对应回调。 |
| 音频管理 | 支持音量的调节、音频的采集与发送。同时您也可以设置音频编码配置，以便您根据实际场景方便快捷地调整音质属性、在常见场景中实现最优的音质效果。 |
| 视频管理 | 支持设置视频属性，包括视频编码的分辨率、码率、帧率、适应性偏好，且支持设置用户视图、视频预览和音频流的发送。 |
| 音视频设备管理及设备事件通知 | 支持音视频采集、播放设备的设置，并提供相应回调。 |
| 自定义视频采集 | 支持配置和推送外部视频源数据。 |
| 耳返功能 | 支持监听本地采集的音频和耳返音量调节，耳返音频具备低延时、高音质等特征，让主播可以实时听到本端的声音。 |
| 媒体补充增强信息 SEI | 支持将时间戳等自定义数据作为流媒体补充增强信息（SEI Supplemental Enhancement Information）的一部分，通过流媒体通道将其与视频内容打包在一起，发送给远端用户，以此实现文本数据与音视频内容的精准同步的目的。 |
| 媒体和数据统计事件通知 | 支持通过监听回调的方式获取首帧解码通知和远端用户操作动态。 |
| 故障排查 | 支持记录音频 dump，方便您分析音频问题。 