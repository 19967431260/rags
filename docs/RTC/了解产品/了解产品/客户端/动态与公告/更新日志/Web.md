本文介绍了网易云信音视频通话 SDK（简称 NERTC SDK）适配 Web 应用（包括 HTML5）的版本功能更新记录。具体功能请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=web) 和 查看 [API 文档](https://doc.yunxin.163.com/nertc/client-apis?platform=web)。

<style>
table th:first-of-type {
    width: 35%;
}
</style>

## **近期重要更新**

- **[5.8.15](#5815-2025-04-29)**：AI 降噪支持背景人声消除，同时支持 IPv6 网络架构。

- **[5.6.50](#5650-2024-12-25)**：更新 AI 降噪 3.0、字幕支持指定翻译语言、支持轻量版变声能力。

- **[5.6.41](#5641-2024-10-29)**：修复开启美声变声后音频延迟逐渐增大的问题。

- **[5.6.40](#5640-2024-10-11)**：支持远端音频流混音，优化移动端特殊场景的体验。

- **[5.6.30](#5630-2024-07-26)**：支持音量增益、增加视频恢复播放策略。

- **[5.6.21](#5621-2024-07-11)**：当触发屏幕共享区域限制时，屏幕共享音频同时关闭。

- **[5.6.20](#5620-2024-07-10)**：屏幕共享支持区域限制。

- **[5.6.10](#5610-2024-06-13)**：新增远端流美声变声功能，具体请参考 [AI 音效-远端流美声变声](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web)。

:::details 单击展开查看 4.6.20 (2022-08-15) ~ 5.6.0 (2024-04-25) 版本的近期重要更新。
- **[5.6.0](#560-2024-04-25)**：

    - 新增实时字幕功能，具体请参考 [打开实时字幕](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#startasrcaptions)。
    - 新增 `video-resize` 事件，当视频分辨率发生变化时触发该事件，具体请参考 [on('video-resize')](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#on)。
    - 从 5.6.0 版本开始，插件版本需同主 SDK 版本一致才可使用。

- **[5.5.30](#5530-2024-02-21)**：

    - 新增音频数据回调功能，具体请参考 [开启音频回调](https://doc.yunxin.163.com/nertc/guide/jQ1ODQ5NDQ?platform=web)。
    - Chrome 122 版本，getStats API 存在变更，会导致 Client 类中 Stats 相关 API 无效，如业务中存在相关依赖请尽快将 NERTC SDK 升级到 5.5.30 版本。

- **[5.5.11](#5511-2023-11-30)**：

    - 原 AI 降噪升级为 **AI 音效**，新增支持美声变声混响。AI 降噪使用方式存在变更，具体请参考 [AI 音效](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web)。
    - 增加 [**啸叫检测**](https://doc.yunxin.163.com/nertc/guide/zk3NjMzNDg?platform=web) 功能。

- **[5.5.10](#5510-2023-11-17)**：支持 [**限定 RTC SDK 的 访问区域**](https://doc.yunxin.163.com/Overseas/docs/DYzMjg1ODI?platform=others#限定-rtc-sdk-的-访问区域)，满足客户在海外访问域名的合规性。
- [5.5.0](#550-2023-09-04) 修复了 Chrome 117 版本（预计 2023 年 9 月 6 日上线） `getStats` API 变化引起的控制台异常报错。
    * 如果您升级到 Chrome 117 版本后，音视频功能正常，但控制台提示每秒 1 条的报错，请尽快将 NERTC SDK 升级到 5.5.0 版本。
    * 在升级期间，您可以申请 [Chrome Origin Trial](https://developer.chrome.com/origintrials/#/register_trial/3633278999381147649)，以避免在线上出现该报错。
- **[4.6.25](#4625-2022-11-08)**：支持 [ **高级 Token 鉴权** ](https://doc.yunxin.163.com/nertc/guide/jQ2MzAzNjY?platform=web)，支持对用户创建、加入房间和订阅、发布音视频流的权限进行校验，帮助您有效避免客户端遭遇破解攻击的问题。
- **[4.6.25](#4625-2022-11-08)**：支持 **AI 降噪**、[ **高级美颜** ](https://doc.yunxin.163.com/nertc/guide/Tc5OTQyNzE?platform=web) 新增去除抬头纹、法令纹、黑眼圈及调整嘴巴宽度和脸长等功能。
- **[4.6.20](#4620-2022-08-15)**：
    - 支持以 **插件化** 方式集成 **美颜**、**虚拟背景**，提升 SDK 集成的灵活性与易操作性，您可以根据需要自行选择是否集成对应特性的动态库，使 App 的包体积更小，具体请参考 [集成 SDK](https://doc.yunxin.163.com/nertc/guide/DM3MDA4NzQ?platform=web)。
    - 支持在视频通话或互动直播的过程中以 **音频辅流** 的形式实现音频共享，具体请参考 [音频共享](https://doc.yunxin.163.com/nertc/guide/TE4MzMzOTc?platform=web)。
:::

## 5.8.33 (2025-12-05)

兼容 iOS 26.2 系统。

## 5.8.32 (2025-10-31)

内部优化。

## 5.8.31 (2025-09-11)

**缺陷修复**

- 修复 Chrome 140+ 版本浏览器中单独发布屏幕共享失败的问题。
- 修复远程流同时使用变声和主动获取音量功能时，变声可能无效的问题。

## 5.8.30 (2025-09-09)

**新增功能**

**多语言字幕支持增强**：`startAsrCaptions` 接口参数扩展，支持设置多源语音、多目标语言等功能，提升多语言场景下的字幕生成体验。

**缺陷修复**

修复 Chrome 140+ 版本浏览器中单独发布视频失败的问题。

**接口变更**

| 接口 | 变更说明 |
|------|----------|
| [`startAsrCaptions`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#startasrcaptions) | 接口参数扩展，新增多源语音和多目标语言设置支持 |

## 5.8.29 (2025-09-05)

**新增功能**

**内网代理支持**：`join` 接口新增 `neRtcServerProxyAddresses` 参数，支持自定义设置内网代理地址，方便企业内网环境下的音视频通信。

**缺陷修复**

修复 SDK 重连时错误发布未授权媒体类型的问题。

**接口变更**

| 接口 | 变更说明 |
|------|----------|
| [`join`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#join) | 新增 `neRtcServerProxyAddresses` 参数，用于配置内网代理地址 |

## 5.8.28 (2025-08-27)

**新增功能**

- **视频配置增强**：`setVideoProfile` 接口新增 `width`、`height` 参数，支持自定义设置摄像头视频采集的宽度和高度。当单独设置 `width`、`height` 参数时，将替代原有的 `resolution` 参数配置。

- **屏幕共享配置增强**：`setScreenProfile` 接口新增 `width`、`height` 参数，支持自定义设置屏幕共享视频的宽度和高度。当单独设置 `width`、`height` 参数时，将替代原有的 `resolution` 参数配置。

**接口变更**

| 接口 | 变更说明 |
|------|----------|
| [`setVideoProfile`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setvideoprofile) | 新增 `width`、`height` 参数，支持自定义视频尺寸设置 |
| [`setScreenProfile`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setscreenprofile) | 新增 `width`、`height` 参数，支持自定义屏幕共享尺寸设置 |

## 5.8.27 (2025-08-01)

**新增功能**

伴音播放功能增强，在 `startAudioMixing` 接口中新增了多项回调参数。

**接口变更**

| 接口 | 变更内容 |
| ---- | ---- |
| [`startAudioMixing()`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#startaudiomixing) | <ul><li>新增 `durationChange` 参数：获取当前伴音文件总时长的回调函数</li><li>新增 `timeUpdate` 参数：获取当前伴音文件播放时长的回调函数</li><li>新增 `interval` 参数：控制 `timeUpdate` 回调频率，默认为 100ms</li></ul> |

## 5.8.26 (2025-07-31)

**新增功能**

- 加入房间时可设置用户昵称。在通话中显示用户友好名称，让其他参与者能够直观识别彼此。
- 调整了背景音乐混音音量范围，使音量控制更加精确直观。

**功能优化**

优化了设备变更事件通知机制，确保在各种环境下都能及时检测到录音设备的变化（`client.on('recording-device-changed')` 事件）。用户在通话过程中切换麦克风设备，如插拔耳机、更换外接设备时能立即获得通知。

**缺陷修复**

修复了在异常情况下离开房间可能失败的问题，提高了系统稳定性，确保用户能够顺利退出通话房间。

**接口变更**

| 接口变更 | 说明 |
|---------|------|
| [`join`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#join) | 新增 `nickname` 参数，允许设置用户在房间中显示的昵称。 |
| [`startAudioMixing`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#startaudiomixing) | `volume` 参数范围从 0-255 调整为更直观的 0-100，默认值为 100。 |

## 5.8.25 (2025-07-17)

**新增功能**

- AI 降噪接口 [`enableAIDenoise`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableaidenoise) 新增 `howlingSuppressionEnable` 参数，支持在降噪时，主动清除音频啸叫。
- 新增啸叫抑制结果回调事件 `localStream.on('howling-suppression-result')`。当通过 [`enableAIDenoise`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableaidenoise) 开启啸叫抑制功能后，NERTC SDK 会持续检测啸叫。如果抑制后音频中仍残留啸叫，SDK 会通过此事件通知您。
- 新增录音设备首次插入回调事件 `client.on('recording-device-changed')`。当用户首次插入麦克风等录音设备并被 SDK 检测到时，会触发此回调。例如，当用户在通话前或通话中插入新的麦克风时，您可以利用此回调自动刷新设备列表，或提示用户切换到新设备，优化用户体验。

**接口变更**

| 接口/事件 | 说明 |
|---------|------|
| [`localStream.on('howling-suppression-result')`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#on) | 新事件，用于接收 AI 降噪后的音频中仍残留的啸叫事件 |
| [`client.on('recording-device-changed')`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 新事件，用于检测用户首次插入麦克风等录音设备 |

## 5.8.21 (2025-07-07)

**新增功能**

<!-- - AI 功能支持：新增 `setMpsNotify` 接口，支持接收 AI 相关信令。适用于需要接入智能语音识别、实时翻译等 AI 能力的场景。 -->
- AI 数据回调：新增 `client.on('ai-data')` 事件，支持监听和处理 AI 数据。适用于需要在界面上展示 AI 处理结果的应用场景。
- 浏览器错误监控：新增 `client.on('abortError')` 事件，支持捕获浏览器中断错误。适用于由于系统异常，无法链接到媒体设备的场景。
- 异常兜底机制：新增 `client.on('unknownError')` 事件，提供全面的错误捕获能力。适用于需要记录和分析未知错误以提高应用稳定性的场景。

**接口变更**

| 接口/事件 | 说明 |
|---------|------|
| [`client.on('ai-data')`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 新事件，用于接收 AI 处理后的数据回调 |
| [`client.on('abortError')`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 新事件，用于捕获浏览器 AbortError 类型错误 |
| [`client.on('unknownError')`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 新事件，用于捕获其他未知类型错误 |

<!-- 
| `setMpsNotify` | 新接口，用于设置和接收 AI 相关信令 |
 -->

## 5.8.20 (2025-07-01)

**功能优化**

- 优化虚拟背景处理流程，通过改进 [`enableBodySegment()`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enablebodysegment) 方法确保视频前处理插件优先完成数据处理，防止原始视频画面在虚拟背景应用过程中出现闪现。适用于视频会议和在线课堂等需要虚拟背景的场景。
- 优化视频水印显示机制，修复在某些情况下可能出现的水印区域黑屏问题。适用于品牌宣传、版权保护等需要在视频中添加水印的场景。
- 优化音频处理流程，提升在异常音频硬件条件下的稳定性，有效减少音频卡顿现象。适用于音频设备质量不稳定的复杂网络环境。
- 完善 TypeScript 类型声明文件，提供更准确的类型提示，提升开发体验和代码质量。

**缺陷修复**

- 修复设备切换问题：当调用 [`switchDevice()`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#switchdevice) 方法切换视频设备时，不再错误地将屏幕共享画面挂载到摄像头视频的父元素上。适用于需要在会议过程中切换摄像头同时保持屏幕共享的场景。
- 修复连接异常处理机制：解决了当 [`open()`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#open) 方法异常阻塞时，调用 [`close()`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#close) 方法无法正常关闭连接的问题，确保资源能够被正确释放。适用于网络环境不稳定导致连接异常的场景。

## 5.8.16 (2025-05-19)

AI 降噪支持自定义背景人声过滤阈值，在嘈杂环境中依然能享受清晰的通话体验。新增 [`setVoiceGate`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setvoicegate) 接口，支持根据使用场景精细调节 AI 降噪功能中对背景人声的过滤程度。

## 5.8.15 (2025-04-29)

- AI 降噪插件针对人声环境进行特殊优化，支持背景人声消除功能，显著提升降噪效果。
- 兼容 IPv6 网络架构，如果您的应用需要在 IPv6 环境中运行，请确保更新到最新版本 SDK。

## 5.8.0 (2025-04-01)

- 新增支持在视频区域和屏幕共享区域添加水印。增强了内容的版权保护，还为企业提供了品牌展示的新途径。
- 优化音频后处理的美声和变声效果。无论是在线会议、直播还是娱乐应用，都能提供更优质的音频体验。具体请参考 [AI 音效](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web#%E6%B7%B7%E6%B5%81%E5%90%8E%E5%8F%98%E5%A3%B0)。

## 5.6.50 (2024-12-25)

**改进优化**

- AI 降噪更新 3.0 版本，降噪效果更优。
- 字幕支持指定翻译语言，具体请参考接口 [`startAsrCaptions`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#startasrcaptions) 和 [基于 RTC SDK 实现与 AI 数字人音视频互动](https://doc.yunxin.163.com/aiagents/guide/zQ3MDQ0NjE?platform=client#%E7%AC%AC%E4%BA%94%E6%AD%A5%E5%BC%80%E5%90%AF%E5%AE%9E%E6%97%B6%E5%AD%97%E5%B9%95) 开启实时字幕章节。

**新增特性**

支持轻量版变声功能。相关使用场景请参考 [招采场景集成最佳实践](https://doc.yunxin.163.com/nertc/guide/jY3OTI2NDM?platform=web#%E5%9B%9B%E5%8F%98%E5%A3%B0%E5%AE%9E%E7%8E%B0%E6%8E%A8%E8%8D%90)。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`setAudioEffectLite`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setaudioeffectlite) | 打开轻量版变声 |
| [`disableAudioEffectLite`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableaudioeffectlite) | 关闭轻量版变声 |

## 5.6.41 (2024-10-29)

**改进优化**

- 修复开启美声变声后，音频延迟逐渐增大的问题。
- 远端音频流混流开启后，支持指定音频输出设备，具体请参考接口 [`setAudioOutput`](https://doc.yunxin.163.com/nertc/references/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setaudiooutput) 和 [AI 音效](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web)。

## 5.6.40 (2024-10-11)

**新增特性**

支持远端音频流混流。支持将多个来自不同远端参与者的音频流（声音）混合成单个音频流。

**改进优化**

优化移动端体验，兼容部分特殊场景。详情请参考 [移动端特殊场景优化](https://doc.yunxin.163.com/nertc/guide/DM3NzExMzg?platform=web)。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`setCodecType`](https://doc.yunxin.163.com/docs/interface/nertc/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#setcodectype) | 指定编解码类型。 |

## 5.6.30 (2024-07-26)

**新增特性**

- 支持采集音量增益，麦克风采集音量可以突破 100。Mozilla Firefox 浏览器暂不支持该特性。
- HTML5 竖屏应用在切换到后台时，可能会导致视频暂停，新增视频恢复播放策略。
- 其它若干项 SDK 优化。

## 5.6.21 (2024-07-11)

**新增特性**

当触发屏幕共享区域限制时，屏幕共享音频同时关闭。

## 5.6.20 (2024-07-10)

**新增特性**

屏幕共享支持区域限制。

<!-- - 实时字幕增加翻译能力，支持翻译为英语/日语。-->

## 5.6.10 (2024-06-13)

**新增特性**

新增远端流美声变声功能，具体请参考 [AI 音效](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web#remoteStreamSample) 远端流美声变声章节。

## 5.6.0 (2024-04-25)

**新增特性**

<!-- - 新增实时字幕功能, 目前暂支持中文语音转中文文字。-->

新增 `video-resize` 事件，当视频分辨率发生变化时触发该事件。

<!-- **新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`startAsrCaptions`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#startasrcaptions) | 开启实时字幕 |
| [`stopAsrCaptions`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#stopasrcaptions) | 关闭实时字幕 | -->

## 5.5.30 (2024-02-21)

**新增特性**

- 支持音频数据回调。使用 Safari 浏览器时，需要在 15 版本及以上。
- 自定义辅音可单独开启。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`enableAudioFrame`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableAudioFrame) | 开启音频 PCM 数据回调 |
| [`disableAudioFrame`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableAudioFrame) | 关闭音频 PCM 数据回调 |

**问题修复**

- 修复了 Chrome 122 版本开始，Client 类中 Stats 相关 API 无效的问题

## 5.5.12 (2023-12-22)

**问题修复**

- 修复移动端 chrome58 拉流黑屏的问题

## 5.5.11 (2023-11-30)

**新增特性**

- 原 AI 降噪升级为 AI 音效，新增支持美声变声混响。AI 降噪使用方式存在变更，具体请参考 [AI 音效](https://doc.yunxin.163.com/nertc/guide/DU1MTA3ODM?platform=web)。
- 支持啸叫检测。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`enableAudioEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableaudioeffect) | 开启美声变声。 |
| [`disableAudioEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableaudioeffect) | 关闭美声变声。 |
| [`setAudioEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setaudioeffect) | 设置美声变声效果。 |
| [`enableAIhowling`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableaihowling) | 开启啸叫检测。 |
| [`disableAIhowling`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableaihowling) | 关闭啸叫检测。 |
| [`onAudioHasHowling`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#onaudiohashowling) | 注册啸叫回调。 |

## 5.5.10 (2023-11-15)

**新增特性**

支持限定访问区域。为满足客户在海外访问域名合规性，网易云信支持 [限定 RTC SDK 的访问区域](https://doc.yunxin.163.com/Overseas/docs/DYzMjg1ODI?platform=others#限定-rtc-sdk-的-访问区域) 功能。无论用户身处何地使用 App，SDK 都只会访问指定区域的域名。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`NERTC.setArea`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setarea) | 指定 RTC Web SDK 访问区域。 |

## 5.5.2 (2023-10-19)

网易云信于 2023 年 10 月 19 日发布了 NERTC SDK 最新版本 5.5.2。

**问题修复**

修复了在谷歌 Chrome 117 以上版本中，调用 `getSessionStats` 和 `getTransportStats` 接口返回数据异常的问题。

## 5.5.0 (2023-09-04)

网易云信于 2023 年 9 月 4 日发布了 NERTC SDK 最新版本 5.5.0。

**新增特性**

音频辅流支持 3A 算法（回声消除 AEC、降噪 ANS、增益补偿 AGC）

**改进优化**

兼容 Vue3 代理。

**问题修复**

- 修复了 Chrome 117 版本（预计 2023 年 9 月 6 日上线） `getStats` API 变化引起的控制台异常报错。

    如果您升级到 Chrome 117 版本后，音视频功能正常，但控制台提示每秒 1 条的报错，请尽快将 NERTC SDK 升级到 5.5.0 版本。

    在升级期间，您可以申请 Chrome Origin Trial，以避免在线上出现该报错。申请地址：<https://developer.chrome.com/origintrials/#/trials/active>。

- 修复了发送端使用 360 极速浏览器 X 可能出现黑屏的问题。
- 修复了发送端未正确关闭屏幕共享音频，导致断网重连后可能出现视频丢失的问题。

- 修复发送端调用 `switchDevice` 切换设备后，`getAudioLevel` 函数的返回值持续为 0 的问题。

- 修复了断网期间日志上报可能丢失的问题。

- 修复了在部分 iOS webview 环境下，反复开关音视频会导致异常行为的问题。

- 修复了服务端调用踢人 API 后，用户重新登录时，报错内容不正确的问题。

- 修改掉线时报错的提示信息，将 MEDIA_TRANSPORT_DISCONNECT 改为 SOCKET_ERROR。

- 修复了火狐浏览器与其他 SDK 共同使用时发生冲突的问题。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`Stream.setAudioProcessing`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setaudioprocessing) | 可以在创建本地流后、采集之前，开启或关闭音频 3A。该接口支持主辅流的音频。 |

**变更 API**
| <div>API</div> | API 说明 |
| --- | --- |
| [`Stream.getAudioLevel`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#getaudiolevel) | 音量的取值范围从 0 ~ 1 修改为 0 ~ 100。一般会议场景下，音量高于 40 可以认为有人在发言。 |

## 5.4.0 (2023-06-15)

网易云信于 2023 年 6 月 15 日发布了 NERTC SDK 最新版本 5.4.0。

**改进优化**

优化了上下行传输质量。

**问题修复**
- 修复了在桌面端高版本 Safari(16.3+) 浏览器中进行屏幕共享时，采集失败的问题。
- 修复了 Safari 15.1 版本浏览器中，摄像头采集分辨率异常的问题。

**变更 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`Stream.open`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#open) | 增加 `enableMediaPub` 参数，用户可以根据需要选择是否发布流。 |

## 4.6.50 (2023-03-15)

网易云信于 2023 年 3 月 15 日发布了 NERTC SDK 最新版本 4.6.50。

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- |
| 调节整个房间的播放音量 | 支持通过 [`Client.setPlaybackVolume`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setplaybackvolume) 调节整个房间所有远端用户在本地的播放音量。详情请参考 [设置通话音量](https://doc.yunxin.163.com/nertc/guide/jY0NjA1ODg?platform=web)。 |
| 获取音频上行 rtt 延迟数据 | 支持通过 [`getLocalAudioStats`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#getlocalaudiostats) 获取音频上行 rtt 延迟数据，以便用户判断当前网络状况好坏。详情请参考 [通话中质量监测](https://doc.yunxin.163.com/nertc/guide/DQ2NDM0NDg?platform=web#本地流音频统计信息)。 |

**问题修复**
- 修复在 iOS 16 上执行 `switchDevice` 切换摄像头后，本地画面停留在第一帧的问题。
- 修复 mute 后再发布音视频，对端收不到 mute 消息的问题。
- 修复 Chrome 85 及以下版本浏览器中，远端音量不显示 active-speaker 的问题。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`Client.setPlaybackVolume`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setplaybackvolume) | 调节房间内所有远端用户在本地的播放音量。 |

**变更 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`subscribe`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#subscribe) | 支持将 `setSubscribeConfig` 和 `subscribe` 合二为一，在 `subscribe` 中直接指定订阅的媒体类型。 |
| [`setLocalRenderMode`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setlocalrendermode) | 视频的宽和高新增支持小数。 |
| [`getLocalAudioStats`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#getlocalaudiostats) | 新增 `rtt` 参数，获取音频上行 rtt 延迟数据，以便用户判断当前网络状况好坏。 |

## 4.6.40 (2023-01-13)

网易云信于 2023 年 1 月 13 日发布了 NERTC SDK 最新版本 4.6.40。

**改进优化**

- 优化错误码（errorCode），可以帮助您快速排查问题原因，具体请参考 [错误码](https://doc.yunxin.163.com/nertc/guide/zU2MDQ4MjU)。
- 优化视频码率参考表，新增 30 帧的帧率选项。
- 优化 Firefox 浏览器环境下的断线重连问题。
- 优化 Electron 平台的音视频体验。

**问题修复**

- 修复使用虚拟背景或高级美颜插件时偶现的视频空白问题。
- 修复使用 AI 降噪功能场景下的已知问题。
- 修复直播推流、云代理、网络状态回调失败的问题。
- 修复 Electron 平台的屏幕共享问题。
- 修复切换伴音与麦克风模式时，麦克风反复开关的问题。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`getCurrentFrameData`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#getcurrentframedata) | 获取当前帧的数据。 |
| [`canPlay`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#canplay) | 判断音视频流是否可以播放。 |
| [`checkBrowserCompatibility`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#checkbrowsercompatibility) | 获取当前浏览器支持 WebRTC 的基本能力。 |

## 4.6.25 (2022-11-08)

网易云信于 2022 年 11 月 8 日发布了 NERTC SDK 最新版本 4.6.25。

::: note note
若您使用的是 iOS 16 系统，**由于系统限制原因**，可能无法正常动态切换视频分辨率。此外，若您使用了自定义视频采集，来源为 Canvas 的视频在本地可能无法正常播放。
:::

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| AI 降噪 | 提供虚拟背景插件 `AIDenoise`，可以与 NERTC Web SDK 搭配使用。支持通过开启 AI 降噪功能，在嘈杂环境中针对背景人声、键盘声等非稳态噪声进行定向降噪，同时也会提升对于环境稳态噪声的抑制，保留更纯粹的人声。详情请参考 [AI 降噪](https://doc.yunxin.163.com/nertc/guide/DYxOTg0NjU)。 |
| 高级 Token 鉴权 | 支持通过权限密钥校验用户的加入或创建房间、发布或订阅音视频流的权限。详情请参考 [高级 Token 鉴权](https://doc.yunxin.163.com/nertc/guide/jQ2MzAzNjY)。 |
| 高级美颜 | 新增去除抬头纹、法令纹、黑眼圈及调整嘴巴宽度和脸长等功能。详情请参考 [高级美颜](https://doc.yunxin.163.com/nertc/guide/Tc5OTQyNzE)。 |

**改进优化**
- 新增部分错误码（errorCode），具体请参考 [错误码](https://doc.yunxin.163.com/nertc/guide/zU2MDQ4MjU)。
- 提升对远端下行流的订阅速度。
- 视频帧率新增 30 帧的可选项。

**问题修复**
- 修复部分设备上出现的视频小流黑屏问题。
- 修复 iOS 16 系统中调用 `stream.play()` 接口无法播放部分远端视频流以及无返回值的问题。
- 修复开启美颜功能后日志停止上传的问题。
- 修复了部分低版本浏览器无法获取本地音量的问题。
- 修复了部分重连场景下，重连过程中抛出 `SOCKET_ERROR` 事件的问题。

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`enableAIDenoise`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableaidenoise) | 开启 AI 降噪。 |
| [`disableAIDenoise`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableaidenoise) | 关闭 AI 降噪。 |
| [`updatePermKey`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#updatepermkey) | 更新高级权限 Token。 |

**变更 API**
| <div>API</div> | API 说明 |
| --- | --- |
| [`getAudioLevel`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#getaudiolevel) | 支持获取远端麦克风的采集音量，可以通过 `mediaType` 指定获取主流或辅流音量。 |
| [`join`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#join) | `JoinOptions` 结构体新增 `permKey` 参数，用于高级 Token 鉴权。 |

## 4.6.21 (2022-09-02)

**改进优化**

- 支持恢复由于系统回收 GPU 资源导致丢失的 WebGL 上下文。
- 修复浏览器显卡黑名单机制导致的 WebGL 兼容问题。
- 修复 Android 端用户无法接收到 Web 端用户离开房间回调的问题。

## 4.6.20 (2022-08-15)

网易云信于 2022 年 8 月 15 日发布了 NERTC SDK 最新版本 4.6.20。

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 虚拟背景 | 提供虚拟背景插件 `VirtualBackground`，可以与 NERTC Web SDK 搭配使用。支持通过开启虚拟背景功能，将用户人像和背景分割开来，虚化用户周围的真实环境，或者以自定义背景色或背景图像替换真实背景。详情请参考 [虚拟背景](https://doc.yunxin.163.com/nertc/guide/TQ1ODA5NjQ)。 |
| 高级美颜 | 提供美颜插件 `AdvancedBeauty`，可以与核心 SDK 搭配使用。支持通过调整美颜相关参数，对人脸进行美型等美颜调整，帮助您轻松实现高级美颜功能。详情请参考 [高级美颜](https://doc.yunxin.163.com/nertc/guide/Tc5OTQyNzE)。 |
| 屏幕共享偏好设置 | 支持在屏幕共享过程中设置共享偏好，根据共享内容为静态或动态画面调整编码倾向。详情请参考 [屏幕共享](https://doc.yunxin.163.com/nertc/guide/TkyODYxMTE)。 |
| 音频辅流 | 支持在视频通话或互动直播的过程中以音频辅流的形式实现音频共享。详情请参考 [音频共享](https://doc.yunxin.163.com/nertc/guide/TE4MzMzOTc)。 |

**改进优化**

| <div>改进优化</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 支持音频双声道兼容模式 | 兼容一些特殊音频设备由于不适配双声道导致的无声问题。详情请参考 [`enableCompatMode`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/modules/nertc.nertc-1.device.html#enablecompatmode) 等。 |
| 支持 ASL 音频选路策略 | 通过 ASL 策略，在大房间的场景中降低客户端上性能消耗，来提升客户端上能支持的用户连接上限。 |
| 增强适配性| 增加 iOS 14.3 及以上版本微信浏览器的适配 |

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`muteAudioSlave`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#muteaudioslave) | 静音音频辅流。 |
| [`unmuteAudioSlave`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#unmuteaudioslave) | 取消静音音频辅流。 |
| [`hasAudioSlave`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#hasaudioslave) | 判断是否有音频辅流。 |
| [`setAudioSlaveVolume`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setaudioslavevolume) | 设置音频辅流的音量。 |
| [`enableCompatMode`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/modules/nertc.nertc-1.device.html#enablecompatmode) | 开启音频双声道兼容模式。 |
| [`disableCompatMode`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/modules/nertc.nertc-1.device.html#disablecompatmode) | 关闭音频双声道兼容模式。 |
| [`registerPlugin`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#registerplugin) | 注册高级美颜/背景分割插件。 |
| [`unregisterPlugin`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#unregisterplugin) | 注销高级美颜/背景分割插件。 |
| [`enableAdvancedBeauty`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enableadvancedbeauty) | 开启高级美颜。 |
| [`disableAdvancedBeauty`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disableadvancedbeauty) | 关闭高级美颜。 |
| [`setAdvBeautyEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setadvbeautyeffect) | 设置美颜效果。 |
| [`presetAdvBeautyEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#presetadvbeautyeffect) | 预设美颜参数。 |
| [`enableBodySegment`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#enablebodysegment) | 开启背景分割。 |
| [`disableBodySegment`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#disablebodysegment) | 关闭背景分割。 |
| [`setBackGround`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setbackground) | 设置背景。 |
| [`Client.on('mute-audio-slave')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 静音音频辅流的回调。 |
| [`Client.on('unmute-audio-slave')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 取消静音音频辅流的回调。 |
| [`localStream.on('plugin-load')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#on) | 高级美颜/背景分割插件加载成功的回调。 |
| [`localStream.on('plugin-load-error')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#on) | 高级美颜/背景分割插件加载失败的回调。 |
| [`localStream.on('basic-beauty-res-complete')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#on) | 通知基础美颜资源加载完成的回调。 |

**变更 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`setVideoEncoderConfiguration`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setvideoencoderconfiguration) | 增加 `contentHint` 参数，以设置屏幕共享偏好。 |
| [`setVideoProfile`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setvideoprofile) | 支持在通话中动态设置视频属性。 |
| [`setSubscribeConfig`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setsubscribeconfig) | `mediaType` 参数新增 `audioSlave` 字段，以配置音频辅流。 |
| [`play`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#play) | `mediaType` 参数新增 `audioSlave` 字段，以配置音频辅流。 |
| [`stop`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#stop) | `mediaType` 参数新增 `audioSlave` 字段，以配置音频辅流。 |
| [`Client.on('stream-added')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | `mediaType` 参数新增 `audioSlave` 字段。 |
| [`Client.on('stream-subscribed')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | `mediaType` 参数新增 `audioSlave` 字段。 |
| [`Client.on('stream-removed')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | `mediaType` 参数新增 `audioSlave` 字段。 |
| [`Client.on('volume-indicator')`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | `type` 参数新增 `audioSlave` 字段。 |
| [`setVideoEncoderConfiguration`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setvideoencoderconfiguration) | 新增 `contentHint` 参数，以设置屏幕共享偏好。 |

## 4.6.10 (2022-06-01)

网易云信于 2022 年 6 月 1 日发布了 NERTC SDK 最新版本 4.6.10。

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 基础美颜 | 网易云信自研的基础美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。详情请参考 [网易云信美颜](https://doc.yunxin.163.com/nertc/guide/jEwOTE5MjE)。 |
| 视频编码水印 | 支持为视频流画面添加编码水印，例如添加公司名称、标语等文字水印、录制时间等时间戳水印、以及 logo 等图片水印。详情请参考 [水印](https://doc.yunxin.163.com/nertc/guide/jE3NzU5MDY)。 |
| 视频截图 | 支持视频截图转 Base64。详情请参考 [视频截图](https://doc.yunxin.163.com/nertc/guide/jgzNDkyMzQ)。 |

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [`setBeautyEffect`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setbeautyeffect) | 开启或关闭美颜。 |
| [`setBeautyEffectOptions`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setbeautyeffectoptions) | 设置美颜参数。 |
| [`setFilter`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setfilter) | 设置滤镜参数。 |
| [`setEncoderWatermarkConfigs`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#setencoderwatermarkconfigs) | 设置视频水印。 |
| [`takeSnapshotBase64`](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#takesnapshotbase64) | 截取指定用户的视频流画面，并生成 Base64 字符串。 |

## 4.6.0 (2022-03-02)

网易云信于 2022 年 3 月 2 日发布了 NERTC SDK 最新版本 4.6.0。

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 支持自定义辅流通道 | 提供辅流传输通道，帮助您传输非摄像头采集的外部视频源等自定义视频源。详情请参考 [自定义视频采集](https://doc.yunxin.163.com/nertc/guide/zg0NDkzOTI?platformId=50082)。 |
| 云代理 | 支持使用云代理服务穿透防火墙限制，使用固定 IP 连接到网易云信服务器。详情请参考 [云代理](https://doc.yunxin.163.com/nertc/guide/Tg4NzAzNDY?platformId=50082)。 |

**改进优化**

| <div>改进优化</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 设备插拔的监听回调 | 监听桌面端设备的麦克风、扬声器、摄像头等外接硬件的插拔动作，当发生相应动作时 SDK 会通过回调接口通知客户。详情请参考 [Client.on("recording-device-changed")](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) 等。 |
| 支持发布大小流 | 优化视频清晰度订阅机制。本地用户可以选择同时发布两种规格的视频流，例如 720P 和 1080P，远端用户可以根据自身的网络情况选择订阅视频的清晰度。详情请参考 [enableDualStream](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#enabledualstream) 等。 |
| Web 桌面端兼容性提升 | 支持 FireFox、Edge 等最新版本的浏览器。详情请参考 [Web 端支持的浏览器类型和版本](https://doc.yunxin.163.com/nertc/guide/TU5NjUzNjU?platformId=50082#Web端支持的浏览器类型和版本)。 |

**新增 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [getAudioEffectsDuration](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#getaudioeffectsduration) | 获取音效文件时长。 |
| [getAudioEffectsCurrentPosition](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/stream.stream-1.html#getaudioeffectscurrentposition) | 获取音效文件当前播放进度。 |
| [enableDualStream](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#enabledualstream) | 设置发送大小流。 |
| [disableDualSteam](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#disabledualstream) | 取消发送大小流。 |
| [setRemoteVideoStreamType](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#setremotevideostreamtype) | 设置接收大流或小流。 |
| [startProxyServer](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#startproxyserver) | 开启云代理服务。 |
| [stopProxyServer](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#stopproxyserver) | 关闭云代理服务。 |
| [Client.on("recording-device-changed")](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 通知应用有音频输入设备被添加、更改或移除的回调。 |
| [Client.on("camera-changed")](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 通知应用有视频输入设备被添加、更改或移除的回调。 |
| [Client.on("playout-device-changed")](https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html/interfaces/client.client-1.html#on) | 通知应用有音频输出设备被添加、更改或移除的回调。 |

**变更 API**

| <div>API</div> | API 说明 |
| --- | --- |
| [createStream](/docs/interface/NERTC_SDK/Latest/Web/html/modules/nertc.nertc-1.html#createstream) | StreamOptions 新增参数 screenAudioSource、screenVideoSource，设置自定义辅流音视频源。 |
| [open](/docs/interface/NERTC_SDK/Latest/Web/html/interfaces/stream.stream-1.html#open) | options 新增参数 screenVideoSource，设置自定义辅流视频源。 |

## 4.5.1 (2021-11-18)

**问题修复**

1. 修复了 iOS 15.1 上 Safari 视频上行发送 H264 会导致页面崩溃的问题。

## 4.5.0 (2021-10-22)

网易云信于 2021 年 10 月 22 日发布了 NERTC SDK 最新版本 4.5.0。

**新增特性**

| <div>新增特性</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| Web 端支持音频共享 | 自 4.5.0 版本开始，在音频共享时，可以同时共享本地播放的音频流和麦克风采集的音频流。详情请参考 [屏幕共享](https://doc.yunxin.163.com/nertc/guide/TkyODYxMTE)。 |
| 云端录制支持通过服务端 API 接口配置 | 云端录制支持通过服务端接口进行录制任务的配置。 |

**改进优化**

| <div>改进优化</div> | <div>特性描述</div> |
| --- | --- | --- | --- |
| 改进了自动播放受限问题 | 自动播放受限表现优化。详情请参考 [浏览器自动播放受限处理](https://doc.yunxin.163.com/nertc/guide/jM3NDE0NTI)。 |
| 包大小优化 | Web SDK 包大小缩减至 0.8MB。 |
| uid 长度 | Web 端 uid 长度对齐移动端。 |

**API 变更**

| <div>API</div> | API 说明 |
| --- | --- |
| [Stream.close](/docs/interface/NERTC_SDK/Latest/Web/api/interfaces/stream.stream-1.html#close) | `type` 参数新增 `screenAudio` 枚举值。 |
| [setCaptureVolume](/docs/interface/NERTC_SDK/Latest/Web/api/interfaces/stream.stream-1.html#setcapturevolume) | 新增 `mediaTypeAudio` 参数。 |
| [takesnapshot](/docs/interface/NERTC_SDK/Latest/Web/api/interfaces/stream.stream-1.html#takesnapshot) | 调用时机由 `Client.publish` 之前调整为 `Client.publish` 前后均可。 |
| [Client.join](/docs/interface/NERTC_SDK/Latest/Web/api/interfaces/client.client-1.html#join) | 从 4.5.0 版本开始，uid 支持 String 类型。为保证跨平台互通，Sting 类型的 uid 需要设置为十进制数字。 |

## 4.4.1 (2021-08-03)

**问题修复**

1. 修复了 频道中有 Linux 端时 active-speaker 回调概率性缺失的问题
2. 修复了日志上传依赖 jQuery 的问题。

## 4.4.0 (2021-07-13)

网易云信于 2021 年 7 月 13 日发布了 NERTC SDK 最新版本 4.4.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
</tr>
<tr>
    <td>加入房间时自动生成 uid</td>
    <td>加入音视频房间时，可以不设置 uid，此时网易云信服务器会自动为您生成一个随机 uid，并支持通过 <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#getuid">getUid</a> 获取本地用户 ID。详情请参考 a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#join">join</a>。</td>
</tr>
<tr>
    <td>支持媒体流加密</td>
    <td>网易云信在默认加密算法的基础上，提供了国密加密方案，进一步保障数据安全。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/TE4MjYwMTU">媒体流加密</a>。</td>
</tr>
<tr>
    <td>支持日志上传</td>
    <td>Web 端加入房间之前开启日志上传，通话结束后相关日志会上传到网易云信服务器，以供问题排查。详情请参考 <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.logger.html#enablelogupload">enableLogUpload</a>。</td>
</tr>
<tr>
    <td>支持 npm 方式获取 Web SDK</td>
    <td>Web SDK 增加 npm 获取方式。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/DM3MDA4NzQ">集成 SDK</a>。</td>
</tr>
</tbody>
</table>

**改进优化**

改善了网络连通性。

**API 变更**

自 4.4.0 开始，入口 WebRTC2 更名为 NERTC，同时兼容 WebRTC2。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setencryptionmode">setEncryptionMode</a></td>
    <td>设置媒体流加密模式。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setencryptionsecret">setEncryptionSecret</a></td>
    <td>设置媒体流加密秘钥。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.logger.html#enablelogupload">enableLogUpload</a></td>
    <td>开启日志上传。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.logger.html#disablelogupload">disableLogUpload</a></td>
    <td>关闭日志上传。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#getuid">getUid</a></td>
    <td>获取本地用户 ID。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#join">join</a></td>
    <td>从 4.4.0 版本开始，uid 可选且默认为 0。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#open">Client.on</a></td>
    <td>增加事件 "crypt-error"。</td>
  </tr>
</table>

**废弃 API**

无。

## 4.3.0 (2021-06-04)

网易云信于 2021 年 6 月 4 日发布了 NERTC SDK 最新版本 4.3.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
</tr>
<tr>
    <td>支持屏幕共享时同时共享本地音频</td>
    <td>Web 端在 Windows 和 macOS 平台的 Chrome 浏览器中支持屏幕共享的同时共享本地播放的音频数据。详情请参考 <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/types.streamoptions.html#screenAudio">screenAudio</a>。</td>
</tr>
<tr>
    <td>支持设备兼容性检测和编解码格式检测</td>
    <td>调用接口即可判断 SDK 对当前浏览器的适配情况、检查 SDK 和当前浏览器同时支持的编解码格式。详情请参考 <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.html#getsupportedcodec">getsupportedcodec</a>、<a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.html#checksystemrequirements">checksystemrequirements</a>。</td>
</tr>
<tr>
    <td>Web 端支持音效功能</td>
    <td>Web 端支持音效功能，可以在通话中增加鼓掌、欢呼等自定义音效设置，增加场景气氛。</td>
</tr>
</tbody>
</table>

**改进优化**

优化高清音质下语音的传输码率，在弱网情况下预计减少 1/3。

**问题修复**

修复 Web SDK 偶现的机关枪声音问题。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.html#getsupportedcodec">getsupportedcodec</a> </td>
    <td>检查 NERTC Web SDK 和当前浏览器同时支持的编解码格式。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//modules/nertc.nertc-1.html#checksystemrequirements">checksystemrequirements</a> </td>
    <td>检查 NERTC Web SDK 对正在使用的浏览器的适配情况。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#playeffect">Stream.playEffect</a> </td>
    <td>播放指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#stopEffect">Stream.stopEffect</a> </td>
    <td>停止播放指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#pauseEffect">Stream.pauseEffect</a> </td>
    <td>暂停播放指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#resumeEffect">Stream.resumeEffect</a> </td>
    <td>恢复播放指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#setVolumeOfEffect">Stream.setVolumeOfEffect</a> </td>
    <td>调节指定音效文件的音量。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#preloadEffect">Stream.preloadEffect</a> </td>
    <td>预加载指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#getEffectsVolume">Stream.getEffectsVolume</a> </td>
    <td>释放指定音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#setEffectsVolume">Stream.setEffectsVolume</a> </td>
    <td>获取所有音效文件播放音量。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#stopAllEffects">Stream.stopAllEffects</a> </td>
    <td>设置所有音效文件播放音量。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#pauseAllEffects">Stream.pauseAllEffects</a> </td>
    <td>停止播放所有音效文件。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#resumeAllEffects">Stream.resumeAllEffects</a> </td>
    <td>暂停播放所有音效文件。</td>
  </tr>
</table>

*变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/types.streamoptions.html#screenAudio">screenAudio</a></td>
    <td>StreamOptions 新增 screenAudio 参数。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#open">screenAudio</a></td>
    <td>Stream.open 增加参数 screenAudio。</td>
  </tr>
</table>

**废弃 API**

无。

## 4.2.1 (2021-05-17)

改进了音频通信质量。

## 4.2.0 (2021-05-12)

网易云信于 2021 年 5 月 12 日发布了 NERTC SDK 最新版本 4.2.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
</tr>
<tr>
    <td>设置用户媒体流优先级</td>
    <td>支持设置本地用户的媒体流为优先级。如果某个用户的优先级为高，那么该用户媒体流的优先级就会高于其他用户，弱网环境下 SDK 会优先保证其他用户收到的、高优先级用户的媒体流的质量。详情请参考 <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setlocalmediapriority">setLocalMediaPriority</a>。</td>
</tr>
<tr>
    <td>画布水印功能</td>
    <td>视频画布中支持添加文字水印、时间戳水印和图片水印，适用于信息安全、版权声明、防伪、宣传等场景。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/jE3NzU5MDY">水印</a>。</td>
</tr>
</tbody>
</table>

**改进优化**

优化戴耳机场景下回声和双讲卡顿效果。优化耳返的延时，从 300ms 降低到 80ms。

**问题修复**

修复蓝牙耳机音频通话被系统电话打断后，无法恢复到蓝牙耳机的问题。

**新增 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/client.client-1.html#setlocalmediapriority">Client.setLocalMediaPriority</a> </td>
    <td>设置本地用户的媒体流优先级。</td>
  </tr>
  <tr>
    <td> <a href="https://doc.yunxin.163.com/nertc/api-refer/web/typedoc/Latest/zh/html//interfaces/stream.stream-1.html#setcanvaswatermarkconfigs">Stream.setCanvasWatermarkConfigs</a> </td>
    <td>添加视频画布水印。</td>
  </tr>
</table>

**变更 API**

无。

**废弃 API**

无。

## 4.1.1 (2021-04-30)

优化媒体订阅的内部流程。

## 4.1.0 (2021-04-07)

网易云信于 2021 年 4 月 7 日发布了 NERTC SDK 最新版本 4.1.0。

**新增特性**

<table>
<tbody>
<tr>
    <th><b>新增特性</b></th>
    <th><b>特性描述</b></th>
</tr>
<tr>
    <td>支持双人通话的独立场景</td>
    <td>NERTC 在 4.1.0 版本中提供了更加适合双人房间场景的底层策略，优化双人房间时的音视频质量效果。双人通话功能适用于点对点通话的业务场景<!--，搭配呼叫组件可以实现点对点呼叫-->。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/TI5ODQzNzY">双人通话</a>。</td>
</tr>
<tr>
    <td>自定义音频渲染</td>
    <td>NERTC SDK 支持自定义音频采集与渲染功能，可以向 NERTC SDK 提供自定义的音频输入源数据，使用自定义的渲染器，并由 NERTC SDK 进行编码推流。详情请参考 <a href="/docs/zUyNzE0ODI/TcwOTkxMzg">自定义音频渲染</a>。</td>
</tr>
<tr>
    <td>Web 端支持视频辅流形式的屏幕共享</td>
    <td>Web 端支持通过辅流形式实现屏幕共享，单独为屏幕共享开启一路上行的视频流，摄像头的视频流作为主流，屏幕共享的视频流作为辅流，两路视频流并行，同时上行摄像头和屏幕两路画面。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/DE1OTk1NjI">屏幕共享</a>。</td>
</tr>
<tr>
    <td>NERTC R​estful API 支持用房间名称（cname）发起调用</td>
    <td>音视频通话和互动直播场景的服务端 API 通过新 URL 的方式支持使用房间名称发起调用，同时原 URL 及调用方式仍旧保留以保证新老兼容。详情请参考 <a href="/https://doc.yunxin.163.com/nertc/guide/zY3NDA3MTc">API 概览</a>。</td>
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
     <td>视频引擎优化</td>
     <td>支持视频 AI 超分，通过机器学习等 AI 算法，改善因受限于网络带宽限制或实时性的要求导致视频分辨偏低的问题，实现低分辨率视频在传输后进行细节补充的效果以优化接收端的视频清晰度，从而提升用户体验。</td>
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
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#muteScreen__anchor">stream.muteScreen()</a> </td>
    <td>开启发送屏幕共享流。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#unmuteScreen__anchor">stream.unmuteScreen()</a> </td>
    <td>停止发送屏幕共享流。</td>
  </tr>
</table>

**变更 API**

<table>
  <tr>
    <th><b>API</b></th>
    <th><b>API 说明</b></th>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#setSubscribeConfig__anchor">remoteStream.setSubscribeConf</a> </td>
    <td>新增 `screen` 属性，可设置是否订阅屏幕共享流。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#takeSnapshot__anchor">remoteStream.takeSnapshot(options)</a> </td>
    <td>新增 `mediaType` 属性，可指定为 `video` 或 `screen`。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#setLocalRenderMode__anchor">localStream.setLocalRenderMode(options, mediaType)</a> </td>
    <td>新增 `mediaType` 参数，可指定为 `video` 或 `screen`。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#setRemoteRenderMode__anchor">remoteStream.setRemoteRenderMode(options, mediaType)</a> </td>
    <td>新增 `mediaType` 参数，可指定为 `video` 或 `screen`。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#startMediaRecording__anchor">remoteStream.startMediaRecording(options)</a> </td>
    <td>新增选项 `screen`，可录制屏幕共享+声音。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#open__anchor">Stream.open(options)</a> </td>
    <td>新增选项 `screen`，用于在通过过程中打开屏幕共享。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Stream.html#close__anchor">Stream.close</a> </td>
    <td>新增选项 `screen`，用于在通过过程中关闭屏幕共享。</td>
  </tr>
  <tr>
    <td> <a href="https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Client.html#join__anchor">client.join</a> </td>
    <td>新增 `mode`，可设置为 1v1，用于开关 1v1 能力。</td>
  </tr>
</table>

**废弃 API**

无。

## <span id="4.0.1- 2021-03-02">4.0.1 (2021-03-02)</span>

**问题修复**

修复偶现的鉴权异常问题。

## <span id="4.0.0- 2021-02-24">4.0.0 (2021-02-24)</span>

网易云信于 2021 年 2 月 24 日发布了 NERTC SDK 最新版本 4.0.0，在音视频能力和性能方面均有显著优化。从 4.0.0 版本开始，NERTC 在 Web 平台的抗丢包能力提升到 70%，支持在旁路推流时设置单路透传和音频编码配置。

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
     <td>Web 端 Qos 优化</td>
     <td>纯音频场景下，Web 端的上下行网络在丢包率 70% 时仍可保证正常通话。</td>
    </tr>
   </tbody>
</table>

**API 变更**

| **API** | **API 说明** |
| --- | --- |
| [addTasks](https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Client.html#addTasks__anchor) | 创建推流任务。rtmpTasks 增加 config 结构体，用于配置音视频流属性。 |
| [updateTasks](https://dev.yunxin.163.com/docs/interface/%E9%9F%B3%E8%A7%86%E9%A2%912.0Web%E7%AB%AF/api/Client.html#deleteTasks__anchor) | 更新推流任务。rtmpTasks 增加 config 结构体，用于配置音视频流属性。 |

## <span id="3.9.1- 2021-01-18">3.9.1 (2021-01-18)</span>

**新增**

适配移动端 H5 上音视频效果，支持 iOS 13+ Safari 浏览器、Android 微信浏览器。

## <span id="3.9.0- 2021-01-08">3.9.0 (2021-01-08)</span>

**新增**
1. Web 端支持主动获取网络连接状态。
2. 直播模式下支持设置房间角色。

**技术优化**

1. 支持全新的网易自研 NEVC 编码协议，具有相较于开源的 AVC 和 HEVC 更优越的性能，同等码率下提升视频整体清晰度，提高鲁棒性和错误恢复能力，优化用户的视频感官体验。
2. 屏幕共享画面优化，提升静态共享画面的清晰度，优化用户体验。
3. 支持暗场景视频图像增强，优化暗场景下的通话体验。

## <span id="3.8.2- 2020-12-29">3.8.2 (2020-12-29)</span>

**改动**

- 流程优化

## <span id="3.8.1- 2020-12-04">3.8.1 (2020-12-04)</span>

**新增**

1. 房间连接状态通知功能
2. 自定义音频、视频输入

## <span id="3.7.0- 2020-09-28">3.7.0 (2020-09-28)</span>

**改动**

- setScreenProfile 接口：增加分辨率的配置

## <span id="3.6.0- 2020-08-20">3.6.0 (2020-08-20)</span>

**新增**

- getSystemStats 接口：获取系统信息

- getTransportStats 接口：获取网络类型和网络连接状况统计数据

- getSessionStats 接口：获取与当前会话相关的统计数据

- getLocalAudioStats 接口：获取本地发布流的音频统计数据

- getLocalVideoStats 接口：获取本地发布流的视频统计数据

- getRemoteAudioStats 接口：获取远端订阅流的音频统计数据

- getRemoteVideoStats 接口：获取远端订阅流的视频统计数据

- connection-state-change 回调: 通知 SDK 的连接状态

- exception 回调: 通知房间内的异常事件。异常事件不是错误，但是往往会引起通话质量问题

- setChannelProfile 接口：设置房间模式

## <span id="3.5.0- 2020-06-23">3.5.0 (2020-06-23)</span>

**新增**

- 新增自定义视频数据输入功能。

- 新增互动直播操作接口

- 新增互动直播状态回调接口

- 互动直播支持占位图片的能力

- safari 13+浏览器的支持

**变更**
- 弃用通话模式设置，统一为多人会议场景。
- 弃用 create API 接口

## <span id="3.4.0- 2020-04-28">3.4.0 (2020-04-28)</span>

**新增**

- 新增互动直播推流功能。

- 新增网络状态回调。

## <span id="3.3.0- 2020-03-31">3.3.0 (2020-03-31)</span>

**新增**

- 新增音频场景设置。

- 新增音频数据回调。

- 新增屏幕共享场景设置。

## <span id="3.2.0- 2020-01-15">3.2.0 (2020-01-15)</span>

- 支持多人会议功能。

- 支持订阅功能。

- 支持音视频通话功能。

- 设备检测功能。

- 新增屏幕共享功能。

- 新增云端伴音功能。

- 新增播放控制。

- 新增声音音量控制。

- 新增视频截图功能。

- 新增客户端录制功能。