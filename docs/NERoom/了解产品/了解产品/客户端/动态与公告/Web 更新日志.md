本文介绍网易云信房间组件（NeteaseRoom，简称 NERoom）Web 端的更新日志。

## <span id="1.44.0 (2026-01-06">1.44.0 (2026-01-06)</span>

**新增特性**

**暗场景增强**：在视频场景光线不足时，改善视频体验。

**API 更新**

类/方法/回调/错误码 | 说明
--- | --- 
`NERoomRtcController.enableVideoLowlightEnhance` | 新增接口，用于开启/关闭视频低光增强功能。
`NEVideoLowlightEnhanceLevel` | 新增枚举，用于设置视频低光增强级别。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.33 版本
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
`NERoomService.getMyInRoomDeviceList` | 新增方法，用于根据查询当前在房的设备列表。
`NERoomRtcController.startScreenShare` | 新增方法，通过 `stopCurrentShare` 参数以支持屏幕共享抢占。
`NERoomWhiteboardController.startWhiteboardShare` | 新增方法，通过 `stopCurrentShare` 参数以支持白板共享抢占。
<!--api中没搜到
`NERoomRtcController.setupRemoteVideoRenderByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频主流渲染器。
`NERoomRtcController.setupRemoteVideoSubStreamRenderByRtcUid` | 新增方法，用于根据 rtcUid 设置远端视频辅流渲染器。
-->

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

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.31 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.41.0 (2025-09-25">1.41.0 (2025-09-25)</span>

**新增特性**

- 新增一系列音频处理能力，包括啸叫控制、音效处理、AI降噪和人声消除等。
- 支持多种变声效果设置。

**API 更新**

类/方法/回调/错误码	| 说明
--- | ---
`NERoomRtcController.disableAIhowling` | 新增方法，用于关闭啸叫检查。
`NERoomRtcController.enableAudioEffect` | 新增方法，用于开启音效。
`NERoomRtcController.setAudioEffect` | 新增方法，用于设置变声效果。
`NERoomRtcController.disableAudioEffect` | 新增方法，用于关闭特效。
`NERoomRtcController.enableAIDenoise` | 新增方法，用于开启 AI 降噪。
`NERoomRtcController.disableAIDenoise` | 新增方法，用于关闭 AI 降噪。
`NERoomRtcController.setVoiceGate` | 新增方法，用于设置背景人声消除阈值。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.27 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.40.0 (2025-08-19">1.40.0 (2025-08-19)</span>

升级底层兼容的组件版本。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.27 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.39.0 (2025-07-04">1.39.0 (2025-07-04)</span>

升级底层兼容的组件版本。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.20 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.38.0 (2025-05-19)">1.38.0 (2025-05-19)</span>

升级底层兼容的组件版本。

**兼容版本**

- 兼容 `NIMSDK` 10.8.30 版本
- 兼容 `NERtcSDK` 5.8.15 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.36.1 (2025-03-21)">1.36.1 (2025-03-21)</span>

**新增特性**

云录制及直播支持采集互动白板画面，可以将白板的画面作为视频流的一部分进行录制或直播，确保观众能够看到白板上的内容。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
[`NERoomWhiteboardController.setupWhiteboardCanvas`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomWhiteboardController.html#setupWhiteboardCanvas) | 更新方法，新增 [`options`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomWhiteboardSetupWhiteboardCanvasOptions.html) 参数，用于设置白板的比例为 16:9。 |

**兼容版本**

- 兼容 `NIMSDK` 10.6.0 版本
- 兼容 `NERtcSDK` 5.6.50 版本
- 兼容 `NEWhiteboard` 3.9.15 版本

## <span id="1.36.0 (2025-02-17)">1.36.0 (2025-02-17)</span>

**新增特性**

- 支持开启/关闭云代理服务。
- 支持在白板初始化时配置防盗链开关。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
[`NERoomRtcController.setCloudProxy`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomRtcController.html#setcloudproxy) | 新增方法，用于是否开启云代理服务。
[`NEWhiteboardController.setupWhiteboardCanvas`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomWhiteboardController.html#setupwhiteboardcanvas) | 新增方法，用于支持白板初始化配置防盗链开关。

**兼容版本**

- 兼容 `NIMSDK` 10.6.0 版本
- 兼容 `NERtcSDK` 5.6.50 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.35.0 (2025-01-23)">1.35.0 (2025-01-23)</span>

**新增特性**

支持麦位管理功能，主要用于多人实时互动。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
[`NERoomSeatController`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomSeatController.html) | 新增麦位管理功能类，主要包括上麦、下麦、抱麦、踢麦等接口。

**兼容版本**

- 兼容 `NIMSDK` 10.5.0 版本
- 兼容 `NERtcSDK` 5.6.50 版本
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
[`NERoomContext.startCloudRecord`](https://doc.yunxin.163.com/neroom/references/web/typedoc/Latest/zh/html/interfaces/index.NERoomContext.html#startcloudrecord) | 新增方法，用于开始云录制以及云录制的相关配置。

**兼容版本**

- 兼容 `NIMSDK` 10.5.0 版本
- 兼容 `NERtcSDK` 5.6.50 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.33.0 (2024-12-03)">1.33.0 (2024-12-03)</span>

优化 H5 播放受限逻辑。

## <span id="1.32.0 (2024-10-22)">1.32.0 (2024-10-22)</span>

**新增特性**

- 支持动态 token 的登录方式。
- 支持发送自定义广播消息功能。
- 支持呼叫会议室设备功能。
- 支持转移自身角色给指定用户。

**新增 API**

类/方法/回调/错误码 | 说明
--- | --- 
`NEAuthService.loginByDynamicToken` | 新增方法，用于实现动态 token 登录。
`NERoomChatController.sendBroadcastCustomMessage` | 新增方法，用于发送自定义广播消息。
`NERoomSIPController.callOutRoomSystem` | 新增方法，用于呼叫会议室设备。
`NERoomContext.handOverMyRole` | 新增方法，用于转移自身角色给指定用户。
`NEClientType` | 设备类型枚举中新增 `H323` 值，表示 H323 平台。 |

**兼容版本**

- 兼容 `NIMSDK` 10.5.0 版本
- 兼容 `NERtcSDK` 5.6.33 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## 1.31.1 (2024-10-18)

**重要更新**

网易会议组件底层兼容的 NIM SDK 版本升级至 10.5.0。如果您的应用单独依赖了 NIM SDK，请同步升级至对应的 NIM SDK 版本，详情请参考《即时通讯 IM》[集成 Web/uni-app/小程序 SDK](https://doc.yunxin.163.com/messaging2/guide/DcyMjA1Njk?platform=client)。

**兼容版本**

- 兼容 [NIM SDK（Web）10.5.0 版本](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1050-2024-10-15)。
- 兼容 [NERTC SDK（Web）5.6.2008 版本](https://doc.yunxin.163.com/nertc/concept/zU5NzI3NTM?platform=client)。

## <span id="1.30.0 (2024-08-20)">1.30.0 (2024-08-20)</span>

**优化改进**

优化弱网下房间内的表现。

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

**兼容版本**

- 兼容 `NIMSDK` 9.14.4 版本
- 兼容 `NERtcSDK` 5.6.0 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.28.0 (2024-05-10)">1.28.0 (2024-05-10)</span>

**新增特性**

- 新增 SIP 外呼能力。
- 新增 APP 内呼叫能力。
- 新增获取聊天室成员信息功能。

**API 更新**

类/方法/回调/错误码|说明
------|--------
`NERoomContext.sipController`|新增属性，用于发起 SIP 外呼。
`NERoomContext.appInviteController`|新增属性，用于发起 APP 应用内呼叫。
`NERoomContext.maxMembers`|新增属性，表示房间最大人数，-1 表示房间内无人数限制。
`NERoomContext.inSIPInvitingMembers`|新增属性，表示正在 SIP 外呼邀请中的成员列表。
`NERoomContext.inAppInvitingMembers`|新增属性，表示正在 App 内呼叫邀请中的成员列表。
`NERoomListener.onMemberSIPInviteStateChanged`|在房间回调中新增“成员SIP邀请状态变更”事件的回调。
`NERoomListener.onMemberAppInviteStateChanged`|在房间回调中新增“成员APP邀请状态变更”事件的回调。
`NERoomMember.isSIPInviting`|新增属性，表示成员是否正在 SIP 外呼邀请中。
`NERoomMember.isAppInviting`|新增属性，表示成员是否正在 App 内呼叫邀请中。
`NERoomMember.inviteState`|新增属性，表示用于标记成员被邀请中的状态。
`NERoomSIPController.callByNumber`|新增方法，支持根据手机号码进行 SIP 外呼。    
`NERoomSIPController.callByUserUuid`|新增方法，支持根据用户 uuid 进行 SIP 外呼。
`NERoomSIPController.callByUserUuids`|新增方法，支持根据用户 uuid 列表进行批量 SIP 外呼。
`NERoomSIPController.cancelCall`|新增方法，支持取消 SIP 外呼。
`NERoomSIPController.removeCall`|新增方法，支持移除 SIP 外呼。
`NERoomSIPController.hangUpCall`|新增方法，支持挂断 SIP 外呼。
`NERoomAppInviteController.callByUserUuid`|新增方法，支持根据用户 uuid 进行 APP 内呼。
`NERoomAppInviteController.callByUserUuids`|新增方法，支持根据用户 uuid 列表进行批量 APP 内呼。
`NERoomAppInviteController.cancelCall`|新增方法，支持取消 APP 内呼。
`NERoomAppInviteController.removeCall`|新增方法，支持移除 APP 内呼。
`NERoomChatController.fetchChatroomMembers`|新增方法，表示获取聊天室成员信息。

**兼容版本**

- 兼容 `NIMSDK` 9.14.4 版本
- 兼容 `NERtcSDK` 5.5.30 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.27.0 (2024-04-03)">1.27.0 (2024-04-03)</span>

**新增特性**

- 新增消息监听回调功能。
- 新增消息操作相关功能。
  - 新增消息未读数管理功能，包括清理和查询消息未读数。
  - 新增会话历史消息管理功能，包括删除和查询会话历史消息。
- 支持管理全量的等候室成员，包括全部准入和全部移除功能。
- 新增房间黑名单功能。
- 修改准入等候室接口，支持配置是否本次房间自动准入。

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
`NEWaitingRoomController.admitMember`|在该方法中新增`autoAdmit`参数，设置是否本次房间自动准入。

**兼容版本**

- 兼容 `NIMSDK` 9.14.4 版本
- 兼容 `NERtcSDK` 5.5.30 版本
- 兼容 `NEWhiteboard` 3.9.6 版本

## <span id="1.19.0 (2023-08-14)">1.19.0 (2023-08-14)</span>

**兼容版本**

- NERTC：兼容 V5.3.7 版本
- NIM：兼容 V9.10.0 版本
- 白板：兼容 V3.9.6 版本

**改进优化**

- 优化并提升加入房间的速度。
- 优化白板加载 SDK 逻辑，避免重复下载链接。

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|----|---- | -------------- | 
| `NERoomListener`|`onRoomRemainingSecondsRenewed`|当房间剩余时长更新时触发此回调。| 
|`NERoomRtcController`|`enableEncryption`|开启媒体流加密。
|^^|`disableEncryption`|关闭媒体流加密。|

**更新 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERtcServerConfig` |新增 RTC 私有化配置地址：`webSocketProxyServer`、`cloudProxyServer`、`statisticsWebSocketServer`。| 
|`endRoom` |新增 `isForce` 参数，用于设置是否强制退出房间，不等待接口请求的返回。

## <span id="1.17.0 (2023-07-04)">1.17.0 (2023-07-04)</span>

**兼容版本**

- NERTC：兼容 V5.3.7 版本
- NIM：兼容 V9.10.0 版本
- 白板：兼容 V3.7.2 版本

**改进优化**

- 优化大房间场景下，SDK 与服务端的信令交互。
- 修复 electron 未开启过音视频情况下开启共享屏幕第一次会失败问题。

**更新 API**

|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomRole`|删除 `superRole`参数，该参数已废弃。 | 
| ^^ | 新增 `hide` 参数，用于设置角色的成员是否需要在成员列表中展示。 |

## <span id="1.15.0 (2023-05-30)">1.15.0 (2023-05-30)</span>

**问题修复**

修复 `onMemberJoinRtcChannel` 回调中 `isSharingWhiteboard` 状态不同步问题。

## <span id="1.14.0 (2023-04-27)">1.14.0 (2023-04-27)</span>

**新增特性**

- 新增 `NERoomWhiteboardController.setCanvasBackgroundColor`，支持设置白板画布背景颜色。
- 新增 `NERoomWhiteboardController.lockCameraWithContent`，支持将白板和被标注物的坐标绑定。
- 设置白板默认画笔为红色。

**问题修复**

- 修复不允许多端登录互踢未抛出事件问题。
- 修复聊天室私有化图片发送失败问题。

**兼容版本**

- NERTC：兼容 V4.6.50 版本
- NIM：兼容 V9.8.0 版本
- 白板：兼容 V3.8.7 版本

## <span id="1.13.0 (2023-04-11)">1.13.0 (2023-04-11)</span>

**新增特性**

- 新增跨应用互通功能。
- 新增支持弱网断网情况关闭本端音视频。

**问题修复**

修复第三方直播 `isSupported` 字段判断错误问题。

**兼容版本**

- NERTC：兼容 V4.6.50 版本
- NIM：兼容 V9.8.0 版本
- 白板：兼容 V3.8.7 版本

## <span id="1.12.0 (2023-03-03)">1.12.0 (2023-03-03)</span>

**兼容版本**

- NERTC：兼容 V4.6.252 版本
- NIM：兼容 V9.6.3 版本
- 白板：兼容 V3.8.7 版本


**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomRtcController`|`pauseLocalAudioRecording` |暂停本地麦克风采集，调用后远端用户听不到本端声音。 | 
|^^|`resumeLocalAudioRecording` |恢复本地麦克风采集，调用后远端用户可以听到本端声音。 | 
|^^|`pauseLocalVideoCapture` |暂停本地视频采集。 | 
|^^|`resumeLocalVideoCapture` |恢复本地视频采集。 | 
|^^|`adjustPlaybackSignalVolume` | 调节所有远端用户在本地播放的混音音量。 | 


**变更 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
|`NERoomListener`|`onRtcRemoteAudioVolumeIndication`|命名变更：`onRtcAudioVolumeIndication` 变更为 `onRtcRemoteAudioVolumeIndication`。<br>行为变更：该回调不再包含本地用户的音量回调，本地用户音量回调提供了单独的接口。

**问题修复**

修复关闭摄像头重新打开时，帧率被重置的问题。

## <span id="1.11.0 (2023-01-09)">1.11.0 (2023-01-09)</span>

**兼容版本**

- 兼容 `NIMSDK` V9.6.3 版本
- 兼容 `NERtcSDK` V4.6.252 版本
- 兼容 `NEWhiteboard` V3.7.7 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> 
|--------------------------------|-----------------------------------------
| 支持配置私有化服务器地址        |  通过 `NERoomKitOptions.serverUrl` 接口配置私有化地址，可下载对应的私有化配置，并在初始化时使用相应配置。


**问题修复**

- 修复订阅过小流后重新设置订阅大流时无效的问题。
- 修复多端登录互踢时，异常提示 `onMemberLeaveRoom` 事件的问题。
- 修复移交主持人场景中，当服务端下发的命令顺序错乱时，移交失败的问题。

## <span id="1.10.0 (2022-12-08)">1.10.0 (2022-12-08)</span>

**兼容版本**

- 兼容 `NIMSDK` V9.6.3 版本
- 兼容 `NERtcSDK` V4.6.252 版本
- 兼容 `NEWhiteboard` V3.7.7 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> 
|--------------------------------|-----------------------------------------
|支持切换语言类型|通过 `NERoomKit.switchLanguage` 接口可将SDK的语言类型切换为中文、英文或日语

**问题修复**

- 优化 H5 播放授权的逻辑。
- 修复 Electron 框架中，屏幕共享失败的问题。

## <span id="1.9.0 (2022-10-31)">1.9.0 (2022-10-31)</span>

**兼容版本**

- 兼容 `NIMSDK` V8.11.3 版本
- 兼容 `NERtcSDK` V4.6.20 版本
- 兼容 `NEWhiteboard` V3.7.7 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 设置本地采集音量                          |  您可以通过设置采集音量调整通话音量。|  <a href="https://doc.yunxin.163.com/neroom/guide/jM5MjQ5MTA?platform=web" target="_blank">设置通话音量</a>
| 伴音和音效                          |  通过混音功能播放掌声、口哨等短时音效，或者为人声添加背景音乐、伴奏音乐或其他场景效果，并将合成后的声音播放给房间内其他成员。在音视频通话或直播场景中，可以更好的烘托气氛、营造多样化语音环境。|  <a href="https://doc.yunxin.163.com/neroom/guide/TE0OTgyNTk?platform=web" target="_blank">伴音和音效</a>
| 设置音频属性                          |  NERoom SDK 默认使用标准音质模式和语音场景。不同应用场景，对于音质、声道、噪声抑制等方面的要求各有不同，您可以根据 App 的场景，通过 `setAudioProfile` 设置音频属性，实现最优的音质效果。|  <a href="https://doc.yunxin.163.com/neroom/guide/jAyOTM5NDc?platform=web" target="_blank">设置音频属性</a>


**新增 API**

|所属类|接口名称 | 接口说明 | 
|--|---- | -------------- | 
|`NERtcController`|`adjustRecordingSignalVolume`|调节本端采集的音量
|^^|`pauseAllEffects`|暂停播放所有音效文件
|^^|`pauseEffect`|暂停播放指定音效文件
|^^|`resumeEffect`|	恢复播放指定音效文件
|^^|`resumeAllEffects`|	恢复播放所有音效文件
|^^|`getEffectDuration`|	获取音效文件时长
|^^|`setChannelProfile`|	设置房间场景
|^^|`setAudioProfile`|设置音频编码属性
|^^|`enableLocalSubStreamAudio`|	开启音频辅流
|^^|`disableLocalSubStreamAudio`|	关闭音频辅流


**问题修复**

修复无音视频设备时，开启音视频进入频道，共享屏幕无法 pub 的问题。


## <span id="1.8.0 (2022-09-26)">1.8.0 (2022-09-26)</span>

**兼容版本**

- 兼容 `NIMSDK` V8.11.3 版本
- 兼容 `NERtcSDK` V4.6.11 版本

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|--------------------------------|-----------------------------------------|----------------|
| 支持多媒体消息                           |  支持发送与接收图片消息和文件消息|  <a href="https://doc.yunxin.163.com/neroom/guide/DI4MjEwNTg?platform=web" target="_blank">消息发送</a> <br><a href="https://doc.yunxin.163.com/neroom/guide/TQ0ODg5ODA?platform=web" target="_blank">消息接收</a>

**新增 API**

|所属类|接口名称 | 接口说明 | 
|----|---- | -------------- | 
| `NERoomChatController` |`sendImageMessage`	| 发送图片消息 	|
| ^^ | `sendFileMessage` 	| 发送文件消息 	|
| ^^ |`cancelSendFileMessage`	| 取消发送文件消息 	|
|`NERoomListener`  | `onReceiveChatroomMessages`	| 接收到消息的回调 	|
| ^^ | `onChatroomMessageAttachmentProgress`	| 监听图片、文件消息的附件下载进度 	|


## <span id="1.7.0 (2022-08-31)">1.7.0 (2022-08-31)</span>

兼容 H5。

## <span id="1.5.0 (2022-07-28)">1.5.0 (2022-07-28)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|:--------------------------------|:-----------------------------------------|:----------------|
| 新增房间剩余结束时间：`NERoomContext.remainingSeconds`            | 可获取当前房间剩余事件。        |   [房间属性](https://doc.yunxin.163.com/neroom/guide/DA1MDMwMTY?platform=web)     |
| 新增白板上传图片和文件           | 新增白板上传图片和文件。         | [互动白板](https://doc.yunxin.163.com/neroom/guide/TA0MDg1NjA?platform=web)       |

## <span id="1.3.0 (2022-06-30)">1.3.0 (2022-06-30)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|:--------------------------------|:-----------------------------------------|:----------------|
| 复用 IM 的账号             | 如果您的 App 之前已集成了 IM SDK，需要再通过 NERoom 集成其他能力，例如音视频通话、白板等，您可以在 NERoom 中开启 IM 复用功能，帮助您在应用中同时集成并使用 NERoom SDK 和 IM SDK。        | [复用 IM 的账号](https://doc.yunxin.163.com/neroom/guide/Dc1MTM0Njg?platform=web)       |
| 本地视频预览             | 在视频会议或在线教育等场景中，主讲人或老师需要在开播前预览本地视频画面。 包括：启用或关闭视频画面预览功能、切换摄像头、测试麦克风、测试扬声器、获取摄像头列表、获取麦克风设备列表、获取扬声器设备列表、切换麦克风设备、切换扬声器设备、获取当前选择的摄像头设备、获取当前选择的扬声器设备、获取当前选择的麦克风设备。      | [本地视频预览](https://doc.yunxin.163.com/neroom/guide/jM2NzE2NzQ?platform=web)       |
| 重置白板视图           | 删除白板页和涂鸦。         | [互动白板](https://doc.yunxin.163.com/neroom/guide/TA0MDg1NjA?platform=web)       |

**新增 API**

|所属类|接口名称 | 接口说明 | 
|:------|:--------------------------------|:-----------------------------------------|
|`NERoomRtcController`|`unsubscribeRemoteVideoStream`|取消订阅远端用户的视频|
|^^|`unsubscribeRemoteVideoSubStream`|取消订阅远端用户的辅流|
|^^|`setLocalVideoConfig`|动态设置视频分辨率质量|
|^^|`setLocalAudioProfile`|动态设置音频质量|
|^^|`startScreenShare`|动态设置共享流分辨率帧率|
|^^|`enumRecordDevices`|切换麦克风|
|^^|`enumCameraDevices`|切换摄像头|
|^^|`enumPlayoutDevices`|切换扬声器|
|^^|`setSelectedRecordDevice`|切换麦克风|
|^^|`setSelectedCameraDevice`|切换摄像头|
|^^|`setSelectedPlayoutDevice`|切换扬声器|
|^^|`getSelectedRecordDevice`|切换麦克风|
|^^|`getSelectedCameraDevice`|切换摄像头|
|^^|`getSelectedPlayoutDevice`|切换扬声器|
|^^|`setupLocalVideoCanvas`|设置本地视图|
|`previewRoomRtcController`|`startPreview`|开启视频预览|
|^^|`stopPreview`|关闭视频预览。|
|^^|`startRecordDeviceTest`|开始测试麦克风|
|^^|`stopRecordDeviceTest`|停止测试麦克风|
|^^|`startPlayoutDeviceTest`|开始测试扬声器|
|^^|`stopPlayoutDeviceTest`|停止测试扬声器|
|`NEWhiteboardController`|`resetWhiteboardCanvas`|重置白板视图|
|`NERoomService`|`getPreviewRoomContext`|加入房间前预览房间上下文|
|^^|`previewRoom`|开启房间预览|

## <span id="1.1.0 (2022-05-18)">1.1.0 (2022-05-18)</span>

**新增特性**

| <div style="width:80px">新增特性</div> | <div style="width:150px">特性描述</div> | <div style="width:80px">相关文档</div> |
|:--------------------------------|:-----------------------------------------|:----------------|
| 房间属性设置和更新             | 房间属性是附加到当前房间上的一系列 key-value键值对， key为属性唯一名称， value 为当前属性值。 NERoom 允许开发者自定义房间属性，并在房间生命周期内对属性进行添加、更新、删除操作，同时还可以监听属性变更通知。               | [房间属性](https://doc.yunxin.163.com/neroom/guide/DA1MDMwMTY?platform=web)       |
| 成员属性设置和更新             | 成员属性是附加到房间特定成员上的一系列 key-value键值对， key为属性唯一名称， value为当前属性值。 NERoom允许开发者自定义成员属性，并在房间生命周期内对成员属性进行添加、更新、删除操作，同时还可以监听属性变更通知。                   | [成员属性](https://doc.yunxin.163.com/neroom/guide/TUxMDEyNTc?platform=web)       |
| 静音和取消静音房间内其他成员   | 拥有相应权限的角色，可以静音或取消静音房间内某个成员。  | [静音和取消静音](https://doc.yunxin.163.com/neroom/guide/jM5MjQ5MTA?platform=web) |
| 开启和关闭房间内其他成员的视频 | 拥有相应权限的角色，可以开启和关闭房间内某个成员的视频。 | [开启和关闭视频](https://doc.yunxin.163.com/neroom/guide/TYwNzgzMzQ?platform=web) |
| 关闭某成员的屏幕共享           | 拥有相应权限的角色，可以关闭某个成员的屏幕共享。    | [屏幕共享](https://doc.yunxin.163.com/neroom/guide/TA5MzA3OTE?platform=web)       |
| 关闭某成员的白板共享           | 拥有相应权限的角色，可以关闭某个成员的白板共享。         | [互动白板](https://doc.yunxin.163.com/neroom/guide/TA0MDg1NjA?platform=web)       |

**新增 API**

|所属类| 接口名称          | 接口说明                                                                                   |
|:------------------------|:------------------------|:--------------------------------------------------------------------------------------------|
| `NERoomContext`|`getPassword`      | 获取房间密码                                                                               |
|^^|`roomProperties`   | 获取当前房间的所有属性                                                                     |
|^^|`updateRoomProperty` | 更新房间属性，房间属性是房间的一个 key/value 键值对                                        |
|^^|`deleteRoomProperty` | 删除房间属性                                                                               |
|^^|`updateMemberProperty`| 更新成员属性，成员属性为成员的一个 key/value 键值对                                        |
|^^|`deleteMemberProperty`| 删除成员属性                                                                               |
|^^|`handOverMyRole`   | 将自身当前的角色转移给对应的用户，自身会恢复到默认的房间角色。只有授权角色才能执行该操作 |
|^^|`changeMyName`      | 修改自己房间内昵称                                                                         |
|^^|`isLocked`   | 查询房间当前锁定状态                                                                       |
|^^|`lockRoom`     | 锁定房间。锁定后成员无法加入                                                               |
|^^|`unlockRoom`      | 解除锁定房间。解除锁定后成员可以加入该房间                                                 |
| `NERoomRtcController`|`muteMemberAudio`  | 关闭成员音频，会进行权限校验               |
|^^|`unmuteMemberAudio`       | 打开成员音频，会进行权限校验               |
|^^|`muteMemberVideo`  | 关闭成员视频，会进行权限校验               |
|^^|`unmuteMemberVideo`     | 打开成员视频，会进行权限校验               |
|^^|`stopMemberScreenShare`    | 关闭房间内成员的屏幕共享，会进行权限校验 |
| `NEWhiteboardController`|`stopMemberWhiteboardShare`               | 关闭房间内成员的白板共享，会进行权限校验             |
| `NERoomListener`|`onRoomPropertiesChanged`    | 房间属性更新事件回调               |
|^^|`onRoomPropertiesDeleted`   | 房间属性删除事件回调               |
|^^|`onMemberNameChanged`   | 成员昵称变更事件回调               |
|^^|`onMemberPropertiesChanged` | 成员属性更新事件回调               |
|^^|`onMemberPropertiesDeleted` | 成员属性删除事件回调               |
|^^|`onRoomLockStateChanged`     | 房间锁定状态变更事件回调           |
|^^|`onRtcActiveSpeakerChanged`   | 当前 RTC 成员音量最大者事件回调 |
| `NEMessageService`|`sendPassThroughMessage`  | 给房间内的用户发送透传消息，如房间内信令；如果对应用户不在线，信令可能丢失             |

**API 变更**

| 接口名称           | 接口变更说明                                                                         |
|:------------------------|:--------------------------------------------------------------------------------------------|
| `NECreateRoomParams` | 新增 `password` 参数，设置当前房间的密码。 新增 `initialProperties` 参数，设置房间属性。 |
| `NEJoinRoomParams`   | 新增 `password` 参数，输入当前房间的密码。 新增 `initialProperties` 参数，设置成员属性。 |

## <span id="1.0.0 (2022-03-31)">1.0.0 (2022-03-31)</span>

网易云信 NERoom SDK 的首次发布！

主要包括房间管理、成员管理、文字聊天室、音视频通话、麦位管理、互动白板等模块化功能。