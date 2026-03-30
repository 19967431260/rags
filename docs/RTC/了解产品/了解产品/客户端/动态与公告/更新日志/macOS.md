本文介绍网易云信音视频通话 NERTC SDK macOS 端的版本更新日志。具体功能请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=macOS) 和 查看 [API 文档](https://doc.yunxin.163.com/nertc/client-apis?platform=macOS)。

<div class="card">
<span style="font-size:16px;"><b>近期重要更新</b></span>
  <ul>
    <li>从 5.6.50 开始，AI 任务支持实时字幕、AI 打断功能。使用示例请参考 <a href="https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client">基于 RTC SDK 实现与 AI 数字人音视频互动</a>。</li>
    <li>从 5.6.10 开始，您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。</li>
    <li>从 5.5.40 开始，为方便开发者快速接入，NERTC SDK 新增多种预设场景。当前支持的预设场景包括标准 1 对 1 音视频通话、高画质 1 对 1 音视频通话、标准语聊房、高音质语聊房、会议场景。</li>
    <li>从 5.5.32 开始，支持定制裁剪一些视频特效功能，有效减小包体积。</li>
    <li>从 5.5.10 开始，支持 <a href="https://doc.yunxin.163.com/Overseas/guide/DYzMjg1ODI?platform=others#%E9%99%90%E5%AE%9A%20RTC%20SDK%20%E7%9A%84%20%E8%AE%BF%E9%97%AE%E5%8C%BA%E5%9F%9F"><b>限定 NERTC SDK 的访问区域</b></a>。在出海场景中，满足客户在全球国家或地区的访问域名的合规性。</li>
  </ul>
</div>

<style>
table th:first-of-type {width: 35%;}
</style>

:::details 单击展开查看 3.0.0 (2019-09-29) ~ 4.6.67 (2023-05-11) 版本 NERTC SDK 的更新日志。

⭐<span style="font-size:16px;"><b>**近期重要更新**</b></span>

- 从 v.6.29 开始，支持 <a href="https://doc.yunxin.163.com/nertc/docs/TgxMzk1MDg?platform=macOS" target="_blank"> **高级 Token 鉴权** </a>, 支持对用户创建、加入房间和订阅、发布音视频流的权限进行校验，帮助您有效避免客户端遭遇破解攻击的问题。
- 从 v.6.20 开始，支持以 **插件化** 方式集成 **美颜**、**虚拟背景**、**AI 降噪**、**AI 啸叫检测**，提升 SDK 集成的灵活性与易操作性，您可以根据需要自行选择是否集成对应特性的动态库，使 App 的包体积更小，具体请参考 <a href="https://doc.yunxin.163.com/nertc/docs/DI3NDEyNDI?platform=macOS" target="_blank">集成 SDK</a>。
- 从 v.6.20 开始，支持通过 **视频辅流通道** 开启本地摄像头采集、自定义视频源输入等，具体请参考 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0f80132a269b2a7b8fca1a9dd2ca31cb" target="_blank">设置视频编码属性</a> 和 [自定义视频采集](https://doc.yunxin.163.com/nertc/docs/TkyMDQzNTA?platform=macOS)。


⭐<span style="font-size:16px;"><b>4.6.53 (2023-05-11)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 自定义加密 | 媒体流加密新增支持自定义加密模式。除了国密算法，您可以使用自己独特的加密算法，使产品更安全、更难被攻击者破解。 | <a href="https://doc.yunxin.163.com/nertc/docs/DgzODM3ODU?platform=macOS" target="_blank">媒体流加密</a> |

⭐<span style="font-size:16px;"><b>4.6.50 (2023-03-28)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 调节本地播放的指定房间内所有远端用户的音量。 | 在多房间场景中，可以使用该方法单独调整主房间或者某个子房间的所有远端用户的播放音量。 | <a href="https://doc.yunxin.163.com/nertc/docs/jUzMjAxNTc?platform=android#设置播放音量" target="_blank">设置通话音量</a> |

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9c7b067fef122f7a54f3a887a851aad1" target="_blank">`adjustChannelPlaybackSignalVolume`</a> | 调节本地播放的指定房间内所有远端用户的音量。 |

⭐<span style="font-size:16px;"><b>4.6.43 (2023-02-16)</b></span>

**问题修复**

- 修复屏幕共享时，PPT 幻灯片放映窗口自动采集的兼容性问题。
- 修复美颜功能在部分 Macbook 设备上崩溃的问题。

⭐<span style="font-size:16px;"><b>4.6.40 (2023-01-10)</b></span>

**升级必看**

自 4.6.40 起，AI 降噪功能以 **插件化** 方式提供，对应的 AI 降噪库为 `NERtcAiDenoise.framework`，可以与核心 SDK（基础音视频库）搭配使用，具体集成方式请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/DI3NDEyNDI" target="_blank">集成 SDK</a>。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 音频裸流传输支持 ASL 选路 | 支持将编码后音频的音量数据传递给 SDK，以支持音频裸流参与 ASL 选路。 | <a href="/https://doc.yunxin.163.com/nertc/guide/Tk1NDc3NzY" target="_blank">音频裸流传输</a> |
| 自定义视频画布颜色 | 支持设置视频画布的背景色，当视频尺寸与显示视窗尺寸不一致时，可以自定义改变传统黑框的颜色。 | <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_canvas.html" target="_blank">`NERtcVideoCanvas`</a> |

**改进优化**

1. 支持平滑入会，优化摄像头预览期间的入会体验。
2. 屏幕共享场景实践优化，支持在播放 PPT 时自动共享该页 PPT。

**变更 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c5aaaa9c1b8d58b1e3ad1f4d7dcdb5c" target="_blank">`pushExternalAudioEncodedFrame`</a> | `encodedAudioFrame` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_audio_encoded_frame.html" target="_blank">`NERtcAudioEncodedFrame`</a>    类型新增 `rms_level` 字段，对应音频裸流主流的音量值。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#af959b21a9e362e8f1896ff206bae3dab" target="_blank">`pushExternalSubStreamAudioEncodedFrame`</a> | `encodedAudioFrame` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_audio_encoded_frame.html" target="_blank">`NERtcAudioEncodedFrame`</a> 类型新增 `rms_level` 字段，对应音频裸流辅流的音量值。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#ad7306ae7edc1cadedceb6c2cde8df279" target="_blank">`setupLocalVideoCanvas`</a> | `canvas` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_canvas.html" target="_blank">`NERtcVideoCanvas`</a> 类型新增 `background_color` 字段，对应本端视频主流画布的背景颜色。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#a16192ada0272bb48adc18848e68dc57d" target="_blank">`setupRemoteVideoCanvas`</a> | `canvas` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_canvas.html" target="_blank">`NERtcVideoCanvas`</a> 类型新增 `background_color` 字段，对应远端视频主流画布的背景颜色。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9abf36ee67a86d2c14d38fbea19764bf" target="_blank">`setupLocalSubStreamVideoCanvas`</a> | `canvas` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_canvas.html" target="_blank">`NERtcVideoCanvas`</a> 类型新增 `background_color` 字段，对应本端视频辅流画布的背景颜色。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a72a28c34a25ae241c75045dc83e84388" target="_blank">`setupRemoteSubStreamVideoCanvas`</a> | `canvas` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_canvas.html" target="_blank">`NERtcVideoCanvas`</a> 类型新增 `background_color` 字段，对应远端视频辅流画布的背景颜色。 |

⭐<span style="font-size:16px;"><b>4.6.29 (2022-11-18)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 高级 Token 鉴权 | 支持对用户创建、加入房间和订阅、发布音视频流的权限进行校验，帮助您有效避免客户端遭遇破解攻击的问题。 | <a href="/https://doc.yunxin.163.com/nertc/guide/TgxMzk1MDg" target="_blank">高级 Token 鉴权 </a> |
| 设置混音文件音调 | 支持调整伴音和音效文件的音调，以实现例如在 K 歌场景中，为了使歌曲更适合主播的声线音域，升高或降低伴奏的音阶。 | <a href="/https://doc.yunxin.163.com/nertc/guide/jg2OTMyMzg" target="_blank">音效与伴音</a> |
| 音视频裸流传输 | 支持音视频裸流传输，您可以向 NERTC SDK 提供自定义格式的音视频编码数据，并由 NERTC SDK 进行推流。 | <a href="/https://doc.yunxin.163.com/nertc/guide/Tk1NDc3NzY" target="_blank">音频裸流传输</a>、<a href="/https://doc.yunxin.163.com/nertc/guide/DEyMzY0NDc" target="_blank">视频裸流传输</a> |

**改进优化**

优化加入房间进程。

**问题修复**

修复已知问题。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#a29bdc1e3e13990b94ab9e92c8c7b5693" target="_blank">`joinChannel`</a> | 加入音视频房间（原同名接口保留，此接口新增 `channel_options` 参数，用于携带自定义入会信息）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a75a8d89af8302e1c2ad9eb02e286174a" target="_blank">`updatePermissionKey`</a> | 设置新的权限密钥。 |
| [`setEffectPitch`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#adf1ee5f8e1d8c27ebd3608e8dc928f2c) | 设置音效文件音调 |
| [`getEffectPitch`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ad5656d4f957583c12f10fe32a8b87b58) | 获取音效文件音调 |
| [`setEffectPosition`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a03da333ef3bb1f6e456807a173d550fd) | 设置音效文件的播放位置 |
| [`getEffectDuration`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a2c4336d60890815ee035ff63f15296fd) | 获取音效文件时长 |
| [`getEffectCurrentPosition`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a26843fa093085650d7fa915e65bbf0e1) | 获取音效文件当前播放进度 |
| [`setAudioMixingPitch`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afc49fa103c6806f5e17aafb41eb3ac4b) | 设置伴音的音调 |
| [`getAudioMixingPitch`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4104afcb0fe83b4c4c0edd63f1021280) | 获取伴音的音调 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c5aaaa9c1b8d58b1e3ad1f4d7dcdb5c" target="_blank">`pushExternalAudioEncodedFrame`</a> | 推送外部音频主流编码帧 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a30426676dc38d4de6d5f7634e58fd870" target="_blank">`pushExternalSubStreamAudioFrame`</a> | 推送外部音频辅流编码帧 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6bf490923f8a8ebbdfdcaa76578dc5cd" target="_blank">`setPreDecodeObserver`</a> | 注册解码前媒体数据观测器 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ab7845fc73174ed9983e27676c747602b" target="_blank">`pushExternalVideoEncodedFrame`</a> | 推送外部视频主流或辅流编码帧 |
| [`setVideoEncoderQosObserver`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a39a436beee4d9f4df98b95853d7160c4) | 注册视频编码 QoS 信息监听器 |
| [`onUserJoined`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler.html#a4dd427d417892f99812ac42ac5db22ac) | 远端用户加入房间回调（原同名回调不建议使用，此回调新增 `joinExtraInfo` 参数，用于返回自定义入会信息）。 |
| [`onUserLeft`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler.html#a05306dbb0e602ea608515b5e394202cf) | 远端用户离开房间回调（原同名回调不建议使用，此回调新增 `joinExtraInfo` 参数，用于返回自定义入会信息）。 |
| [`onPermissionKeyWillExpire`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a4c21a3a69a9ad33e2b6fe3b4c7927ed2) | 权限密钥即将过期回调。 |
| [`onUpdatePermissionKey`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#abbeaf66b26926389fef32eb6cb2ec4bc) | 更新权限密钥成功回调。 |
| [`onAudioEffectTimestampUpdate`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a98d0770e5d6981422560185899cd63fd) | 本地音效文件播放进度信息回调 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_pre_decode_observer.html#ac6012e89321a7678e3c1f192c26a0b89" target="_blank">`onFrame`</a> | 解码前媒体数据回调 |
| [`onRequestSendKeyFrame`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#aa8c5f0e420db19a085d580f188a09cc2) | I 帧请求事件回调 |
| [`onVideoCodecUpdated`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#ad186cc362106a2935556b3c16ec643b5) | 视频编码器类型信息回调 |
| [`onBitrateUpdated`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_video_encoder_qos_observer.html#a6f810bbc3dd564a1ce49a82a98cdbae8) | 视频码率信息回调 |

⭐<span style="font-size:16px;"><b>4.6.22 (2022-11-02)</b></span>

**改进优化**

1. 视频后处理中增加丢帧处理机制。
2. 新增全局初始化 `libcurl` 及清理机制。

⭐<span style="font-size:16px;"><b>4.6.20 (2022-09-08)</b></span>

**升级必看**

自 4.6.20 起，支持以 **插件化** 方式集成美颜、虚拟背景等功能，提升 SDK 集成的灵活性与易操作性，您根据需要自行选择是否集成对应特性的动态库，以实现轻量接入裁剪包，更多请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/DI3NDEyNDI" target="_blank">集成 SDK</a>。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 视频辅流通道优化 | 支持通过视频辅流通道开启本地摄像头采集、自定义视频源输入等。 | <a href="/https://doc.yunxin.163.com/nertc/guide/zQwNDE1MDU" target="_blank">设置视频属性</a> |
| 监听音频辅流音量 | 支持监听房间内远端用户音频辅流的瞬时音量的回调。 | <a href="/https://doc.yunxin.163.com/nertc/guide/jY5MzQxOTU" target="_blank">监听发言者音量</a> |

**改进优化**

1. 优化高级美颜效果。
2. 优化虚拟背景效果。
2. HTTP DNS 解析优化，实现防域名劫持。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a62d647ee76d11d5790f314e652030878" target="_blank">`updateScreenCaptureParameters`</a> | 更新屏幕共享相关参数。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#ad958fcb663c93a8c84d516effc50e863" target="_blank">`enableLocalVideo(type,enabled)`</a> | 开启或关闭本地视频流的采集和发送（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aedefd8d66a0239826db8d319a6a17f8c" target="_blank">`muteLocalVideoStream(type,mute)`</a> | 取消或恢复发布本地视频流（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0f80132a269b2a7b8fca1a9dd2ca31cb" target="_blank">`setVideoConfig(config,type)`</a> | 设置视频编码属性（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道，且支持在房间内 **动态调用**）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ad54272e9afe1803d01b28408e73badf6" target="_blank">`setCameraCaptureConfig(type,config)`</a> | 设置本地摄像头的采集配置（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a63fc96049bcae9967ae548d92dc388f0" target="_blank">`setExternalVideoSource(type,enable)`</a> | 开启外部视频输入（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aa76b020f35b3623642f210cb291915e7" target="_blank">`pushExternalVideoFrame(type,frame)`</a> | 推送外部视频帧（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aff8e53ae30f5c65263a70fd813c960cf" target="_blank">`startVideoPreview(type)`</a> | 开启视频预览（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae24f563744d3de79d1d012493ba0fac7" target="_blank">`stopVideoPreview(type)`</a> | 关闭视频预览（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_video_device_manager.html#a8da8a94bec7110acc5fc0416a4b812f6" target="_blank">`setDevice(device_id,type)`</a> | 选择视频采集设备（原同名接口废弃，此接口新增 `type` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_video_device_manager.html#a0c4e083f34adcfc18f93ab4f57b84c2f" target="_blank">`getDevice(device_id,type)`</a> | 获取当前使用的视频采集设备信息（原同名接口废弃，此接口新增 `type` 参数，用于开启辅流通道）。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1cc0d1d2f951e1d87f86022186086603" target="_blank">`setLocalVideoMirrorMode(type,mirror_mode)`</a> | 设置本地视频镜像模式（原同名接口保留，此接口新增 `type` 参数，用于开启辅流通道）。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#afff9e85783a59bd32b85db7c12a22c53" target="_blank">`onSubStreamAudioFrameDidRecord`</a> | 辅流采集音频数据回调。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a43c7b0c38a3b0f2f08f7e6c9d249d972" target="_blank">`onUserVideoMute(uid,mute,videoStreamType)`</a> | 远端用户暂停或恢复发送视频流的回调（原同名回调保留，此接口新增 `videoStreamType` 参数，用于辅流通道）。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a4290cb9c42e73178ec5c8a5b6376c527" target="_blank">`onFirstVideoFrameDecoded(uid,width,height,type)`</a> | 已接收到远端视频首帧并完成解码的回调（原同名回调保留，此接口新增 `type` 参数，用于辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a59243fe41b7c71a9ea2daf1cc30f2fb0" target="_blank">`onFirstVideoDataReceived(uid,type)`</a>     | 已显示远端视频首帧的回调（原同名回调保留，此接口新增 `type` 参数，用于辅流通道）。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#acff5c56e9b620b86d33db3a827783279" target="_blank">`onLocalVideoWatermarkState`</a> | `state` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/namespacenertc.html#a14a4bd97dafec1f6c2005e3898b4dad4" target="_blank">`NERtcLocalVideoWatermarkState`</a> 类型新增 `kNERtcLocalWatermarkStateSetSuccess` 等 5 种枚举值，支持字体设置错误等新增水印异常状态回调。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a5917377045d6151993c6866e28b40464" target="_blank">`onRemoteAudioVolumeIndication`</a> | `speakers` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_audio_volume_info.html" target="_blank">`NERtcAudioVolumeInfo`</a> 类型新增 `subStreamVolume` 字段，对应远端辅流音量回调值。 |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#a3b2f9fc878339976305e9d260dc45682" target="_blank">`setBeautyEffectWithValue:atType:`</a> | `type` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html" target="_blank">`NERtcBeautyEffectType`</a>     类型新增 `kNERtcBeautyShortFace` 等 5 种枚举值，支持短脸等新增美颜效果。 |

⭐<span style="font-size:16px;"><b>4.6.13 (2022-06-29)</b></span>

**改进优化**

稳定性提升。

⭐<span style="font-size:16px;"><b>4.6.12 (2022-06-15)</b></span>

**改进优化**

修改默认的日志打印等级为 info。

**问题修复**

1. 修复一些场景下的 SDK 上报问题。
2. 修复音频设备切换问题。
3. 修复使用虚拟背景功能场景下的已知问题。
4. 修复部分场景下的帧率下降问题。

⭐<span style="font-size:16px;"><b>4.6.10 (2022-06-01)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 网易云信美颜 | 网易云信自研的基础美颜和高级美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。 | [网易云信美颜](/https://doc.yunxin.163.com/nertc/guide/Dc0NTk1NjM) |
| 音频辅流 | 支持通过辅流输入伴音文件或自定义音频源。 | [音效与伴音](/https://doc.yunxin.163.com/nertc/guide/jg2OTMyMzg) <br>[自定义音频采集与渲染](/https://doc.yunxin.163.com/nertc/guide/jUzOTUyNzE) |
| 自定义混响效果 | 支持自定义设置本地人声的混响回声效果，赋予声音一定的立体效果。 | [美声变声与混响](/https://doc.yunxin.163.com/nertc/guide/DEwMjAxNTQ) |
| 视频编码水印 | 支持为视频流画面添加编码水印，例如添加公司名称、标语等文字水印、录制时间等时间戳水印、以及 logo 等图片水印。 | [水印](/https://doc.yunxin.163.com/nertc/guide/TMzODg5NTg) |

**改进优化**

1. 修复同一 uid 在多端登录导致的互踢问题。
2. 分离音频的引擎启动逻辑和流发布逻辑，有效减少大房间的性能压力。
3. 支持在房间中根据不同场景切换音频模式，即允许在加入房间后动态切换 audioProfile。

**新增 API**

| API | API 说明 |
| --- | --- |
| [`startBeauty`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#ad2af10fa91062cbf1a63032ec5e34520)     | 开启美颜功能模块。    |
| [`stopBeauty`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#ad3c544274940ddd8b2790dcefe3ee5e6)     | 结束美颜功能模块。    |
| [`isOpenBeauty`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#a7dc8895e201f0ead7eb08e9a1aab1342)     | 暂停或恢复美颜效果。    |
| [`setBeautyEffectWithValue`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#a3b2f9fc878339976305e9d260dc45682)     | 设置美颜效果。    |
| [`addTempleteWithPath`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#a94205bcc6739dcf10c66e9e3422e0006) | 导入美颜资源或模型。 |
| [`addBeautyFilterWithPath`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#ac262a135d491f29765b5395f398de0ee)     | 添加滤镜效果。    |
| [`removeBeautyFilter`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/interface_n_e_rtc_beauty.html#a36c86d8ec8dd3fd7bc4c7b57c2ec99e0)     | 移除滤镜。    |
| [`enableAudioVolumeIndication`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afc6ac753580afdfc61470684826ba9f4)     | 开启说话者音量提示（原同名接口保留，此接口新增 enableVad 参数，用于设置是否启用本地采集人声监测）。    |
| [`onLocalAudioVolumeIndication`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a758b7b32a196ba57a1d658514fdc52a9)     | 提示本地用户瞬时音量的回调（原同名接口保留，此接口新增 vadFlag 参数，用于监测是否存在人声）。    |
| [`enableLocalSubStreamAudio`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#acb645a5a1cb5afecce680b434dd4c365)     | 开启音频辅流。    |
| [`subscribeRemoteSubStreamAudio`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0b202ab655cb6340a61f46e3d25e4df6)     | 订阅远端用户辅流。    |
| [`muteLocalSubStreamAudio`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6ee5eba011bd7d548559c3f35189294f)     | 静音本地音频辅流。    |
| [`setExternalSubStreamAudioSource`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5a20869b06cde0cd1f27b30a8b59fc7f)     | 开启外部音频辅流输入。    |
| [`pushExternalSubStreamAudioFrame`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a30426676dc38d4de6d5f7634e58fd870)     | 推送外部音频辅流数据帧。    |
| [`onUserSubStreamAudioStart`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ac25ac6d99552bad5df1230f95dd4fa41) | 通知远端用户开启音频辅流的回调。 |
| [`onUserSubStreamAudioStop`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#abee8de5ba478662532cdaeb97df0ce3f) | 通知远端用户关闭音频辅流的回调。 |
| [`onUserSubStreamAudioMute`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ac62b4496eee82ab491a0a974817c9fc1) | 通知远端用户暂停或恢复音频辅流的回调。 |
| [`setAudioSubscribeOnlyBy`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a3bbf6feca230d6d11d2a7f3c391d7602)     | 设置本地用户音频只能被房间内其他指定用户订阅。    |
| [`setStreamAlignmentProperty`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0614f1ac47dc2412897db52d543cb3a7)     | 对齐本地系统时间与服务端时间。    |
| [`getNtpTimeOffset`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a371de1d9e1db5a78640de51f078162fa)     | 获取本地系统时间与服务端时间的差值。    |
| [`setLocalVoiceReverbParam`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a201700a4ea2b2368436b77f14e8067cf)     | 开启本地语音混响效果。    |
| [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a45ecd234816646e288e420f0a3a4b346)     | 设置视频水印。    |
| [`onLocalVideoWatermarkState`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#acff5c56e9b620b86d33db3a827783279)     | 通知水印是否成功设置的回调。    |
| [`setScreenCaptureMouseCursor`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a05fddbeddc5f4d542bf4213cd9f08a06)     | 设置共享屏幕时是否显示鼠标。    |
| [`enableMediaPub`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aa708fcf7730759a6338a3ab42829e303) | 发布或停止发布本地音频。 |
| [`onPlaybackSubStreamAudioFrameBeforeMixing`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#a91f715fc703f652fda466c496f9b66bc) | 获取开启音频辅流的远端用户的辅流数据。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| [`startAudioMixing`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5246f41018a7cbcddafd58b54f2aa790) | Option 参数新增 startTimeStamp 和 sendWithAudioType 字段，设置文件播放的起始位置和音频类型。 |
| [`setAudioProfile`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a34c04a16ffdd9702636191073b3dbe99) | 支持在房间内动态调用此接口设置音频属性。 |
| [`setupLocalVideoCanvas`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#ad7306ae7edc1cadedceb6c2cde8df279) | Canvus 参数新增 mirror_mode 字段，设置视频镜像模式。 |
| [`setupRemoteVideoCanvas`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#a16192ada0272bb48adc18848e68dc57d) | Canvus 参数新增 mirror_mode 字段，设置视频镜像模式。 |
| [`setCameraCaptureConfig`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a322058b472af317697dd88e63d9f6bd5) | Config 参数废弃 preference 字段。 |

**废弃 API**

| API | API 说明 |
| --- | --- |
| [`setLocalCanvasWatermarkConfigs`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8841ed31fda3c75d1825a2eee1a7d989) | 此接口已废弃，请使用新接口 [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a45ecd234816646e288e420f0a3a4b346)。 |
| [`setRemoteCanvasWatermarkConfigs`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c66e844c26e4132df88f94a0ff7f53c) | 此接口已废弃。 |

⭐<span style="font-size:16px;"><b>4.6.0 (2022-02-28)</b></span>

网易云信于 2022 年 2 月 28 日发布了 NERTC SDK 最新版本 4.6.0。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 设置音频订阅优先级 | 支持优先订阅远端某用户发布的音频流。在 ASL 策略下，即在服务器线路上选择最清晰的三条音频流传输给本地用户时，本地用户设置优先订阅一个成员的音频流后，即使该成员的说话音量较低或不够清晰，本地用户仍能接收到该指定成员的音频流。 | [设置音频订阅优先级](/https://doc.yunxin.163.com/nertc/guide/Dg5NzEyNTM?platformId=50251) |
| 音频循环缓存录制 | 在原有的支持实时写文件基础上，支持设置仅录制最近一段时间内的音频数据，最高为 15 分钟。 | [客户端音频录制](/https://doc.yunxin.163.com/nertc/guide/Dc0MDQ2NDI?platformId=50251) |
| 共享系统音频 | 支持将本地播放的音频或视频文件的声音分享给远端用户。 | [音频共享](/https://doc.yunxin.163.com/nertc/guide/DQ5MzUzMDA?platformId=50251) |
| 设置虚拟背景 | 支持自动识别用户人像，并将人像周围的环境替换为指定颜色的图片或自定义图像。 | [设置虚拟背景](/https://doc.yunxin.163.com/nertc/guide/Dc4NDM1MzE?platformId=50251) |
| 云代理 | 支持使用云代理服务穿透防火墙限制，使用固定 IP 连接到网易云信服务器。 | [使用云代理](/https://doc.yunxin.163.com/nertc/guide/TUxOTAyMTU?platformId=50251) |

**改进优化**

| 改进优化 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 单声道最高支持码率提升 | 单声道最高音频码率从 64 Kbps 提升至 96 Kbps。 | [设置音频属性](/https://doc.yunxin.163.com/nertc/guide/TkyMjM1MTk?platformId=50251) |

**新增 API**

| API | API 说明 |
| --- | --- |
| [setRemoteHighPriorityAudioStream](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html#a87d04c6b4e6559bcf9c2f79a15b7e26e) | 设置某用户的音频流为高优先级。 |
| [startAudioRecordingWithConfig](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8824e3c55dc5e946b652d7378b3abd8b) | 开启音频录制。 |
| [setCloudProxy](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ade9d3ad8490b2b17492b150773041948) | 开启并设置云代理服务。 |
| [enableVirtualBackground](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a991e26085c72577c984801cb078033f3) | 开启或关闭虚拟背景功能。 |
| [checkNECastAudioDriver](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a2f7d89b813a8ca8659503670a96bd9f0) | 检测设备是否安装最新版本的虚拟声卡。 |
| [onCheckNECastAudioDriverResult](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a662fa013d310d9782d07130bcaef9981) | 检测安装声卡的内容回调。 |
| [onVirtualBackgroundSourceEnabled](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a5a97f3127d454acee2cc24d91325308d) | 通知虚拟背景是否成功开启的回调。 |
| [onMediaRightChange](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a306d34928a341803fdd279e27f24fa66) | 通知音视频权限是否被禁止的回调。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| [startAudioRecording](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#aeb8c89674903a1d520c9bcb1e317bf21) | 新增参数 recordPosition、recordCycleTime，但均只可设为默认值，建议您改用新接口 [startAudioRecordingWithConfig](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8824e3c55dc5e946b652d7378b3abd8b)。 |
| [setExcludeWindowList](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#af8f973d982c661f15c306758f5cc7bbb) | macOS 端支持在开启屏幕共享后，通过此方法动态调整需要屏蔽的窗口列表。 |
| [setVideoConfig](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340) | 通过 orientation_mode 设置本地视频编码的旋转方向时会同时影响本端预览画面和远端视频画面。 |

⭐<span style="font-size:16px;"><b>4.5.0 (2021-10-22)</b></span>

网易云信于 2021 年 10 月 22 日发布了 NERTC SDK 最新版本 4.5.0。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 多房间管理 | 加入多个频道后，用户可以同时接收多个频道的流，但只能同时在一个频道内发流。该功能适用于用户需要同时接收多个频道的流，或频繁切换频道发流的场景。 | [加入多房间](/https://doc.yunxin.163.com/nertc/guide/Dc4MjU4NzA) |
| 通话前网络探测 | 在通话前进行 Last-mile 网络探测，可以获取通话前上下行网络的带宽、丢包、网络抖动和往返时延数据，有效帮助本地用户判断和预测上行网络质量是否良好。 | [通话前网络探测](/https://doc.yunxin.163.com/nertc/guide/TMwOTMyMzY) |
| 摄像头采集偏好设置 | 通过设置摄像头采集偏好，您可以根据实际场景选择优先保证设备性能还是视频质量。 | [setCameraCaptureConfig](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a322058b472af317697dd88e63d9f6bd5) |
| 云端录制支持通过服务端 API 接口配置 | 云端录制支持通过服务端接口进行录制任务的配置。 | - |

**改进优化**

| 改进优化 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 优化本地视频编码属性配置 | - 支持动态调整。在 4.5.0 版本之前，本地视频编码配置在下次开启本端视频时生效。4.5.0 版本开始，您可以根据业务需求，在通话中动态调整视频分辨率等编码属性。 | [setVideoConfig](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340) |\
| | - 分辨率设置超限时取上限值（1080P）。在 4.5.0 版本之前，通过 [setVideoConfig](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340) 设置分辨率时，如果分辨率设置超出参数上限（1080P），则取最小值 360P。4.5.0 版本开始，取最大值 1080P。 | |
| 静音状态下回调采集音量 | 支持设置静音状态下是否返回真实采集音量 | [setParameters](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d):enable_report_volume_when_mute |
| 设置音频设备选择策略 | 桌面端通过 [setParameters](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d) 提供音频设备选择策略参数，可以指定 SDK 优先选择可用设备。 | [setParameters](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d):audio_device_auto_select_type |

**新增 API**

| API | API 说明 |
| --- | --- |
| [subscribeAllRemoteAudioStream](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a60cc44260c67b9735e29115d117ca5dd) | 取消或恢复订阅所有远端用户音频流。 |
| [setCameraCaptureConfig](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a322058b472af317697dd88e63d9f6bd5) | 设置本地摄像头的采集偏好等配置。 |
| [onPlaybackAudioFrameBeforeMixing](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#a2cac2ef6d25a77a1f5667d9ecfb23f46) | 获取指定远端用户混音前的音频数据。在多房间场景下可以通过 channelId 识别不同的房间。原接口 [onPlaybackAudioFrameBeforeMixing](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#aca7dbc83c24716955c4d64b8cd5206f7) 即将废弃，请改用新接口。 |
| [createChannel](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#aaad999ec7dae22a41ae1d083b3612c89) | 创建并获取一个 IRtcChannel 对象，用于多房间场景。 |
| [IRtcChannel](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_channel.html) 接口类 | 在指定房间中实现实时音视频功能。通过创建多个 IRtcChannel 对象，用户可以同时加入多个房间。 |
| [IRtcChannelEventHandler](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_channel_event_handler.html) 接口类 | 用于 SDK 向 App 发送 IRtcChannel 回调事件通知，App 通过继承该接口类的方法获取 SDK IRtcChannel 的事件通知。 |
| [startLastmileProbeTest](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a9c3c3916e214ad79387cad15f63a2796) | 开始通话前网络质量探测。 |
| [stopLastmileProbeTest](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#aeb4a64edddb84ffd3eee0433a2480e90) | 停止通话前网络质量探测。 |
| [onLastmileQuality](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a0437260f6aace77a05441d691e27ae7e) | 通话前网络上下行 last mile 质量状态回调。 |
| [onLastmileProbeResult](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a4f7132c17875c27e6759a93aea67b939) | 通话前网络上下行 Last mile 质量探测报告回调。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| [setParameters](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a7a9135f32ad0e10feb536944fd5a8ab2) | 增加参数 `enable_report_volume_when_mute`，设置本地用户静音时是否返回原始音量。 |\
| | 增加参数 `audio_device_auto_select_type`，设置音频设备自动选择策略。 |
| [NERtcVideoLayerSendStats](/docs/interface/NERTC_SDK/Latest/PC/html/structnertc_1_1_n_e_rtc_video_layer_send_stats.html) | 新增 `capture_width` 和 `capture_height`，查看视频采集宽高。 |
| [setLocalVideoConfig](/docs/interface/NERTC_SDK/Latest/PC/html//docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340) | - 生效时机由下次开启本段视频时生效，改为实时生效。 |\
| | - 分辨率参数设置超限时取最大值。 |

**废弃 API**

| API | API 说明 |
| --- | --- |
| [onPlaybackAudioFrameBeforeMixing](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#aca7dbc83c24716955c4d64b8cd5206f7) | 即将废弃，请改用新接口 [onPlaybackAudioFrameBeforeMixing](/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_n_e_rtc_audio_frame_observer.html#a2cac2ef6d25a77a1f5667d9ecfb23f46)。新接口在多房间场景下可以通过 channelId 识别不同的房间。 |

⭐<span style="font-size:16px;"><b>4.4.2 (2021-09-08)</b></span>

网易云信于 2021 年 9 月 8 日发布了 NERTC SDK 最新版本 4.4.2。

**问题修复**

修复某些场景下的入会失败问题。

⭐<span style="font-size:16px;"><b>4.4.1 (2021-09-03)</b></span>

网易云信于 2021 年 9 月 3 日发布了 NERTC SDK 最新版本 4.4.1。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
    <th><b>相关文档</b></th>
</tr>
<tr>
    <td>加入房间时自动生成 uid</td>
    <td>加入音视频房间时，可以不设置 uid，此时网易云信服务器会自动为您生成一个随机 uid，并在 onJoinChannel 中返回。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#acc3f404cee7cd1b56b5019776dbb660a">joinChannel</a></td>
</tr>
<tr>
    <td>支持音频共享</td>
    <td>在音视频房间中，本地用户可以采集本地声卡的音频数据，并传输给远端用户。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#acc3f404cee7cd1b56b5019776dbb660a">startSystemAudioLoopbackCapture</a></td>
</tr>
<tr>
    <td>支持视频 AI 超分功能</td>
    <td>客户端开启 AI 超分功能之后，符合超分条件的视频流会自动进行 AI 超分处理。</td>
    <td><a href="/https://doc.yunxin.163.com/nertc/guide/DgzODM3ODU">AI 超分</a></td>
</tr>
<tr>
    <td>支持媒体流加密</td>
    <td>网易云信在默认加密算法的基础上，提供了国密加密方案，进一步保障数据安全。</td>
    <td><a href="/https://doc.yunxin.163.com/nertc/guide/TU5MDc0MzQ">媒体流加密</a></td>
</tr>
<tr>
    <td>支持静音状态下回调采集音量</td>
    <td>支持设置静音状态下是否返回真实采集音量</td>
    <td> KNERtcKeyEnableReportVolumeWhenMute </td>
</tr>
</tbody>
</table>

**改进优化**

完善音效功能。

**问题修复**

修复一些偶现的崩溃问题。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a2c95d6b6f1efb3f4b696ea59be9f1655">enableSuperResolution</a></td>
    <td>启用或停止 AI 超分。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4192d089c314b9090fc0d868ca3d2bf4">enableEncryption</a></td>
    <td>开启或关闭媒体流加密。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a44ea82286265381d1a2348fbe5c591b7">enableLoopbackRecording</a></td>
    <td>开启声卡采集。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5b1891d6b398f0fb755541edc993beb1">adjustLoopbackRecordingSignalVolume</a></td>
    <td>调节声卡采集信号音量。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td>setParameters </td>
    <td>增加参数 KNERtcKeyEnableReportVolumeWhenMute。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#acc3f404cee7cd1b56b5019776dbb660a">joinChannel</a></td>
    <td>从 4.4.0 版本开始，uid 可选且默认为 0。</td>
  </tr>
</table>

**废弃 API**

无

⭐<span style="font-size:16px;"><b>4.3.4 (2021-07-13)</b></span>

**问题修复**

修复屏幕共享下偶现的 crash。

⭐<span style="font-size:16px;"><b>4.3.0 (2021-06-04)</b></span>

网易云信于 2021 年 6 月 4 日发布了 NERTC SDK 最新版本 4.3.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
    <th><b>相关文档</b></th>
</tr>
<tr>
    <td>伴音音量设置的生效周期调整</td>
    <td>通过 startAudioMixing 播放伴音时，如果手动设置了伴音播放音量或发送音量，则当前通话中再次调用时默认沿用此设置。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5246f41018a7cbcddafd58b54f2aa790">startAudioMixing</a></td>
</tr>
<tr>
    <td>支持更多伴音格式</td>
    <td>伴音格式支持 MP3、M4A、AAC、3GP、WMA 和 WAV。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9c4a27db0bc0e1c946c4cef1cb42e6f8">playEffect</a></td>
</tr>
<tr>
    <td>视频编码属性支持旋转方向模式和镜像模式</td>
    <td>默认情况下，SDK 在编码时不对视频作镜像和旋转操作。您可以通过参数来设置视频编码的旋转方向模式和镜像模式，以控制远端用户看到的视频画面。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340">setVideoConfig</a></td>
</tr>
<tr>
    <td>视频流回退</td>
    <td>网络不理想的环境下，音视频的质量都会下降。为提升用户体验，您可以通过指定接口设置视频流回退选项。在网络条件差、无法同时保证音频和视频质量的情况下，SDK 会自动将视频流从大流切换为小流，或将媒体流回退为音频流，从而提高音视频质量。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6e7bf7b866be1f34690abb0cd067807d">setLocalPublishFallbackOption</a> 等视频流回退相关 API。</td>
</tr>
<tr>
    <td>跨房间媒体流转发</td>
    <td>在 NERTC 直播场景的音视频房间中，跨房间媒体流转发功能可实现主播角色跨房间与其他主播实时交流互动，在娱乐场景下可实现跨直播间连麦效果。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/DY2Njk2ODA">跨房间媒体流转发 </a> </td>
</tr>
</tbody>
</table>

**改进优化**

优化高清音质下语音的传输码率，在弱网情况下预计减少 1/3。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6e7bf7b866be1f34690abb0cd067807d">setLocalPublishFallbackOption</a></td>
    <td>设置弱网条件下发布的音视频流回退选项。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a062663d28d66d7d3578565e1c39342d2">setRemoteSubscribeFallbackOption</a></td>
    <td>设置弱网条件下订阅的音视频流回退选项。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a20e69e301bed98bf8737ef70c0596c3f">onLocalPublishFallbackToAudioOnly</a></td>
    <td>本地发布流已回退为音频流或恢复为音视频流回调。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a3fe2c727e6dc4e23c1047f3e31718855">onRemoteSubscribeFallbackToAudioOnly</a></td>
    <td>远端订阅流已回退为音频流或恢复为音视频流回调。</td>
  </tr>
  <tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a3c217fa914aad57cd006caa26b12ffe3">startChannelMediaRelay</a> </td>
    <td>开始跨房间媒体流转发。</td>
  </tr>
  <tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a4a1a35c122cd0bba634b312fd00399eb">updateChannelMediaRelay</a> </td>
    <td>更新媒体流转发的目标房间。</td>
  </tr>
  <tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#a55348f3e72af97ef6b9eabb8adfec11b">stopChannelMediaRelay</a> </td>
    <td>停止跨房间媒体流转发。</td>
    </tr>
  <tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ab8c4d3c3a2d3f695200694ab3805dd62">onMediaRelayStateChanged</a> </td>
    <td>跨房间媒体流转发状态发生改变回调。</td>
  </tr>
  <tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a4e6ab72395627936258caa5a176654f9">onMediaRelayEvent</a> </td>
    <td>媒体流相关转发事件回调。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>变更说明</b></th>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5246f41018a7cbcddafd58b54f2aa790">startAudioMixing</a></td>
    <td>通过 startAudioMixing 播放伴音时，如果手动设置了伴音播放音量或发送音量，则当前通话中再次调用时默认沿用此设置。</td>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9c4a27db0bc0e1c946c4cef1cb42e6f8">playEffect</a></td>
    <td>伴音格式支持 MP3、M4A、AAC、3GP、WMA 和 WAV。</td>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac50b8b00d7237e518d3d785e63377340">setVideoConfig</a></td>
    <td>增加 mirror_mode 用于指定镜像模式。增加 orientation_mode 用于指定旋转方向模式。</td>
  </tr>
</table>

**废弃 API**

无

⭐<span style="font-size:16px;"><b>4.2.1 (2021-05-19)</b></span>

网易云信于 2021 年 5 月 19 日发布了 NERTC SDK 最新版本 4.2.1。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
    <th><b>相关文档</b></th>
</tr>
<tr>
    <td>调节远端用户在本地播放的音量</td>
    <td>通过 adjustUserPlaybackSignalVolume 可以调节指定远端用户混音后的音频流在本地播放的音量。</td>
    <td><a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/Latest/iOS/html/protocol_i_n_e_rtc_engine_ex-p.html#ac18e835c5a7b2123e25eff15de54f825">adjustUserPlaybackSignalVolume</a></td>
</tr>
</tbody>
</table>

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/Latest/iOS/html/protocol_i_n_e_rtc_engine_ex-p.html#ac18e835c5a7b2123e25eff15de54f825">adjustUserPlaybackSignalVolume</a></td>
    <td>调节本地播放的指定远端用户的信号音量。</td>
  </tr>
</table>

**变更 API**

无

**废弃 API**

无

⭐<span style="font-size:16px;"><b>4.2.0 (2021-05-12)</b></span>

网易云信于 2021 年 5 月 12 日发布了 NERTC SDK 最新版本 4.2.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
    <th><b>相关文档</b></th>
</tr>
<tr>
    <td>支持双人通话的独立场景</td>
    <td>NERTC 在 4.1.0 版本中提供了更加适合双人房间场景的底层策略，优化双人房间时的音视频质量效果。双人通话功能适用于点对点通话的业务场景，搭配呼叫组件可以实现点对点呼叫。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/TYxODI3MjA">双人通话</a> </td>
</tr>
<tr>
    <td>音视频房间快速切换</td>
    <td>NERTC SDK 通过新增 API switchChannel 支持直播场景下的音视频房间快速切换。直播场景下，音视频房间中的观众角色可以通过该方法快速切换房间。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#a827ecfee86c395f564a18012fa919b59">switchChannel</a> </td>
</tr>
<tr>
    <td>NERTC R​estful API 支持用房间名称（cname）发起调用</td>
    <td>音视频通话和互动直播场景的服务端 API 通过新 URL 的方式支持使用房间名称发起调用，同时原 URL 及调用方式仍旧保留以保证新老兼容。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/zY3NDA3MTc">API 概览</a> </td>
</tr>
<tr>
    <td>自定义音频渲染</td>
    <td>NERTC SDK 支持自定义音频渲染功能。拉取远端发送的音频数据之后，可使用自定义的渲染器进行音频渲染。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/jUzOTUyNzE">自定义音频渲染</a> </td>
</tr>
<tr>
    <td>设置用户媒体流优先级</td>
    <td>支持设置本地用户的媒体流为优先级。如果某个用户的优先级为高，那么该用户媒体流的优先级就会高于其他用户，弱网环境下 SDK 会优先保证其他用户收到的、高优先级用户的媒体流的质量。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aaf1800b55ee5c5c53f6af694bbd4b74b">setLocalMediaPriority</a></td>
</tr>
<tr>
    <td>客户端截图功能</td>
    <td>支持针对实时视频流进行截图，包括本地主流画面、本地辅流画面、远端主流和辅流画面。音视频通话过程中，用户可以通过视频截图功能截取实时视频流画面，以便后续的存档分析、事件备忘、证据留存等等。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/jQyOTI1NTM">视频截图</a> </td>
</tr>
<tr>
    <td>客户端音频录制</td>
    <td>支持在客户端侧进行实时音频流录制，包含房间内所有用户混流后的音频数据。开启录制时可以指定录制文件的存放路径及格式、录制采样率、音质等。</td>
    <td> <a href="/https://doc.yunxin.163.com/nertc/guide/Dc0MDQ2NDI">客户端音频录制</a> </td>
</tr>
</tbody>
</table>

**改进优化**

<table>
  <thead>
    <tr>
     <th><b>新增功能</b></th>
     <th><b>功能描述</b></th>
    </tr>
  </thead>
   <tbody>
    <tr>
     <td>优化音视频大房间的表现效果</td>
     <td>客户端上实现音频选路策略 ASL，在大房间的场景中降低客户端上性能消耗，来提升客户端上能支持的用户连接上限。配合级联服务器的使用，可以将房间内并发人数提升到万人。详细说明请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/Tk0MzA1ODc?platformId=50002#如何创建 RTC 大房间？">大房间使用说明</a>。</td>
    </tr>
    <tr>
     <td>优化变声美声效果</td>
     <td>改造现有美声变声接口，提供更加丰富的美声和混响效果。新版美声变声接口有改动，若您已接入美声功能，升级 4.1.0 版本时请注意接口变更。详细说明请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/DEwMjAxNTQ">美声与变声</a>。</td>
    </tr>
    <tr>
     <td>视频引擎优化</td>
     <td><ul><li>支持视频 AI 超分，通过机器学习等 AI 算法，改善因受限于网络带宽限制或实时性的要求导致视频分辨偏低的问题，实现低分辨率视频在传输后进行细节补充的效果以优化接收端的视频清晰度，从而提升用户体验。</li><li>NE265 新增支持 iOS 端硬件编码，目前 NE265 编码协议，支持 mac&windows&iOS 端的编码和 Native 全端的解码。整体压缩效率较 NE264 提升 40，但编码速度慢 25%。</li></ul></td>
    </tr>
    <tr>
     <td>耳机场景下效果优化</td>
     <td>优化戴耳机场景下回声和双讲卡顿效果。优化耳返的延时，从 300ms 降低到 80ms。</td>
    </tr>
   </tbody>
</table>

**问题修复**

修复蓝牙耳机音频通话被系统电话打断后，无法恢复到蓝牙耳机的问题。

**新增 API**

<table>
<tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine.html#a827ecfee86c395f564a18012fa919b59">switchChannel</a> </td>
    <td>直播场景下快速切换音视频房间。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#af1d4e68e36c0e30d7bed6e5e00fc51d8">setAudioEffectPreset</a> </td>
    <td>设置 SDK 预设的人声的变声音效。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a81b7ea061c4b61a518689ab3bf83e17a">setVoiceBeautifierPreset</a> </td>
    <td>设置 SDK 预设的美声效果。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ab1ff742d724ab296826a3128b98c60d9">setLocalVoicePitch</a> </td>
    <td>设置本地语音音调。</td>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a37efd1ec3002171e754fadd46663867d">setLocalVoiceEqualization</a> </td>
    <td>设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#adf31aa3cfb4fa6cec57fbac46b47595d">setExternalAudioRender</a> </td>
    <td>设置外部音频渲染。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a22f7611bf3d9462c03d3bf77f1e5fdb4">pullExternalAudioFrame</a> </td>
    <td>拉取外部音频数据。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aaf1800b55ee5c5c53f6af694bbd4b74b">setLocalMediaPriority</a> </td>
    <td>设置本地用户的媒体流优先级。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0c64c195919c2fb4c98ad32f1057afc6">takeLocalSnapshot</a> </td>
    <td>本地视频画面截图。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a28966129e4f879209bf06e01617fa50a">takeRemoteSnapshot</a> </td>
    <td>远端视频画面截图。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_n_e_rtc_take_snapshot_callback.html#ad4cb868ec2fbd8bd35efc3101f343687">onTakeSnapshotResult</a> </td>
    <td>截图结果回调。   </td>
    </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aeb8c89674903a1d520c9bcb1e317bf21">startAudioRecording</a> </td>
    <td>开始客户端录音。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a396bf624ce83207b668954a32fba49dc">stopAudioRecording</a> </td>
    <td>停止客户端录音。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a1eabc3477df26bde007bcaf69bb19d0f">onAudioRecording</a> </td>
    <td>音频录制状态回调。</td>
  </tr><tr>
    <td> <a href="/docs/interface/NERTC_SDK/Latest/PC/html/classnertc_1_1_i_rtc_engine_ex.html#af8f973d982c661f15c306758f5cc7bbb">setExcludeWindowList</a> </td>
    <td>设置共享指定屏幕区域时，需要屏蔽的窗口列表。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d">setParameters</a> </td>
    <td>复杂参数设置接口，增加 1V1 参数。</td>
  </tr>
</table>

**废弃 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> setLocalVoiceEqualizationPreset </td>
    <td>设置 SDK 预设的美声效果。推荐改用新方法 setVoiceBeautifierPreset。</td>
  </tr>
  <tr>
    <td> setLocalVoiceEqualization</td>
    <td>设置本地语音音效均衡。推荐改用新方法 setLocalVoiceEqualization。</td>
  </tr>
  <tr>
    <td>setLocalVoiceChangerPreset</td>
    <td>使用 SDK 预设的变声效果。推荐改用新方法 setAudioEffectPreset 和 setLocalVoicePitch。</td>
  </tr>
  <tr>
    <td> setLocalVoiceReverbPreset </td>
    <td>使用 SDK 预设的混响效果。推荐改用新方法 setVoiceBeautifierPreset。</td>
  </tr>
</table>

⭐<span style="font-size:16px;"><b><span id="[4.0.1] - 2021-03-05"> 4.0.1 (2021-03-05)</span></b></span>

**修复**

1. 修复 video 下码率分配异常的问题。
2. 优化音频质量。

⭐<span style="font-size:16px;"><b><span id="[4.0.0] - 2021-02-24"> 4.0.0 (2021-02-24)</span></b></span>

网易云信于 2021 年 2 月 24 日发布了 NERTC SDK 最新版本 4.0.0，在音视频能力和性能方面均有显著优化。从 4.0.0 版本开始，NERTC 支持媒体补充增强信息（SEI）、可设置视频镜像模式、新增美声变声功能。

⭐<span style="font-size:16px;"><b><span id="新增特性">新增特性</span></b></span>

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
    <th><b>相关文档</b></th>
</tr>
<tr>
    <td>发送媒体补充增强信息</td>
    <td>NERTC 支持将时间戳等自定义数据作为流媒体补充增强信息（SEI Supplemental Enhancement Information）的一部分，通过流媒体通道将其与视频内容打包在一起，发送给远端用户，以此实现文本数据与音视频内容的精准同步的目的。</td>
    <td><a href="/https://doc.yunxin.163.com/nertc/guide/TUzNDA1NDQ">媒体补充增强信息</a></td>
</tr>
<tr>
    <td>美声与变声</td>
    <td>支持美声的预设效果、美声的自定义调节、变声的预设效果和混响的场景化效果。</td>
    <td><a href="/https://doc.yunxin.163.com/nertc/guide/zUxMDI5MDM">美声与变声</a></td>
</tr>
<tr>
    <td>自定义音频渲染</td>
    <td>NERTC SDK 支持自定义音频渲染功能。拉取远端发送的音频数据之后，可使用自定义的渲染器进行音频渲染。</td>
    <td><a href="/https://doc.yunxin.163.com/nertc/guide/zUxMDI5MDM">自定义音频采集与渲染</a></td>
</tr>
</tbody>
</table>

⭐<span style="font-size:16px;"><b><span id="改进优化">改进优化</span></b></span>

<table>
  <thead>
    <tr>
     <th><b>新增功能</b></th>
     <th><b>功能描述</b></th>
    </tr>
  </thead>
   <tbody>
    <tr>
     <td>伴音错误码优化</td>
     <td>增加伴音任务状态相关的错误码，为伴音问题排查提供依据。</td>
    </tr>
   </tbody>
</table>

**<span id="新增 API">新增 API</span>**

| **API** | **API 说明** |
| --- | --- |
| [setLocalVoiceEqualizationPreset](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a79fe83fc07f87dbf00fdbd8b838914e0) | 设置 SDK 预设的美声效果。 |
| [setLocalVoiceEqualizations](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a03054858d70109c4378a701c6fb25a50) | 设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率。 |
| [setLocalVoiceReverbPreset](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aadac953901152fb2d9f4b63827da8d61) | 设置 SDK 预设的混响效果。 |
| [setLocalVoiceChangerPreset](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a91f68db9b7efbce9b0f177b481f35d3f) | 设置 SDK 预设的人声的变声音效。 |
| [sendSEIMsg](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aea98675fa90088569a24e57a4edf145a) | 通过主流通道发送媒体补充增强信息。 |
| [sendSEIMsg](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac8e8af17dcb2d80d2e1e00a9d0bd4856) | 发送媒体补充增强信息。通过本接口可指定发送 SEI 时使用主流或辅流通道。 |
| [onRecvSEIMsg](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a7ae085dd56871d5f27abc6498c02d6ac) | 收到远端流的 SEI 内容回调。 |

**<span id="变更 API">变更 API</span>**

| **API** | **API 说明** |
| --- | --- |
| [onAudioMixingStateChanged](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a39351279a586979bc1ef25d10433894b) | 伴音错误码回调。NERtcAudioMixingErrorCode 中增加 NERtcAudioMixingErrorFatal 等错误码。 |
| [addLiveStreamTask](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae53d9d69d13da31179e98c467b3788d5) | 创建推流任务。NERtcLiveStreamTaskInfo 增加 config 结构体，用于配置音视频流属性。 |
| [updateLiveStreamTask](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#abba8d7c5094509960589e9b6e56c0ef6) | 更新推流任务。NERtcLiveStreamTaskInfo 增加 config 结构体，用于配置音视频流属性。 |

⭐<span style="font-size:16px;"><b><span id="[3.9.0] - 2021-01-08"> 3.9.0 (2021-01-08)</span></b></span>

**新增**

1. 新增实时音视频辅流功能。
2. 支持设置屏幕共享内容类型。
3. 直播模式下支持设置房间角色。
4. 支持自定义音频输入。
5. 音频支持 AI 降噪能力。
6. 支持音视频啸叫检测。

**技术优化**

1. 支持全新的网易自研 NEVC 编码协议，具有相较于开源的 AVC 和 HEVC 更优越的性能，同等码率下提升视频整体清晰度，提高鲁棒性和错误恢复能力，优化用户的视频感官体验。
2. 屏幕共享画面优化，提升静态共享画面的清晰度，优化用户体验。
3. 支持暗场景视频图像增强，优化暗场景下的通话体验。

⭐<span style="font-size:16px;"><b><span id="[3.8.1] - 2020-12-04"> 3.8.1 (2020-12-04)</span></b></span>

**新增**

1. 房间连接状态通知功能。
2. 支持视频设备调试与配置。
3. 在语音场景中新增一档高清语音选项。

⭐<span style="font-size:16px;"><b><span id="[3.7.3] - 2020-11-20"> 3.7.3 (2020-11-20)</span></b></span>

**优化**

针对音视频引擎底层模块进行优化。

⭐<span style="font-size:16px;"><b><span id="[3.7.1] - 2020-10-29"> 3.7.1 (2020-10-29)</span></b></span>

**修复**

- 修复释放 engine 偶发的 crash 问题

- 修复播放采样率异常触发的麦开启问题

⭐<span style="font-size:16px;"><b><span id="[3.7.0] - 2020-09-28"> 3.7.0 (2020-09-28)</span></b></span>

**新增**

- 新增发布流类型配置以及大小流开关。

- 新增视频属性灵活配置。

- 新增双声道效果支持。

**优化**

- 回声消除模块优化，提升单讲、双讲场景下的音质效果。

- 进入房间时默认打开音频设备。

⭐<span style="font-size:16px;"><b><span id="[3.6.2] - 2020-08-31"> 3.6.2 (2020-08-31)</span></b></span>

**新增**

- 新增支持视频外部渲染。

**修复**

- 修复异常网络下偶现的崩溃的问题。

- 修复偶现无声音问题。

⭐<span style="font-size:16px;"><b><span id="[3.6.0] - 2020-08-20"> 3.6.0 (2020-08-20)</span></b></span>

**新增**

- 新增音视频质量透明数据回调功能。

- 新增音视频设置房间模式功能。

- 新增伴音在线音频文件支持。

**优化**

- 优化本地渲染体验，使渲染效果更加流畅。

- 优化音频质量，保证多端音量稳定。

⭐<span style="font-size:16px;"><b><span id="[3.5.2] - 2020-07-21"> 3.5.2 (2020-07-21)</span></b></span>

**优化**

- 语音场景下优化音频降噪能力，提升默认的降噪等级。

⭐<span style="font-size:16px;"><b><span id="[3.5.1] - 2020-07-06"> 3.5.1 (2020-07-06)</span></b></span>

**修复**

- 修复无远端音频的情况下，音频回调不会触发的问题。

⭐<span style="font-size:16px;"><b><span id="[3.5.0] - 2020-05-28"> 3.5.0 (2020-06-23)</span></b></span>

**新增**

- 新增自定义视频数据输入功能。

- 新增互动直播支持占位图片功能。

- 新增订阅/取消订阅所有远端音频功能。

**优化**

- 优化视频清晰度订阅机制，通过订阅大小流的方式来选择订阅视频的清晰度。

- 优化蓝牙耳机通话场景适配。

- 优化视频抗丢包能力,视频抗丢包能力提升到 40%（50ms rtt 情况下）。

**变更**

- 弃用通话模式设置，统一为多人会议场景。

⭐<span style="font-size:16px;"><b><span id="[3.4.2] - 2020-05-28"> 3.4.2 (2020-05-28)</span></b></span>

**新增**

- 支持 NAT64 网络。

**优化**

- 互动直播任务，连续操作的时序保证。

⭐<span style="font-size:16px;"><b><span id="[3.4.1] - 2020-05-11"> 3.4.1 (2020-05-11)</span></b></span>

**优化**

- 修复了 iOS 在某些版本上偶现的崩溃问题。

⭐<span style="font-size:16px;"><b><span id="[3.4.0] - 2020-04-28"> 3.4.0 (2020-04-28)</span></b></span>

**新增**

- 新增互动直播推流功能。

- 音频效果优化，新增音乐场景模式支持。

- 新增网络状态回调。

**优化**

- 音频通话效果优化。

- 网络切换优化，网络变更音视频恢复更加流畅。

⭐<span style="font-size:16px;"><b><span id="[3.3.0] - 2020-03-31"> 3.3.0 (2020-03-31)</span></b></span>

**新增**

- 新增音频场景设置。

- 新增音频数据回调。

- 新增屏幕共享功能。

⭐<span style="font-size:16px;"><b><span id="[3.2.0] - 2020-01-15"> 3.2.0 (2020-01-15)</span></b></span>

**新增**

- 新增录屏模式。

- 支持音视频加密功能。

- 接口优化接入更加方便。

⭐<span style="font-size:16px;"><b><span id="[3.1.0] - 2019-11-19"> 3.1.0 (2019-11-19)</span></b></span>

**新增**

- 支持多人会议功能。

- 支持多流发送与订阅功能。

⭐<span style="font-size:16px;"><b><span id="[3.0.0] - 2019-09-29"> 3.0.0 (2019-09-29)</span></b></span>

**新增**

- 支持音视频通话功能。
:::

## 5.9.15 (2025-12-18)

**新增功能**

- **AI 降噪增强**：音频 AI 降噪场景下利用声纹人声增强技术，显著提升背景人声降噪效果。
- **编码前马赛克功能**：支持外部调用设置编码前马赛克，提供马赛克和区域马赛克两种处理能力。
- **视频暗光增强**：新增暗光增强功能，可在光线亮度偏低和亮度不均匀环境下，自适应调整视频画面亮度值，恢复并凸显图像细节信息，全面提升视频图像视觉效果。
- **Player 点播支持**：Player 组件新增点播功能支持。
- **会中设备检测**：支持会中的音视频设备检测功能。
- **批注合流功能**：屏幕共享支持和外部输入的批注合流。

**功能优化**

- **设备管理优化**：优化视频设备变化机制。 
- **共享声音易用性改进**：优化屏幕共享时的音频处理流程。

## 5.9.10 (2025-09-24)

**新增功能**

- **屏幕共享增强**：支持配置色彩空间配置选项，提升共享内容的色彩还原度和观看体验。
- **音频缓冲配置优化**：支持普通耳返缓冲区大小的配置，有效降低音频延迟，提升实时互动体验。
- **视频调试工具增强**：支持不同类型的视频数据导出，便于开发调试和问题排查，相关接口请参考 [`setVideoDump`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a43a025a2cdf282ab7ca33f466eea1d70)。
- **音频调试功能增强**：音频数据导出支持分级生成不同类型的文件，并可配置生成带时间戳的文件名。

**功能优化**

- **KTV 场景优化**：调整默认音效参数配置，提升 KTV 模式下人声表现力和音质体验。
- **背景音乐保护**：改进噪声门限和 AI 语音检测算法，避免对小音量背景音乐的误判，保证音乐流畅播放。

## 5.9.5 (2025-08-14)

- 辅流音频音质增强，支持配置码率、采样频率、声道模式（单声道/双声道）、音频编码模式等参数。
- 共享声音降噪优化。
- 修复已知问题，提升用户体验。

## 5.9.0 (2025-07-02)

**新增功能**

- **新增视频色彩空间功能**：支持多种色彩标准（如 BT.709）和色彩范围（Limited/Full Range），适用于高质量视频直播、影视制作及专业视频会议场景，提升视频画质表现力。
    - 支持设置视频采集的色彩空间参数，通过 `NERtcCameraCaptureConfiguration` 配置。
    - 支持在自采集模式下设置色彩空间参数，通过 `NERtcVideoFrame` 中的 [`color_space_range`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_frame.html#afb19a34d84b7b0c07743e330e0590c26)（色彩范围）和 [`color_space_matrix`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_video_frame.html#a3da9962b3693d3a2dd20e8d1cde3bb28)（色彩矩阵标准）相关枚举选项。
    - 支持画面渲染和自渲染时的色彩空间处理。
    - 支持截图功能和视频算法（美颜、人脸检测、视频增强等）兼容各种色彩空间。

- **RTMP 拉流播放功能**：拉流时无需加入房间<!--，与 RTMP 推流功能互斥（当前版本暂不支持 B 帧及多路流拉取） -->，适用于直播观看和直播连麦场景，实现更灵活的内容分发。

- **字幕翻译增强**：支持多源语言和多目标语言的实时翻译，具体通过 [dst_languages](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_a_s_r_caption_config.html#a10877a31fdebf03c8840872b17ad593d) 和 [src_languages](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_a_s_r_caption_config.html#a90ce57d3c22ed9a1f29f98f07e4d7b5a) 字段指定语言。

- **跨房间推流控制**：提供更精细的直播控制能力，支持暂停（`pause`）和恢复（`resume`）跨房间推流。

- **虚拟背景能力上报**：在用户加入房间事件时，上报设备支持的虚拟背景能力级别信息，适用于需要根据设备性能动态调整虚拟背景效果的场景。

**功能优化**

- 优化音频处理系统，提升 AEC 回声消除效果，音质效果优化。
- 改进屏幕共享性能，降低高分辨率共享时的资源占用。
- 优化多显示器场景下的屏幕选择和捕获逻辑。

**缺陷修复**

- 修复在某些 Apple Silicon 设备上摄像头初始化延迟的问题。
- 修复在 macOS Ventura 及更高版本系统上的权限请求机制。
- 修复多种音频处理相关问题，提升通话稳定性。

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

- 新增支持 IPv6 网络解析与接入，提升全球网络兼容性。
- 新增音频的 AI 降噪与啸叫检测功能开关，开发者可一键启用或关闭。
- 新增支持 AI 服务相关操作的数据回调（[`onAiData`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a751d63d82944233eb1077ebce7c586eb)）。

## 5.8.0 (2025-02-26)

- 支持 Simulcast（Simultaneous Multistream，多流传输）视频编码和传输技术，同时发送三个不同分辨率和码率的视频流，提高音视频的网络条件和设备性能适应性。相关 API 请参考 [`setVideoStreamLayerCount`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html#ae255c20378309d07a3238d9c714f1920)。
- 其他已知问题优化修复。

## 5.7.0 (2025-01-20)

- 支持通过加密的 WSS（WebSocket Secure）协议通道传输实时通信中的信令数据。
- 将实时视频流推流到直播服务器时，支持超时检测，提升直播的稳定性。
- 修复已知问题，提升用户体验。

## 5.6.50 (2024-12-27)

**新增特性**

- AI 任务支持实时字幕、AI 打断功能。相关接口请参考 [`startASRCaption`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1689a0bdcf317353d05e806bcb4140d7)。使用示例请参考 <a href="https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client">基于 RTC SDK 实现与 AI 数字人音视频互动</a>。

- 本地录制支持纯音频录制。相关接口请参考 [`addLocalRecorderStreamForTask`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1689a0bdcf317353d05e806bcb4140d7)，使用示例请参考 [本地录制](https://doc.yunxin.163.com/nertc/guide/jE4MTM3NzE?platform=macOS)。

- 本地录制支持对录制文件进行 MP4 转码。相关接口请参考 [`stopLocalRecorderRemuxMp4`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a115e5599310219d54897737b12feafe7)。

- 本地录制支持录制音频共享声音。

**升级更新**

支持 XCFramework 框架格式。采用 [手动集成](https://doc.yunxin.163.com/nertc/guide/DI3NDEyNDI?platform=macOS#%E6%96%B9%E5%BC%8F%E4%BA%8C%E6%89%8B%E5%8A%A8%E9%9B%86%E6%88%90) RTC SDK 的开发者，在从低版本升级至 5.6.50 版本时，请注意 `.framework` 文件已更名为 `.xcframework`，需重新添加 XCFramework 依赖。更多详情请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/TU2NDQwNzQ?platform=macOS#5650)。

## 5.6.40 (2024-11-22)

**新增特性**

- 新增本地录制功能，录制的文件可存储在设备的内置存储或外接存储设备上。您可以调用 [`addLocalRecorderStreamForTask`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a423faa49f1bd4e92a1e70ba2fd6f149c) 等相关接口实现功能。
- 新增两路视频传输通道，用户可以同时发送两路视频流。最高可同时支持发送四路视频。适用于直播、监控、远程协作等场景中。
- 提升虚拟背景容错能力。传入无效文件作为虚拟背景时，虚拟背景使用单色模式。
- 支持使用视频文件作为虚拟背景（`kNERtcBackgroundVideo`）。
- 新增获取网络类型功能（[`getNetworkType`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aed26e7c2f27a84c157bdc678447003e5)），包括 2G、3G、4G、5G、Wi-Fi、运营商网络、以太网、无网络等结果。
- 新增网络变化回调（`onNetworkConnectionTypeChanged`）。

**升级更新**

针对构建了多房间功能的用户需注意，多房间场景下的接口行为变更如下：

- 本地音频采集和发送接口 [`enableLocalAudio`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html#ac746f2cd380bbfeee1a0d56957a387aa) 打开音频设备时，行为互斥修改为不互斥。
- 本地媒体流（主流）的发送接口 [`enableMediaPub`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html#add4150cf7de0bec23523a216c978245c) 发布音频流时，行为不互斥修改为互斥。

即在多房间下实现发送音频流，如果只需保持设备按需开启，您需要：

1. 先关闭上一个房间的音频流，即 `enableMediaPub`=`false` / `enableLocalAudio`=`false`。
2. 然后在当前房间实现发送音频数据流，即 `enableMediaPub`=`true` / `enableLocalAudio`=`true`。

在多房间下实现发送音频流，如果需要音频采集设备一直开启，您需要：

1. 在成员加入每个房间前，调用一次 `enableLocalAudio`。
2. 后续音频流发布到具体的房间只需由 `enableMediaPub` 控制。

## 5.6.34 (2024-10-31)

修复已知问题。

## 5.6.30 (2024-08-22)

- 新增直播推流的实时质量透明数据回调。
- 提升了音频共享功能的易用性：
    - 支持在无麦克风权限的情况下，开启音频共享。
    - 修复了偶现的音频共享无声的问题。
- 提升了虚拟背景开启的设备适配性和覆盖面。具体请参考 [`getFeatureSupportedType()`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a46ff91f4e6554478ffa909ee59722312) 和 [`enableVirtualBackground()`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a449e5810ccd9e8e66cea2942baf0fd06)。
- 改进了通话模式下的回声消除策略。
- 提升了通话模式下的突发弱网抗性。
- 日志系统支持多进程架构。

## 5.6.25 (2024-07-24)

- [`NERtcLiveStreamTaskInfo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_live_stream_task_info.html) 中 `taskId` 字段变更为可选，支持不设置或设置为空。在这种情况下，推流任务 ID 由 SDK 生成并管理，并将在用户离开时自动清除。如果需要手动清除推流任务，调用 removeLiveStreamTask 接口，并将 task_id 指定为空即可。
- 提升了 CDN 推流成功率。

## 5.6.20 (2024-07-10)

- 增加了标准场景下的 KTV 模式（[`kNERtcChannelProfileKaraoke`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/namespacenertc.html#ac30f4b7ce13da5d664df0d2a6986e940)），优化外放情况下的音质，深度适配 K 歌业务场景。
- 扩大了智码超清的适用范围。在远端使用硬件解码视频的情况下，也能完整支持。
- 优化了使用外部渲染时的性能。

## 5.6.10 (2024-06-14)

- 提升了秀场直播场景中的音视频效果，以及接入易用性。从 5.6.10 版本起，您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。
- 改进了视频编码策略，在低端机型设备上也有更好地的能表现。
- 优化了软编模式下的视频抗锯齿算法，提升了视频清晰度。

## 5.6.0 (2024-05-10)

- 优化了屏幕共享，支持过滤排除自身进程相关窗口，支持共享虚拟桌面。
- 优化 QoS 弱网环境的对抗算法，提升抖动网络下的音频质量。
- 优化了音频编解码算法，提升音频质量。
- 减小了 SDK 包的体积。
- 增强了应用运行稳定性。

## 5.5.40 (2024-04-03)

**新增特性**

- 为方便开发者快速接入，SDK 新增多种预设场景。当前支持的预设场景包括：标准 1 对 1 音视频通话、高画质 1 对 1 音视频通话、标准语聊房、高音质语聊房、会议场景。
- 支持初始化时指定 audio dump 路径。

**改进优化**

优化 AI 降噪设置，提升降噪效果。

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`setAudioProfile [1/2]`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afdf5835ec7a5cabf46c43f2b4cc8b030) | 设置音频编码属性 |
| [`setAudioScenario`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a9e04d67b24dd6ff47551ca20fe3e3cd1) | 设置音频编码属性的应用场景 |

**变更 API**

| 接口 | 变更说明 |
| ---- | ---- |
| [`NERtcChannelProfileType`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/namespacenertc.html#ac30f4b7ce13da5d664df0d2a6986e940) | 房间场景新增以下枚举值：<li>kNERtcChannelProfileVideoCall = 3<li>kNERtcChannelProfileHighQualityVideoCall = 4<li>kNERtcChannelProfileChatroom = 5<li>kNERtcChannelProfileHighQualityChatroom = 6<li>kNERtcChannelProfileMeeting = 7 |

## 5.5.32 (2024-03-15)

**改进优化**

- 优化音频编码传输策略，提升弱网和带限场景下的适应能力，降低设备功耗。
- 优化音频 3A 算法，提升扬声器外放场景的交互音质。
- 支持定制裁剪一些视频特效功能，减小包体积。

## 5.5.30 (2024-02-29)

**变更 API**

| 接口/回调/类 | 接口/回调/类说明 |
| ---- | ---- |
| [`NERtcScreenCaptureParameters`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_screen_capture_parameters.html#a2777e899ce17ed9c28ee353c0121b099) | 新增加成员变量 `force_update_data`，用于设置 SDK 高亮时，是否触发 [`onScreenCaptureSourceDataUpdate`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel_event_handler.html#a148a63ee934f3b10ab48e7149722fbaa) 回调。默认为 `false`（不回调）。 |

**改进优化**

- 提升了屏幕共享的采集效率。
- 提升了重新开始屏幕共享时的响应速度。

**问题修复**

修复了视频渲染的偶现崩溃问题。

## 5.5.21 (2024-01-18)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`isFeatureSupported`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a8e0c108aabf5d3405e1623e1effa7ba1) | 查询当前设备是否支持虚拟背景功能。 |

**变更 API**

| 接口 | 变更说明 |
| ---- | ---- |
| [`NERtcErrorCode`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/namespacenertc.html#af062cfe332d58922ac8c020d55f9bb17) | 新增以下枚举值：<li>kNERtcErrJoinInterruptedDueToLeaveAction = 30028<li>kNERtcErrJoinInterruptedDueToDestroyAction = 30029<li>kNERtcErrJoinInterruptedDueToAppTermination = 30030 |
| [`NERtcEncryptionConfig`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_encryption_config.html) | 增加成员变量自定义加密回调 `observer`。 |
| [`NERtcEncryptionMode`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/namespacenertc.html#a7764748e566fbe9a5738478228088b25) | 增加枚举自定义加密模式 `EncryptionModeCustom`。 |
| [`NERtcFeatureType`](https://doc.yunxin.163.com/docs/interface/nertc/macOS/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_feature_type.html) | 增加枚举 `NERtcFeatureType.kNERTCVirtualBackground`，功能类型为虚拟背景。 |

**改进优化**

低端设备音频质量改进。

## 5.5.11 (2023-12-05)

- 提升首次安装时的登录成功率。
- 修复特定条件下小概率的房间角色错误问题。
- 提升语聊房场景的音频效果。
- 提升稳定性。

## 5.5.10 (2023-10-31)

**升级必看**

如果您计划将应用中使用的旧版本 RTC SDK 从 5.5.2 升级为当前版本，请根据接口变更，更新相应的代码，具体请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/Dk2NTU1NDM?platform=Android)。

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| 范围语音 | 在一个 RTC 房间内，用户可以与一定距离内的其他用户进行实时语音通话，支持 **仅小队** 或 **所有人** 的语音模式。它可以让玩家在游戏中实时交流，从而更好地协调战术和策略。 | [范围语音](https://doc.yunxin.163.com/nertc/guide/DQ0MTc0NTY?platform=macOS) |
| 音频推拉流的黑白名单 | 您可以设置推流白名单、拉流白名单或拉流黑名单，从而实现只推流给指定用户或只订阅指定用户的音频，以便满足游戏语音等场景下的需求。 | [设置音频转发路由](https://doc.yunxin.163.com/nertc/guide/TA4MjQ1NTM?platform=macOS)
| 限定访问区域 | 为满足客户在海外访问域名合规性，云信支持访问区域限制功能。无论用户身处何地使用 App，SDK 都只会访问指定区域的域名。 | [限定 RTC SDK 的 访问区域](https://doc.yunxin.163.com/Overseas/docs/DYzMjg1ODI?platform=others#限定-rtc-sdk-的-访问区域)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [ `initSpatializer`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4cad276e2451c1db83595ccde648de5c) | 初始化空间音效 |
| [ `setAudioRecvRange`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aa2a512b95a1f7e63f7badbcee4bcf9c8) | 设置空间音效的距离衰减属性和语音范围 |
| [ `setRangeAudioTeamID`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a59d6a3682f8caf0a269fbbadd98c490f) | 设置范围语音的队伍号 |
| [ `setRangeAudioMode`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a07611bb7ed19996d07325c7a7f25c87f) | 设置范围语音的模式 |
| [ `setSubscribeAudioAllowlist`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aeaaf2f1c998691211506399ab2c1df89) | 设置只订阅指定用户的音频流 |
| [ `setSubscribeAudioBlocklist`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae16ccf75a8965adb3328708a50423665) | 设置不订阅指定用户的音频流 |
| [`onFirstVideoFrameRender`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel_event_handler.html#a065b0cbd8cef7c30eb85d8828b115640) | 已接收到远端视频首帧并完成渲染的回调 |
| [`onAudioHasHowling`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a3d791701962ed5e7ebd81bda8fee1570) | 啸叫消失的回调 |

**变更 API**

| 接口/回调 | 变更说明 |
| ---- | ---- |
| [`NERtcDistanceRolloffModel`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/namespacenertc.html#aed5324bd7a40767f0f2c6ae857fa9e2c) | 空间音效的距离衰减模式新增`kNERtcDistanceRolloffLinearOnly(3)`选项，表示仅线性衰减，没有方位效果 |
| [`setAudioRecvRange`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#aa2a512b95a1f7e63f7badbcee4bcf9c8) | 接口名称修改，对应的原接口名称为 `UpdateSpatializerAudioRecvRange`。 |
| [`updateSelfPosition`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a7d1e68f02ce3128fd85837bd431cce1f) | 接口名称修改，对应的原接口名称为 `UpdateSpatializerSelfPosition`。 |
| [`enableSpatializer`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a67b3b111c797d82912ef931f095ed23a) | 新增 `apply_to_team` 参数。 |
| [`NERtcPositionInfo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/structnertc_1_1_n_e_rtc_position_info.html) | 结构体名称修改，对应的原结构体名称为 `NERtcSpatializerPositionInfo`。 |
| [`NERtcOption`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/namespacenertc.html#aae48c04d286d3c3701054d7a10226fc1) | 新增 `area_code_type` 参数，用于限定访问区域。 |
| [`onAudioHasHowling`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a3d791701962ed5e7ebd81bda8fee1570) | 原先只有检测到啸叫时会触发 `onAudioHasHowling（true）`回调，5.5.10 版本新增当啸叫消失时，也会触发 `onAudioHasHowling（false）`回调。 |

**改进优化**

- 优化断网重连之后音画同步效果。
- 优化弱网场景入会时长和首帧耗时。
- 画质不变情况下，降低视频码率和性能开销。
- 优化音乐场景下回声消除和降噪效果。

## 5.4.10 (2023-10-20)

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| 屏幕共享 | 屏幕共享支持获取可共享的窗口列表、高亮显示共享窗口的边框、在屏幕共享过程中快速切换共享的窗口。 | [屏幕共享](https://doc.yunxin.163.com/nertc/guide/TgyMjE3MDE?platform=macOS) |

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`getScreenCaptureSources`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.4.10/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a10585dd4a762ccebd06addbb7c57c096) | 获取可共享窗口和屏幕的列表。 |
| [`setScreenCaptureSource`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.4.10/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a39f8b8e9b6aa1c428ce225beacb8896d) | 在屏幕共享过程中快速切换共享的窗口。 |

**变更 API**

| 接口/回调 | 变更说明 |
| ---- | ---- |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a1c10c8522dc6715388ffe62f165beed7" target="_blank">`startScreenCaptureByScreenRect`</a> | 开启屏幕共享的 [`NERtcScreenCaptureParameters`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.4.10/zh/html/structnertc_1_1_n_e_rtc_screen_capture_parameters.html) 参数中，新增 `enable_high_light`、`high_light_width`、`high_light_color`、`high_light_length`字段，用于设置高亮显示共享窗口的边框参数。 |
| [`startScreenCaptureByDisplayId`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5cb1422adb8f08cb30ca70cc0822db89) | ^^ |
| <a href="https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a8eab357982a5fa500e4e5d5eadb42923" target="_blank">`startScreenCaptureByWindowId`</a> | ^^ |
| [`startScreenCaptureByDisplayId`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.4.10/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a5cb1422adb8f08cb30ca70cc0822db89) | 由原先的只支持 macOS 平台，修改为同时支持 macOS 和 macOS 平台。 |

## 5.5.2 (2023-10-07)

**改进优化**

- 优化信令连接，提高在 UDP 不通情况下的入会速度和成功率。
- 优化信令数据，提高入会速度。

## 5.5.0 (2023-08-29)

**改进优化**

- 优化 SDK 的包体积大小
- 优化 SDK 的首帧耗时

- 优化 ne264 编码器，提升弱网场景的视频体验
- 优化视频 pipeline，提升中低端手机的视频流畅度
- 虚拟背景功能适配更多机型

- 视频水印功能支持所有设备和平台
- 虚拟背景和视频水印功能启用硬件分级策略
- 针对低性能设备，提供更加稳定的音频质量
- 在 Music 场景，声音外放时，优化回声消除效果
- 针对噪声和回声处的音量放大做适当控制

- 支持华为 AudioKit

## 5.4.7 (2023-08-09)

**问题修复**

修复部分已知问题。

## 5.4.3 (2023-07-27)

**改进优化**

- 音频 opus 编码器支持 24kHz 采样率。
- Windows 端支持硬件编码和硬件解码，桌面端适配硬编硬解。
- 针对 Windows 端和 macOS 端，优化增益调整策略，使主讲人的语音更突出，通过控制其他杂音（周围小声音或远处干扰音）的语音放大策略。

**问题修复**

修复部分已知问题。

## 5.4.1 (2023-07-18)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`onRemoteVideoReceiveSizeChanged`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ae1258721f277ca0c39fc546bb595a50c) | 远端视频分辨率变化的回调。 |
| [`onLocalVideoRenderSizeChanged`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a8a48c702016e6a3c0d293f1ff0babd21) | 本地视频预览分辨率变化的回调。 |

**问题修复**

修复部分已知问题。

## 5.4.0 (2023-07-04)

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| 空间音效 | 空间音效也称 3D 音效，是通过在音频信号中添加空间信息，使得听众可以感受到声音来自于特定的位置和空间环境。它可以增强音频的真实感和沉浸感，让听众感受到更加真实的声音效果。 | [空间音效](https://doc.yunxin.163.com/nertc/guide/TUxNzg0NjM?platform=macOS) |

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`enableSpatializer`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a0f3fcf9e337d633b215a25c7d346582b) | 开启/关闭空间音效。 |
| [`updateSpatializerAudioRecvRange`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ae7e407ee359548e341b470110392bb93) | 设置空间音效的距离衰减属性和语音范围。 |
| [`setSpatializerRoomProperty`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a6fa56b1bcb25fe14765422eab70911ea) | 设置房间混响属性。 |
| [`enableSpatializerRoomEffects`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ab0aac4e7b96a08636de717911faa8e5b) | 开启或关闭空间音效的房间混响效果。 |
| [`updateSpatializerSelfPosition`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#afbc1b907c9620afa66e39d7506f425da) | 设置说话者和接收者的位置信息。 |
| [`setSpatializerRenderMode`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4a48f2700aa45fb781d864e8a045f47e) | 设置渲染模式。 |

**改进优化**

- AI 降噪能力优化，提升了人声音质和降噪量，有效地抑制各种噪声而不会损伤人声。在教育和会议场景中，它针对人声（如小孩声和笑声）做了保护，避免这些声音被过度抑制。
- 优化 AEC 算法，重点改进本端和远端双讲时的效果。
- 通过优化音频 NACK 请求，降低音频在弱网环境下的端到端延时。
- 在弱网络条件下优化首帧耗时。
- 改善极端弱网络环境下的视频清晰度。
- 优化包大小，移除 VP9 编码。
- 优化 NE264 编码器。

## 5.3.11 (2023-08-16)

**问题修复**

修复部分已知问题。

## 5.3.8 (2023-07-21)

**问题修复**

修复部分已知问题。
## 5.3.7 (2023-06-16)

**问题修复**

修复部分已知问题。

## 5.3.6 (2023-06-02)

**问题修复**

修复部分已知问题。

## 5.3.5 (2023-05-24)

**新增特性**

支持纯音频 SDK。请通过 [网易云信 SDK 下载中心](https://doc.yunxin.163.com/nertc/sdk-download) 下载纯音频的 SDK 包。

**问题修复**

修复部分已知问题。

## 5.3.3 (2023-05-15)
**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- | --- |
| 调节本地播放的指定房间内所有远端用户的音量。 | 在多房间场景中，可以使用该方法单独调整主房间或者某个子房间的所有远端用户的播放音量。 | <a href="https://doc.yunxin.163.com/nertc/guide/zUyNTE3MDU?platform=macOS#设置播放音量" target="_blank">设置通话音量</a> |

**改进优化**

新增支持 Mac ARM 64 架构。

## 5.3.1 (2023-05-05)

网易云信于 2023 年 5 月 5 日正式发布 NERTC SDK 5.3.1 版本。该版本提供统一的业务需求实现和更友好的跨平台接入支持，并以更小的包体积帮助您实现快速接入。

**升级必看**

如果您计划将应用中使用的旧版本 RTC SDK 从 4.6.X 升级为当前版本，请根据接口变更，更新相应的代码，具体请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/TU2NDQwNzQ?platform=macOS)。

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| 插件化集成人脸增强、视频超分、视频降噪功能 | 支持通过插件化集成人脸增强、视频嘲讽、视频降噪功能，提升 SDK 集成的灵活性与易操作性，减小 App 的包体积。 | [集成 SDK](https://doc.yunxin.163.com/nertc/guide/DI3NDEyNDI?platform=macOS) |
| 本地数据通道 | 支持通过本地数据通道传输除音、视频数据之外的其他数据。 | 不涉及 |
| 子房间功能优化 | 支持自定义视频采集、设置房间中用户音量实时回调、切换前后置摄像头。 | [多房间管理](https://doc.yunxin.163.com/nertc/guide/Dc4MjU4NzA?platform=macOS) |
| 麦克风关闭时发伴音 | 支持用户在麦克风关闭时，发送伴音。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/jg2OTMyMzg?platform=macOS) |

**改进优化**

- 支持非主播角色成员或在连接异常状态下，删除推流任务。
- 支持通过不同的 uid 进入子房间。
- 支持日志加密默认开启。
- 各端对齐日志的内容、文件命名和默认存放路径。macOS 端的默认日志路径为：`~/Documents/Logs`。

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`enableLocalData`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#ac7ab6b0db45682faf6fcaed5b12c1bb9) | 开启或关闭本地数据通道。 |
| [`subscribeRemoteData`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a7c40cfd10e99b2db987af27e368425ed) | 取消或恢复订阅指定远端用户数据通道流。 |
| [`sendData`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a3d33758e10a15f8fc960e40de1c65a83) | 通过数据通道发送数据。 |
| [`onUserDataStart`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a930d21feabc51faa24a18f03757b1753) | 远端用户通过数据通道发送数据的回调。 |
| [`onUserDataStop`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a90017fb1ffa97b1545c4bb3c3e264452) | 远端用户停用数据通道的回调。 |
| [`onUserDataReceiveMessage`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a620db38063c0589fa006c9cb9b085a8a) | 远端用户通过数据通道接收数据的回调。 |
| [`onUserDataStateChanged`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#a60d718a50c283ed5af42be80daa4a40c) | 远端用户数据通道使用状态改变通知回调。 |
| [`onUserDataBufferedAmountChanged`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ae4105f8e752f4ee92e8d2d881ac829e5) | 远端用户数据通道待传输数据量改变通知回调。 |

**变更 API**

| 接口/回调 | 变更说明 |
| ---- | ---- |
| [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a45ecd234816646e288e420f0a3a4b346) | `NERtcVideoWatermarkTextConfig` 和 `NERtcVideoWatermarkTimestampConfig` 结构体里的 `fontPath` 名字改为 `fontName`。 |
| [`NERtcLocalVideoWatermarkState`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/namespacenertc.html#a14a4bd97dafec1f6c2005e3898b4dad4) | 删除了 `kNERtcLocalVideoWatermarkStateFontPathEmpty` 这个状态。 |
| [`enableLocalVideo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_channel.html#a5c336b19e3c9b0db9a73b9515d7108d7) | 开启屏幕共享接口 `startScreenCapture` 与开启本地视频辅流通道接口 [`enableLocalVideo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_channel.html#a5c336b19e3c9b0db9a73b9515d7108d7) 互斥。<ul><li>如果当前正在屏幕共享，调用 [`enableLocalVideo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_channel.html#a5c336b19e3c9b0db9a73b9515d7108d7) 开启辅流时，需要调用`stopScreenCapture` 先停止屏幕共享。<li>如果当前正在使用本地视频辅流通道进行本地摄像头采集或者外部自定义视频输入，调用 `startScreenCapture` 开启屏幕共享时，需要先调用 [`enableLocalVideo`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_channel.html#a5c336b19e3c9b0db9a73b9515d7108d7) 停止辅流。
| [`onCaptureVideoFrame`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ad0423dae090d924f82a8765bacca3365) | 视频采集数据回调 [`onCaptureVideoFrame`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_event_handler_ex.html#ad0423dae090d924f82a8765bacca3365) 默认关闭。若您使用了视频采集数据回调功能，请先调用 [`setParameter`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d)方法开启此回调，将`kNERtcKeyEnableVideoCaptureObserver`参数设置为 `true`。 |
| [`setParameter`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a4d39a81643f19979461ec0bb569f4a0d) | 新增 kNERtcKeyEnableVideoCaptureObserver 字段，用于开启视频采集数据回调。 |
| [`NERtcEngineContext`](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/V5.3.1/zh/html/structnertc_1_1_n_e_rtc_engine_context.html) | 废弃 `log_file_max_size_KBytes` 字段，日志加密和压缩后，不能完全按照该 size 进行控制。 |

**功能下线**

5.3.0 及之后版本不再支持 [**画布水印（setLocalCanvasWatermarkConfigs 和 setRemoteCanvasWatermarkConfigs）**](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_channel.html#a8cd5388d0e2dff89f8fb297dfc76d02b) 功能，统一使用 [**编码水印（setLocalVideoWatermarkConfigs）**](https://doc.yunxin.163.com/nertc/references/macOS/doxygen/Latest/zh/html/classnertc_1_1_i_rtc_engine_ex.html#a45ecd234816646e288e420f0a3a4b346)。编码水印可以从源头保证数据的真实性，具体请参考 [水印](https://doc.yunxin.163.com/nertc/guide/TMzODg5NTg?platform=macOS)。