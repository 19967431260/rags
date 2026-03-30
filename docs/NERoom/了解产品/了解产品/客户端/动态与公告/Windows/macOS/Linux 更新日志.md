本文介绍网易云信房间组件（NeteaseRoom，简称 NERoom）Windows 和 macOS 端的更新日志。

## <span id="1.44.0 (2026-01-06">1.44.0 (2026-01-06)</span>

**新增特性**

**暗场景增强**：在视频场景光线不足时，改善视频体验。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.enableVideoLowlightEnhance` | 新增接口，用于开启/关闭视频低光增强功能。
`NEVideoLowlightEnhanceLevel` | 新增枚举，用于设置视频低光增强级别。

**兼容版本**

- NERTC：兼容 V5.9.15 版本
- NIM：兼容 V10.9.33 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.43.0 (2025-11-21">1.43.0 (2025-11-21)</span>

**新增特性**

- **多设备支持**：支持同账号多设备同时加入房间。
- **共享抢占**：支持屏幕/白板共享抢占功能。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NEJoinRoomParams` | 新增 `kickOtherDevice` 属性，用于配置如果房间中该账号已经有其他设备加入房间，是否踢掉其他设备。默认为 `true`。
`INERoomContext.enableMultiDevice` | 新增方法，开启/关闭当前房间同账号多设备加入。
`INERoomContext` | 新增 `isRoomMultiDeviceEnabled` 属性，用于获取房间是否开启多设备模式。
`INERoomMember` | 新增 `connectedDeviceList` 属性，用于获取该成员所有已连接的设备列表。
`NEConnectedDevice` | 新增以下属性：<ul><li>`isAudioConnected`：表示当前设备的音频是否连接。</li><li>`isAudioOn`：表示当前设备的音频是否激活。</li><li>`isVideoOn`：表示当前设备的视频是否激活。</li><li>`isSharingScreen`：表示当前设备的屏幕共享是否激活。</li><li>`isSharingSystemAudio`：表示当前设备的系统音频共享是否激活。</li></ul>
`INERoomContext.leaveRoom` | 新增重载方法，在离开房间时，指定离开类型（单设备/所有设备离开）。
`NERoomLeaveRoomType` | 新增枚举，用于定义离开房间的类型。`ALL`：所有设备一起离开；`ONLY_SELF`：仅当前设备离开。
`NERoomEndReason` | 新增 `KICK_BY_OTHER_DEVICE` 枚举，表示同账号多设备加入房间时被其他设备主动踢出。
`INERoomListener.onRoomMultiDeviceEnableChanged` | 新增事件回调，用于监听房间多设备状态变更。
`INERoomListener.onMemberConnectedDeviceListChanged` | 新增事件回调，用于监听成员的设备列表变更。
`INERoomRtcController.subscribeRemoteVideoStreamByRtcUid` | 新增方法，用于根据 rtcUid 订阅/取消订阅远端视频主流。
`INERoomRtcController.subscribeRemoteVideoSubStreamByRtcUid` | 新增方法，用于根据 rtcUid 订阅/取消订阅远端视频辅流。
`INERoomRtcController.setupRemoteVideoCanvasByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频主流渲染器。
`INERoomRtcController.setupRemoteVideoSubStreamCanvasByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频辅流渲染器。
`INERoomService.getMyInRoomDeviceList` | 新增方法，用于根据查询当前在房的设备列表。
`INERoomRtcController.startScreenShare` | 新增方法，通过 `stopCurrentShare` 参数以支持屏幕共享抢占。
`INERoomWhiteboardController.startWhiteboardShare` | 新增方法，通过 `stopCurrentShare` 参数以支持白板共享抢占。
<!--不支持
`NERoomContext.kickMyDeviceOut` | 新增方法，支持从房间内踢除指定设备。
-->

**⚠️变更**

在多设备的场景下，部分参数的定义会存在歧义，以下将对存在歧义的字段进行说明：

参数 | 本端成员 | 远端成员
--- | --- | ---
`INERoomMember.rtcUid` | 当前设备的音视频房间用户 ID | 第一个加入房间设备的音视频房间用户 ID
`INERoomMember.isAudioConnected` | 本端设备的音频连接状态 | 所有设备聚合的音频连接状态
`INERoomMember.isAudioOn` | 本端设备的音频状态 | 所有设备聚合的音频状态
`INERoomMember.isVideoOn` | 本端设备的视频状态 | 所有设备聚合的视频状态
`INERoomMember.isSharingScreen` | 本端设备的屏幕共享状态 | 所有设备聚合的屏幕共享状态
`INERoomMember.isSharingSystemAudio` | 本端设备的系统音频共享状态 | 所有设备聚合的系统音频共享状态

**兼容版本**

- NERTC：兼容 V5.9.10 版本
- NIM：兼容 V10.9.33 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.41.0 (2025-09-25">1.41.0 (2025-09-25)</span>

**新增特性**

新增字幕翻译配置，支持多源语言和多目标语言转换，大幅扩展支持的语言范围。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.setCaptionTranslationConfig` | 新增方法，用于设置字幕翻译配置。较 `setCaptionTranslationLanguage` 接口，该接口可配置多源语言和多目标语言，支持的语言更丰富。

**变更**

使用新的房间场景模板。

**兼容版本**

- NERTC：兼容 V5.9.10 版本
- NIM：兼容 V10.9.33 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.40.0 (2025-08-19">1.40.0 (2025-08-19)</span>

**新增特性**

开启屏幕共享时支持设置屏幕共享的视频参数。

**兼容版本**

- NERTC：兼容 V5.9.5 版本
- NIM：兼容 V10.9.33 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.39.0 (2025-07-04">1.39.0 (2025-07-04)</span>

**新增特性**

- 支持发送自定义广播消息。
- 支持发送定向消息。向房间内的指定身份的用户列表发送自定义消息。

**优化**

日志打印规范。

**兼容版本**

- NERTC：兼容 V5.9.0 版本
- NIM：兼容 V10.8.30 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.38.0 (2025-05-19)">1.38.0 (2025-05-19)</span>

<!--该功能暂未实现
**优化**

优化麦位逻辑，防止漏麦。

-->

**兼容版本**

- NERTC：兼容 V5.8.15 版本
- NIM：兼容 V10.8.30 版本
- 白板：兼容 V3.9.15 版本

## <span id="1.36.0 (2025-02-17)">1.36.0 (2025-02-17)</span>

**新增特性**

- 支持开启/关闭云代理服务。
- 支持在白板初始化时配置防盗链开关。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.setCloudProxy` | 新增方法，用于是否开启云代理服务。
`NEWhiteboardController.setupWhiteboardCanvas` | 新增方法，用于支持白板初始化配置防盗链开关。

**兼容版本**

- NERTC：兼容 V5.7.0 版本
- NIM：兼容 V10.6.0 版本
- 白板：兼容 V3.9.13 版本

## <span id="1.34.0 (2024-12-31)">1.34.0 (2024-12-31)</span>

**新增特性**

- 支持啸叫检测功能，主要用于检测是否由于设备距离过近产生啸叫。
- 支持云录制功能。
- 支持白板与批注的语言切换功能。
- 新增本地录制功能。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomListener.onAudioHasHowling(Boolean)` | 在房间回调中新增 “啸叫检测” 事件的回调。
`NERoomContext.startCloudRecord` | 新增方法，用于开始云录制以及云录制的相关配置。
`NERoomRtcController.startLocalRecord` | 新增方法，用于开启本地录制。
`NERoomRtcController.stopLocalRecord` | 新增方法，用于停止本地录制。
`NERoomRtcController.updateLocalRecordLayouts` | 新增方法，用于更新本地录制布局。
`NERoomRtcController.pushLocalRecorderVideoFrame` | 新增方法，用于推送本地录制视频帧。
`NERoomRtcController.stopLocalRecorderRemux` | 新增方法，用于停止录制文件转码为 mp4 格式。
`NERoomRtcController.remuxFlvToMp4` | 新增方法，用于将 flv 转码为 mp4 格式。
`NERoomRtcController.stopRemuxFlvToMp4` | 新增方法，用于停止将 flv 转码为 mp4 格式。
`INERoomListener.onLocalRecorderStatus` | 在房间回调中新增 “本地录制状态” 事件的回调。
`INERoomListener.onLocalRecorderError` | 在房间回调中新增 “本地录制错误” 事件的回调。

**兼容版本**

- NERTC：兼容 V5.6.50 版本
- NIM：兼容 V10.6.0 版本
- 白板：兼容 V3.9.13 版本

## <span id="1.32.0 (2024-10-22)">1.32.0 (2024-10-22)</span>

**新增特性**

- 支持动态 token 的登录方式。
- 支持发送自定义广播消息功能。
- 支持呼叫会议室设备功能。
- 支持开启/关闭本地视频设备。
- 支持转移自身角色给指定用户。
- 支持获取虚拟背景支持类型。

  部分性能不足的设备会提示不支持虚拟背景功能，但支持 **强制开启** 该功能。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NEAuthService.loginByDynamicToken` | 新增方法，用于实现动态 token 登录。
`NERoomChatController.sendBroadcastCustomMessage` | 新增方法，用于发送自定义广播消息。
`NERoomSIPController.callOutRoomSystem` | 新增方法，用于呼叫会议室设备。
`NERoomRtcController.enableLocalVideo` | 新增方法，用于开启/关闭本地视频设备。
`NERoomContext.handOverMyRole` | 新增方法，用于转移自身角色给指定用户。
`NERoomRtcBaseController.getVirtualBackgroundSupportedType` | 新增方法，用于获取虚拟背景支持类型。
`NERoomRtcBaseController.enableVirtualBackground` | 新增方法，用于强制开启虚拟背景。
`NEClientType` | 设备类型枚举中新增 `H323` 值，表示 H323 平台。 |

**兼容版本**

- NERTC：兼容 V5.6.33 版本
- NIM：兼容 V10.5.0 版本
- 白板：兼容 V3.9.13 版本

## 1.31.1 (2024-10-18)

**重要更新**

网易会议组件底层兼容的 NIM SDK 版本升级至 10.5.0。如果您的应用单独依赖了 NIM SDK，请同步升级至对应的 NIM SDK 版本，详情请参考《即时通讯 IM》[集成 Windows/macOS SDK](https://doc.yunxin.163.com/messaging2/guide/zQ3MzQyMzQ?platform=client)。

**兼容版本**

- 兼容 [NIM SDK（macOS&Windows）10.5.0 版本](https://doc.yunxin.163.com/messaging2/concept/zY1NDUxNzc?platform=client#1050-2024-10-16)。
- 兼容 [NERTC SDK（macOS&Windows）5.6.2008 版本](https://doc.yunxin.163.com/nertc/concept/zQwNDM1NDc?platform=client)。

## <span id="1.21.0 (2023-11-06)">1.21.0 (2023-11-06)</span>

**适配版本**

- NERTC 兼容 V5.5.203(Windows)，V5.5.205(macOS)。
- NIM 兼容 V9.13.0。

**新增 API**

|接口名称 | 接口说明 | 
|-------- | -------------- | 
|`NERoomRtcController::startBeauty`| 通过指定资源路径开启美颜。|
|`NERoomRtcController::installAudioCaptureDriver`|新增检查并自动安装 macOS 共享音频驱动。 |
|`NERoomRtcController::startBeauty`|新增通过指定资源路径开启美颜接口。|
|`NERoomRtcController::getScreenCaptureSourceList`| 新增枚举可共享源接口提供屏幕共享其他 API 调用。|

::: note note
新增新的共享 API 通过 NERoomSourceID 指定共享源，原同名 API 标记废弃。
- `NERoomRtcController::startAppShare`
- `NERoomRtcController::startScreenShare`
- `NERoomRtcController::startRectShare`
- `NERoomRtcController::switchScreenCaptureSource`
:::

**功能变更**

屏幕共享默认使用动画模式，最高支持 30FPS。

**问题修复**

修复极端场景下退出聊天室崩溃问题。

**适配版本**

- NERTC：兼容 V5.5.203(Windows)/V5.5.205(macOS)。
- NIM：兼容 V9.13.0。

## <span id="1.20.0 (2023-09-06)">1.20.0 (2023-09-06)</span>

**适配版本**

- NERTC：兼容 V5.4.7 版本
- NIM：兼容 V9.12.2 版本
- 白板：兼容 V3.9.6 版本

**新增 API**

`INERoomListener::onRoomRemainingSecondsRenewed`：会议时长变更的回调。

**功能变更**

- 本地分辨率设置为自动模式时，加入房间前预览视频的分辨率使用 720P。
- 区域共享的分辨率，根据加入会议时，NERoom 服务器下发的 NERoom 模板中的分辨率进行设置，不再使用原始分辨率。
- 只有在初始化指定 `useAssetServerConfig` 为 true 时，才使用用户传入的自定义白板地址，否则将返回默认白板地址。

**问题修复**

- 修复在断网重连后，没有正确响应互踢通知的问题。
- 修复断网重连后，拉取增量数据后返回 1004，未正确退出的问题。
- 修复加入会议未设置自动开启音频设备时，调用 `unmuteMyAudio` 没有开启音频设备的问题。
- 修复个别场景下异常退出的问题。

## <span id="1.19.0 (2023-08-14)">1.19.0 (2023-08-14)</span>

**适配版本**

- NERTC：兼容 V5.4.6 版本
- NIM：兼容 V9.12.1 版本
- 白板：兼容 V3.9.6 版本

**新增 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomRtcController.enableEncryption`|开启媒体流加密。
|`NERoomRtcController.disableEncryption`|关闭媒体流加密。

**更新 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERtcServerConfig` |新增 RTC 私有化配置地址：`statisticsDispatchServer`、`statisticsBackupServer`。| 


**改进优化**

- 优化并提升加入房间速度（兼容历史服务器版本，私有化环境若期望提高加入房间速度请升级最新服务器版本）。
- 优化退出房间流程，即使在网络状态不佳的情况下，也能快速退出房间。

**问题修复**

- 修复屏幕共享时，未使用服务器模板中设置的共享参数的问题。
- 修复加入会议后无法收到互踢通知的问题。

## <span id="1.17.0 (2023-07-05)">1.17.0 (2023-07-05)</span>

**适配版本**

- NERTC：兼容 V5.3.7 版本
- NIM：兼容 V9.10.0 版本
- 白板：兼容 V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 美颜滤镜        | 支持通过美颜资源或模型打造多种个性化的滤镜。 |  [云信美颜](https://doc.yunxin.163.com/neroom/guide/TU1MTUwNDk?platform=pc)
| 暂停或恢复播放音乐文件。|支持通过 `pauseAudioMixing` 和 `resumeAudioMixing` 接口暂停或恢复播放音乐文件。| [伴音和音效](https://doc.yunxin.163.com/neroom/guide/TE5NzAyNDQ?platform=pc)


**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `INERoomRtcController`|`enableMediaPub`|开启或关闭本地媒体流（主流）的发送。 该方法用于开始或停止向网络发送本地音频或视频数据。 | 
|^^ |`enableAudioAINS`|开启音频 AI 降噪。 | 
|^^ |`setBeautyFilterLevel` |设置滤镜强度。 | 
|^^ |`removeBeautyFilter` |移除滤镜效果。 | 
|^^ |`addBeautySticker` |添加美颜贴纸。 | 
|^^ |`removeBeautySticker`|移除美颜贴纸。|
|^^ |`pauseAudioMixing`|暂停播放音乐文件及混音。 | 
|^^ |`resumeAudioMixing` |恢复播放音乐文件及混音。|
|^^ |`setClientRole` |设置用户在 RTC 房间角色。|

**改进优化**

- 支持 Apple Silicon 芯片，将 x86_64 和 arm64 架构合并到一个包内。
- 将 framework 修改为 dylib，并使用传统的 GNU 导出目录结构。
- 增加 Debug 接口文件，方便接入调试。在 Windows 下，Debug 包名为 `roomkitd.dll`；在 Mac 下，Debug 包名为 `libroomkitd.dylib`。

## <span id="1.13.0 (2023-04-11)">1.13.0 (2023-04-11)</span>

**适配版本**

- NERTC：兼容 V4.6.43 版本
- NIM：兼容 V9.8.0 版本
- 白板：兼容 V3.7.2 版本

**问题修复**

- 修复部分场景切换 PPT 失败的问题。
- 修复部分场景偶现崩溃的问题。

## <span id="1.12.0 (2023-03-03)">1.12.0 (2023-03-03)</span>

**适配版本**

- NERTC：兼容 V4.6.43 版本
- NIM：兼容 V9.7.0 版本
- 白板：兼容 V3.7.2 版本

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomRtcController`|`pauseLocalAudioRecording` |暂停本地麦克风采集，调用后远端用户听不到本端声音。 | 
|^^|`resumeLocalAudioRecording` |恢复本地麦克风采集，调用后远端用户可以听到本端声音。 | 
|^^|`pauseLocalVideoCapture` |暂停本地视频采集。 | 
|^^|`resumeLocalVideoCapture` |恢复本地视频采集。 | 
|`INEPreviewRoomRtcController`|`adjustPlaybackSignalVolume` |调节所有远端用户在本地的播放音量。 | 


## <span id="1.11.0 (2023-01-12)">1.11.0 (2023-01-12)</span>

**适配版本**

- 兼容 `NIM` V9.7.0 版本
- 兼容 `NERtc` V4.6.29 版本
- 兼容 `WHITEBOARD` V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> |
|--------------------------------|-----------------------------------------|
| 支持配置私有化服务器地址        |  通过 `NERoomKitOptions.serverUrl` 接口配置私有化地址，可下载对应的私有化配置，并在初始化时使用相应配置。


**问题修复**

修复部分场景下静音后无效的问题。

## <span id="1.10.0 (2022-12-07)">1.10.0 (2022-12-07)</span>

**适配版本**

- 兼容 `NIM` V9.7.0 版本
- 兼容 `NERtc` V4.6.29 版本
- 兼容 `WHITEBOARD` V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> 
|--------------------------------|-----------------------------------------
|支持切换语言类型|通过 `NERoomKit.switchLanguage` 接口可将 SDK 的语言类型切换为中文、英文或日语。


**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomKit`|`switchLanguage` |切换语言类型 | 

**问题修复**

解决音视频状态信息上报偶现崩溃的问题。

## <span id="1.9.0 (2022-10-31)">1.9.0 (2022-10-31)</span>

**适配版本**

- 兼容 `NIM` V9.1.3.1218 版本
- 兼容 `NERtc` V4.6.21 版本
- 兼容 `WHITEBOARD` V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 设置本地采集音量    |  您可以通过设置采集音量调整通话音量。|  <a href="https://doc.yunxin.163.com/neroom/guide/DY5NTc0ODI?platform=pc" target="_blank">设置通话音量</a>
| 伴音和音效              |  通过混音功能播放掌声、口哨等短时音效，或者为人声添加背景音乐、伴奏音乐或其他场景效果，并将合成后的声音播放给房间内其他成员。在音视频通话或直播场景中，可以更好的烘托气氛、营造多样化语音环境。|  <a href="https://doc.yunxin.163.com/neroom/guide/TE5NzAyNDQ?platform=pc" target="_blank">伴音和音效</a>
| 美声       |  在多人语聊或 K 歌场景中，美声功能可以美化主播或连麦者的声音，混响功能可以让声音更具立体感，提升场景的娱乐氛围，烘托气氛。|  <a href="https://doc.yunxin.163.com/neroom/guide/TU5NDYzODI?platform=pc" target="_blank">美声</a>
| 设置音频属性      |  NERoom SDK 默认使用标准音质模式和语音场景。不同应用场景，对于音质、声道、噪声抑制等方面的要求各有不同，您可以根据 App 的场景，通过 setAudioProfile 设置音频属性，实现最优的音质效果。|  <a href="https://doc.yunxin.163.com/neroom/guide/DM3MjEwMjQ?platform=pc" target="_blank">设置音频属性</a>

**新增 API**

|所属类|接口名称 | 接口说明 | 
|--|---- | -------------- | 
|`NERoomRtcController`|`adjustRecordingSignalVolume`|调节本端采集的音量
|^^|`startAudioMixing`|开始伴音|
|^^|`stopAudioMixing` |结束伴音|
|^^|`setAudioMixingSendVolume` |设置伴音的发送音量
|^^|`setAudioMixingPlaybackVolume`|设置伴音的播放音量
|^^|`playEffect`|播放指定音效文件|
|^^|`setEffectSendVolume`|设置音效文件发送音量|
|^^|`setEffectPlaybackVolume`|设置音效文件播放音量|
|^^|`pauseEffect`|暂停指定音效
|^^|`pauseAllEffects` | 暂停所有音效
|^^|`resumeEffect` |恢复播放指定音效
|^^|`resumeAllEffects` |恢复播放所有音效
|^^|`stopAllEffects` |停止播放所有音效文件
|^^|`setAudioProfile` |设置音频编码配置，可以在加入房间后设置|
|^^|`setChannelProfile`|设置房间场景|
|^^|`setLocalVoicePitch`|设置本地语音音调|
|^^|`setLocalVoiceEqualization`|设置本地语音音效均衡|
|^^|`setLocalVoiceReverbParam`|设置本地语音混响|
|^^|`setRecordDeviceMute` |静音或取消静音采集的麦克风声音
|^^|`enableLocalAudioSubStream`|	开启音频辅流
|^^|`disableLocalAudioSubStream`|	关闭音频辅流
|^^|`getNtpTimeOffset() `|	获取本地系统时间与服务端时间差值
|^^|`setStreamAlignmentProperty`|	对齐本地系统与服务端的时间
|^^|`setAudioSubscribeOnlyBy`|	设置自己的音频只能被房间内指定的人订阅，默认房间内所有其他人都可以订阅自己的音频
|^^|`sendSEIMsg`|	通过主流通道发送媒体增强补充信息（SEI）
|^^|`setAudioFrameObserver`|	设置音频帧监听
|^^|`setParameters`|	设置音视频通话的相关参数
|^^|`setMixedAudioFrameParameters`|	设置录制和播放声音混音后的数据格式
|^^|`setRecordingAudioFrameParameters`|	设置采集的音频格式
|`INERoomListener`|`onRtcRecvSEIMsg`|	远端流的 SEI 内容回调
|^^|`onRtcUserAudioSubStreamStart`|	远端用户开启音频辅流的回调
|^^|`onRtcUserAudioSubStreamStop`|	远端用户停用音频辅流的回调
|`INERoomWhiteboardController`|`setupWhiteboardCanvas`|	设置白板视图
|^^|`setEnableDraw`|		重置白板视图
|^^|`resetWhiteboardCanvas`|	设置白板可绘制

**删除 API**

|所属类|接口名称 | 接口说明 | 
|--|---- | -------------- | 
|`INERoomWhiteboardController`|`getWhiteboardLoginMessage`	|获取白板登录消息字符串，该接口已废弃。
|^^|`getWhiteboardAuthMessage`	|获取白板认证消息字符串，该接口已废弃。
|^^| `getWhiteboardLogoutMessage`	|获取白板登出消息字符串，该接口已废弃。
|^^|`getWhiteboardDrawEnableMessage`	|获取白板绘制权限消息字符串，该接口已废弃。
|^^| `getWhiteboardToolConfigMessage`	|获取白板工具栏配置消息字符串，该接口已废弃。

**问题修复**

修复直播时出现的推流地址 `pushUrl`为空的问题。


## <span id="1.8.0 (2022-09-27)">1.8.0 (2022-09-27)</span>

**适配版本**

- 兼容 `NIM` V9.1.3.1218 版本
- 兼容 `NERtc` V4.6.13 版本
- 兼容 `WHITEBOARD` V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div>
|--------------------------------|-----------------------------------------
| 支持成员头像。                          |  支持设置用户的头像。

**新增 API**

|所属类|接口名称 | 接口说明 | 
|--|---- | -------------- | 
|`NEJoinRoomParams`|`avatar`|加入房间时可以设置临时的用户头像。
|`INERoomMember`| `getAvatar` |获取当前房间中成员的临时头像。
|`INERoomWhiteboardController`|`getWhiteboardUploadLogMessage`|获取白板工具栏日志按钮是否显示的配置信息。

**修改优化**

Windows 平台新增支持 x64 架构。

**问题修复**

- 修复删除房间属性后，房间未正常结束，下次进入同一个房间会崩溃的问题。
- 修复离开房间失败时，没有抛出 `INERoomListener#onRoomEnd` 事件的问题。

## <span id="1.7.0 (2022-08-31)">1.7.0 (2022-08-31)</span>

**适配版本**

- 兼容 `NIM` V9.1.3.1218 版本
- 兼容 `NERtc` V4.6.13 版本
- 兼容 `WHITEBOARD` V3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 支持多媒体消息                           |  支持发送与接收图片消息和文件消息。|  <a href="https://doc.yunxin.163.com/neroom/guide/TIzNDIyNTM?platform=pc" target="_blank">发送消息</a>  <br><a href="https://doc.yunxin.163.com/neroom/guide/Tc0NzQ4Mzk?platform=pc" target="_blank">接收消息</a>
| 复用 IM 的账号             | 如果您的 App 之前已集成了 IM SDK，需要再通过 NERoom 集成其他能力，例如音视频通话、白板等，您可以在 NERoom 中开启 IM 复用功能，帮助您在应用中同时集成并使用 NERoom SDK 和 IM SDK。        | <a href="https://doc.yunxin.163.com/neroom/guide/DUyOTc5MjM?platform=pc" target="_blank">复用 IM 的账号</a>  |

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomListener`  |  `onChatroomMessageAttachmentProgress`| 监听图片、文件消息的附件下载进度 	|
| `NERoomChatController` |`sendImageMessage`| 发送图片消息 	|
| ^^ |`sendFileMessage`	| 发送文件消息 	|
| ^^ | `downloadAttachment`| 下载图片、文件消息的附件 	|
| ^^ | `cancelDownloadAttachment`| 取消下载图片、文件消息的附件 	|
|`INERoomKit`| `addGlobalEventListener`|添加全局事件监听器|
|^^  | `removeGlobalEventListener`|移除全局事件监听器|
|`NERoomKitOptions` |`reuseIM`|复用 IM 账号|

**修改优化**

HTTP 请求头增加 App Key 字段。

**问题修复**

- 解决断网重连后加入房间，加入聊天室失败问题。
- 解决偶现的加入房间卡死问题。

## <span id="1.5.0 (2022-07-30)">1.5.0 (2022-07-30)</span>

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomContext`  | `getRemainingSeconds`| 查询房间剩余时间	|
| ^^ |  `fetchChatRoomMembers`| 查询聊天室成员信息 	|
| `NERoomLiveController` |  `addLiveStreamTask`| 开始推流任务 	|
| ^^ | `updateLiveStreamTask`</a> 	| 更新推流任务 	|
| ^^ |  `removeLiveStreamTask`| 停止推流任务件 	|
| `NERoomRtcController` |  `startAudioMixing`| 开始混音	|
|^^| `stopAudioMixing`|停止混音|
|^^  | `setAudioMixingSendVolume`|调节混音发送音量|
|^^ | `setAudioMixingPlaybackVolume`|调节伴奏播放音量|
|^^|`playEffect`|播放指定音效文件|
|^^  | `stopEffect`|停止播放指定音效文件|
|^^ | `setEffectSendVolume`|设置音效文件发送音量|
|^^| `setEffectPlaybackVolume`|设置音效文件播放音量|
|^^  | `stopAllEffects`|停止播放所有音效文件|
|^^ |`startChannelMediaRelay`|开始跨房间媒体流转发|
|^^ | `stopChannelMediaRelay`|停止跨房间媒体流转发|

## <span id="1.3.0 (2022-06-30)">1.3.0 (2022-06-30)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 虚拟背景                           | NERoom SDK 通过自动识别用户人像，虚化用户周围的真实环境，或者以指定颜色的图片或自定义图像替代真实背景，从而实现设置虚拟背景。 | [虚拟背景](https://doc.yunxin.163.com/neroom/guide/TI5MzcyMDU?platform=pc)           |
| 云信美颜|云信自研的基础美颜和高级美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。|[云信美颜](https://doc.yunxin.163.com/neroom/guide/TU1MTUwNDk?platform=pc)|

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`INEPreviewRoomRtcController`|`enableVirtualBackground` | 启动虚拟背景 | 
|^^|`startBeauty`|启用美颜模块|
|^^|`stopBeauty`|结束美颜模块|
|^^|`enableBeauty`|打开美颜功能|
|^^|`setBeautyEffect`|开启指定美颜效果，并设置美颜强度|
|`NERoomListener`|`onRtcVirtualBackgroundSourceEnabled`| 虚拟背景开启和关闭的通知事件 | 


## <span id="1.1.0 (2022-05-18)">1.1.0 (2022-05-18)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 房间属性设置和更新             | 房间属性是附加到当前房间上的一系列 key-value键值对， key为属性唯一名称， value 为当前属性值。 NERoom 允许开发者自定义房间属性，并在房间生命周期内对属性进行添加、更新、删除操作，同时还可以监听属性变更通知。               | [房间属性](https://doc.yunxin.163.com/neroom/guide/zE4MzA4MzE?platform=pc)       |
| 成员属性设置和更新             | 成员属性是附加到房间特定成员上的一系列 key-value键值对， key为属性唯一名称， value为当前属性值。 NERoom允许开发者自定义成员属性，并在房间生命周期内对成员属性进行添加、更新、删除操作，同时还可以监听属性变更通知。                   | [成员属性](https://doc.yunxin.163.com/neroom/guide/Tg4MzgzMzU?platform=pc)       |
| 静音和取消静音房间内其他成员   | 拥有相应权限的角色，可以静音或取消静音房间内某个成员。      | [静音和取消静音](https://doc.yunxin.163.com/neroom/guide/DY5NTc0ODI?platform=pc) |
| 开启和关闭房间内其他成员的视频 | 拥有相应权限的角色，可以开启和关闭房间内某个成员的视频。           | [开启和关闭视频](https://doc.yunxin.163.com/neroom/guide/Dk0Njg3MTk?platform=pc) |
| 关闭某成员的屏幕共享          | 拥有相应权限的角色，可以关闭某个成员的屏幕共享。     | [屏幕共享](https://doc.yunxin.163.com/neroom/guide/TY4NTEyMTk?platform=pc)       |
| 关闭某成员的白板共享           | 拥有相应权限的角色，可以关闭某个成员的白板共享。         | [互动白板](https://doc.yunxin.163.com/neroom/guide/TIxMjU4NDg?platform=pc)       |
| 直播               | NERoom 的直播基于专业的跨平台视频编解码技术和大规模视频内容分发网络，提供稳定流畅、高可靠、高并发的直播服务，助力轻松打造企业级在线直播平台。      | [直播](https://doc.yunxin.163.com/neroom/guide/TgwNTY2Mzk?platform=pc)           |

**新增 API**

|所属类| 接口名称                   | 接口说明                                       |
|---------------------------------|---------------------------------|------------------------------------------------|
|`NERoomListener`| `onRoomPropertiesChanged` | 房间属性更新事件回调               |
|^^|`onRoomPropertiesDeleted`      | 房间属性删除事件回调               |
|^^|`onMemberNameChanged`           | 成员昵称变更事件回调               |
|^^|`onMemberPropertiesChanged`    | 成员属性更新事件回调               |
|^^|`onMemberPropertiesDeleted`  | 成员属性删除事件回调               |
|^^|`onRoomLockStateChanged`     | 房间锁定状态变更事件回调           |
|^^|`onRtcRemoteAudioVolumeIndication`   | RTC 成员音量大小事件回调            |
|^^|`onRoomLiveStateChanged`        | 直播状态变更事件回调               |
|`NEJoinRoomParams`| `password`        | 输入当前房间的密码         |
|^^|`initialMyProperties`|设置成员属性|
|`NECreateRoomParams`|`password`         | 设置当前房间的密码         |
|^^|`initialRoomProperties`|设置房间属性|
|`NERoomMessage`| `fromNick`         | 发送端昵称         |
|`NERoomEndReason`|`kNERoomEndReasonKickSelf`      | 当相同账号在其他端加入会议时，会把其他端从正在进行的会议中踢出            |
|`NEMessageService`| `sendPassThroughMessage`       | 给房间内的用户发送透传消息，如房间内信令；如果对应用户不在线，信令可能丢失             |
| `NEWhiteboardController`|`stopMemberWhiteboardShare`               | 关闭房间内成员的白板共享，会进行权限校验             |
| `NERoomLiveController`|`startLive`    | 开启直播     |
|^^|`stopLive`   | 停止直播     |
|^^|`updateLive`   | 更新直播     |
|^^|`getLiveInfo`  | 获取直播信息 |
|`INERoomRtcController`| `muteMemberAudio`               | 关闭成员音频，会进行权限校验               |
|^^| `unmuteMemberAudio`             | 打开成员音频，会进行权限校验               |
|^^| `muteMemberVideo`                 | 关闭成员视频，会进行权限校验               |
|^^| `unmuteMemberVideo`            | 打开成员视频，会进行权限校验               |
|^^| `stopMemberShare`          | 关闭房间内成员的屏幕共享，会进行权限校验 |
|^^| `setupRemoteVideoCanvas`      | 设置远端用户视频渲染对象                       |
|^^| `setupRemoteSubVideoCanvas`| 设置远端的辅流视频渲染对象                     |
|`NERoomContext`| `getPassword`           | 获取房间密码                                                                               |
|^^| `getRtcStartTime`         | 获取房间 RTC 开始时间，单位 ms                                                                  |
| ^^| `getRemoteMembers`       | 根据 uuid 查询成员对象                                                                     |
| ^^| `getLiveController`     | 直播功能控制器，可开启、关闭、更新直播                                                     |
|^^| `getRoomProperties`       | 获取当前房间的所有属性                                                                     |
| ^^| `updateRoomProperty`  | 更新房间属性，房间属性是房间的一个 key/value 键值对                                        |
| ^^| `deleteRoomProperty` | 删除房间属性                                                                               |
| ^^| `updateMemberProperty`| 更新成员属性，成员属性为成员的一个 key/value 键值对                                        |
| ^^| `deleteMemberProperty` | 删除成员属性                                                                               |
| ^^| `handOverMyRole`     | 将自身当前的角色转移给对应的用户，自身会恢复到默认的房间角色。只有授权角色才能执行该操作 |
| ^^| `changedMyName`        | 修改自己房间内昵称                                                                         |
| ^^| `isRoomLocked`         | 查询房间当前锁定状态                                                                       |
| ^^| `lockRoom`           | 锁定房间。锁定后成员无法加入                                                               |
| ^^| `unlockRoom`      | 解除锁定房间。解除锁定后成员可以加入该房间                                                 |

## <span id="1.0.0 (2022-03-31)">1.0.0 (2022-03-31)</span>

网易云信 NERoom SDK 的首次发布！

主要包括房间管理、成员管理、文字聊天室、音视频通话、麦位管理、互动白板、直播等模块化功能。