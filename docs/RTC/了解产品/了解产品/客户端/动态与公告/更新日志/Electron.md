本文介绍网易云信音视频通话 NERTC SDK Electron 端的版本更新日志，客户端 API 请参考 [NERTC Electron SDK 概览](https://doc.yunxin.163.com/nertc/references/electron/typedoc/Latest/zh/index.html)。

## 5.5.21-rc-995 (2024-07-18)

- 新增多房间功能。
- 新增加入房间切换房间支持附加信息相关接口。
- 新增开启本地视频主辅流相关接口。
- 新增批量订阅/不订阅指定用户音频流相关接口。
- 新增本地系统和服务器时间获取、对齐相关接口。
- 新增设置本地摄像头主辅流采集和视频配置接口。
- 新增预览支持主辅流。
- 新增开启/关闭本地主辅流发送接口。
- 新增音频主辅流dump接口。
- 新增支持虚拟背景接口。
- 新增云代理服务接口。
- 新增数据通道相关接口。
- 新增美颜相关接口。
- 新增语音范围、空间音效相关接口。
- 新增水印相关接口。

## 4.4.8 (2022-01-18)

**新增特性**

| <div style="width:80px">新增功能</div> | <div style="width:100px">功能描述</div> | <div style="width:100px">相关 API</div> |
| --- | --- | --- |
| 切换房间 | 房间场景为直播场景时，房间中角色为观众的成员可以调用该方法从当前房间快速切换至另一个房间。 | [switchChannel](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#switchChannel) |
| 设置本地用户的媒体流优先级 | 支持设置本地用户的媒体流为优先级。如果本地用户的优先级为高，则该用户媒体流的优先级就会高于其他用户，那么弱网环境下 SDK 会优先保证其他用户收到的本地用户媒体流的质量。 | [setLocalMediaPriority](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setLocalMediaPriority) |
| 客户端音频录制 | 支持在客户端侧进行实时音频流录制，包含房间内所有用户混流后的音频数据。开启录制时可以指定录制文件的音质等。 | [startAudioRecording](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#startAudioRecording) 等客户端音频录制相关 API |
| 跨房间媒体流转发 | 在 NERTC 直播场景的音视频房间中，跨房间媒体流转发功能可实现主播角色跨房间与其他主播实时交流互动，在娱乐场景下可实现跨直播间连麦效果。 | [startChannelMediaRelay](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#startChannelMediaRelay) 等跨房间媒体流转发相关 API |
| 视频流回退 | 网络不理想的环境下，音视频的质量都会下降。为提升用户体验，您可以通过指定接口设置视频流回退选项。在网络条件差、无法同时保证音频和视频质量的情况下，SDK 会自动将视频流从大流切换为小流，或将媒体流回退为音频流，从而提高音视频质量。 | [setLocalPublishFallbackOption](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setLocalPublishFallbackOption) 等视频流回退相关 API |
| 支持视频 AI 超分功能 | 客户端开启 AI 超分功能之后，符合超分条件的视频流会自动进行 AI 超分处理。 | [enableSuperResolution](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#enableSuperResolution) |

**新增 API**

| <div style="width:150px">接口名称</div> | 接口说明 |
| --- | --- |
| [captureImageByUid](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#captureImageByUid) | 在指定用户的画布上截图。 |
| [switchChannel](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#switchChannel) | 快速切换音视频房间。 |
| [setLocalMediaPriority](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setLocalMediaPriority) | 设置本地用户的媒体流优先级。 |
| [setExcludeWindowList](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setExcludeWindowList) | 设置屏幕捕捉时需屏蔽的窗口列表, 该方法在捕捉过程中可动态调用。 |
| [startAudioRecording](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#startAudioRecording) | 开始客户端录音。 |
| [stopAudioRecording](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#stopAudioRecording) | 停止客户端录音。 |
| [startChannelMediaRelay](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#startChannelMediaRelay) | 开始跨房间媒体流转发。 |
| [updateChannelMediaRelay](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#updateChannelMediaRelay) | 更新媒体流转发的目标房间。 |
| [stopChannelMediaRelay](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#stopChannelMediaRelay) | 停止跨房间媒体流转发。 |
| [setLocalPublishFallbackOption](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setLocalPublishFallbackOption) | 设置弱网条件下发布的音视频流回退选项。 |
| [setRemoteSubscribeFallbackOption](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setRemoteSubscribeFallbackOption) | 设置弱网条件下订阅的音视频流回退选项。 |
| [enableSuperResolution](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#enableSuperResolution) | 启用或停止 AI 超分。 |
| [setLocalPublishFallbackOption](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#setLocalPublishFallbackOption) | 通话前网络上下行 Last mile 质量探测报告回调。 |
| [onScreenCaptureStatus](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onScreenCaptureStatus) | 屏幕共享暂停/恢复/开始/结束等回调。 |
| [onAudioRecording](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onAudioRecording) | 音频录制状态回调。 |
| [onMediaRelayStateChanged](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onMediaRelayStateChanged) | 跨房间媒体流转发状态发生改变回调。 |
| [onMediaRelayEvent](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onMediaRelayEvent) | 媒体流相关转发事件回调。 |
| [onLocalPublishFallbackToAudioOnly](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onLocalPublishFallbackToAudioOnly) | 本地发布流已回退为音频流、或已恢复为音视频流回调。 |
| [onRemoteSubscribeFallbackToAudioOnly](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onRemoteSubscribeFallbackToAudioOnly) | 订阅的远端流已回退为音频流、或已恢复为音视频流回调。 |

**变更 API**

| <div style="width:150px">接口名称</div> | 接口变更说明 |
| --- | --- |
| [initialize](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#initialize) | 参数新增私有化服务器地址字段。 |
| [adjustUserPlaybackSignalVolume](https://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#adjustUserPlaybackSignalVolume) | 删除流类型参数。 |
| [onReceSEIMsg](https://doc.yunxin.163.comhttps://doc.yunxin.163.com/docs/interface/NERTC_SDK/Latest/Electron/NERtcEngine.html#event:onRecvSEIMsg) | 更名为 onRecvSEIMsg。 |

**废弃 API**

| <div style="width:150px">接口名称</div> | 接口变更说明 |
| --- | --- |
| enableLocalAudioStream | 开关本地音频发送。从 V4.4.8 版本开始废弃。 |
| setRemoteHighPriorityAudioStream | 设置远端用户音频流优先级。从 V4.4.8 版本开始废弃。 |
| subscribeRemoteAudioSubStream | 取消或恢复订阅指定远端用户音频辅流。从 V4.4.8 版本开始废弃。 |

## 4.1.110 (2021-08-12)

**新增特性**

Electron 功能对齐 NERTC 原生 SDK，版本升级至 V4.1.100。

支持 SEI、美声变声、音频流优先级、声卡采集、录音音量设置功能。详细信息请查看 API 变更。

**变更特性**

- 声卡采集接口改为 `enableLoopbackRecording`。
- 屏幕或应用共享兼容 `Electron->desktopCapture->getSources` 接口传递的所有屏幕 ID 及应用 ID。

**问题修复**

- macOS 下无法正常执行前端回调
- 部分接口拷贝字符串长度超限溢出导致崩溃
- 部分回调接口返回的字符串数据异常无法正常显示或崩溃

**新增 API**

| API | API 说明 |
| --- | --- |
| `sendSEIMsg` | 发送媒体补充增强信息（SEI） |
| `sendSEIMsgEx` | 发送媒体补充增强信息（SEI） |
| `setAudioEffectPreset` | 设置 SDK 预设的人声的变声音效 |
| `setVoiceBeautifierPreset` | 设置 SDK 预设的美声效果。调用该方法可以为本地发流用户设置 SDK 预设的人声美声效果 |
| `setLocalVoicePitch` | 设置本地语音音调。该方法改变本地说话人声音的音调 |
| `setLocalVoiceEqualization` | 设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率 |
| `setRemoteHighPriorityAudioStream` | 设置远端用户音频流高优先级 |
| `subscribeRemoteAudioSubStream` | 取消或恢复订阅指定远端用户的音频辅流 |
| `enableLocalAudioStream` | 开关本地音频发送 |
| `enableLoopbackRecording` | 开启声卡采集 |
| `adjustLoopbackRecordingSignalVolume` | 调节声卡采集信号音量 |
| `adjustUserPlaybackSignalVolume` | 调节本地播放的指定远端用户的指定流类型的信号音量 |

**废弃 API**

| API | API 说明 |
| --- | --- |
| `startSystemAudioLoopbackCapture` | 请改用 `enableLoopbackRecording` 接口。 |
| `stopSystemAudioLoopbackCapture` | 请改用 `enableLoopbackRecording` 接口。 |
| `setSystemAudioLoopbackCaptureVolume` | 请改用 `enableLoopbackRecording` 接口。 |

## 4.1.0 (2021-04-08)

NERTC Electron SDK 首次正式发布。

- 支持实时音视频通话场景及互动直播场景。
- 支持 Windows 和 macOS 双端 SDK 集成。