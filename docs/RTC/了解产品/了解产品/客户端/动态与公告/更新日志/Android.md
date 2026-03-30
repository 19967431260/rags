本文介绍网易云信音视频通话 NERTC SDK Android 端的版本更新日志。具体功能请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=android) 和 查看 [API 文档](https://doc.yunxin.163.com/nertc/client-apis?platform=android)。

<div class="card">
<span style="font-size:16px;"><b>近期重要更新</b></span>
  <ul>
    <li>从 5.6.50 开始，AI 任务支持实时字幕、AI 打断功能。使用示例请参考 <a href="https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client">基于 RTC SDK 实现与 AI 数字人音视频互动</a>。</li>
    <li>从 5.6.10 开始，您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。详情请参考 <a href="https://doc.yunxin.163.com/nertc/guide/Tc4MDgyMjY?platform=android">CDN 推流</a>。</li>
    <li>从 5.5.40 开始，为方便开发者快速接入，NERTC SDK 新增多种预设场景。当前支持的预设场景包括标准 1 对 1 音视频通话、高画质 1 对 1 音视频通话、标准语聊房、高音质语聊房、会议场景。</li>
    <li>从 5.5.32 开始，支持定制裁剪一些视频特效功能，有效减小包体积。</li>
    <li>从 5.5.10 开始，支持 <a href="https://doc.yunxin.163.com/Overseas/guide/DYzMjg1ODI?platform=others#%E9%99%90%E5%AE%9A%20RTC%20SDK%20%E7%9A%84%20%E8%AE%BF%E9%97%AE%E5%8C%BA%E5%9F%9F"><b>限定 NERTC SDK 的访问区域</b></a>。在出海场景中，满足客户在全球国家或地区的访问域名的合规性。</li>
  </ul>
</div>

<style>
table th:first-of-type {width: 35%;}
</style>

:::details 单击展开查看 3.0.0 (2019-09-29) ~ 4.6.67 (2023-11-30) 版本 NERTC SDK 的更新日志。

⭐<span style="font-size:16px;"><b>重要更新提示</b></span>
  <ul>
    <li>从 4.6.29 开始，支持 <a href="https://doc.yunxin.163.com/nertc/guide/DU3Mjk0MzQ" target="_blank"><b>高级 Token 鉴权</b></a>, 支持对用户创建、加入房间和订阅、发布音视频流的权限进行校验，帮助您有效避免客户端遭遇破解攻击的问题。</li>
    <li>从 4.6.20 开始，支持以 <b>插件化</b> 方式集成 <b>美颜</b>、<b>虚拟背景</b>、<b>AI 降噪</b>、<b>AI 啸叫检测</b>，提升 SDK 集成的灵活性与易操作性，您可以根据需要自行选择是否集成对应特性的动态库，使 App 的包体积更小，具体请参考 <a href="https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI" target="_blank">集成 SDK</a>。</li>
    <li>从 4.6.20 开始，支持通过 <b>视频辅流通道</b> 开启本地摄像头采集、自定义视频源输入等，具体请参考 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ac0ae5d451a01fe2510d1c21e909c247a" target="_blank">设置视频编码属性</a> 和 <a href="https://doc.yunxin.163.com/nertc/guide/zA4ODA1NTM?platform=android">自定义视频采集</a>。</li>
  </ul>
</div>

⭐<span style="font-size:16px;"><b>4.6.67 (2023-11-30)</b></span>

**问题修复**

适配安卓 14 系统，修复小部分机型的崩溃问题。

⭐<span style="font-size:16px;"><b>4.6.65 (2023-10-31)</b></span>

**问题修复**

- SDK 数据上报相关的优化和调整。
- 修复 `setVideoCallback` 接口返回的 I420 数据格式问题。
- 修复由于系统异常导致 SDK 崩溃问题。

⭐<span style="font-size:16px;"><b>4.6.61 (2023-09-01)</b></span>

**新增特性**

| 新增特性 | 特性描述 |
| --- | --- |
| 外部 PCM 音频数据混音 | 支持将外部 PCM 数据混入 RTC 本地播放或者发送远端，用于实现例如 **一起看抖音** 等场景。 |

**新增 API**

 API | API 说明 |
--- | --- |
[`NERtcEx#startExternalAudioMixing()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a3cb1264b68e0e7c46dc63daf4adc8eff) | 开启外部 PCM 音频数据混音
[`NERtcEx#stopExternalAudioMixing()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#add832adf6c84e9e53f6d9309385f698a) | 关闭外部 PCM 音频数据混音
[`NERtcEx#pushExternalAudioMixingFrame()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aba81e55cf6208e8f21a1631ed02e3628) | 推送 PCM 音频帧数据用于混音
[`NERtcEx#setExternalAudioMixingPlaybackVolume()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ab90b3d3bd76d3820d7d22d943e12860e) | 设置外部 PCM 数据混音本地播放音量
[`NERtcEx#getExternalAudioMixingPlaybackVolume()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad0b77e1b826c74d76dfb0d34c4cfac3b) | 获取外部 PCM 数据混音的播放音量
[`NERtcEx#setExternalAudioMixingSendVolume()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2e9d25b5af7f2423ff9d5c54dbbab7a9) | 设置外部 PCM 数据混音发送音量
[`NERtcEx#getExternalAudioMixingSendVolume()` ](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1b6891bf2e9bcaeaf9e6efb77c28a1e6) | 获取外部 PCM 数据混音的播放音量
[`NERtcCallbackEx#onLocalAudioFirstPacketSent()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.61/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#af51ddce0b451fefe0610e152a59f3865) | 本地第一帧音频发送到远端的回调

**问题修复**

- 修复频繁调用 `playEffect` 和 `stopEffect` 导致无响应的问题。

- 在不开启本地音频采集但播放伴音的场景中，优化角色切换时的音频发送逻辑。

⭐<span style="font-size:16px;"><b>4.6.56 (2023-06-30)</b></span>

**改进优化**

当用户未赋予 `BLUETOOTH_CONNECT` 权限时，支持使用手机麦克风采集声音。

**问题修复**

- 修复 Android 多线程环境下，个别 API 调用引起的崩溃问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b>4.6.53 (2023-05-11)</b></span>

**新增特性**

| 新增特性 | 特性描述 |
| --- | --- |
| 自定义加密 | <a href="https://doc.yunxin.163.com/nertc/guide/DQwNjAzMDY?platform=android" target="_blank">媒体流加密</a> 新增支持自定义加密模式。除了国密算法，您可以使用自己独特的加密算法，使产品更安全、更难被攻击者破解。 |

⭐<span style="font-size:16px;"><b>4.6.52 (2023-05-04)</b></span>

**问题修复**

- 修复了个别 Android 机型上出现的黑屏闪烁问题。
- 修复了 Android 端偶现的日志打印奔溃问题。

⭐<span style="font-size:16px;"><b>4.6.50 (2023-03-28)</b></span>

**升级必看**

从 4.6.43 升级至 4.6.50 版本，涉及如下接口变更，您需要结合实际业务场景更新相关的 App 代码：

| 变更描述 | 集成修改建议 |
| ---- | ---- | ---- |
| `IVideoRender` 中增加 `setExternalRender` 方法，自定义使用外部渲染器时的视频数据类型。 | 为避免编译失败，您需要在代码中对该接口增加空实现 |
| `IVideoRender` 中增加 `isExternalRender` 方法，查询当前是否已设置外部渲染器。 | 若需要实现自定义渲染，该接口的值请设置为 `true` |
| `IVideoRender` 中增加 `setVideoBufferType` 方法，设置为外部渲染。 | 为避免编译失败，您需要在代码中对该接口增加空实现 |
| `IVideoRender` 中增加 `getVideoBufferType` 方法，获取当前视频视频数据类型。 | 按需要的真实的视频数据类型返回就行

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 调节本地播放的指定房间内所有远端用户的音量。 | 在多房间场景中，可以使用该方法单独调整主房间或者某个子房间的所有远端用户的播放音量。 | <a href="https://doc.yunxin.163.com/nertc/guide/jUzMjAxNTc?platform=android#设置播放音量" target="_blank">设置通话音量</a> |

**改进优化**

- App 进程从后台切换至前台时，增加开启摄像头的失败重试次数。
- 修复部分场景下，误触发 `onError` 回调的问题。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a4c92ede9b8470f83aae95317c4158004" target="_blank">`adjustChannelPlaybackSignalVolume`</a> | 调节本地播放的指定房间内所有远端用户的音量。 |
| `setVideoBufferType` | 自定义使用外部渲染器时的视频数据类型。 |
| `getVideoBufferType` | 获取当前视频视频数据类型。 |
| `setExternalRender` | 设置为外部渲染。 |
| `isExternalRender` | 查询当前是否已设置外部渲染器。 |

⭐<span style="font-size:16px;"><b>4.6.43 (2023-02-20)</b></span>

**问题修复**

修复了并发加房间时，偶现的多线程崩溃问题。

⭐<span style="font-size:16px;"><b>4.6.42 (2023-02-01)</b></span>

**问题修复**

- 修复 http3 请求导致的崩溃问题。
- 兼容部分鸿蒙系统的崩溃问题。

⭐<span style="font-size:16px;"><b>4.6.40 (2023-01-10)</b></span>

**升级必看**

自 4.6.40 起，AI 降噪功能以 **插件化** 方式提供，对应的 AI 降噪库为 `libNERtcAiDenoise.so`，可以与核心 SDK（基础音视频库）搭配使用，具体集成方式请参考 <a href="https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI" target="_blank">集成 SDK</a>。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 音频裸流传输支持 ASL 选路 | 支持将编码后音频的音量数据传递给 SDK，以支持音频裸流参与 ASL 选路。 | <a href="https://doc.yunxin.163.com/nertc/guide/Dc1NTM2MTA" target="_blank">音频裸流传输</a> |
| 自定义视频画布颜色 | 支持设置视频画布的背景色，当视频尺寸与显示视窗尺寸不一致时，可以自定义改变传统黑框的颜色。 | - |

**改进优化**

- 支持平滑入会，优化摄像头预览期间的入会体验。
- 支持动态设置引擎回调，提高多场景切换的易用性。
- 子房间支持权限密钥相关回调的事件通知。

**问题修复**

修复入会场景下的已知问题。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a125cf1bb27e87e23c9da7bd89f5d0cc7" target="_blank">`setNERtcCallback`</a> | 设置事件通知回调。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html#a45138854fdf975f42a7e3c3ff14f9511" target="_blank">`onPermissionKeyWillExpire`</a> | （子房间）权限密钥即将过期回调。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html#a34a713196fd3f0fdf43ccfa3b8e609c5" target="_blank">`onUpdatePermissionKey`</a> | （子房间）更新权限密钥成功回调。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac78574d45092ea560886d8d0cc5e1b6a" target="_blank">`pushExternalAudioEncodedFrame`</a> | `encodedAudioFrame` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_encoded_frame.html" target="_blank">`NERtcAudioEncodedFrame`</a>    类型新增 `rmsLevel` 字段，对应音频裸流主流的音量值。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac78574d45092ea560886d8d0cc5e1b6a" target="_blank">`pushExternalSubStreamAudioEncodedFrame`</a> | `encodedAudioFrame` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#abc15d2647292e4ef1c65bfb7a0a18836" target="_blank">`NERtcAudioEncodedFrame`</a>    类型新增 `rmsLevel` 字段，对应音频裸流辅流的音量值。 |

⭐<span style="font-size:16px;"><b>4.6.29 (2022-11-18)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 高级 Token 鉴权 | 支持对用户创建、加入房间和订阅、发布音视频流的权限进行校验，帮助您有效避免客户端遭遇破解攻击的问题。 | <a href="https://doc.yunxin.163.com/nertc/guide/DU3Mjk0MzQ" target="_blank">高级 Token 鉴权 </a> |
| 设置混音文件音调 | 支持调整伴音和音效文件的音调，以实现例如在 K 歌场景中，为了使歌曲更适合主播的声线音域，升高或降低伴奏的音阶。 | <a href="https://doc.yunxin.163.com/nertc/guide/zA2MTIwNjk" target="_blank">音效与伴音</a> |
| 音视频裸流传输 | 支持音视频裸流传输，您可以向 NERTC SDK 提供自定义格式的音视频编码数据，并由 NERTC SDK 进行推流。 | <a href="https://doc.yunxin.163.com/nertc/guide/Dc1NTM2MTA" target="_blank">音频裸流传输</a>、<a href="https://doc.yunxin.163.com/nertc/guide/DQzNDk3ODE" target="_blank">视频裸流传输</a> |

**改进优化**

优化加入房间进程。

**问题修复**

- 修复伴音场景下的已知问题。
- 修复无法正常加入房间的问题。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a53a91a0990a55753e319f1719761b599" target="_blank">`joinChannel`</a> | 加入音视频房间（原同名接口保留，此接口新增 `channelOptions` 参数，用于携带自定义入会信息）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ac2d5b0020278cc81e69c8df81c862b4a" target="_blank">`updatePermissionKey`</a> | 设置新的权限密钥。 |
| [`setEffectPitch`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a21714c1b3f02363756fae2b4faf3c749) | 设置音效文件的音调。 |
| [`getEffectPitch`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aecb034dfcbadb6e28c7a33821b30e947) | 获取音效文件的音调。 |
| [`setEffectPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a57a974d0bf765b527058c7dac150699b) | 设置音效文件的播放位置。 |
| [`getAudioMixingPitch`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aaf80dd3bcf1590a689c6dc262cf2a418) | 获取伴音文件的音调。 |
| [`setAudioMixingPitch`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a6aa203077e0d9c1df6e5205d00a551c7) | 设置伴音文件的音调。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac78574d45092ea560886d8d0cc5e1b6a" target="_blank">`pushExternalAudioEncodedFrame`</a> | 推送外部音频主流编码帧。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#abc15d2647292e4ef1c65bfb7a0a18836" target="_blank">`pushExternalSubStreamAudioEncodedFrame`</a> | 推送外部音频辅流编码帧。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a601f459db392590ba0edea86376a356b" target="_blank">`setPreDecodeObserver`</a> | 注册解码前媒体数据观测器。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a6838f1da1f06d06a7e17164e9be60387" target="_blank">`pushExternalVideoEncodedFrame`</a> | 推送外部视频主流或辅流编码帧。 |
| [`setVideoEncoderQosObserver`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1f2a45aba16f257292018b10e70b033d) | 注册视频编码 QoS 信息监听器。 |
| [`onUserJoined`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback.html#ab45b16f9e05378c0e8b383f02aeb89a6) | 远端用户加入房间回调（原同名回调不建议使用，此回调新增 `joinExtraInfo` 参数，用于返回自定义入会信息）。 |
| [`onUserLeave`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback.html#af9b8bdecbdda52fcdfe092ef59cd2710) | 远端用户离开房间回调（原同名回调不建议使用，此回调新增 `leaveExtraInfo` 参数，用于返回自定义入会信息）。 |
| [`onPermissionKeyWillExpire`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a0e96d5648217e1f90c5e589cbf395b74) | 权限密钥即将过期回调。 |
| [`onUpdatePermissionKey`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#afb31b7cd35c95fb1b1aa4bd64346058e) | 更新权限密钥成功回调。 |
| [`onAudioEffectTimestampUpdate`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a62545c14cb5321e18c97eb8fa80cdd69) | 音效文件播放进度回调。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1predecoder_1_1_n_e_rtc_pre_decode_observer.html#a91a24226449d5e6ebb8434b0ad54c9a4" target="_blank">`onFrame`</a> | 解码前媒体数据回调。 |
| [`onRequestSendKeyFrame`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_encoder_qos_observer.html#a5a76bffbea1223336712ae89da38c12c) | I 帧请求事件回调。 |
| [`onVideoCodecUpdated`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_encoder_qos_observer.html#aeb91f0ae2d07a9603b822e66d1bcfb21) | 视频编码器类型信息回调。 |
| [`onBitrateUpdated`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_encoder_qos_observer.html#a7e865ad0746d5dd744075d6cd458b56f) | 视频码率信息回调。 |

⭐<span style="font-size:16px;"><b>4.6.22 (2022-11-02)</b></span>

**改进优化**

1. 视频后处理中增加丢帧处理机制。
2. 视频采集帧率提升。
3. 耳返延时优化。

**问题修复**

1. 修复订阅远端音视频流与画布设置的异步问题。
2. 修复安全通审核自动打码视频主流，但在视频辅流中生效的问题。

⭐<span style="font-size:16px;"><b>4.6.20 (2022-09-08)</b></span>

**升级必看**

1. 自 4.6.20 起，支持以 **插件化** 方式集成美颜、虚拟背景等功能，提升 SDK 集成的灵活性与易操作性，您根据需要自行选择是否集成对应特性的动态库，以实现轻量接入裁剪包，更多请参考 <a href="https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI" target="_blank">集成 SDK</a>。
2. 自 4.6.20 起，实现 **网易云信美颜** 所必需的资源文件（**beauty** 文件夹以及人脸模型文件 **model.dat**）已经随 SDK 发布至 maven 仓库中，若您已手动拷贝上述美颜资源文件且通过 Maven 集成 SDK，请参考以下步骤进行升级。
    1. 在本地项目中删除 `assets` 目录下的美颜资源文件夹 **beauty** 以及人脸模型文件 **model.dat**、**netease.lic** （若存在）。
    2. 更新 Maven 仓库的 NERTC SDK 版本为 4.6.20 或更新版本。
    3. 卸载 App 后重试（覆盖安装无法清空 App 私有目录，本地美颜资源版本号可能无法检测到 SDK 版本升级而无法重新拷贝资源文件）。
    ::: note note
    若您不按上述步骤进行操作，可能会出现本地美颜资源文件版本号与 App 私有目录下的美颜资源不匹配的情况，从而导致花屏等其他异常问题。
    :::
3. 自 4.6.20 起，新增了以下回调：
    - 远端用户暂停或恢复发送视频流回调：<a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a33f0fa75d8a9bd31bc9dc6dd54de8f6b" target="_blank">`onUserVideoMute(streamType)`</a>
    - 已显示首帧远端视频的回调：<a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5196530aff2a0518a1b9a4f3306219c9" target="_blank">`onFirstVideoDataReceived(streamType)`</a>
    - 已接收到远端视频首帧并完成解码的回调：<a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a8dbc8636e3aa3473c48ffee043d47996" target="_blank">`onFirstVideoFrameDecoded(streamType)`</a>

    若您在初始化引擎时实现的回调类是 **`NERtcCallbackEx`**，则需要 **手动** 在该实现类中新增以上回调方法。若您实现的是 **`AbsNERtcCallbackEx`** 类，则无需更新代码。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 视频辅流通道优化 | 支持通过视频辅流通道开启本地摄像头采集、自定义视频源输入等。 | <a href="https://doc.yunxin.163.com/nertc/guide/jEzNTM2NDg" target="_blank">设置视频属性</a> |
| 监听音频辅流音量 | 支持监听房间内远端用户音频辅流的瞬时音量的回调。 | <a href="https://doc.yunxin.163.com/nertc/guide/Tk3NTA4MDg" target="_blank">监听发言者音量</a> |

**改进优化**

1. 优化高级美颜效果。
2. HTTP DNS 解析优化，实现防域名劫持。

**新增 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ad5c6e217dacfc20546617d98e3b5ba9b" target="_blank">`enableLocalVideo(streamType,enable)`</a> | 开启或关闭本地视频流的采集和发送（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道，且支持在房间内动态调用）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a62d4b02f3f3c3b231f03a1da23f1b845" target="_blank">`muteLocalVideoStream(streamType,mute)`</a> | 取消或恢复发布本地视频流（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ac0ae5d451a01fe2510d1c21e909c247a" target="_blank">`setLocalVideoConfig(videoConfig,streamType)`</a> | 设置视频编码属性（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ada5553b88fe5dd19572872fb59eee564" target="_blank">`setCameraCaptureConfig(captureConfig,streamType)`</a> | 设置本地摄像头的采集配置（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a0b6f78498f4dfa59697af30679130f02" target="_blank">`setExternalVideoSource(streamType,enable)`</a> | 开启外部视频输入（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a17b9103fc32185304dd742663620c2d5" target="_blank">`pushExternalVideoFrame(streamType,frame)`</a> | 推送外部视频帧（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#afbf7f0de6fdd33a63d9f8bb60031e5f8" target="_blank">`startVideoPreview(streamType)`</a> | 开启视频预览（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a23f4d820a20c7be94ae4d793a81c8a0d" target="_blank">`stopVideoPreview(streamType)`</a> | 关闭视频预览（原同名接口保留，此接口新增 `streamType` 参数，用于开启辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a33f0fa75d8a9bd31bc9dc6dd54de8f6b" target="_blank">`onUserVideoMute(uid,muted,streamType)`</a> | 远端用户暂停或恢复发送视频流的回调（原同名接口保留，此接口新增 `streamType` 参数，用于辅流通道）。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a8dbc8636e3aa3473c48ffee043d47996" target="_blank">`onFirstVideoFrameDecoded(userID,width,height,streamType)`</a> | 已接收到远端视频首帧并完成解码的回调（原同名接口保留，此接口新增 `streamType` 参数，用于辅流通道）。    |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5196530aff2a0518a1b9a4f3306219c9" target="_blank">`onFirstVideoDataReceived(userID,streamType)`</a>     | 已显示远端视频首帧的回调（原同名接口保留，此接口新增 `streamType` 参数，用于辅流通道）。    |

**变更 API**

| API | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5eb74e9f5f569f007d467e2b63d1221e" target="_blank">`onLocalVideoWatermarkState`</a> | `state` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_constants_1_1_n_e_rtc_local_video_watermark_state.html" target="_blank">`NERtcLocalVideoWatermarkState`</a> 类型新增 `LVW_STATE_SET_SUCCESS` 等 4 种枚举值，支持字体设置错误等新增水印异常状态回调。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a79a2c28cf1b135ae0cbf9a4bba76b9f7" target="_blank">`onRemoteAudioVolumeIndication`</a> | `volumeArray` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1stats_1_1_n_e_rtc_audio_volume_info.html" target="_blank">`NERtcAudioVolumeInfo`</a>    类型新增 `subStreamVolume` 字段，对应远端辅流音量回调值。 |
| <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aaef90028fe9cc598bf4bf1d5310bc71c" target="_blank">`setBeautyEffect`</a> | `beautyType` 参数对应的 <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_beauty_effect_type.html" target="_blank">`NERtcBeautyEffectType`</a> 类型新增 `kNERtcBeautyShortFace` 等 5 种枚举值，支持短脸等新增美颜效果。 |

⭐<span style="font-size:16px;"><b>4.6.14 (2022-08-15)</b></span>

**改进优化**

修复部分场景下的偶现崩溃。

⭐<span style="font-size:16px;"><b>4.6.13 (2022-06-29)</b></span>

**改进优化**

1. 稳定性提升。
2. 优化部分机型（Android 11）校验 BLUETOOTH_CONNECT 权限逻辑。

⭐<span style="font-size:16px;"><b>4.6.12 (2022-06-15)</b></span>

**问题修复**

1. 修复部分场景下的崩溃问题。
2. 修复部分场景下的帧率下降问题。
3. 修复使用虚拟背景功能场景下的已知问题。

⭐<span style="font-size:16px;"><b>4.6.10 (2022-06-01)</b></span>

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 虚拟背景 | 支持通过自动识别用户人像，虚化用户周围的真实环境，或者以指定颜色的图片或自定义图像替代真实背景。 | [虚拟背景](/https://doc.yunxin.163.com/nertc/guide/Tk4NDA3MjM) |
| 网易云信美颜 | 网易云信自研的基础美颜和高级美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。 | [网易云信美颜](/https://doc.yunxin.163.com/nertc/guide/DQ1OTY0NjI) |
| 音频辅流 | 支持通过辅流输入伴音文件或自定义音频源。 | [音效与伴音](/https://doc.yunxin.163.com/nertc/guide/zA2MTIwNjk) <br>[自定义音频采集与渲染](/https://doc.yunxin.163.com/nertc/guide/jIwNDc3MjE) |
| 自定义混响效果 | 支持自定义设置本地人声的混响回声效果，赋予声音一定的立体效果。 | [美声变声与混响](/https://doc.yunxin.163.com/nertc/guide/zk0MjA3Mzk) |
| 视频编码水印 | 支持为视频流画面添加编码水印，例如添加公司名称、标语等文字水印、录制时间等时间戳水印、以及 logo 等图片水印。 | [水印](/https://doc.yunxin.163.com/nertc/guide/zM5OTkzMDA) |

**改进优化**

1. 修复同一 uid 在多端登录导致的互踢问题。
2. 分离音频的引擎启动逻辑和流发布逻辑，有效减少大房间的性能压力。
3. 支持在房间中根据不同场景切换音频模式，即允许在加入房间后动态切换 audioProfile。

**新增 API**

| API | API 说明 |
| --- | --- |
| [`enableVirtualBackground`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad1b6de36f54e4c9c3ab04249c89c4906) | 开启虚拟背景。    |
| [`onVirtualBackgroundSourceEnabled`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#aaa70fbf1467e098754e0f2290b779dc5)     | 通知虚拟背景是否成功开启的回调。    |
| [`startBeauty`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac22e1e77ba106e1914fc730746419941)     | 开启美颜功能模块。    |
| [`stopBeauty`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a9d67ff2a3600cde7598c27e496ac4587)     | 结束美颜功能模块。    |
| [`enableBeauty`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a49bc7e4b28dab2ce8d0e490b0a5da6b8)     | 暂停或恢复美颜效果。    |
| [`setBeautyEffect`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aaef90028fe9cc598bf4bf1d5310bc71c)     | 设置美颜效果。    |
| [`addBeautyFilter`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa3fca3e7507b2b6e38f36e39cdec3f4e)     | 添加滤镜效果。    |
| [`removeBeautyFilter`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a43c927780296d672d5585cd2c7d0bb9d)     | 移除滤镜。    |
| [`setBeautyFilterLevel`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a60eb78630d79d87a073c04336b758ba9)     | 设置滤镜强度。    |
| [`enableAudioVolumeIndication`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a6140aa4e47851211c23db9e78d5e0ec0)     | 开启说话者音量提示（原同名接口保留，此接口新增 enableVad 参数，用于设置是否启用本地采集人声监测）。    |
| [`onLocalAudioVolumeIndication`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html#a71ff97d2269442f27a19f309d64133d4)     | 提示本地用户瞬时音量的回调（原同名接口保留，此接口新增 vadFlag 参数，用于监测是否存在人声）。    |
| [`enableLocalSubStreamAudio`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adee9c69ac723cd4161f384bc13928693)     | 开启音频辅流。    |
| [`subscribeRemoteSubStreamAudio`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2c6aeea4a21d9828f02e2ef3bdcd1748)     | 订阅远端用户辅流。    |
| [`muteLocalSubStreamAudio`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a56b68924afac8dbcd269174bce6f3445)     | 静音本地音频辅流。    |
| [`setExternalSubStreamAudioSource`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aac575f3161f150c8b2a151d9acd467fb) | 开启自定义音频辅流采集。 |
| [`pushExternalSubStreamAudioFrame`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a18829d74ec8ce20956cf508398a65dbf) | 将外部音频辅流数据帧推送给 NERTC SDK。 |
| [`onUserSubStreamAudioStart`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#ae9a94ee4ba319ec013ee351a865571ef)     | 通知远端用户开启音频辅流的回调。    |
| [`onUserSubStreamAudioStop`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#ac92a2086d8e9e34dc1fd1a0d3473667c)     | 通知远端用户关闭音频辅流的回调。    |
| [`onUserSubStreamAudioMute`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a2ed24a9a55aae27ef5565f3f63d5e2a0)     | 通知远端用户暂停或恢复音频辅流的回调。    |
| [`setAudioSubscribeOnlyBy`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#af788c31dde946e47e62a0cdd7b4246dd)     | 设置本地用户音频只能被房间内其他指定用户订阅。    |
| [`setStreamAlignmentProperty`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a317655c26cf8dd6dc5504ba9720aed9a)     | 对齐本地系统时间与服务端时间。    |
| [`getNtpTimeOffset`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a32137284c2c58f4ac55e812b148d4ffc)     | 获取本地系统时间与服务端时间的差值。    |
| [`setLocalVoiceReverbParam`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a17eb244af334cf9b7b0802f58255da3a)     | 开启本地语音混响效果。    |
| [`switchCameraWithPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2594628645064b7f87fa9da87c80778b)     | 指定前置或后置摄像头。    |
| [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1f14d1727ef2a5d00a4b1b8170a3040c)     | 设置视频水印。    |
| [`onLocalVideoWatermarkState`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5eb74e9f5f569f007d467e2b63d1221e)     | 通知水印是否成功设置的回调。    |
| [`enableMediaPub`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#afca8cc32d2022f79212bd665efa3da18)     | 发布或停止发布本地音频。    |
| [`onRecordSubStreamAudioFrame`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#aa480c1f114c2353c2ef81f001092cd57)     | 本地音频辅流数据回调。    |
| [`onPlaybackSubStreamAudioFrameBeforeMixing`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#a356d35b9bec5ad8307c9cdd1ff3d3c7f)     | 获取开启音频辅流的远端用户的辅流数据。    |

**变更 API**

| API | API 说明 |
| --- | --- |
| [`startAudioMixing`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a69df08ee03787f3f9fcc551ed7158e13) | Option 参数新增 startTimeStamp 和 sendWithAudioType 字段，设置文件播放的起始位置和音频类型。 |
| [`setAudioProfile`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a577e39135f6388f4d02e4cb72f97a9f3) | 支持在房间内动态调用此接口设置音频属性。 |
| [`setCameraCaptureConfig`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a9aa68f7f4c96b7a84a04e79941dc9015) | captureConfig 参数废弃 preference 字段。 |

**废弃 API**

| API | API 说明 |
| --- | --- |
| [`setLocalCanvasWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adda6b8ba5fa1564c48b40cc358252a19) | 此接口已废弃，请使用新接口 [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1f14d1727ef2a5d00a4b1b8170a3040c)。 |
| [`setRemoteCanvasWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa3c1eeb07206579eec6e522a1779004b) | 此接口已废弃。 |

⭐<span style="font-size:16px;"><b>4.6.1 (2022-03-08)</b></span>

修复极端场景下的偶现崩溃。

⭐<span style="font-size:16px;"><b>4.6.0 (2022-02-28)</b></span>

网易云信于 2022 年 2 月 28 日发布了 NERTC SDK 最新版本 4.6.0。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 设置音频订阅优先级 | 支持优先订阅远端某用户发布的音频流。在 ASL 策略下，即在服务器线路上选择最清晰的三条音频流传输给本地用户时，本地用户设置优先订阅一个成员的音频流后，即使该成员的说话音量较低或不够清晰，本地用户仍能接收到该指定成员的音频流。 | [设置音频订阅优先级](/https://doc.yunxin.163.com/nertc/guide/DQ0OTEwNjU?platformId=50002) |
| 音频循环缓存录制 | 在原有的支持实时写文件基础上，支持设置仅录制最近一段时间内的音频数据，最高为 15 分钟。 | [客户端音频录制](/https://doc.yunxin.163.com/nertc/guide/DIyNDE2ODk?platformId=50002) |
| 共享系统音频 | 支持将本地播放的音频或视频文件的声音分享给远端用户。 | [音频共享](/https://doc.yunxin.163.com/nertc/guide/DE4NTE1MzI?platformId=50002) |
| 视频图像畸变矫正 | 支持通过畸变矫正算法调整视窗内元素边角，还原真实画面和场景。 | [视频图像畸变矫正](/https://doc.yunxin.163.com/nertc/guide/zkxNzc5NjM?platformId=50002) |
| 云代理 | 支持使用云代理服务穿透防火墙限制，使用固定 IP 连接到网易云信服务器。 | [云代理](/https://doc.yunxin.163.com/nertc/guide/jQ0NTQ1OTM?platformId=50002) |

**改进优化**

| 改进优化 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 单声道最高支持码率提升 | 单声道最高音频码率从 64 Kbps 提升至 96 Kbps。 | [设置音频属性](/https://doc.yunxin.163.com/nertc/guide/jE2ODgxMjA?platformId=50002) |
| 音视频 2.0 SDK 增加裁剪包选项 | 用户可以根据实际场景中使用功能的差异，裁剪不需要的功能项。目前可裁剪的功能项包括：视频通话、耳返、AI 降噪、AI 超分、美声变声、H265 和 VP8 视频编解码技术、Protocol Buffers 协议、SCTP 协议等。 | - |

**新增 API**

| API | API 说明 |
| --- | --- |
| [NEMeetingOptions#showMemberTag](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ae89c16ccd946828f5183b6608ed1d5b8) | 设置某用户的音频流为高优先级。 |
| [startAudioRecordingWithConfig](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac2012f7c4a5975221b6995052e12b791) | 开启音频录制。 |
| [enableLoopbackRecording](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ab58bf9505ec8005bf54affb13df84d74) | 开启或关闭音频共享。 |
| [adjustLoopBackRecordingSignalVolume](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a95b92c66b776e9268dc451bb76ade940) | 调整音频共享音量。 |
| [enableVideoCorrection](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adf5c48ab6329131938c1fd971c419204) | 开启视频图像畸变矫正功能。 |
| [setVideoCorrectionConfig](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a0a581e6bd0dc95c18fafd93c58f1cc40) | 设置视频图像矫正参数。 |
| [setCloudProxy](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad75ea6108a06db64ed7d77e894810f0d) | 开启并设置云代理服务。 |
| [onMediaRightChange](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a0c55cc3bd60798320d72d5fd4c117b06) | 通知音视频权限是否被禁止的回调。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| [startAudioRecording](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a43a5efaa4fcde0dbaaecf4b450809784) | 新增参数 recordPosition、recordCycleTime，但均只可设为默认值，建议您改用新接口 [startAudioRecordingWithConfig](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac2012f7c4a5975221b6995052e12b791)。 |
| [setLocalVideoConfig](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2) | 通过 orientationMode 设置本地视频编码的旋转方向时会同时影响本端预览画面和远端视频画面。 |

⭐<span style="font-size:16px;"><b>4.5.3 (2022-02-15)</b></span>

**新增特性**

支持自定义设置视频输入的旋转偏移量。

⭐<span style="font-size:16px;"><b>4.5.1 (2021-11-12)</b></span>

修复极端场景下的偶现崩溃。

⭐<span style="font-size:16px;"><b>4.5.0 (2021-10-22)</b></span>

网易云信于 2021 年 10 月 22 日发布了 NERTC SDK 最新版本 4.5.0。

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 多房间管理 | 加入多个频道后，用户可以同时接收多个频道的流，但只能同时在一个频道内发流。该功能适用于用户需要同时接收多个频道的流，或频繁切换频道发流的场景。 | [加入多房间](/https://doc.yunxin.163.com/nertc/guide/TIwMTQzNTU) |
| 通话前网络探测 | 在通话前进行 Last-mile 网络探测，可以获取通话前上下行网络的带宽、丢包、网络抖动和往返时延数据，有效帮助本地用户判断和预测上行网络质量是否良好。 | [通话前网络探测](/https://doc.yunxin.163.com/nertc/guide/Tc0NDEyNDE) |
| 摄像头采集偏好设置 | 通过设置摄像头采集偏好，您可以根据实际场景选择优先保证设备性能还是视频质量。 | [setCameraCaptureConfig](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a9aa68f7f4c96b7a84a04e79941dc9015) |
| 云端录制支持通过服务端 API 接口配置 | 云端录制支持通过服务端接口进行录制任务的配置。 | - |

**改进优化**

| 改进优化 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 优化本地视频编码属性配置 | - 支持动态调整。在 4.5.0 版本之前，本地视频编码配置在下次开启本端视频时生效。V4.5.0 版本开始，您可以根据业务需求，在通话中动态调整视频分辨率等编码属性。 | [setLocalVideoConfig](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2) |\
| | - 分辨率设置超限时取上限值（1080P）。在 4.5.0 版本之前，通过 [setLocalVideoConfig](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2) 设置分辨率时，如果分辨率设置超出参数上限（1080P），则取最小值 360P。V4.5.0 版本开始，取最大值 1080P。 | |
| 静音状态下回调采集音量 | 支持设置静音状态下是否返回真实采集音量 | KEY_ENABLE_REPORT_VOLUME_WHEN_MUTE |

**集成变更**

集成 NERTC Android SDK 4.5.0 版本时，需要额外添加 report 库依赖。后续集成其他版本时，建议删除该行。

```Java
implementation 'com.netease.yunxin:report:2.1.0'
```

**新增 API**

| API | API 说明 |
| --- | --- |
| [setCameraCaptureConfig](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a9aa68f7f4c96b7a84a04e79941dc9015) | 设置本地摄像头的采集偏好等配置。 |
| [getCurrentCamera](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad8dec7fc36c99bc06bb30447ecfcc002) | 查看当前摄像头方向。 |
| [onPlaybackAudioFrameBeforeMixingWithUserID](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#a2fbdeb37e4e8f09f56d910467a400ac9) | 获取指定远端用户混音前的音频数据。在多房间场景下可以通过 channelId 识别不同的房间。原接口 [onPlaybackAudioFrameBeforeMixingWithUserID](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#adcabc16a28b2fb94e33f0be439fc87da) 即将废弃，请改用新接口。 |
| [createChannel](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#afbb8cd6e77c35384e9c91a9ea4c3498e) | 创建并获取一个 NERtcChannel 对象，用于多房间场景。 |
| [NERtcChannel](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html) 接口类 | 在指定房间中实现实时音视频功能。通过创建多个 NERtcChannel 对象，用户可以同时加入多个房间。 |
| [NERtcChannelCallback](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html) 接口类 | 异步回调接口，用户需要实现该接口来完成对 NERtcChannelCallback 各种状态回调的处理。 |
| [startLastmileProbeTest](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a04f88aceade968a815d0a6df6024d246) | 开始通话前网络质量探测。 |
| [stopLastmileProbeTest](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa21aae237bdc8acc69c9808d7a9f7a1e) | 停止通话前网络质量探测。 |
| [onLastmileQuality](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#ae4dc6a5628f33da01dbec21e039e642d) | 通话前网络上下行 last mile 质量状态回调。 |
| [onLastmileProbeResult](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#aac82c1f641ef99f2f0028fbef03a17fe) | 通话前网络上下行 Last mile 质量探测报告回调。 |

**变更 API**

| API | API 说明 |
| --- | --- |
| [setParameters](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a7a9135f32ad0e10feb536944fd5a8ab2) | 增加参数 `KEY_ENABLE_REPORT_VOLUME_WHEN_MUTE`，设置本地用户静音时是否返回原始音量。 |
| [NERtcVideoLayerSendStats](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1stats_1_1_n_e_rtc_video_layer_send_stats.html) | 新增 `capWidth` 和 `capHeight`，查看视频采集宽高。 |
| [setLocalVideoConfig](/docs/interface/NERTC_SDK/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2) | - 生效时机由下次开启本段视频时生效，改为实时生效。 |\
| | - 分辨率参数设置超限时取最大值。 |

**废弃 API**

| API | API 说明 |
| --- | --- |
| [onPlaybackAudioFrameBeforeMixingWithUserID](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#adcabc16a28b2fb94e33f0be439fc87da) | 即将废弃，请改用新接口 [onPlaybackAudioFrameBeforeMixingWithUserID](/docs/interface/NERTC_SDK/Latest/Android/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_frame_observer.html#a2fbdeb37e4e8f09f56d910467a400ac9)。新接口在多房间场景下可以通过 channelId 识别不同的房间。 |

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
    <td>提升安卓平台 SDK 的集成易用性。</td>
    <td>新增 <a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_abs_n_e_rtc_callback_ex.html">AbsNERtcCallbackEx</a>，用于简化 NERtcCallbackEx 接口的实现，init 时推荐使用 AbsNERtcCallbackEx。</td>
    <td><a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_abs_n_e_rtc_callback_ex.html">AbsNERtcCallbackEx</a></td>
</tr>
<tr>
    <td>支持静音状态下回调采集音量</td>
    <td>支持设置静音状态下是否返回真实采集音量</td>
    <td><a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_parameters.html#a32be5f10e15c2b750af4ec0d85d0d31e">KEY_ENABLE_REPORT_VOLUME_WHEN_MUTE</a></td>
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
    <td><a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_abs_n_e_rtc_callback_ex.html">AbsNERtcCallbackEx</a></td>
    <td>简化 NERtcCallbackEx 接口的实现。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td><a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a7a9135f32ad0e10feb536944fd5a8ab2">setParameters</a> </td>
    <td>增加参数 <a href="https://dev.yunxin.163.com/docs/interface/NERTC_SDK/en/Latest/Android/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_parameters.html#a32be5f10e15c2b750af4ec0d85d0d31e">KEY_ENABLE_REPORT_VOLUME_WHEN_MUTE</a>。</td>
  </tr>
</table>

⭐<span style="font-size:16px;"><b>4.4.0 (2021-07-13)</b></span>

网易云信于 2021 年 7 月 13 日发布了 NERTC SDK 最新版本 4.4.0。

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
    <td>加入音视频房间时，可以不设置 uid，此时网易云信服务器会自动为您生成一个随机 uid。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a2a44081baf4bd457749d1c48cd2def36">joinChannel</a></td>
</tr>
<tr>
    <td>支持视频 AI 超分功能</td>
    <td>客户端开启 AI 超分功能之后，符合超分条件的视频流会自动进行 AI 超分处理。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/guide/zYzMjc0NTA">AI 超分</a></td>
</tr>
<tr>
    <td>支持媒体流加密</td>
    <td>网易云信在默认加密算法的基础上，提供了国密加密方案，进一步保障数据安全。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/guide/DQwNjAzMDY">媒体流加密</a></td>
</tr>
</tbody>
</table>

**改进优化**

- 网络类型检测新增 5G 类型。
- 解耦麦克风和伴音功能，在不开本地音频采集的前提下，可以直接使用伴音。
- 优化跨网情况下网络重连场景。当用户网络发现变更时，对应的媒体服务器地址也会择优重连。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad017b8e4bc01310f71756f27f11f7366">getEffectDuration</a></td>
    <td>获取音效文件时长。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad5c30ac6fd61ac73599cb83f5967fdd2">getEffectCurrentPosition</a></td>
    <td>获取音效的播放进度。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aac496904ddedb36e07c7e55f172ccf50">enableSuperResolution</a></td>
    <td>启用或停止 AI 超分。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a4debf8b1f096ce1314e8bc055b7dd0b3">enableEncryption</a></td>
    <td>开启或关闭媒体流加密。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>变更说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a69df08ee03787f3f9fcc551ed7158e13">startAudioMixing</a></td>
    <td>从 4.4.0 版本开始，开启或关闭本地音频采集的操作不再影响音乐文件播放，即 enableLocalAudio(false) 后仍旧可以播放音乐文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a2a44081baf4bd457749d1c48cd2def36">joinChannel</a></td>
    <td>从 4.4.0 版本开始，uid 可选且默认为 0。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5225935a3303ed16faff92449fcdc8b7">onConnectionTypeChanged</a></td>
    <td>增加 CONNECTION_5G 枚举。</td>
  </tr>
</table>

**废弃 API**

无

⭐<span style="font-size:16px;"><b>4.3.2 (2021-06-23)</b></span>

修复了伴音相关的稳定性问题。

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
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a69df08ee03787f3f9fcc551ed7158e13">startAudioMixing</a></td>
</tr>
<tr>
    <td>支持更多伴音格式</td>
    <td>伴音格式支持 MP3、M4A、AAC、3GP、WMA 和 WAV。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa1d2db8963a298822ae2781c206a209c">playEffect</a></td>
</tr>
<tr>
    <td>在音视频通话协议中支持 VP8 编解码</td>
    <td>移动端新增了 VP8 编解码器，可以与仅支持 VP8 的浏览器通过 VP8 编码进行音视频通话。</td>
    <td>-</td>
</tr>
<tr>
    <td>视频编码属性支持旋转方向模式和镜像模式</td>
    <td>默认情况下，SDK 在编码时不对视频作镜像和旋转操作。您可以通过参数来设置视频编码的旋转方向模式和镜像模式，以控制远端用户看到的视频画面。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2">setLocalVideoConfig</a></td>
</tr>
<tr>
    <td>视频流回退</td>
    <td>网络不理想的环境下，音视频的质量都会下降。为提升用户体验，您可以通过指定接口设置视频流回退选项。在网络条件差、无法同时保证音频和视频质量的情况下，SDK 会自动将视频流从大流切换为小流，或将媒体流回退为音频流，从而提高音视频质量。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a582abbcc13e5cb74eed5781c2b097075">setLocalPublishFallbackOption</a> 等视频流回退相关 API。</td>
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
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a878f1e81a4e89e89cc1fe9155a86faf6">adjustUserPlaybackSignalVolume</a></td>
    <td>调节本地播放的指定远端用户的信号音量。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a582abbcc13e5cb74eed5781c2b097075">setLocalPublishFallbackOption</a></td>
    <td>设置弱网条件下发布的音视频流回退选项。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a6e068099572e9485d944cf3cb81d7fd5">setRemoteSubscribeFallbackOption</a></td>
    <td>设置弱网条件下订阅的音视频流回退选项。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a7fa844d7d2445d0954cc3037b9f1722d">onLocalPublishFallbackToAudioOnly</a></td>
    <td>本地发布流已回退为音频流或恢复为音视频流回调。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#aeeaa4a6882351694c0823862116e3406">onRemoteSubscribeFallbackToAudioOnly</a></td>
    <td>远端订阅流已回退为音频流或恢复为音视频流回调。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>变更说明</b></th>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a69df08ee03787f3f9fcc551ed7158e13">startAudioMixing</a></td>
    <td>通过 startAudioMixing 播放伴音时，如果手动设置了伴音播放音量或发送音量，则当前通话中再次调用时默认沿用此设置。</td>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa1d2db8963a298822ae2781c206a209c">playEffect</a></td>
    <td>伴音格式支持 MP3、M4A、AAC、3GP、WMA 和 WAV。</td>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a20a4f919dbc80cfe7a95cf631e886cf2">setLocalVideoConfig</a></td>
    <td>增加 mirrorMode 用于指定镜像模式。增加 orientationMode 用于指定旋转方向模式。</td>
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
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a878f1e81a4e89e89cc1fe9155a86faf6">adjustUserPlaybackSignalVolume</a></td>
</tr>
<tr>
    <td>跨房间媒体流转发</td>
    <td>在 NERTC 直播场景的音视频房间中，跨房间媒体流转发功能可实现主播角色跨房间与其他主播实时交流互动，在娱乐场景下可实现跨直播间连麦效果。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/TcyNDYwNjc">跨房间媒体流转发</a> </td>
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
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a878f1e81a4e89e89cc1fe9155a86faf6">adjustUserPlaybackSignalVolume</a></td>
    <td>调节本地播放的指定远端用户的信号音量。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aab6a2600bd3799a6a500610989f61c5a">startChannelMediaRelay</a> </td>
    <td>开始跨房间媒体流转发。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ae4f5b5827d6b23fe062d2b4726934844">updateChannelMediaRelay</a> </td>
    <td>更新媒体流转发的目标房间。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aefe628b0f3b1aac7b9f9f61ee0c502c1">stopChannelMediaRelay</a> </td>
    <td>停止跨房间媒体流转发。</td>
    </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a50b06dedbdb5840f45ba02803773f1f8">onMediaRelayStatesChange</a> </td>
    <td>跨房间媒体流转发状态发生改变回调。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a2b64c4992afc0e759b729b92341c3191">onMediaRelayReceiveEvent</a> </td>
    <td>媒体流相关转发事件回调。</td>
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
    <td>设置用户媒体流优先级</td>
    <td>支持设置本地用户的媒体流为优先级。如果某个用户的优先级为高，那么该用户媒体流的优先级就会高于其他用户，弱网环境下 SDK 会优先保证其他用户收到的、高优先级用户的媒体流的质量。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#acc8d4cf57cde35eb284506544ce9200f">setLocalMediaPriority</a></td>
</tr>
<tr>
    <td>客户端截图功能</td>
    <td>支持针对实时视频流进行截图，包括本地主流画面、本地辅流画面、远端主流和辅流画面。音视频通话过程中，用户可以通过视频截图功能截取实时视频流画面，以便后续的存档分析、事件备忘、证据留存等等。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/zg4NTYwMzU">视频截图</a> </td>
</tr>
<tr>
    <td>画布水印功能</td>
    <td>视频画布中支持添加文字水印、时间戳水印和图片水印，适用于信息安全、版权声明、防伪、宣传等场景。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/zM5OTkzMDA">水印</a> </td>
</tr>
<tr>
    <td>客户端音频录制</td>
    <td>支持在客户端侧进行实时音频流录制，包含房间内所有用户混流后的音频数据。开启录制时可以指定录制文件的存放路径及格式、录制采样率、音质等。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/DIyNDE2ODk">客户端音频录制</a> </td>
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
     <td>优化耳机场景表现效果</td>
     <td>优化戴耳机场景下回声和双讲卡顿效果。优化耳返的延时，从 300ms 降低到 80ms。</td>
    </tr>
    <tr>
     <td>安卓端支持 NE265</td>
     <td>安卓端支持 NE265，整体压缩效率较 NE264 提升 40%，同等带宽下，视频质量明显提升。</td>
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
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#acc8d4cf57cde35eb284506544ce9200f">setLocalMediaPriority</a> </td>
    <td>设置本地用户的媒体流优先级。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#afc29ad8c9cd348258158363315ddaecf">takeLocalSnapshot</a> </td>
    <td>本地视频画面截图。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2302b9bdcedb445e469bbc146e771b30">takeRemoteSnapshot</a> </td>
    <td>远端视频画面截图。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_take_snapshot_callback.html#af57dea2ab3242916fd7c1d1e3fe98b30">onTakeSnapshotResult</a> </td>
    <td>截图结果回调。   </td>
    </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adda6b8ba5fa1564c48b40cc358252a19">setLocalCanvasWatermarkConfigs</a> </td>
    <td>添加本地视频画布水印。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa3c1eeb07206579eec6e522a1779004b">setRemoteCanvasWatermarkConfigs</a> </td>
    <td>添加远端视频画布水印。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a43a5efaa4fcde0dbaaecf4b450809784">startAudioRecording</a> </td>
    <td>开始客户端录音。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ab4ff2d36cccec5c63e16595e043bb858">stopAudioRecording</a> </td>
    <td>停止客户端录音。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a8bda9b434b1e886536629f6e066b979b">onAudioRecording</a> </td>
    <td>音频录制状态回调。</td>
  </tr>
</table>

**变更 API**

无

**废弃 API**

无

⭐<span style="font-size:16px;"><b>4.1.1 (2021-04-07)</b></span>

网易云信于 2021 年 4 月 7 日发布了 NERTC SDK 最新版本 4.1.1。

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
    <td>NERTC 在 4.1.1 版本中提供了更加适合双人房间场景的底层策略，优化双人房间时的音视频质量效果。双人通话功能适用于点对点通话的业务场景。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/zI1NzI4Mjg">双人通话</a> </td>
</tr>
<tr>
    <td>NERTC R​estful API 支持用房间名称（cname）发起调用</td>
    <td>音视频通话和互动直播场景的服务端 API 通过新 URL 的方式支持使用房间名称发起调用，同时原 URL 及调用方式仍旧保留以保证新老兼容。</td>
    <td> <a href="https://doc.yunxin.163.com/nertc/guide/zY3NDA3MTc">API 概览</a> </td>
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
     <td>客户端上实现音频选路策略 ASL，在大房间的场景中降低客户端上性能消耗，来提升客户端上能支持的用户连接上限。配合级联服务器的使用，可以将房间内并发人数提升到万人。详细说明请参考 <a href="https://doc.yunxin.163.com/nertc/guide/Tk0MzA1ODc?platformId=50002#如何创建 RTC 大房间？">大房间使用说明</a>。</td>
    </tr>
    <tr>
     <td>优化变声美声效果</td>
     <td>改造现有美声变声接口，提供更加丰富的美声和混响效果。新版美声变声接口有改动，若您已接入美声功能，升级 4.1.1 版本时请注意接口变更。详细说明请参考 <a href="https://doc.yunxin.163.com/nertc/guide/zk0MjA3Mzk">美声与变声</a>。</td>
    </tr>
    <tr>
     <td>视频引擎优化</td>
     <td><ul><li>支持视频 AI 超分，通过机器学习等 AI 算法，改善因受限于网络带宽限制或实时性的要求导致视频分辨偏低的问题，实现低分辨率视频在传输后进行细节补充的效果以优化接收端的视频清晰度，从而提升用户体验。</li><li>NE265 新增支持 iOS 端硬件编码，目前 NE265 编码协议，支持 mac&windows&iOS 端的编码和 Native 全端的解码。整体压缩效率较 NE264 提升 40，但编码速度慢 25%。</li><li>NE264 新增支持 AOS 端的硬件编码器，编码效率更高，优化支持硬件编码的设备上的用户体验。</li></ul></td>
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
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac9e50866795b049608004cf7940c8c21">setAudioEffectPreset</a> </td>
    <td>设置 SDK 预设的人声的变声音效。
</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a49b534de15e973af1322908f741cf98e">setVoiceBeautifierPreset</a> </td>
    <td>设置 SDK 预设的美声效果。
</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ace5cca7ad63c1d7da4e3500040de9661">setLocalVoicePitch</a> </td>
    <td>设置本地语音音调。
</td>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a0623664274006e4eb2e36dad2b7a10fd">setLocalVoiceEqualization</a> </td>
    <td>设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率。</td>
  </tr>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td><a href="https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a7a9135f32ad0e10feb536944fd5a8ab2">setParameters</a> </td>
    <td>复杂参数设置接口。</td>
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
    <td> setLocalVoiceEqualizations</td>
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

⭐<span style="font-size:16px;"><b>4.0.3 (2021-03-26)</b></span>

**修复**

- 修复偶现的 crash 问题
- 优化音视频通话过程中带宽使用情况

⭐<span style="font-size:16px;"><b><span id="[4.0.1] - 2021-03-05"> 4.0.1 (2021-03-05)</span></b></span>

**修复**

1. 修复 video 下码率分配异常的问题。
2. 优化音频质量。

⭐<span style="font-size:16px;"><b><span id="[4.0.0] - 2021-02-24"> 4.0.0 (2021-02-24)</span></b></span>

网易云信于 2021 年 2 月 24 日发布了 NERTC SDK 最新版本 4.0.0，在音视频能力和性能方面均有显著优化。从 4.0.0 版本开始，NERTC 支持媒体补充增强信息（SEI）、新增美声变声功能。

**新增特性**

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
    <td><a href="https://doc.yunxin.163.com/nertc/guide/jc1ODM0NjY">媒体补充增强信息</a></td>
</tr>
<tr>
    <td>美声与变声</td>
    <td>支持美声的预设效果、美声的自定义调节、变声的预设效果和混响的场景化效果。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/guide/zk0MjA3Mzk">美声与变声</a></td>
</tr>
<tr>
    <td>自定义音频渲染</td>
    <td>NERTC SDK 支持自定义音频渲染功能。拉取远端发送的音频数据之后，可使用自定义的渲染器进行音频渲染。</td>
    <td><a href="https://doc.yunxin.163.com/nertc/guide/jIwNDc3MjE">自定义音频采集与渲染</a></td>
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
     <td>NEVC 移动端支持优化</td>
     <td>NEVC 是网易自研的高性能视频编码器，具有相较于开源的 AVC 和 HEVC 更优越的性能。NEVC 支持安卓端的软件解码，丰富了 NEVC 对于移动端的支持，优化了移动端的视频编解码效果，优化用户的视频感官体验。</td>
    </tr>
    <tr>
     <td>伴音错误码优化</td>
     <td>增加伴音任务状态相关的错误码，为伴音问题排查提供依据。</td>
    </tr>
   </tbody>
</table>

**API 变更**

**<span id="新增 API">新增 API</span>**

| **API** | **API 说明** |
| --- | --- |
| setLocalVoiceEqualizationPreset | 设置 SDK 预设的美声效果。 |
| setLocalVoiceReverbPreset | 设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率。 |
| setLocalVoiceReverbPreset | 设置 SDK 预设的混响效果。 |
| setLocalVoiceChangerPreset | 设置 SDK 预设的人声的变声音效。 |
| [sendSEIMsg](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a7666f8a39b964fc3d752d0dada8bb78c) | 通过主流通道发送媒体补充增强信息。 |
| [sendSEIMsg](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adee87e71357d39a409e86b44c63b6e5c) | 发送媒体补充增强信息。通过本接口可指定发送 SEI 时使用主流或辅流通道。 |
| [onRecvSEIMsg](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a5a132b459b8f448a77983503fc8bde60) | 收到远端流的 SEI 内容回调。 |
| [setExternalAudioRender](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aaeaad17e53eacf77e2834fc720e77ae2) | 设置外部音频渲染 |
| [pullExternalAudioFrame](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a38ebac377d16f741e104843a230bfe5b) | 拉取外部音频数据 |

**<span id="变更 API">变更 API</span>**

| **API** | **API 说明** |
| --- | --- |
| [onAudioMixingStateChanged](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a012c8093eaaf29da09a40779a2494468) | 伴音错误码回调。NERtcConstants.AudioMixingError 中增加 AUDIO_MIXING_ERROR_CODEC_OPEN 等错误码。 |
| [addLiveStreamTask](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad2041ecad6d89313da6c52b34f1a36a3) | 创建推流任务。NERtcLiveStreamTaskInfo 增加 config 结构体，用于配置音视频流属性。 |
| [updateLiveStreamTask](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a03076e65c0123a135780fd34d7c58321) | 更新推流任务。NERtcLiveStreamTaskInfo 增加 config 结构体，用于配置音视频流属性。 |
| [setAudioProfile](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a577e39135f6388f4d02e4cb72f97a9f3) | 设置音频场景与模式。scenario 参数新增 CHATROOM 枚举值，表示语音聊天室场景。 |

⭐<span style="font-size:16px;"><b><span id="[3.9.0] - 2021-01-08"> 3.9.0 (2021-01-08)</span></b></span>

**新增**

1. 支持主动获取网络连接状态。
2. 新增实时音视频辅流功能。
3. 支持设置屏幕共享内容类型。
4. 直播模式下支持设置房间角色。
5. 支持自定义音频输入。
6. 音频支持 AI 降噪能力。
7. 支持音视频啸叫检测。

**技术优化**

1. 支持全新的 NEVC 编码协议，同等码率下提升视频整体清晰度，提高鲁棒性和错误恢复能力。
2. 屏幕共享画面优化，提升静态共享画面的清晰度，优化用户体验。
3. 支持暗场景视频图像增强，优化暗场景下的通话体验。

⭐<span style="font-size:16px;"><b><span id="[3.8.2] - 2020-12-17"> 3.8.2 (2020-12-17)</span></b></span>

**修复**

修复房间名称抄送不准确的问题。

⭐<span style="font-size:16px;"><b><span id="[3.8.1] - 2020-12-04"> 3.8.1 (2020-12-04)</span></b></span>

**新增**

1. 房间连接状态通知功能。
2. 支持视频设备调试与配置。
3. 在语音场景中新增一档高清语音选项。

**变更**

1. 屏幕录制功能 SDK 内部不在创建前台服务，改由应用自定义创建。

⭐<span style="font-size:16px;"><b><span id="[3.7.3] - 2020-11-20"> 3.7.3 (2020-11-20)</span></b></span>

> **注意**：如果需要通过 Gradle 方式集成 3.7.X 版本的 NERTC SDK，请手动在 `build.gradle` 中额外加入一行 `implementation 'com.netease.yunxin:report:2.0.3'`。后续如果需要集成 3.8.X 及以上版本时，无需添加该行，建议删除。详细集成方式请参考 [集成 SDK（Android）](/https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI)。

**优化**

针对音视频引擎底层模块进行优化。

⭐<span style="font-size:16px;"><b><span id="[3.7.1] - 2020-10-20"> 3.7.1 (2020-10-20)</span></b></span>

> **注意**：如果需要通过 Gradle 方式集成 3.7.X 版本的 NERTC SDK，请手动在 `build.gradle` 中额外加入一行 `implementation 'com.netease.yunxin:report:2.0.3'`。后续如果需要集成 3.8.X 及以上版本时，无需添加该行，建议删除。详细集成方式请参考 [集成 SDK（Android）](/https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI)。

**修复**

- 修复 Android 屏幕共享内容被裁剪的问题。

⭐<span style="font-size:16px;"><b><span id="[3.7.0] - 2020-09-28"> 3.7.0 (2020-09-28)</span></b></span>

> **注意**：如果需要通过 Gradle 方式集成 3.7.X 版本的 NERTC SDK，请手动在 `build.gradle` 中额外加入一行 `implementation 'com.netease.yunxin:report:2.0.3'`。后续如果需要集成 3.8.X 及以上版本时，无需添加该行，建议删除。详细集成方式请参考 [集成 SDK（Android）](/https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI)。

**新增**

- 新增发布流类型配置以及大小流开关。

- 新增视频属性灵活配置。

- 新增双声道效果支持。

**优化**

- 回声消除模块优化，提升单讲、双讲场景下的音质效果。

- 进入房间时默认打开音频设备。

⭐<span style="font-size:16px;"><b><span id="[3.6.2] - 2020-08-31"> 3.6.2 (2020-08-31)</span></b></span>

**修复**

- 修复异常网络下偶现的崩溃的问题。

⭐<span style="font-size:16px;"><b><span id="[3.6.0] - 2020-08-20"> 3.6.0 (2020-08-20)</span></b></span>

**新增**

- 新增音视频质量透明数据回调功能。

- 新增音视频设置房间模式功能。

- 新增伴音在线音频文件支持。

**优化**

- 优化视频编码质量以及编码器优化。

- 优化本地渲染体验，使渲染效果更加流畅。

- 优化音频质量，保证多端音量稳定。

- 优化屏幕共享，性能整体提升。

⭐<span style="font-size:16px;"><b><span id="[3.5.2] - 2020-07-21"> 3.5.2 (2020-07-21)</span></b></span>

**优化**

- 语音场景下优化音频降噪能力，提升默认的降噪等级。

⭐<span style="font-size:16px;"><b><span id="[3.5.1] - 2020-07-06"> 3.5.1 (2020-07-06)</span></b></span>

**修复**

- 修复无远端音频的情况下，音频回调不会触发的问题。

- 修复 32 位 CPU 下偶现的崩溃问题

⭐<span style="font-size:16px;"><b><span id="[3.5.0] - 2020-06-23"> 3.5.0 (2020-06-23)</span></b></span>

**新增**

- 新增自定义视频数据输入功能。

- 新增互动直播支持占位图片功能。

- 新增订阅/取消订阅所有远端音频功能。

**优化**

- 优化视频清晰度订阅机制，通过订阅大小流的方式来选择订阅视频的清晰度

- 优化蓝牙耳机通话场景适配。

- 优化视频抗丢包能力,视频抗丢包能力提升到 40%（50ms rtt 情况下）。

**变更**

- 弃用通话模式设置，统一为多人会议场景。

**修复**

- 客户端互动直播的请求在高频场景下无序的问题。

⭐<span style="font-size:16px;"><b><span id="[3.4.2] - 2020-05-27"> 3.4.2 (2020-05-27)</span></b></span>

**优化**

- 优化互动直播 `addLiveStreamTask`、`updateLiveStreamTask`、`removeLiveStreamTask` 接口的调用时序问题

⭐<span style="font-size:16px;"><b><span id="[3.4.1] - 2020-05-11"> 3.4.1 (2020-05-11)</span></b></span>

**优化**

- 修复蓝牙耳机在某些机型上的无声问题

⭐<span style="font-size:16px;"><b><span id="[3.4.0] - 2020-04-28"> 3.4.0 (2020-04-28)</span></b></span>

**新增**

- 新增互动直播推流功能。

- 音频效果优化，新增音乐场景模式支持。

- 新增网络状态回调。

**优化**

- 音频通话效果优化，适配 50+ 主流机型。

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

- 全面支持 arm64，armv7，x86 三大 CPU 架构。
:::

## 5.9.20 (2026-01-30)

**新增功能**

支持请求大型语言模型。

**新增 API**

| API | 说明 |
| --- | --- |
| `requestLLM` | 发送请求给大型语言模型，通过 `onAiData` 返回数据。

## 5.9.15 (2025-12-18)

**新增功能**

- **编码前马赛克功能**：支持外部调用设置编码前马赛克，提供马赛克和区域马赛克两种处理能力。
- **视频暗光增强**：新增暗光增强功能，可在光线亮度偏低和亮度不均匀环境下，自适应调整视频画面亮度值，恢复并凸显图像细节信息，全面提升视频图像视觉效果。
- **Player 点播支持**：Player 组件新增点播功能支持。
- **批注合流功能**：屏幕共享支持和外部输入的批注合流。

**功能优化**

- **性能提升**：优化视频前处理延时。

## 5.9.10 (2025-09-24)

**新增功能**

- **屏幕共享增强**：支持配置色彩空间配置选项，提升共享内容的色彩还原度和观看体验。
- **音频缓冲配置优化**：支持普通耳返缓冲区大小的配置，有效降低音频延迟，提升实时互动体验。
- **视频调试工具增强**：支持不同类型的视频数据导出，便于开发调试和问题排查，相关接口请参考 [`setVideoDump`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a170648e8ae88227f3d2a178169e00e5c)。
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
    - 支持在自采集模式下设置色彩空间参数，通过 `NERtcVideoFrame` 中的 [`ColorRange`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_frame_1_1_color_range.html)（色彩范围）和 [`ColorMatrix`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_frame_1_1_color_matrix.html)（色彩矩阵标准）相关枚举选项。
    - 支持画面渲染和自渲染时的色彩空间处理。
    - 支持截图功能和视频算法（美颜、人脸检测、视频增强等）兼容各种色彩空间。

- **RTMP 拉流播放功能**：拉流时无需加入房间<!--，与 RTMP 推流功能互斥（当前版本暂不支持 B 帧及多路流拉取） -->，适用于直播观看和直播连麦场景，实现更灵活的内容分发。

- **字幕翻译增强**：支持多源语言和多目标语言的实时翻译，具体通过 [dstLanguageArr](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_a_s_r_caption_config.html#a94fbb1609804bc55463179aedc094777) 和 [srcLanguageArr](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_a_s_r_caption_config.html#a8f94ca48636aa9e26f1af7ad079ecde4) 字段指定语言。

- **跨房间推流控制**：提供更精细的直播控制能力，支持暂停（`pause`）和恢复（`resume`）跨房间推流。

- **虚拟背景能力上报**：在用户加入房间事件时，上报设备支持的虚拟背景能力级别信息，适用于需要根据设备性能动态调整虚拟背景效果的场景。

**功能优化**

- 优化音频处理系统，提升 AEC 回声消除效果，音质效果优化。
- 优化视频引擎性能，降低中低端设备上的 CPU 和内存占用。
- 改进摄像头采集在特定 Android 设备上的兼容性问题。

**缺陷修复**

- 修复在部分 Android 设备上切换摄像头可能导致预览画面比例异常的问题。
- 修复特定场景下音频路由切换不生效的问题。
- 修复多种音频处理相关问题，提升通话稳定性。

## 5.8.21 (2025-06-09)

**新增功能**

**自定义重连时长配置**：支持开发者根据业务需求自定义网络重连时长，可设置重连间隔和最大重连次数。适用于网络环境不稳定的远程会议、在线客服、医疗问诊等场景，确保通话连续性。

**功能优化**

- **网络连接性能提升**：媒体连接建立过程优化，支持 IPv4 和 IPv6 并发连接，自动选择最优网络路径，显著提升首次连接速度和连接成功率。适用于跨国视频会议、复杂网络环境下的移动办公场景。

- **AI 降噪功能优化**：AI 降噪模块体积减少，降低应用包大小的同时保持卓越降噪效果，有效消除键盘声、环境噪音等干扰。

- **音频性能优化**：默认启用 OpenSL ES 音频引擎，提供更低延迟的音频处理能力，音频延迟降低，显著改善通话音质和实时性。适用于对音频质量要求极高的专业会议、音乐协作、语音社交场景。

## 5.8.15 (2025-04-29)

- 媒体传输层现支持 IPv4 和 IPv6 网络协议的同时连接，大幅提高了网络适应性。
- 针对视频中流处理机制，优化了多人视频会议中的资源分配和传输控制。
- 修复了多项潜在问题。

## 5.8.10 (2025-04-01)

AI 降噪升级到 4.0 版本。AI 降噪新增音效增强模式，可精准消除背景人声，提升语音清晰度，优化通话体验。

## 5.8.5 (2025-03-20)

- 新增支持 IPv6 网络解析与接入，提升全球网络兼容性。
- 新增音频的 AI 降噪与啸叫检测功能开关，开发者可一键启用或关闭。
- 新增支持 AI 服务相关操作的数据回调（[`onAiData`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a6ddfe6ffa6eff678f4da48956913676b)）。

## 5.8.0 (2025-02-26)

- 支持 Simulcast（Simultaneous Multistream，多流传输）视频编码和传输技术，同时发送三个不同分辨率和码率的视频流，提高音视频的网络条件和设备性能适应性。相关 API 请参考 [`setVideoStreamLayerCount`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#a4ea15d83c70b3e8fbaaf46e560d801dd)。
- 其他已知问题优化修复。

## 5.7.0 (2025-01-20)

- 支持通过加密的 WSS（WebSocket Secure）协议通道传输实时通信中的信令数据。
- 将实时视频流推流到直播服务器时，支持超时检测，提升直播的稳定性。
- 修复已知问题，提升用户体验。

## 5.6.50 (2024-12-27)

- AI 任务支持实时字幕、AI 打断功能。相关接口请参考 [`startASRCaption`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a3a596178454004ffa60048408452e255)。使用示例请参考 [基于 RTC SDK 实现与 AI 数字人音视频互动](https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client)。

- 支持适配 16KB 内存页大小的设备。从 Android 15 开始，AOSP 支持配置为使用 16 KB 页面大小的设备。详情请参考《安卓官方文档》[支持 16 KB 的页面大小](https://developer.android.com/guide/practices/page-sizes?hl=zh-cn)。5.6.50 版本起，RTC SDK 支持 16 KB 内存页大小，确保开发者 App 在使用 4 KB 和 16 KB 内存页大小的设备上运行的兼容性和性能表现。

## 5.6.40 (2024-11-22)

**新增特性**

- 新增两路视频传输通道，用户可以同时发送两路视频流。最高可同时支持发送四路视频。适用于直播、监控、远程协作等场景中。
- 提升虚拟背景容错能力。传入无效文件作为虚拟背景时，虚拟背景使用单色模式。
- 新增获取网络类型功能（[`getNetworkType`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad00adc7c87bd5ccd5830ffb2a1ae743e)），包括 2G、3G、4G、5G、Wi-Fi、运营商网络、以太网、无网络等结果。

**升级更新**

针对构建了多房间功能的用户需注意，多房间场景下的接口行为变更如下：

- 本地音频采集和发送接口 [`enableLocalAudio`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#ae58404186fa79c1282aede11080454a7) 打开音频设备时，互斥修改为不互斥。
- 本地媒体流（主流）的发送接口 [`enableMediaPub`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#aa3c99dc8a1945b2b30e4083f5e847046) 发布音频流时，不互斥修改为互斥。

即在多房间下实现发送音频流，如果只需保持设备按需开启，您需要：

1. 先关闭上一个房间的音频流，即 `enableMediaPub`=`false` / `enableLocalAudio`=`false`。
2. 然后在当前房间实现发送音频数据流，即 `enableMediaPub`=`true` / `enableLocalAudio`=`true`。

在多房间下实现发送音频流，如果需要音频采集设备一直开启，您需要：

1. 在成员加入每个房间前，调用一次 `enableLocalAudio`。
2. 后续音频流发布到具体的房间只需由 `enableMediaPub` 控制。

## 5.6.30 (2024-08-22)

- 新增直播推流的实时质量透明数据回调。
- 提升了虚拟背景开启的设备适配性和覆盖面。具体请参考 [`getFeatureSupportedType()`](https://doc.yunxin.163.com/nertc/references/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#aecbd19de281ca06629c15a7a65a0ca5c) 和 [`enableVirtualBackground()`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a458b4d7e37dd5c599ebe447e72ef20c2)。
- 改进了通话模式下的回声消除策略。
- 提升了通话模式下的突发弱网抗性。

## 5.6.25 (2024-07-24)

- [`NERtcLiveStreamTaskInfo`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1live_1_1_n_e_rtc_live_stream_task_info.html) 中 `taskId` 字段变更为可选，支持不设置或设置为空。在这种情况下，推流任务 ID 由 SDK 生成并管理，并将在用户离开时自动清除。如果需要手动清除推流任务，调用 removeLiveStreamTask 接口，并将 task_id 指定为空即可。
- 提升了 CDN 推流成功率，详细教程请参考 [CDN 推流](https://doc.yunxin.163.com/nertc/guide/Tc4MDgyMjY?platform=android)。

## 5.6.20 (2024-07-10)

- 增加了标准场景下的 KTV 模式（[`Karaoke`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_constants_1_1_r_t_c_channel_profile.html#afe890be80d817959af5b5c13477ee335)），优化外放情况下的音质，深度适配 K 歌业务场景。
- 扩大了智码超清的适用范围。在远端使用硬件解码视频的情况下，也能完整支持。
- 优化了使用外部渲染时的性能。
- 提升了部分安卓系统手机的视频清晰度，改善锯齿现象。
- 修复了部分华为系列平板上出现的视频画面方向不正确问题。
- 在最新版本的华为品牌手机上，支持了虚拟背景的能力。

## 5.6.10 (2024-06-14)

- 提升了秀场直播场景中的音视频效果，以及接入易用性。从 5.6.10 版本起，您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。详情请参考 [CDN 推流](https://doc.yunxin.163.com/nertc/guide/Tc4MDgyMjY?platform=android)。
- 改进了视频编码策略，在低端机型设备上也有更好地的能表现。
- 优化了软编模式下的视频抗锯齿算法，提升了视频清晰度。

## 5.6.0 (2024-05-10)

- 优化 QoS 弱网环境的对抗算法，提升抖动网络下的音频质量。
- 优化了音频编解码算法，提升音频质量。
- 减小了 SDK 包的体积。
- 增强了应用运行稳定性。

## 5.5.40 (2024-04-03)

**新增特性**

- 为方便开发者快速接入，SDK 新增多种预设场景。当前支持的预设场景包括：标准 1 对 1 音视频通话、高画质 1 对 1 音视频通话、标准语聊房、高音质语聊房、会议场景。
- 支持初始化时指定 audio dump 路径。

**改进优化**

- 优化 AI 降噪设置，提升降噪效果。
- 支持自定义设置音频路由。

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`setAudioProfile [1/2]`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a6e5e0fdae26c2d6e2066d29df4bd4c59) | 设置音频编码属性 |
| [`setAudioScenario`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#a3b509c58dd72098f863acf82e922fc23) | 设置音频编码属性的应用场景 |

**变更 API**

| 接口 | 变更说明 |
| ---- | ---- |
| [`RTCChannelProfile`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_constants_1_1_r_t_c_channel_profile.html) | 房间场景新增以下枚举值：<li>int STANDARD_VIDEOCALL = 3;<li>int HIGHQUALITY_VIDEOCALL = 4;<li>int STANDARD_CHATROOM = 5;<li>int HIGHQUALITY_CHATROOM = 6;<li>int MEETING = 7; |
| [`NERtcOption`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_option.html#af8b8d43865c3482cde3911377d62556c) | 新增 `audioDumpDir` 参数，用于初始化时指定 audio dump 路径。 |

## 5.5.32 (2024-03-15)

**改进优化**

- 优化音频编码传输策略，提升弱网和带限场景下的适应能力，降低设备功耗。
- 优化音频 3A 算法，提升扬声器外放场景的交互音质。
- 支持定制裁剪一些视频特效功能，减小包体积。

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`onLocalAudioFirstPacketSent`](https://doc.yunxin.163.com/nertc/references/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html#a895f5d33b614f09f34a98476cd4de48a) | 音频首帧发送回调 |

## 5.5.30 (2024-02-29)

**改进优化**

提升了自定义加密功能的易用性。

## 5.5.21 (2024-01-18)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`NERtcPacketObserver`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1encryption_1_1_n_e_rtc_packet_observer.html) | 数据包回调 observer。 |
| [`isFeatureSupported`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a8e0c108aabf5d3405e1623e1effa7ba1) | 查询当前设备是否支持虚拟背景功能。 |

**变更 API**

| 接口 | 变更说明 |
| ---- | ---- |
| [`ErrorCode`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_constants_1_1_error_code.html) | 新增以下枚举值：<li>int ENGINE_ERROR_JOIN_INTERRUPTED_DUE_TO_LEAVE_ACTION = 30028;<li>int ENGINE_ERROR_JOIN_INTERRUPTED_DUE_TO_DESTROY_ACTION = 30029;<li>int ENGINE_ERROR_JOIN_INTERRUPTED_DUE_TO_APP_TERMINATION = 30030; |
| [`NERtcEncryptionConfig `](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1encryption_1_1_n_e_rtc_encryption_config.html) | 增加成员变量自定义加密回调 `observer`。 |
| [`EncryptionMode`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1encryption_1_1_n_e_rtc_encryption_config_1_1_encryption_mode.html) | 增加枚举自定义加密模式 `EncryptionModeCustom`。 |
| [`NERtcFeatureType`](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_feature_type.html) | 增加枚举 `NERtcFeatureType.VIRTUAL_BACKGROUND`，功能类型为虚拟背景。 |

**改进优化**

- 提升安卓平台硬件视频编码的适配能力
- 虚拟背景功能支持 MTK 芯片

## 5.5.12 (2023-12-15)

**改进优化**

修复小概率的音量回调不准确问题。

## 5.5.11 (2023-12-05)

**改进优化**

- 提升首次安装时的登录成功率。
- 修复特定条件下小概率的房间角色错误问题。
- 修复安卓端外部视频输入的预览镜像逻辑。
- 提升语聊房场景的音频效果。
- 适配安卓 14 系统，修复小部分机型的崩溃问题。
- 提升稳定性。

## 5.5.10 (2023-10-31)

**升级必看**

如果您计划将应用中使用的旧版本 NERTC SDK 从 5.5.2 升级为当前版本，请根据接口变更，更新相应的代码，具体请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/Dk2NTU1NDM?platform=Android)。

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| 范围语音 | 在一个 RTC 房间内，用户可以与一定距离内的其他用户进行实时语音通话，支持 **仅小队** 或 **所有人** 的语音模式。它可以让玩家在游戏中实时交流，从而更好地协调战术和策略。 | [范围语音](https://doc.yunxin.163.com/nertc/guide/TkyNTg3MDU?platform=android) |
| 音频推拉流的黑白名单 | 您可以设置推流白名单、拉流白名单或拉流黑名单，从而实现只推流给指定用户或只订阅指定用户的音频，以便满足游戏语音等场景下的需求。 | [设置音频转发路由](https://doc.yunxin.163.com/nertc/guide/Dg2MTUwMDc?platform=android)
| 限定访问区域 | 为满足客户在海外访问域名合规性，云信支持访问区域限制功能。无论用户身处何地使用 App，SDK 都只会访问指定区域的域名。 | [限定 NERTC SDK 的 访问区域](https://doc.yunxin.163.com/Overseas/guide/DYzMjg1ODI?platform=others#%E9%99%90%E5%AE%9A%20RTC%20SDK%20%E7%9A%84%20%E8%AE%BF%E9%97%AE%E5%8C%BA%E5%9F%9F) |

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [ `initSpatializer`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#aabfb4fc5dea6bb7e2ad6115741893c4b) | 初始化空间音效。 |
| [ `setAudioRecvRange`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#a1270412a8afef8bb8ae1e9d724eec1fc) | 设置空间音效的距离衰减属性和语音范围。 |
| [ `setRangeAudioTeamID`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#aff82e9cd4df29a4761088e11b2365003) | 设置范围语音的队伍号。 |
| [ `setRangeAudioMode`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#aef5f55f57290dad16fa17b953ca10604) | 设置范围语音的模式。 |
| [ `setSubscribeAudioAllowlist`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#a7e8c120824a19935511b74224fa9875a) | 设置只订阅指定用户的音频流。 |
| [ `setSubscribeAudioBlocklist`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#abbe729985a97a05ea2f5a79060f41c8c) | 设置不订阅指定用户的音频流。 |
| [`onFirstVideoFrameRender`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_abs_n_e_rtc_callback_ex.html#a55537db118e0e50ad14d59f6a48a270d) | 已接收到远端视频首帧并完成渲染的回调。 |
| [`onAudioHasHowling`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_process_observer.html#ab6c483608f6db4e7bd8d7d2ed68fa7b3) | 啸叫消失的回调。 |
| [`setCallbackHandler`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a09106809872cf975fe95282250de9b9b) | 若您的业务系统想要接入并获取 SDK 的统计数据，您可以根据需要调用该接口修改回调事件的队列线程。 |
| [`onLabFeatureCallback`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel_callback.html#a1925d2f0be31f4e115c380b311e9ef29) | 定制功能回调，建议空实现。如有需要请联系技术支持。 |

**变更 API**

| 接口/回调 | 变更说明 |
| ---- | ---- |
| [`NERtcDistanceRolloffModel`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/enumcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_distance_rolloff_model.html) | 空间音效的距离衰减模式新增`kNERtcDistanceRolloffLinearOnly(3)`选项，表示仅线性衰减，没有方位效果 |
| [`setAudioRecvRange`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#a1270412a8afef8bb8ae1e9d724eec1fc) | 接口名称修改，对应的原接口名称为 `UpdateSpatializerAudioRecvRange`。 |
| [`updateSelfPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#a6be3f81ba92e598c7471fa2a434e393e) | 接口名称修改，对应的原接口名称为 `UpdateSpatializerSelfPosition`。 |
| [`enableSpatializer`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1channel_1_1_n_e_rtc_channel.html#aec10a7085c4ff06b90ca9aa82d8e690a) | 接口名称修改（接口首字母改为小写），新增 `applyToTeam` 参数。 |
| [`NERtcPositionInfo`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_position_info.html) | 结构体名称修改，对应的原结构体名称为 `NERtcSpatializerPositionInfo`。 |
| [`NERtcOption`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_option.html) | 新增 `areaCodeType` 参数，用于限定访问区域。 |
| [`onAudioHasHowling`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1audio_1_1_n_e_rtc_audio_process_observer.html#ab6c483608f6db4e7bd8d7d2ed68fa7b3) | 原先只有检测到啸叫时会触发 `onAudioHasHowling（true）`回调，V5.5.10 版本新增当啸叫消失时，也会触发 `onAudioHasHowling（false）`回调。 |
| [`NERtcVideoConfig`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1video_1_1_n_e_rtc_video_config.html) | 删除摄像头位置参数 `frontcamera`。 |

**改进优化**

- 优化断网重连之后音画同步效果。
- 优化弱网场景入会时长和首帧耗时。
- 画质不变情况下，降低视频码率和性能开销。
- 优化音乐场景下回声消除和降噪效果。

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
- 优化 Android 硬件编解码，适配更多设备
- 视频水印功能支持所有设备和平台
- 虚拟背景和视频水印功能启用硬件分级策略
- 针对低性能设备，提供更加稳定的音频质量
- 在 Music 场景，声音外放时，优化回声消除效果
- 针对噪声和回声处的音量放大做适当控制

- 支持华为 AudioKit

## 5.4.9 (2023-09-12)
**新增特性**

- 外接摄像头时，支持多摄像头切换。
- camera 1 支持外接摄像头的动态热插拔。

## 5.4.8 (2023-08-29)

**问题修复**

- 修复鸿蒙手机偶现的异常问题。

- 修复部分已知问题。

## 5.4.7 (2023-08-09)

**问题修复**

修复部分已知问题。

## 5.4.3 (2023-07-27)

**改进优化**

音频 opus 编码器支持 24kHz 采样率。

**问题修复**

修复部分已知问题。

## 5.4.1 (2023-07-18)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`onRemoteVideoSizeChanged`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#ac4595c4cd7711a9ecd2ca3da3f29d458) | 远端视频分辨率变化的回调。 |
| [`onLocalVideoRenderSizeChanged`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a818a22a12019c9cde531cdcc453461cb) | 本地视频预览分辨率变化的回调。 |

**问题修复**

修复部分已知问题。

## 5.4.0 (2023-07-04)

**新增特性**

| 新增特性 | 特性描述 |
| ---- | ---- |
| [空间音效](https://doc.yunxin.163.com/nertc/guide/TY3NjAzNDE?platform=android) | 空间音效也称 3D 音效，是通过在音频信号中添加空间信息，使得听众可以感受到声音来自于特定的位置和空间环境。它可以增强音频的真实感和沉浸感，让听众感受到更加真实的声音效果。 |

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`EnableSpatializer`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa18b381094069638ef3e6c4204cb3abc) | 开启/关闭空间音效。 |
| [`UpdateSpatializerAudioRecvRange`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a468dfc67596667c5ae7e2b7aa092f3a5) | 设置空间音效的距离衰减属性和语音范围。 |
| [`SetSpatializerRoomProperty`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a4cc83a66bba064af6afe87f6378b01cd) | 设置房间混响属性。 |
| [`EnableSpatializerRoomEffects`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a7e786be3b904d70ccdd92a7e1e8ac2e7) | 开启或关闭空间音效的房间混响效果。 |
| [`UpdateSpatializerSelfPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ae2779ed0241dd3218ebbb77b1696f430) | 设置说话者和接收者的位置信息。 |
| [`SetSpatializerRenderMode`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a15a434c7071fad0196b977d6935ef82e) | 设置渲染模式。 |
| [`NERtcExternalVideoRenderer.setLocalExternalVideoRenderer`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a705e537d1d3c98146a95c29641718640) | 自定义本地视频渲染器。 |
| [`NERtcExternalVideoRenderer.setRemoteExternalVideoRenderer`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a6ae4f25a100d221804c5297cfea71b0b) | 自定义远端视频渲染器。 |

**改进优化**

- AI 降噪能力优化。

    提升了人声音质和降噪量，有效地抑制各种噪声而不会损伤人声。在教育和会议场景中，它针对人声（如小孩声和笑声）做了保护，避免这些声音被过度抑制。
- 优化 AEC 算法，重点改进本端和远端双讲时的效果。

    可在双讲场景下保存清晰、流畅的近端人声，为用户在会议、语聊等场景下提供更舒适的通话体验。
- 通过优化音频 NACK 请求，降低音频在弱网环境下的端到端延时。
- 在弱网环境下优化首帧耗时。
- 改善极端弱网环境下的视频清晰度。
- 优化包大小。

    5.4.0 版本开始，默认支持 vp8 编解码能力，不再支持 vp9 编解码能力，在保障客户端与 Web 端互通能力的同时，减小包体大小。
- Android 硬件编解码适配。

    Android 默认使用 camera2，提升摄像头的图像采集质量。同时加强了硬件功能和编解码质量的稳定性，可支持更多的手机设备。
- 优化 NE264 编码器。
- 提升低端手机的发送帧率。

    改善了低端机上前处理的帧率，及性能受限情况下的编码稳定性，低端机上可提升视频发送帧率。
- 当用户未赋予 `BLUETOOTH_CONNECT` 权限时，支持使用手机麦克风采集声音。

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

- 修复安卓 SDK 在特定场景下部分回调不生效的问题。
- 修复部分已知问题。

## 5.3.5 (2023-05-24)

**新增特性**

支持纯音频 SDK。请通过 [网易云信 SDK 下载中心](https://doc.yunxin.163.com/nertc/sdk-download) 下载纯音频的 SDK 包。

**问题修复**

修复部分已知问题。

## 5.3.3 (2023-05-15)

**新增特性**

| 新增特性 | 特性描述 | 相关文档 |
| --- | --- | --- |
| 调节本地播放的指定房间内所有远端用户的音量。 | 在多房间场景中，可以使用该方法单独调整主房间或者某个子房间的所有远端用户的播放音量。 | <a href="https://doc.yunxin.163.com/nertc/guide/jUzMjAxNTc?platform=android#设置播放音量" target="_blank">设置通话音量</a> |

**问题修复**

修复部分已知问题。

## 5.3.1 (2023-05-05)

网易云信于 2023 年 5 月 5 日正式发布 NERTC SDK 5.3.1 版本。该版本提供统一的业务需求实现和更友好的跨平台接入支持，并以更小的包体积帮助您实现快速接入。

**升级必看**

如果您计划将应用中使用的旧版本 NERTC SDK 从 4.6.X 升级为当前版本，请根据接口变更，更新相应的代码，具体请参考 [升级指南](https://doc.yunxin.163.com/nertc/guide/Dk2NTU1NDM?platform=Android)。

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ----
| 插件化集成人脸增强、视频超分、视频降噪功能 | 支持通过插件化集成人脸增强、视频超分、视频降噪功能，提升 SDK 集成的灵活性与易操作性，减小 App 的包体积。 | [集成 SDK](https://doc.yunxin.163.com/nertc/guide/DcyNDc0ODI?platform=android) |
| 本地数据通道 | 支持通过本地数据通道传输除音频、视频数据之外的其他数据。例如传输游戏数据、传输传感器数据等。 | 不涉及 |
| 子房间功能优化 | 支持自定义视频采集、设置房间中用户音量实时回调、切换前后置摄像头。 | [多房间管理](https://doc.yunxin.163.com/nertc/guide/TIwMTQzNTU?platform=android) |
| 麦克风关闭时发伴音 | 支持用户在麦克风关闭时，发送伴音。 | [音效与伴音](https://doc.yunxin.163.com/nertc/guide/zA2MTIwNjk?platform=android) |

**改进优化**

- 支持非主播角色成员或在连接异常状态下，删除推流任务。
- 支持通过不同的 uid 进入子房间。
- 支持日志加密默认开启。
- 各端对齐日志的内容、文件命名和默认存放路径。Android 端的默认日志路径为：`sdcard/Android/data/your_app_name/files/rtc_log`。

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`enableLocalData`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa06d3d69f2cbcf82e30b727704018888) | 开启或关闭本地数据通道。 |
| [`subscribeRemoteData`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ab15da8c3326e250e369284260e1ac8a7) | 取消或恢复订阅指定远端用户数据通道流。 |
| [`sendData`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aa126e90451d5234198fca48405204d25) | 通过数据通道发送数据。 |
| [`onUserDataStart`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#aa748fdb62d6d0016d9f45271e5187d2e) | 远端用户通过数据通道发送数据的回调。 |
| [`onUserDataStop`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#ab841d868d613e8f55768373eb163be50) | 远端用户停用数据通道的回调。 |
| [`onUserDataReceiveMessage`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a3b05bc8083971c7f849fa2690b97a88b) | 远端用户通过数据通道接收数据的回调。 |
| [`onUserDataStateChanged`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_abs_n_e_rtc_callback_ex.html#a7ae3d6492ab02f068b6f3212bd1be22b) | 远端用户数据通道使用状态改变通知回调。 |
| [`onUserDataBufferedAmountChanged`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh//html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a6ba78ed39b647180b00c8088828a8c47) | 远端用户数据通道待传输数据量改变通知回调。 |

**变更 API**

| 接口/回调 | 变更说明 |
| ---- | ---- |
| [`setLocalVideoWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1f14d1727ef2a5d00a4b1b8170a3040c) | `NERtcVideoWatermarkTextConfig` 和 `NERtcVideoWatermarkTimestampConfig` 结构体里的 `fontPath` 名字改为 `fontNameOrPath`。 |
| [`NERtcLocalVideoWatermarkState`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_constants_1_1_n_e_rtc_local_video_watermark_state.html) | 删除了 kNERtcLocalVideoWatermarkStateFontPathEmpty 这个 state。 |
| [`RemoveLiveStreamTask`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac72c0e04551af133cec49a1dc0b7aabc) | 接口的调用时机变更，支持在不加入房间的状态下调用该接口，以便用户在切换角色之后、`ondisconnect` 等异常情况下删除推流任务。
| [`switchCameraWithPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2594628645064b7f87fa9da87c80778b) | 调用 [`enableLocalVideo()`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc.html#ad5c6e217dacfc20546617d98e3b5ba9b) 接口进行本地视频采集与发送时，采集的摄像头行为变更，由之前的延用上一次摄像头配置，改为默认采用[`switchCameraWithPosition`](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V5.3.1/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a2594628645064b7f87fa9da87c80778b) 接口中指定的前置摄像头或后置摄像头。

**功能下线**

V5.3.0 及之后版本不再支持 [**画布水印（setLocalCanvasWatermarkConfigs 和 setRemoteCanvasWatermarkConfigs）**](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#adda6b8ba5fa1564c48b40cc358252a19) 功能，统一使用 [**编码水印（setLocalVideoWatermarkConfigs）**](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a1f14d1727ef2a5d00a4b1b8170a3040c)。编码水印可以从源头保证数据的真实性，具体请参考 [水印](https://doc.yunxin.163.com/nertc/guide/zM5OTkzMDA?platform=android)。