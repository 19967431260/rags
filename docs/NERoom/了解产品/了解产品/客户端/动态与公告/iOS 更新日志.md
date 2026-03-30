本文介绍网易云信房间组件（NeteaseRoom，简称 NERoom）iOS 端的更新日志。

## <span id="1.44.0 (2026-01-06">1.44.0 (2026-01-06)</span>

**新增特性**

**暗场景增强**：在视频场景光线不足时，改善视频体验。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.enableVideoLowlightEnhance` | 新增接口，用于开启/关闭视频低光增强功能。
`NEVideoLowlightEnhanceLevel` | 新增枚举，用于设置视频低光增强级别。

**兼容版本**

- 兼容 `NIMSDK` 10.9.42 版本
- 兼容 `NERtcSDK` 5.9.15 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.5 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.43.0 (2025-11-21">1.43.0 (2025-11-21)</span>

**新增特性**

- **多设备支持**：支持同账号多设备同时加入房间。
- **共享抢占**：支持屏幕/白板共享抢占功能。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NEJoinRoomParams` | 新增 `kickOtherDevice` 属性，用于配置如果房间中该账号已经有其他设备加入房间，是否踢掉其他设备。默认为 `true`。
`NERoomContext.enableMultiDevice` | 新增方法，开启/关闭当前房间同账号多设备加入。
`NERoomContext` | 新增 `isRoomMultiDeviceEnabled` 属性，用于获取房间是否开启多设备模式。
`NERoomMember` | 新增 `connectedDeviceList` 属性，用于获取该成员所有已连接的设备列表。
`NEConnectedDevice` | 新增以下属性：<ul><li>`isAudioConnected`：表示当前设备的音频是否连接。</li><li>`isAudioOn`：表示当前设备的音频是否激活。</li><li>`isVideoOn`：表示当前设备的视频是否激活。</li><li>`isSharingScreen`：表示当前设备的屏幕共享是否激活。</li><li>`isSharingSystemAudio`：表示当前设备的系统音频共享是否激活。</li></ul>
`NERoomContext.kickMyDeviceOut` | 新增方法，支持从房间内踢除指定设备。
`NERoomContext.leaveRoom` | 新增重载方法，在离开房间时，指定离开类型（单设备/所有设备离开）。
`NELeaveRoomType` | 新增枚举，用于定义离开房间的类型。`ALL`：所有设备一起离开；`ONLY_SELF`：仅当前设备离开。
`NERoomEndReason` | 新增 `KICK_BY_OTHER_DEVICE` 枚举，表示同账号多设备加入房间时被其他设备主动踢出。
`NERoomListener.onRoomMultiDeviceEnableChanged` | 新增事件回调，用于监听房间多设备状态变更。
`NERoomListener.onMemberConnectedDeviceListChanged` | 新增事件回调，用于监听成员的设备列表变更。
`NERoomRtcController.subscribeRemoteVideoStreamByRtcUid` | 新增方法，用于根据 rtcUid 订阅/取消订阅远端视频主流。
`NERoomRtcController.subscribeRemoteVideoSubStreamByRtcUid` | 新增方法，用于根据 rtcUid 订阅/取消订阅远端视频辅流。
`NERoomRtcController.setupRemoteVideoRenderByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频主流渲染器。
`NERoomRtcController.setupRemoteVideoSubStreamRenderByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频辅流渲染器。
`NERoomService.getMyInRoomDeviceList` | 新增方法，用于根据查询当前在房的设备列表。
`NERoomRtcController.startScreenShare` | 新增方法，通过 `stopCurrentShare` 参数以支持屏幕共享抢占。
`NERoomWhiteboardController.startWhiteboardShare` | 新增方法，通过 `stopCurrentShare` 参数以支持白板共享抢占。

**⚠️变更**

在多设备的场景下，部分参数的定义会存在歧义，以下将对存在歧义的字段进行说明：

参数 | 本端成员 | 远端成员
--- | --- | ---
`NERoomMember.rtcUid` | 当前设备的音视频房间用户 ID | 第一个加入房间设备的音视频房间用户 ID
`NERoomMember.isAudioConnected` | 本端设备的音频连接状态 | 所有设备聚合的音频连接状态
`NERoomMember.isAudioOn` | 本端设备的音频状态 | 所有设备聚合的音频状态
`NERoomMember.isVideoOn` | 本端设备的视频状态 | 所有设备聚合的视频状态
`NERoomMember.isSharingScreen` | 本端设备的屏幕共享状态 | 所有设备聚合的屏幕共享状态
`NERoomMember.isSharingSystemAudio` | 本端设备的系统音频共享状态 | 所有设备聚合的系统音频共享状态

**兼容版本**

- 兼容 `NIMSDK` 10.9.45 版本
- 兼容 `NERtcSDK` 5.9.10 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.5 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.42.0 (2025-10-15">1.42.0 (2025-10-15)</span>

**新增特性**

新增拉流播放功能，支持开始拉流、停止拉流、暂停拉流、恢复拉流等操作。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NEPlayerService` | 新增拉流播放器管理服务类，用于管理播放器实例。
`NEPlayer` | 新增拉流播放器类，用于开始拉流、停止拉流、暂停拉流、恢复拉流等相关的操作。
`NEPlayerListener` | 新增拉流播放器事件简体监听器，提供完整的播放回调机制。

**修复**

修复离开房间，RTC 可能无法被释放的问题。

**兼容版本**

- 兼容 `NIMSDK` 10.9.42 版本
- 兼容 `NERtcSDK` 5.9.10 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.4 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.41.0 (2025-09-25">1.41.0 (2025-09-25)</span>

**新增特性**

- 新增字幕翻译配置，支持多源语言和多目标语言转换，大幅扩展支持的语言范围。
- 新增音频编码属性以及音频场景设置。
- 支持获取音视频房间用户 ID。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.setCaptionTranslationConfig` | 新增方法，用于设置字幕翻译配置。较 `setCaptionTranslationLanguage` 接口，该接口可配置多源语言和多目标语言，支持的语言更丰富。
`NERoomRtcController.setAudioProfile` | 新增方法，用于单独设置音频编码属性，不设置音频场景。
`NERoomRtcController.setAudioScenario` | 新增方法，用于设置音频场景。
`NERoomMember` | 新增 `rtcUid` 属性，用于获取音视频房间用户 ID。

**变更**

- 将 `NERoomBase` 切换为 `NEXKitBase` 库。
- 使用新的房间场景模板。

**兼容版本**

- 兼容 `NIMSDK` 10.9.10 版本
- 兼容 `NERtcSDK` 5.9.10 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.4 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.40.0 (2025-08-19">1.40.0 (2025-08-19)</span>

**新增特性**

开启屏幕共享时支持设置屏幕共享的视频参数。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.startScreenShare` | 新增方法，用于开启屏幕共享。较 `startScreenShare(callback:)` 接口，入参新增屏幕共享配置 `configuration`（`NERoomVideoSubStreamConfiguration`），可设置屏幕共享的视频参数。

**兼容版本**

- 兼容 `NIMSDK` 10.9.10 版本
- 兼容 `NERtcSDK` 5.9.5 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.4 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.39.0 (2025-07-04">1.39.0 (2025-07-04)</span>

**新增特性**

- 支持跨房间推流功能。
- 支持发送自定义广播消息。
- 支持发送定向消息。向房间内的指定身份的用户列表发送自定义消息。
- 支持麦位相关监听能力。
- 支持直播房间踢人功能。

**优化**

- 优化字幕日志。
- 日志打印规范。
- `serverUrl` 支持 https 前缀格式补全。

**修复**

- 修复 `onReceiveChatroomMessages` 收到 `RoomNotificationMessages` 类型消息时，属性 `members` 的角色错误的问题。
- 修复多次进出房间后，可能收不到部分 `NERoomListener` 回调的问题。
- 修复正在断网时，对方互踢，网络恢复后，成员列表错误导致的问题。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.startChannelMediaRelay` | 新增方法，开始跨房间推流转发。该接口替换原接口（`NERoomRtcController.startChannelMediaRelay(callback: NECallback)`），较原接口入参新增房间 ID（`roomUuid`）。注：原接口废弃。
`NERoomRtcController.stopChannelMediaRelay` | 新增方法，停止跨房间媒体流转发。该接口替换原接口（`stopChannelMediaRelay()`），较原接口入参新增房间 ID（`roomUuid`）。注：原接口废弃。
`NERoomChatController.sendBroadcastCustomMessage` | 新增方法，用于发送自定义广播消息。
`NEMessageChannelService.sendCustomMessageToRoles` | 新增方法，用于发送定向消息。可选择 **使用当前登录用户鉴权** 或 **使用传入的信息鉴权** 两种方式（入参不同的两个接口）。
`NESeatEventListener` | 在麦位管理的回调中新增昵称、头像等详细的用户信息。
 `onSeatManagersChanged` | 在麦位管理回调中新增 “麦位申请” 事件的回调。
 `onSeatRequestCancelled` | 在麦位管理回调中新增 “麦位申请取消” 事件的回调。
 `onSeatRequestApproved` | 在麦位管理回调中新增 “麦位申请通过” 事件的回调。
 `onSeatRequestRejected` | 在麦位管理回调中新增 “麦位申请拒绝” 事件的回调。
 `onSeatInvitationReceived` | 在麦位管理回调中新增 “麦位邀请” 事件的回调。
 `onSeatInvitationCancelled` | 在麦位管理回调中新增 “麦位邀请取消” 事件的回调。
 `onSeatInvitationAccepted` | 在麦位管理回调中新增 “麦位邀请通过” 事件的回调。
 `onSeatInvitationRejected` | 在麦位管理回调中新增 “麦位邀请拒绝” 事件的回调。
 `onSeatLeave` | 在麦位管理回调中新增 “麦位离开” 事件的回调。
 `onSeatKicked` | 在麦位管理回调中新增 “麦位被踢” 事件的回调。
`NESeatItem` | 新增 `userInfo` 属性，表示用户信息。
`NERoomMember` | 新增 `relayInfo` 属性，表示原房间的信息。
`NEJoinRoomOptions` | 新增 `autoStartVideo` 字段，用于配置是否自动打开视频并发送视频流，默认不打开。

**兼容版本**

- 兼容 `NIMSDK` 10.9.10 版本
- 兼容 `NERtcSDK` 5.9.1 版本
- 兼容 `NECoreKit` 9.7.9 版本
- 兼容 `NECoreIM2Kit` 1.1.4 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.38.0 (2025-05-19)">1.38.0 (2025-05-19)</span>

**优化**

优化麦位逻辑，防止漏麦。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.9.0 版本
- 兼容 `NECoreKit` 9.7.8 版本
- 兼容 `NECoreIM2Kit` 1.1.2 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.36.1 (2025-03-03)">1.36.1 (2025-03-03)</span>

**新增特性**

新增聊天室连接状态监听能力。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomListener.onChatroomStateChange` | 在房间回调中新增 “聊天室连接状态” 事件的回调。

**兼容版本**

- 兼容 `NIMSDK` 10.6.0 版本
- 兼容 `NERtcSDK` 5.7.0 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

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

- 兼容 `NIMSDK` 10.6.0 版本
- 兼容 `NERtcSDK` 5.7.0 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.34.0 (2024-12-31)">1.34.0 (2024-12-31)</span>

**新增特性**

- 支持啸叫检测功能，主要用于检测是否由于设备距离过近产生啸叫。
- 支持云录制功能。
- 支持白板与批注的语言切换功能。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomListener.onAudioHasHowling(Boolean)` | 在房间回调中新增 “啸叫检测” 事件的回调。
`NERoomContext.startCloudRecord` | 新增方法，用于开始云录制以及云录制的相关配置。

**兼容版本**

- 兼容 `NIMSDK` 10.6.0 版本
- 兼容 `NERtcSDK` 5.6.50 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.7.2 版本
- 兼容 `NECoreIM2Kit` 1.0.6 版本

## <span id="1.33.1 (2024-12-26)">1.33.1 (2024-12-26)</span>

修复因 token 超时引起的加入 RTC 房间失败的问题。

## <span id="1.33.0 (2024-11-29)">1.33.0 (2024-11-29)</span>

**新增特性**

- 支持消息内容审核（反垃圾）功能。
- 支持在发送消息时设置扩展信息（`senderExtension`）。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomListener.onAntiSpamMessageIntercepted` | 在房间回调中新增 “消息被反垃圾规则拦截” 事件的回调。
`NERoomChatController.sendDirectTextMessage` | 新增接口，支持设置扩展信息（`senderExtension`）。
`NERoomChatController.sendBroadcastTextMessage` |  新增接口，支持设置扩展信息（`senderExtension`）。
`NERoomChatController.sendGroupTextMessage` |  新增接口，支持设置扩展信息（`senderExtension`）。

**兼容版本**

- 兼容 `NIMSDK` 10.5.0 版本
- 兼容 `NERtcSDK` 5.6.33 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.7.0 版本
- 兼容 `NECoreIM2Kit` 10.0.0 版本

## <span id="1.32.1 (2024-10-22)">1.32.0 (2024-10-25)</span>

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
`NERoomRtcController.setupShareKit` | 新增方法，用于设置应用的 scheme，在屏幕共享扩展倒计时读秒结束后会自动返回应用。
`NEClientType` | 设备类型枚举中新增 `H323` 值，表示 H323 平台。 |

**兼容版本**

- 兼容 `NIMSDK` 10.5.0 版本
- 兼容 `NERtcSDK` 5.6.33 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.7.0 版本
- 兼容 `NECoreIM2Kit` 10.0.0 版本

## 1.31.1 (2024-10-18)

**重要更新**

网易会议组件底层兼容的 NIM SDK 版本升级至 10.5.0。如果您的应用单独依赖了 NIM SDK，请同步升级至对应的 NIM SDK 版本，详情请参考《即时通讯 IM》[集成 iOS SDK](https://doc.yunxin.163.com/messaging2/guide/zk2MjQ5OTc?platform=client)。

**兼容版本**

- 兼容 [NIM SDK（iOS）10.5.0 版本](https://doc.yunxin.163.com/messaging2/concept/TIxNTgxOTk?platform=client#1050-2024-10-15)。
- 兼容 [NERTC SDK（iOS）5.6.2008 版本](https://doc.yunxin.163.com/nertc/concept/TcyMzY0ODg?platform=client)。

## <span id="1.31.0 (2024-08-29)">1.31.0 (2024-08-29)</span>

**新增特性**

- 支持关闭批注共享功能。
- 成员在 PC 端发起音频共享后，支持成员的系统音频共享状态查询和监听以及管理员操作。
- 优化字幕功能，支持设置字幕翻译语言、支持查询当前字幕消息翻译语言和内容。
- 更新白板 Web 页访问地址为 CDN 地址。

**新增 API**

类/方法/回调/错误码|说明
------|--------
`NERoomRtcController.setCaptionTranslationLanguage`|新增方法，用于设置字幕翻译语言。
`NERoomCaptionMessage.translationLanguage`|新增属性，表示当前字幕消息翻译语言
`NERoomCaptionMessage.translationContent`|新增属性，表述当前字幕消息翻译内容。
`NERoomAnnotationController.stopAnnotationShare`|新增方法，用于关闭批注共享。
`NERoomMember.isSharingSystemAudio`|新增方法，用于查询当前成员是否正在共享系统音频。
`NERoomRtcController.stopMemberSystemAudioShare`|新增方法，用于停止成员系统音频共享。
`NERoomListener.onMemberSystemAudioShareStateChanged`|在房间回调中新增 “成员系统音频共享状态变更” 事件的回调。
`NERoomCaptionTranslationLanguage`|新增枚举，表示字幕目标翻译语言，支持三种字幕目标翻译语言。

**兼容版本**

- 兼容 `NIMSDK` 9.17.0 版本
- 兼容 `NERtcSDK_Special` 5.6.2008 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.7 版本
- 兼容 `NECoreIM2Kit` 9.6.10 版本

## <span id="1.30.2 (2024-08-20)">1.30.2 (2024-08-20)</span>

**优化改进**

优化弱网下房间内的表现。

**兼容版本**

- 兼容 `NIMSDK` 9.16.1 版本
- 兼容 `NERtcSDK_Special` 5.6.2008 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.7 版本
- 兼容 `NECoreIM2Kit` 9.6.9 版本

## <span id="1.30.0 (2024-07-22)">1.30.0 (2024-07-22)</span>

**新增特性**

- 支持离线消息推送能力，具体实现流程请参考 [实现离线推送](https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS)。
- 支持音视频房间语音转字幕功能。

**新增 API**

类/方法/回调/错误码|说明
------|--------
`NERoomRtcController.enableCaption`|新增方法，在音视频房间中用于开启/关闭字幕。
`NERoomListener.onCaptionStateChanged`|在房间回调中新增 “字幕状态变更” 事件的回调。
`NERoomListener.onReceiveCaptionMessages`|在房间回调中新增 “接收字幕消息” 事件的回调。
`NERoomCaptionState`|新增对象，表示音视频房间的字幕开启状态。可用于判断当前音视频房间的字幕状态。
`NERoomCaptionErrorCode`|新增对象，表示音视频房间的字幕相关错误码。可用于判断当前音视频房间的字幕状态。
`NERoomKit.updateApnsToken`|新增方法，用于更新推送Token。

**变更 API**

类/方法/回调/错误码|说明
------|--------
`NERoomChatController.fetchChatroomHistoryMessages`|接口行为变更。该接口取消通过标签查询历史消息的能力。

**兼容版本**

- 兼容 `NIMSDK` 9.16.1 版本
- 兼容 `NERtcSDK_Special` 5.6.2008 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.7 版本
- 兼容 `NECoreIM2Kit` 9.6.9 版本

## <span id="1.29.0 (2024-06-12)">1.29.0 (2024-06-12)</span>

**新增特性**

- 新增获取 SDK 日志路径能力。
- 新增音视频多房间能力，包括加入/离开音视频子房间，开启/关闭音视频房间音频模块，以及对音视频房间中的音频管理等功能。
- 新增批注白板能力，用于观看 PC 端发起的透明白板批注。
- 支持音视频房间最大人数的设置与获取能力。
- 支持获取等候室中的主持人信息。


**API 新增**

类/方法/回调/错误码|说明
------|--------
`NERoomKit.getSDKLogPath`|新增方法，用于获取 SDK 日志路径。
`NERoomRtcController.joinRtcChannel`|新增方法，用于加入指定的音视频子房间。
`NERoomRtcController.leaveRtcChannel`|新增方法，用于离开指定的音视频子房间。
`NERoomRtcController.enableMediaPub`|新增方法，用于开启/关闭指定音视频房间的音频流发布。
`NERoomRtcController.adjustChannelPlaybackSignalVolume`|新增方法，用于调整指定音视频房间的混音播放音量。
`NERoomRtcController.enableAudioVolumeIndication`|新增方法，用于开启/关闭音视频房间的音量数据回调。
`NERoomRtcController.enableLocalAudio`|新增方法，用于开启/关闭音视频房间的音频模块。
`NERoomContext.annotationController`|新增类，批注白板控制器，用于观看 PC 端发起的透明白板批注。
`NERoomAnnotationController.setEnableDraw`|新增方法，用于设置批注是否可绘制。
`NERoomAnnotationController.setupCanvas`|新增方法，用于设置批注视图。
`NERoomAnnotationController.resetCanvas`|新增方法，用于重置批注白板。
`NERoomAnnotationController.lockCameraWithContent`|新增方法，用于将批注白板与被标注物的坐标进行绑定。
`NERoomAnnotationController.isAnnotationEnabled`|新增属性，表示当前批注是否开启。
`NERoomAnnotationController.isSupported`|新增属性，表示是否支持批注功能。
`NERoomListener.onRoomAnnotationEnableChanged`|在房间回调中新增 “房间批注状态变更” 事件的回调。
`NERoomListener.onRtcChannelDisconnect`|在房间回调中新增 “RTC 频道断连” 事件的回调。
`NERoomListener.onRtcChannelError`|在房间回调中新增 “RTC 频道错误” 事件的回调。
`NERoomListener.onRtcLocalAudioVolumeIndication`|在房间回调中新增 “RTC 频道本端音量” 事件的回调。
`NERoomListener.onRtcRemoteAudioVolumeIndication`|在房间回调中新增 “RTC 频道远端音量” 事件的回调。
`NECreateRoomParams.maxMembers`|新增属性，表示在创建房间时指定房间的最大人数。
`NERoomListener.onRoomMaxMembersChanged`|在房间回调中新增 “房间最大人数变更” 事件的回调。
`NEWaitingRoomController.getWaitingRoomManagerList`|新增方法，用于主动查询等候室中的主持人以及联席主持人的信息。
`NEWaitingRoomListener.onManagersUpdated`|在等候室回调中新增 “主持人或联席主持人信息变更” 事件的回调。

**API 变更**

- `NERoomCustomSessionMessage` 重命名为 `NERoomSessionMessage`，其中的字段不变。
- 删除 `NERoomMessageSessionListener`。
- `NEMessageChannelService` 中删除 `addSessionMessageListener` 和 `removeSessionMessageListener`。
- `NEMessageChannelListener` 中新增以下回调：
  - `onSessionMessageReceived`：接收到自定义会话消息。
  - `onSessionMessageDeleted`：自定义消息被删除。
  - `onSessionMessageRecentChanged`：最近会话列表变更。
  - `onSessionMessageAllDeleted`：自定义消息被清空。

**问题修复**

修复 `RTC Disconnect` 事件中未正确修改 `localMember.isLocalInRtcChannel` 的问题。

**兼容版本**

- 兼容 `NIMSDK` 9.16.1 版本
- 兼容 `NERtcSDK` 5.5.40 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.7 版本
- 兼容 `NECoreIM2Kit` 9.6.9 版本

## <span id="1.28.0 (2024-05-09)">1.28.0 (2024-05-09)</span>

**新增特性**

- 新增 SIP 外呼能力。
- 新增 APP 内呼叫能力。
- 新增获取聊天室成员信息功能。

**API 更新**

类/方法/回调/错误码|说明
------|--------
`NERoomContext.sipController`|新增属性，用于发起 SIP 外呼。
`NERoomContext.appInviteController`|新增属性，用于发起 APP 应用内呼叫。
`NERoomContext.maxMembers`|新增属性，表示房间最大人数，-1 表示房间内无人数限制。
`NERoomContext.inSIPInvitingMembers`|新增属性，表示正在 SIP 外呼邀请中的成员列表。
`NERoomContext.inAppInvitingMembers`|新增属性，表示正在 App 内呼叫邀请中的成员列表。
`NERoomListener.onMemberSIPInviteStateChanged`|在房间回调中新增“成员SIP邀请状态变更”事件的回调。
`NERoomListener.onMemberAppInviteStateChanged`|在房间回调中新增“成员APP邀请状态变更”事件的回调。
`NERoomMember.isSIPInviting`|新增属性，表示成员是否正在 SIP 外呼邀请中。
`NERoomMember.isAppInviting`|新增属性，表示成员是否正在 App 内呼叫邀请中。
`NERoomMember.inviteState`|新增属性，表示用于标记成员被邀请中的状态。
`NERoomSIPController.callByNumber`|新增方法，支持根据手机号码进行 SIP 外呼。    
`NERoomSIPController.callByUserUuid`|新增方法，支持根据用户 uuid 进行 SIP 外呼。
`NERoomSIPController.callByUserUuids`|新增方法，支持根据用户 uuid 列表进行批量 SIP 外呼。
`NERoomSIPController.cancelCall`|新增方法，支持取消 SIP 外呼。
`NERoomSIPController.removeCall`|新增方法，支持移除 SIP 外呼。
`NERoomSIPController.hangUpCall`|新增方法，支持挂断 SIP 外呼。
`NERoomAppInviteController.callByUserUuid`|新增方法，支持根据用户 uuid 进行 APP 内呼。
`NERoomAppInviteController.callByUserUuids`|新增方法，支持根据用户 uuid 列表进行批量 APP 内呼。
`NERoomAppInviteController.cancelCall`|新增方法，支持取消 APP 内呼。
`NERoomAppInviteController.removeCall`|新增方法，支持移除 APP 内呼。
`NERoomChatController.fetchChatroomMembers`|新增方法，表示获取聊天室成员信息。
`NEAuthEvent.RECONNECTED`|新增事件，表示 IM 重连成功。

**兼容版本**

- 兼容 `NIMSDK` 9.16.1 版本
- 兼容 `NERtcSDK` 5.5.40 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.7 版本
- 兼容 `NECoreIM2Kit` 9.6.9 版本

## <span id="1.27.0 (2024-04-03)">1.27.0 (2024-04-03)</span>

**新增特性**

- 新增消息监听回调功能。
- 新增消息操作相关功能。
  - 新增消息未读数管理功能，包括清理和查询消息未读数。
  - 新增会话历史消息管理功能，包括删除和查询会话历史消息。
- 支持管理全量的等候室成员，包括全部准入和全部移除功能。
- 新增房间黑名单功能。
- 修改准入等候室接口，支持配置是否本次房间自动准入。
- 支持私有化配置 RTC 的 LBS 地址。
- 调整日志的默认级别为 Info。

**API 更新**

类/方法/回调/错误码|说明
------|--------
`NEMessageChannelService.addReceiveSessionMessageListener`|添加消息监听的回调。
`NEMessageChannelService.removeReceiveSessionMessageListener`|移除消息监听的回调。
`NERoomMessageSessionListener`|新增消息监听的回调事件。具体包括以下事件：<li>`onReceiveSessionMessage`：接收到自定义消息<li>`onChangeRecentSession`：最近会话聊天记录变更<li>`onDeleteSessionMessage`：自定义消息被删除<li>`onDeleteAllSessionMessage`：自定义消息全部被删除
`NEMessageChannelService.clearUnreadCount`|新增清理未读数的方法。
`NEMessageChannelService.queryUnreadMessageList`|新增查询未读数的方法。
`NEMessageChannelService.deleteSessionMessage`|新增删除会话消息的方法。
`NEMessageChannelService.deleteAllSessionMessage`|新增删除所有会话消息的方法。
`NEMessageChannelService.getSessionMessagesHistory`|新增获取会话消息历史记录的方法。
`NERoomContext.changeMembersRole`|新增批量修改房间成员角色的方法，仅房间创建者和管理员可修改。
`NERoomContext.kickMemberOut`|在该方法中新增`toBlacklist`参数，表示移除人员时是否将其加入黑名单。
`NERoomContext.enableRoomBlacklist`|新增开启/关闭黑名单功能方法。
`NERoomContext.isRoomBlackListEnabled`|新增获取黑名单状态方法，查看是否开启黑名单功能。
`NEWaitingRoomController.admitAllMembers`|新增准入等候室全部成员的方法。
`NEWaitingRoomController.expelAllMembers`|新增移除等候室全部成员的方法。在移除时可以设置是否允许被移除的成员重新加入房间。
`NEWaitingRoomListener`|在等候室回调中新增“全部等候室成员”事件的回调（`onAllMembersKicked`）。
`NERoomListener`|在房间回调中新增“黑名单状态”事件的回调（`onRoomBlacklistStateChanged`）。
`NERtcServerConfig`|在该类中新增`lbsServer`属性，支持私有化配置 RTC 的 LBS 地址。
`NEWaitingRoomController.admitMember`|	在该方法中新增`autoAdmit`参数，设置是否本次房间自动准入。
`NEErrorCode.CHATROOM_NOT_EXISTS`|新增“聊天室不存在”的错误码。

**兼容版本**

- 兼容 `NIMSDK` 9.15.1 版本
- 兼容 `NERtcSDK` 5.5.33 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.6 版本
- 兼容 `NECoreIM2Kit` 9.6.8 版本

## <span id="1.26.0 (2024-03-06)">1.26.0 (2024-03-06)</span>

**新增特性**

- 支持音频连接/断开功能。  
- 支持管理员修改房间成员名称。
- 聊天室消息支持获取发送端头像。

**API 更新**

接口/类/枚举|说明
------|--------
`NERoomRtcController.reconnectMyAudio`|新增方法，通过该方法重连本地音频。
`NERoomRtcController.disconnectMyAudio` |新增方法，通过该方法断开本地音频。
`NERoomMember.isAudioConnected` |新增属性，表示房间内成员的音频断开状态。
`NERoomListener.onMemberAudioConnectStateChanged`|新增回调，监听成员音频连接状态的变更，用于上报成员断开或重连音频的通知。
`NERoomListener.onMemberNameChanged`|新增回调，用于上报成员名称被修改的通知，且带有操作者信息。
`NEWaitingRoomListener.onMemberNameChanged` |新增回调，用于上报成员名称被修改的通知，且带有操作者信息。
`NERoomContext.changeMemberName`|新增方法，用于管理员修改房间里的成员的昵称。
`NERoomChatMessage.fromAvatar`|新增属性，表示支持获取聊天室消息的发送端头像。
`NEMessageChannelListener.onReceiveCustomMessage`|新增回调，用于上报未知类型的消息。

**兼容版本**

- 兼容 `NIMSDK` 9.14.2 版本
- 兼容 `NERtcSDK` 5.5.23 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.6 版本
- 兼容 `NECoreIM2Kit` 9.6.6 版本

## <span id="1.25.2 (2024-01-25)">1.25.2 (2024-01-25)</span>

**升级**

升级 `NERtcSDK` 至 5.5.21 版本。

**兼容版本**

- 兼容 `NIMSDK` 9.14.1 版本
- 兼容 `NERtcSDK` 5.5.21 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.6 版本
- 兼容 `NECoreIM2Kit` 9.6.6 版本

## <span id="1.25.1 (2024-01-15)">1.25.1 (2024-01-15)</span>

**升级**

升级 `NERtcSDK_Special` 至 5.5.207 版本，以解决海外 LBS 引起的加入房间失败问题。

**兼容版本**

- 兼容 `NIMSDK` 9.14.1 版本
- 兼容 `NERtcSDK_Special` 5.5.207 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.6 版本
- 兼容 `NECoreIM2Kit` 9.6.6 版本

## <span id="1.25.0 (2024-01-10)">1.25.0 (2024-01-10)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.14.1 版本
- 兼容 `NERtcSDK_Special` 5.5.203 版本
- 兼容 `NEWhiteboard` 3.9.6 版本
- 兼容 `NECoreKit` 9.6.6 版本
- 兼容 `NECoreIM2Kit` 9.6.6 版本

**新增特性**

- 新增等候室功能。

  - 创建聊天室时，支持两种聊天室类型：主聊天室和等候室聊天室。
  - 创建房间时，可设置是否开启等候室。
  - 可以在等候聊天室中，向所有成员或指定成员发送消息。

- 新增聊天室消息记录预览功能。

- 支持设置视频编码属性，包括编码分辨率、裁剪模式、码率、帧率等。

**变更 API**

|<div style="width:120px">接口/类/枚举</div>  | 接口说明 | 
|------- | -------------- | 
|`NEChatroomType`|新增 `NEChatroomType` 枚举，分为主聊天室和等候室聊天室两种类型。
|`NERoomChatMessage`|`NERoomChatMessage` 对象新增 `chatroomType` 属性，区分主聊天室消息和等候室消息。
|`NERoomChatController.joinChatroom`|该方法新增 `chatroomType` 入参，可配置该参数加入不同类型的聊天室。
|`NERoomChatController.leaveChatroom` |该方法新增 `chatroomType` 入参，可配置该参数离开不同类型的聊天室。
|`NERoomChatController.sendBroadcastTextMessage`| `NERoomChatController` 中的所有发送消息方法都新增 `chatroomType` 入参，可配置该参数发送消息至不同的聊天室类型。
|`NERoomChatController.sendGroupTextMessage`|^^
|`NERoomChatController.sendDirectTextMessage`|^^
|`NERoomChatController.sendImageMessage`|^^
|`NERoomChatController.sendFileMessage`|^^
|`NERoomChatController.fetchChatroomMembers`|该方法新增 `chatroomype` 入参，可配置该参数获取不同类型的聊天室成员。
|`NERoomChatController.fetchChatroomHistoryMessages`|该方法新增 `chatroomType` 入参，可配置该参数在房间内获取不同类型的聊天室消息记录。
|`NERoomChatController.recallChatroomMessage`|该方法新增 `chatroomType` 入参，可配置该参数撤回不同类型的聊天室消息记录。
| `NERoomService.fetchChatroomHistoryMessages`|新增预览聊天室消息记录方法，可配置 `chatroomType` 参数获取不同类型的聊天室消息记录。<note type =note>该方法支持在房间外调用，当房间销毁归档后，可通过该接口来预览聊天室消息记录。
|`NECreateRoomOptions.enableWaitingRoom`|在 `NECreateRoomOptions` 中新增 `enableWaitingRoom` 属性，创建房间时可设置是否开启等候室，true，开启；false，关闭（默认）。
| `NERoomContext.isInWaitingRoom`|新增查询是否在等候室方法。加入房间后，通过该方法可查询当前是否在等候室。
|`NERoomContext.waitingRoomController`|新增等候室控制器，包含开启/关闭等候室、成员管理、等候室信息查询等功能。
|`NEWaitingRoomListener`|新增 `NEWaitingRoomController.addListener`（`NEWaitingRoomListener`）事件监听器，可监听等候室成员（包括本端）加入、离开、准入、等候室信息变更等事件。
|`NERoomContext.rejoinAfterAdmittedToRoom`|新增重新正式加入房间方法。等候室中的成员需要管理员准入才能加入房间，成员在监听到被管理员准入后，可重新正式加入房间。
|`NERoomRtcBaseController.setLocalVideoConfig`|该方法可设置视频编码属性，包括编码分辨率、裁剪模式、码率、帧率等。|

**修复**

修复部分已知问题。

## <span id="1.23.0 (2023-11-30)">1.23.0 (2023-11-30)</span>

**新增特性**

- 支持在房间中查询历史消息和撤回消息，具体请参见 [消息撤回](https://doc.yunxin.163.com/neroom/guide/DMyMDc1NTY?platform=iOS) 和 [历史消息查询](https://doc.yunxin.163.com/neroom/guide/zM1NjM0NTI?platform=iOS)。
- 新增云端录制会议能力，具体请参见 [云端录制](https://doc.yunxin.163.com/neroom/guide/zg0OTk2NjU?platform=iOS)。

**新增 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NERoomContext.startCloudRecord`|开始云端录制。|
|`NERoomContext.stopCloudRecord`|停止云端录制。|
|`NERoomService.getRoomCloudRecordList`|获取房间中的云端录制列表。|
|`NERoomChatController.fetchChatroomHistoryMessages`|查询房间中的历史消息。|
|`NERoomChatController.recallChatroomMessage`|在房间中撤回指定消息。|

**变更 API**

|<div style="width:120px">接口/类/枚举</div>  | 接口说明 | 
|------------- | -------------- | 
|`NERoomListener`|房间监听器中 `NERoomListener` 新增 `onRoomCloudRecordStateChanged` 事件，监听云端录制的开始和结束。事件中包含 `state`（云端录制状态）和 `operateBy`（状态变更操作者信息）。
|`NERoomContext`|房间上下文中的房间属性 `roomProperties` 中新增 `roomProperties.record.recordId` 属性，表示录制状态。属性变更会触发 `onRoomPropertiesChanged` 事件。
|`NERoomContext`|房间上下文 `NERoomContext` 中新增 `isCloudRecording` 属性，可用于查询是否在云端录制中。  
|`NERoomChatNotificationMessage`|聊天室通知消息 `NERoomChatNotificationMessage` 中新增 `recalledMessageId` 属性，可用来获取被撤回的消息 ID。
|`NERoomChatEventType`|房间操作 `NERoomChatEventType` 中新增枚举 `recall`，表示消息撤回操作。

::: note notice
修改 `NERoomChatController` 接口中的发送消息接口，将 `callback` 类型为 `NECallback<NERoomChatMessage>`。

这里以给单人定向发送消息方法为例，将 `public func sendDirectTextMessage(userUuid: String, message: String, callback: NECallback<AnyObject>? = nil)` 改造成 `public func sendDirectTextMessage(userUuid: String, message: String, callback: NECallback<NERoomChatMessage>? = nil)`。
:::

**兼容版本**

- 兼容 `NIMSDK` 9.12.0 版本
- 兼容 `NERtcSDK_Special` 5.5.203 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.22.0 (2023-11-08)">1.22.0 (2023-11-08)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 房间禁言      | 允许房间创建者或管理员在房间内将所有成员禁言，同时也禁止所有成员开启音频和视频功能。| [房间禁言](https://doc.yunxin.163.com/neroom/guide/TY0Njk2NDk?platform=iOS)
| 黑名单        | 允许房间创建者或管理员将房间内的指定成员添加到黑名单，黑名单中的成员将被移除出房间且无法重新加入房间。 | [黑名单](https://doc.yunxin.163.com/neroom/guide/jczMjk5MTk?platform=iOS)
| 成员禁言          | 允许房间创建者或管理员设置指定成员禁言或使用音频和视频功能。当成员被禁言时，将无法在房间内发消息，使用音频和视频功能。 | [成员禁言](https://doc.yunxin.163.com/neroom/guide/DM5ODIwODU?platform=iOS)

**兼容版本**

- 兼容 `NIM` 9.12.0 版本
- 兼容 `NERtcSDK_Special` 5.5.203 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

**新增 API**

| 接口名称 | 接口说明 |
| -------- | -------- | 
|`banRoomChat` |设置房间所有成员禁言。|
|`unbanRoomChat` |取消房间所有成员禁言。|
|`banRoomAudio` |设置房间内所有成员禁用音频功能。|
|`unbanRoomAudio`|取消房间内所有成员禁用音频功能。|
|`banRoomVideo`|设置房间内所有成员禁用视频功能。|
|`unbanRoomVideo` |取消房间内所有成员禁用视频功能。|
|`addToBlacklist` |添加指定成员到黑名单。|
|`removeFromBlacklist` |将指定成员移除出黑名单。|
|`getBlacklist` |获取房间内黑名单列表。|
|`banMemberChat` |设置成员禁言。|
|`unbanMemberChat` |取消成员禁言。|
|`banMemberAudio`| 设置成员禁用音频功能。|
|`unbanMemberAudio` | 取消成员禁用音频功能。|
|`banMemberVideo` | 设置成员禁用视频功能。|
|`unbanMemberVideo` | 取消成员禁用视频功能。|
|`getChatBannedMembers` |获取房间内禁言成员列表。|
|`getAudioBannedMembers` | 获取禁止使用音频功能的成员列表。|
|`getVideoBannedMembers`| 获取禁止使用视频功能的成员列表。|
|`onRoomChatBanStateChanged` | 房间禁言回调。|
|`onRoomAudioBanStateChanged` | 房间音频禁用回调。|
|`onRoomVideoBanStateChanged` | 房间视频禁用回调。|
|`onMemberChatBanStateChanged` | 成员禁言回调。|
|`onMemberAudioBanStateChanged`| 成员音频禁用回调。|
|`onMemberVideoBanStateChanged` | 成员视频禁用回调。|
|`onMemberAddToBlacklist` | 成员被拉黑回调。|
|`onMemberRemoveFromBlacklist` | 成员被取消拉黑回调。|

## <span id="1.20.0 (2023-09-05)">1.20.0 (2023-09-05)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.12.0 版本
- 兼容 `NERtcSDK_Special` 5.4.8 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

**新增 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NERoomContext.roomExt`|获取到当前房间的扩展信息
|`NERoomContext.changeRoomName`|修改房间的名称
|`NERoomContext.changeRoomExt`|修改房间的扩展信息
|`NERoomContext.changeMyExt`|修改自己的扩展信息
|`NERoomListener.onRoomNameChanged`| 房间名称已变更的回调
|`NERoomListener.onRoomExtChanged`| 房间扩展信息变更的回调
|`NERoomListener.onRoomConnectStateChanged`|房间连接状态已改变的回调。IM 或 RTC 断开时，触发disconnect 状态，IM 和 RTC重连成功后，触发 reconnect 状态
|`NERoomListener.onMemberExtChanged`|成员扩展信息变更的回调
|`NESeatEventListenerExt.onSeatRequestSubmitted`、`onSeatRequestCancelled`、`onSeatRequestApproved`、`onSeatRequestRejected`|原来的同名回调保留，新回调新增`ext`参数，用于获取申请上麦时设置的自定义信息

**更新 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NECreateRoomParams`|新增 `roomExt`参数，支持房主在创建房间的时候就设置房间的扩展信息
|`NEJoinRoomParams`|新增`ext`参数，支持房主在加入房间的时候就设置房间的扩展信息
|`NERoomMember`|新增`ext`参数，支持获取成员的扩展信息
|`NESeatItem`|新增`ext` 参数，用于获取申请上麦时设置的自定义信息
|`NESeatRequestItem`|新增`ext` 参数，用于获取申请上麦时设置的自定义信息
|`NERoomSeatController.submitSeatRequest`|新增`ext` 参数，用于设置申请上麦时的自定义信息
|`NERoomContext.changeMyName`|接口行为变更。回调不再关注修改聊天室昵称成功与否，以兼容在不加聊天室的使用场景

## <span id="1.19.0 (2023-08-14)">1.19.0 (2023-08-14)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.12.0 版本
- 兼容 `NERtcSDK_Special` 5.4.3 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

**改进优化**

优化并提升加入房间的速度。

**新增 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomListener.onRoomRemainingSecondsRenewed` |当房间剩余时长更新时触发此回调。| 
|`NERoomRtcController.enableEncryption`|开启媒体流加密。
|`NERoomRtcController.disableEncryption`|关闭媒体流加密。

**更新 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERtcServerConfig` |新增 RTC 私有化配置地址：`sdkConfigServer`、`statisticsDispatchServer`、`statisticsBackupServer`| 
|`NERoomContext.remainingSeconds` |房间剩余时长字段的类型修改为 `Int` 类型

## <span id="1.18.0 (2023-07-31)">1.18.0 (2023-07-31)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.12.0 版本
- 兼容 `NERtcSDK_Special` 5.4.0 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

**新增 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`changeSeatIndex` |切换麦位| 

## <span id="1.17.0 (2023-07-04)">1.17.0 (2023-07-04)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.10.0 版本
- 兼容 `NERtcSDK_Special` 5.3.7 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**改进优化**

优化大房间场景下，SDK 与服务端的信令交互。

**更新 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomRole` |删除 `superRole`参数，该参数已废弃 | 
| ^^ | 新增 `hide` 参数，用于设置角色的成员是否需要在成员列表中展示 |

## <span id="1.16.0 (2023-06-20)">1.16.0 (2023-06-20)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.10.0 版本
- 兼容 `NERtcSDK_Special` 5.3.7 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> |
|--------------------------------|-----------------------------------------|
| 支持 AI 降噪        |  NERoom SDK 为您提供网易云信自研 AI 算法降噪功能，可智能分析环境音成分，自动甄别并过滤环境噪声。开启 AI 降噪之后，在嘈杂的环境中可以针对背景人声、键盘声等非稳态噪声进行定向降噪，同时也会提升对于环境稳态噪声的抑制，保留更纯粹的人声。
|支持音频共享  |在屏幕共享或共享本地播放的音乐文件等场景中，用户常常需要将本地系统音频发送至远端。NERoom 提供了音频共享功能，帮助您在共享屏幕的同时也能播放本地背景音，或者共享本地视频文件或音乐文件的声音，为您规避播放在线音乐文件可能会遇到的版权问题。 

**新增 API**

所属的类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomRtcController`|`enableAudioAINS` |开启/关闭音频智能降噪 | 
|^^ |`enableLoopbackRecording`| 在屏幕共享时，支持开启/关闭音频共享 |

## <span id="1.15.0 (2023-06-02)">1.15.0 (2023-06-02)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.10.0 版本
- 兼容 `NERtcSDK_Special` 4.6.50 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 支持使用 IM 账号登录 NERoom        |  如果您的 App 之前已集成了 IM SDK，已经存在 IM 账号，可以直接使用 NERoom 提供的 `loginByIM` 接口登录 NERoom。|  [复用 IM 的账号](https://doc.yunxin.163.com/neroom/guide/jU1ODMwNTg?platform=iOS)

**改进优化**

- 新增对 IM 登录状态 `loseConnection` 的监听，用于在长时间断网情况下销毁 `roomContext`。
- `onNERtcEngineDidDisconnect` 不再触发 `NERoomListener` 的 `onRtcChannelError` 回调，改为内部处理直接销毁 `roomContext`。

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NEAuthService`|`loginByIM` |IM 账号鉴权 | 

**更新 API**

|所属类 | 接口说明 | 
|---- | -------------- | 
|`NERoomKitOptions`| 移除`reuseIM` 参数。复用逻辑改为 SDK 内部完成。如果已经登录过 NIM，则内部直接复用。
| `NERoomLiveLayout`|直播布局新增自定义布局（`custom`），值为 5。

## <span id="1.14.0 (2023-04-27)">1.14.0 (2023-04-27)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.8.0 版本
- 兼容 `NERtcSDK_Special` 4.6.50 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomWhiteboardController`|`setCanvasBackgroundColor` |设置白板的画布背景颜色。 | 
|^^   |`lockCameraWithContent`|将白板和被标注物（例如电子文档、PPT等）的坐标信息绑定。防止多端进行协作编辑时，其他端的用户对白板进行放大或缩小，而导致标注内容大小不一致等问题。|

## <span id="1.13.0 (2023-04-11)">1.13.0 (2023-04-11)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.8.0 版本
- 兼容 `NERtcSDK_Special` 4.6.50 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NEPreviewRoomRtcController`|`stopPreview(Boolean)` |关闭预览时，销毁RTC实例。 | 

**新增属性**

|所属类|属性名称 | 接口说明 | 
|----|---- | -------------- | 
| `NEJoinRoomParams`|`crossAppAuthorization` |跨AppKey的房间鉴权 | 
| `NEMessageChannelService.sendCustomMessage`|`crossAppAuthorization` |跨AppKey的房间鉴权 | 

**改进优化**

优化在弱网或无网络情况下，关闭本端音视频的操作。

## <span id="1.12.2 (2023-03-31)">1.12.2 (2023-03-31)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.6.4 版本
- 兼容 `NERtcSDK_Special` 4.6.43 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增属性**

|所属类|属性名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomKitOptions`|`APNSCerName` |推送证书信息 | 

**改进优化**

RTC的生命周期随使用而变，不再在登录完成后初始化。

## <span id="1.12.1 (2023-03-30)">1.12.1 (2023-03-30)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.6.4 版本
- 兼容 `NERtcSDK_Special` 4.6.43 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**改进优化**

修复 `resumeIM` 设值不生效的问题。

## <span id="1.12.0 (2023-03-03)">1.12.0 (2023-03-03)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.6.4 版本
- 兼容 `NERtcSDK_Special` 4.6.43 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomRtcController`|`pauseLocalAudioRecording` |暂停本地麦克风采集，调用后远端用户听不到本端声音。 | 
|^^|`resumeLocalAudioRecording` |恢复本地麦克风采集，调用后远端用户可以听到本端声音。 | 
|^^|`pauseLocalVideoCapture` |暂停本地视频采集。 | 
|^^|`resumeLocalVideoCapture` |恢复本地视频采集。 | 
|^^|`enableAudioVolumeIndication` |启用说话者音量提示。 App 通过此接口可以获取当前谁在说话以及说话者的音量。  | 
|^^|`adjustPlaybackSignalVolume` | 调节所有远端用户在本地播放的混音音量。 | 
|^^|` enableMediaPub` | 开启或关闭本地媒体流（主流）的发送。  | 
|`NEPreviewRoomRtcController` |`startLastmileProbeTest`|开始通话前网络质量探测。|
|^^ |`stopLastmileProbeTest`|停止通话前网络质量探测。|
|`NERoomListener`|`onRtcLocalAudioVolumeIndication`|提示房间内本地用户瞬时音量的回调。 该回调默认为关闭状态。|
|`NEPreviewRoomListener`|`onRtcLastmileQuality`|报告本地用户的网络质量。|
|^^|`onRtcLastmileProbeResult`|报告通话前网络上下行 last mile 质量。|

**更新 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NERoomListener.onRtcRemoteAudioVolumeIndication`|命名变更：`onRtcAudioVolumeIndication` 变更为 `onRtcRemoteAudioVolumeIndication`。<br>行为变更：该回调不再包含本地用户的音量回调，本地用户音量回调提供了单独的接口。

**改进优化**

支持通过 `uploadLog` 上报日志给 NERoom。

## <span id="1.11.0 (2023-01-09)">1.11.0 (2023-01-09)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.6.4 版本
- 兼容 `NERtcSDK_Special` 4.6.29 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> 
|--------------------------------|-----------------------------------------
| 支持配置私有化服务器地址        |  通过 `NERoomKitOptions.serverUrl` 接口配置私有化地址，可下载对应的私有化配置，并在初始化时使用相应配置。

**更新 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NERoomCreateAudioEffectOption`|增加 `progressInterval` 参数，配置音频文件播放进度的回调间隔，默认为 1000ms。

## <span id="1.10.0 (2022-12-06)">1.10.0 (2022-12-06)</span>

**兼容版本**

- 兼容 `NIMSDK` 9.6.4 版本
- 兼容 `NERtcSDK_Special` 4.6.29 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> |
|--------------------------------|-----------------------------------------|
| 聊天室消息新增通知消息类型                          |  新增 `NERoomChatNotificationMessage`，用于接收聊天室内的通知消息，例如成员进出。
|支持创建通话类型房间与直播类型房间 |`NERoomService.createRoom` 接口创建房间时，可通过 `NECreateRoomParams.roomProfile` 参数指定房间类型。
|支持以观众角色加入房间|通过 `NERoomService.joinRoom` 加入类型为 `NERoomProfile.LIVE_BROADCASTING` 的房间时，可设置 `NEJoinRoomParams.role` 为 `NERoomBuiltinRole.OBSERVER`，实现以观众角色进入房间，适用于 PK 直播等场景。
|支持设置加入房间时，是否打开本地音频设备|通过 `NERoomService.joinRoom` 的 `enableMyAudioDeviceOnJoinRtc` 字段，配置加入 RTC 房间时，是否打开本地音频设备，默认关闭。
|支持切换语言类型|通过 `NERoomKit.switchLanguage` 接口可将 SDK 的语言类型切换为中文、英文或日语。

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomChatMessage`|`NERoomChatNotificationMessage` |消息通知 | 
| `NERoomKit`|`switchLanguage` |切换语言类型 | 

**更新 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NERoomService.createRoom`|增加 `NECreateRoomParams.roomProfile` 参数，用于创建房间时指定房间类型。
|`NERoomService.joinRoom`|新增 `enableMyAudioDeviceOnJoinRtc` 参数。用于配置加入 RTC 房间时，是否开启本地音频设备。默认关闭。<br>该选项若配置为开启，则 SDK 会提前初始化音频设备，但不会对外发送本地音频流。如果需要发送音频流，还需要调用 `NERoomRtcController.unmuteMyAudio` 方法。

## <span id="1.8.0 (2022-09-27)">1.8.0 (2022-09-27)</span>

**新增特性**

支持设置用户的头像。

**更新 API**

|接口名称 | 接口说明 | 
|---- | -------------- | 
|`NEJoinRoomParams`|增加 `avatar` 参数，加入房间时可以设置临时的用户头像。
|`NERoomMember` |增加 `avatar` 参数，获取当前房间中成员的临时头像。

**兼容版本**

- 兼容 `NIMSDK` 8.11.11 版本
- 兼容 `NERtcSDK_Special` 4.6.13 版本
- 兼容 `NEWhiteboard` 3.7.2 版本

## <span id="1.7.0 (2022-08-31)">1.7.0 (2022-08-31)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 支持多媒体消息                           |  支持发送与接收图片消息和文件消息|  <a href="https://doc.yunxin.163.com/neroom/guide/TE1NDMyMTU?platform=iOS" target="_blank">发送消息</a> <br><a href="https://doc.yunxin.163.com/neroom/guide/Tg0MzA4MjU?platform=iOS" target="_blank">接收消息</a>

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomChatFileMessage`|- | 文件消息 | 
|`NERoomChatImageMessage` | -	| 图片消息 	|
|`NERoomListener`  |  `onReceiveChatroomMessages`| 接收到文件消息和图片消息的回调 	|
| ^^ | `onChatroomMessageAttachmentProgress`	| 监听图片、文件消息的附件上传/下载进度 	|
| NERoomChatController | `sendImageMessage`	| 发送图片消息 	|
| ^^ |`sendFileMessage` 	| 发送文件消息 	|
| ^^ | `downloadAttachment`	| 下载图片、文件消息的附件 	|
| ^^ |`cancelDownloadAttachment`	| 取消下载图片、文件消息的附件 	|

**兼容版本**

- 兼容 `NIMSDK` 8.11.11 版本
- 兼容 `NERtcSDK_Special` 4.6.13 版本

## <span id="1.3.0 (2022-06-30)">1.3.0 (2022-06-30)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 虚拟背景                           | NERoom SDK 通过自动识别用户人像，虚化用户周围的真实环境，或者以指定颜色的图片或自定义图像替代真实背景，从而实现设置虚拟背景。 | [虚拟背景](https://doc.yunxin.163.com/neroom/guide/Dc3NjEzMjc?platform=iOS)           |
| 云信美颜|云信自研的基础美颜和高级美颜功能，支持在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，或通过画面滤镜改变视频的色调与氛围。|[云信美颜](https://doc.yunxin.163.com/neroom/guide/zYwNjc5ODI?platform=iOS)|

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomRtcBaseController`|`enableVirtualBackground`| 启动虚拟背景。 | 
| ^^ | `startBeauty` 	| 开启美颜功能模块。 	|
| ^^ | `stopBeauty`	| 结束美颜功能模块。 	|
| ^^ | `enableBeauty` 	| 暂停或恢复美颜效果。 	|
| ^^ | `setBeautyEffect` 	| 设置美颜效果。 	|
| ^^ |`addBeautyFilter`| 添加滤镜效果。|
| ^^ |`setBeautyFilterLevel`|设置滤镜强度。|
| ^^ | `removeBeautyFilter`	| 移除滤镜。 	|
|`NERoomListener`|`onRtcVirtualBackgroundSourceEnabled` | 虚拟背景开启和关闭的通知事件。 | 
|`NERoomLiveController`|`addLiveStreamTask`|添加旁路推流任务。|
| ^^|`updateLiveStreamTask`|更新旁路推流任务。|
| ^^|`removeLiveStreamTask`|删除旁路推流任务。|
|`NERoomKit`|`isInitialized`|获取鉴权服务。|

## <span id="1.1.0 (2022-05-18)">1.1.0 (2022-05-18)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 耳返                           | 耳返即耳机采集监听，在设备上插入耳机或耳麦后，可以从耳机侧听到本设备麦克风采集到的声音，主要用来监听本地采集的音频。耳返音频具备低延时、高音质等特征，可以实时向主播等参与音频互动的成员反馈本端的声音数据，让主播可以实时听到本端的声音。耳返功能一般用于在线 KTV、连麦 PK、演唱会等娱乐场景。 | [耳返](https://doc.yunxin.163.com/neroom/guide/DA5NzI4Mjk?platform=iOS)           |
| 伴音和音效                     | 支持通过混音功能播放掌声、口哨等短时音效，或者为人声添加背景音乐、伴奏音乐或其他场景效果，并将合成后的声音播放给房间内其他成员。在音视频通话或直播场景中，可以更好的烘托气氛、营造多样化语音环境。      | [伴音和音效](https://doc.yunxin.163.com/neroom/guide/DgzMDUyOTY?platform=iOS)    |
| 房间属性设置和更新             | 房间属性是附加到当前房间上的一系列 key-value键值对， key为属性唯一名称， value 为当前属性值。 NERoom 允许开发者自定义房间属性，并在房间生命周期内对属性进行添加、更新、删除操作，同时还可以监听属性变更通知。               | [房间属性](https://doc.yunxin.163.com/neroom/guide/zQ2MTkzMDY?platform=iOS)       |
| 成员属性设置和更新             | 成员属性是附加到房间特定成员上的一系列 key-value键值对， key为属性唯一名称， value为当前属性值。 NERoom允许开发者自定义成员属性，并在房间生命周期内对成员属性进行添加、更新、删除操作，同时还可以监听属性变更通知。                   | [成员属性](https://doc.yunxin.163.com/neroom/guide/jM3MzM2OTI?platform=iOS)       |
| 静音和取消静音房间内其他成员   | 拥有相应权限的角色，可以静音或取消静音房间内某个成员。      | [静音和取消静音](https://doc.yunxin.163.com/neroom/guide/zQ3NDE4NTA?platform=iOS) |
| 开启和关闭房间内其他成员的视频 | 拥有相应权限的角色，可以开启和关闭房间内某个成员的视频。           | [开启和关闭视频](https://doc.yunxin.163.com/neroom/guide/TQ1ODU5Mjc?platform=iOS) |
| 设置本地视图                   | 在视频通话前，可以设置本地视图。            | [本地视频预览](https://doc.yunxin.163.com/neroom/guide/TMzMDYxNzE?platform=iOS)   |
| 关闭某成员的屏幕共享           | 拥有相应权限的角色，可以关闭某个成员的屏幕共享。    | [屏幕共享](https://doc.yunxin.163.com/neroom/guide/zk3OTUwNDg?platform=iOS)       |
| 关闭某成员的白板共享           | 拥有相应权限的角色，可以关闭某个成员的白板共享。         | [互动白板](https://doc.yunxin.163.com/neroom/guide/Dc4MDc2NDg?platform=iOS)       |
| 直播                           | NERoom 的直播基于专业的跨平台视频编解码技术和大规模视频内容分发网络，提供稳定流畅、高可靠、高并发的直播服务，助力轻松打造企业级在线直播平台。      | [直播](https://doc.yunxin.163.com/neroom/guide/Dk5MTQ1NjQ?platform=iOS)           |

**新增 API**

|所属类|接口名称 | 接口说明 | 
|---- | -------------- | -------------- |
|`NERoomKit`|`sdkVersions` | 获取SDK版本信息 | 
| `NERoomContext`|`password`             | 获取房间密码                                                                               |
| ^^|`rtcStartTime`         | 房间 RTC 开始时间，单位 ms                                                                  |
| ^^|`getMember`          | 根据 uuid 查询成员对象                                                                     |
| ^^|`liveController`        | 直播功能控制器，可开启、关闭、更新直播                                                     |
| ^^|`properties`          | 获取当前房间的所有属性                                                                     |
| ^^|`updateRoomProperty`   | 更新房间属性，房间属性是房间的一个 key/value 键值对                                        |
| ^^|`deleteRoomProperty`  | 删除房间属性                                                                               |
| ^^|`updateMemberProperty`| 更新成员属性，成员属性为成员的一个 key/value 键值对                                        |
| ^^|`deleteMemberProperty` | 删除成员属性                                                                               |
| ^^|`handOverMyRole`    | 将自身当前的角色转移给对应的用户，自身会恢复到默认的房间角色。只有授权角色才能执行该操作 |
| ^^|`changeMyName`         | 修改自己房间内昵称                                                                         |
| ^^|`isRoomLocked`          | 查询房间当前锁定状态                                                                       |
| ^^|`lockRoom`           | 锁定房间。锁定后成员无法加入                                                               |
| ^^|`unlockRoom`          | 解除锁定房间。解除锁定后成员可以加入该房间                                                 |
| `NEPreviewRoomRtcController`|`startPreview`         | 开启预览              |
|^^|`setupLocalVideoCanvas`|设置本地视图|
| `NERoomRtcController`|`muteMemberAudio`                 | 关闭成员音频，只有授权角色才能执行该操作               |
| ^^|`unmuteMemberAudio`             | 打开成员音频，只有授权角色才能执行该操作               |
| ^^|`muteMemberVideo`                | 关闭成员视频，只有授权角色才能执行该操作               |
| ^^|`unmuteMemberVideo`          | 打开成员视频，只有授权角色才能执行该操作               |
| ^^|`stopMemberScreenShare`          | 关闭房间内成员的屏幕共享，只有授权角色才能执行该操作 |
| ^^|`setupRemoteVideoCanvas`      | 设置远端用户视频渲染对象                       |
| ^^|`setupRemoteSubStreamVideoCanvas` | 设置远端的辅流视频渲染对象                     |
| ^^|`startRtcChannelMediaRelay`        | 开始跨房间媒体流转发                           |
| ^^|`stopRtcChannelMediaRelay`         | 停止跨房间媒体流转发                           |
| ^^|`setSpeakerphoneOn`              | 打开或关闭扬声器                               |
| ^^|`isSpeakerphoneOn`             | 查询扬声器是否开启                             |
| ^^|`startAudioDump`                  | 打开音频 Dump                                   |
| ^^|`stopAuDioDump`                 | 停止音频 Dump                                   |
| ^^|`enableAudioVolumeIndication`   | 启用说话者音量提示                             |
| ^^|`enableEarBack`              | 开启或关闭耳返功能                             |
| ^^|`startAudioMixing`            | 开始播放音乐文件                               |
| ^^|`stopAudioMixing`               | 停止播放音乐文件                               |
| ^^|`playEffect`                      | 播放指定音效文件                               |
| ^^|`stopEffect`                     | 停止播放指定音效文件                           |
| ^^|`setAudioMixingSendVolume`      | 调节伴音发送音量                               |
| ^^|`setAudioMixingPlaybackVolume`  | 调节伴音播放音量                               |
| ^^|`setEffectSendVolume`           | 设置音效文件发送音量                           |
| ^^|`setEffectPlaybackVolume`        | 设置音效文件播放音量                           |
| ^^|`stopAllEffect`                 | 停止播放所有音效文件                           |
| `NERoomLiveController`|`startLive`     | 开启直播     |
| ^^|`stopLive`     | 停止直播     |
| ^^|`updateLive`   | 更新直播     |
| ^^|`getLiveInfo` | 获取直播信息 |
| `NEWhiteboardController`|`stopMemberWhiteboardShare`                | 关闭房间内成员的白板共享，只有授权角色才能执行该操作             |
| `NERoomListener`|`onRoomPropertiesChanged`     | 房间属性更新事件回调               |
| ^^|`onRoomPropertiesDeleted`      | 房间属性删除事件回调               |
|  ^^|`onMemberNameChanged`         | 成员昵称变更事件回调               |
|  ^^|`onMemberPropertiesChanged`    | 成员属性更新事件回调               |
|  ^^|`onMemberPropertiesDeleted`   | 成员属性删除事件回调               |
|  ^^|`onRoomLockStateChanged`     | 房间锁定状态变更事件回调           |
| ^^|` onRtcAudioVolumeIndication`    | RTC 成员音量大小事件回调            |
|  ^^|`onRtcAudioOutputDeviceChanged` | RTC 音频输出设备变更事件回调       |
|  ^^|`onRoomLiveStateChanged`       | 直播状态变更事件回调               |
| `NEMessageChannelService`|`sendCustomMessage`              | 给房间内的用户发送透传消息，如房间内信令；如果对应用户不在线，信令可能丢失             |
| `NERoomEndReason`|`selfKick`            | 当相同账号在其他端加入会议时，会把其他端从正在进行的会议中踢出            |
| `NERoomChatMessage`|`fromNick`       | 发送端昵称         |
|`NECreateRoomParams`|`initialProperties`|设置房间属性|
| `NEJoinRoomParams`|`password`         | 输入当前房间的密码         |
|^^|`initialProperties`|设置成员属性|

## <span id="1.0.0 (2022-03-31)">1.0.0 (2022-03-31)</span>

网易云信 NERoom SDK 的首次发布！

主要包括房间管理、成员管理、文字聊天室、音视频通话、麦位管理、互动白板、直播等模块化功能。