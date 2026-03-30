本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）稳定版适配 Flutter 开发框架 v1.x.x 及以下版本的更新日志。有关开发版 v10.x.x，请参考《IM 即时通讯 V10》[Flutter 更新日志](https://doc.yunxin.163.com/messaging2/concept/DMwMjA0MDI?platform=client)。

:::note notice
- NIM Flutter SDK 目前支持 Android 和 iOS。非移动端（包括 Windows、macOS 和 Web）仍为 **Beta 版本**，处于内测阶段，敬请期待。
- NIM Flutter SDK 依赖的第三方推送 SDK 版本说明请参考 [第三方推送厂商限制](https://doc.yunxin.163.com/messaging/guide/DUyOTg3NTY?platform=flutter)。
:::

## **近期重要更新**

- 从 v1.7.0 起，支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动。
- 从 v1.7.0 起，支持 Android 荣耀推送功能。
- 从 v1.8.2 起，支持话单消息功能。
- 从 v1.9.0 起，支持 AI 数字人功能，通知支持 AI 数字人流式输功能。

## <span id="[1.9.0 - 2025-04-28]">1.9.0 (2025-04-28)</span>

- 新增 AI 数字人功能。<!--详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。-->
- AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
- 新增查询当前服务器时间接口（`getServerTime`）。

## <span id="[1.8.2 - 2024-12-17]">1.8.2 (2024-12-17)</span>

**新增特性**

-  Android 和 iOS 平台支持话单消息功能。
-  Android 平台支持 AGP8（Android Gradle Plugin）和 Java 17 版本。

**问题修复**

修复 iOS 端中反垃圾相关问题。

**兼容版本**

- Android NIM SDK 升级到 v9.19.4 版本。
- iOS NIM SDK 升级到 v9.19.3 版本。

## <span id="[1.8.0 - 2024-11-01]">1.8.0 (2024-11-01)</span>

修复 iOS 端私有化配置的问题。

## <span id="[1.7.9 - 2024-09-06]">1.7.9 (2024-09-06)</span>

- Android 端新增 `MixPushService`，实现 token 回调。
- iOS 端 `Event` 新增 `nimConifg` 字段。
- 修复 iOS 端自动登录 authType 错误的问题。
- Android&iOS SDK 更新到 V9.18.0 版本。

## <span id="[1.7.8 - 2024-07-22]">1.7.8 (2024-07-22)</span>

- Android NIM SDK 升级到 v9.17.1 版本，以解决消息附件 URL（ThumbURL）的问题。
- iOS NIM SDK 升级到 v9.17.0 版本。

## <span id="[1.7.7 - 2024-04-11]">1.7.7 (2024-04-11)</span>

- iOS 端的初始化方法中增加 `NIMIOSSDKOptions.enableFCS` 参数，支持融合存储。
- 修复 iOS 端视频消息没有 path 的问题。

## <span id="[1.7.6 - 2024-03-08]">1.7.6 (2024-03-08)</span>

- Android NIM SDK 升级到 v9.15.0 版本。
- iOS NIM SDK 升级到 v9.15.1 版本，以解决动态登录 token 的问题。

## <span id="[1.7.5 - 2024-02-21]">1.7.5 (2024-02-21)</span>

**新增特性**

- 新增 pullHistoryById 接口（Android 和 iOS）。
- 新增 makeNotifyContentProvider 回调（Android）。
- 新增 makeTickerProvider 回调（Android）。
- 新增 makeRevokeMsgTipProvider 回调（Android）。

## <span id="[1.7.4 - 2024-01-25]">1.7.4 (2024-01-25)</span>

**新增特性**

- 新增 convertMessageToJson 接口（Android 和 iOS），用于将 IMMessage 对象转换成 JSON 格式的字符串。
- 新增 convertJsonToMessage 接口（Android 和 iOS），用于将 JSON 格式的字符串转换成 IMMessage 对象。
- 新增 getCurrentAccount 接口（Android 和 iOS），获取当前用户的 IM 账号。
- 新增 onMessagesDelete 回调（Android 和 iOS），用于多端同步消息删除回调。
- 在自定义系统通知对象 CustomNotification 中新增 sendToOnlineUserOnly 属性（Android 和 iOS），表示发送自定义消息时只发送给在线用户。
- 新增 allMessagesReadForIOS 回调（iOS），用于 iOS 所有消息都被已读时的回调。

**修复**

- 修复 iOS 端信令 `call` 方法中 `offline` 无效的问题。
- 修复 iOS 端收到 web 发送的消息时 `senderClientType` 错误的问题。

## <span id="[1.7.3 - 2023-11-08]">1.7.3 (2023-11-08)</span>

**修复**

- 修复 iOS 端本地没有用户信息时，调用 `getUserInfo` 方法报错的问题。
- 修复 iOS 端加入群组未触发回调的问题。

**依赖更新**

- 将依赖的 Android NIMSDK 升级至 9.13.1 版本。
- 将依赖的 iOS NIMSDK 升级至 9.13.1 版本。
- 将依赖的 `yunxin_alog` 升级至 2.0.0 版本。

## <span id="[1.7.2 - 2023-10-13]">1.7.2 (2023-10-13)</span>

**修复**

修复 iOS 端 [`checkLocalAntiSpam`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/checkLocalAntiSpam.html) 方法返回 `content` 错误的问题。

**依赖更新**

将依赖的 Android NIMSDK 升级至 9.13.0 版本。

## <span id="[1.7.1 (2023-08-10"> 1.7.1 (2023-08-10))</span>

修复 iOS 端收到自定义消息时 `SessionId` 错误的问题。

## <span id="[1.7.0 (2023-07-21"> 1.7.0 (2023-07-21))</span>

**新增特性**

- 支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动。
- 支持 Android 荣耀推送功能。
- 新增动态查询连续完整的历史消息功能。
- 新增群组成员移除和变更的回调。
- 新增 iOS 角标未读数回调。
- 支持搜索和删除缓存资源功能。
- 优化聊天室登录的内部逻辑，与原生端保持一致。

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`onTeamMemberUpdate`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/onTeamMemberUpdate.html) | 新增群组成员信息更新的回调
| [`onTeamMemberRemove`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/onTeamMemberRemove.html) | 新增移除群组成员的回调
| [`registerBadgeCount`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/registerBadgeCount.html) | 新增 iOS 角标未读数的回调
| [`getMessagesDynamically`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/getMessagesDynamically.html) | 新增动态查询连续完整的历史消息接口
| [`searchResourceFiles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/searchResourceFiles.html) | 新增搜索缓存的文件资源接口
| [`removeResourceFiles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/removeResourceFiles.html) | 新增删除缓存的文件资源接口
| `NIMMessage` | 消息体中新增机器人信息字段（`robotInfo`），用于实现机器人消息功能

**修复**

修复 iOS 平台中事件发布状态变更（`eventSubscribeStream`）异常的问题。

**依赖更新**

`nim_core_platform_interface` 升级至 1.7.0。

## <span id="[1.6.2 (2023-06-15"> 1.6.2 (2023-06-15))</span>

将依赖的 NIMSDK 升级至 9.11.0 版本。

## <span id="[1.6.0 (2023-04-24"> 1.6.0 (2023-04-24))</span>

**新增特性**

- 新增 [游客功能](https://doc.yunxin.163.com/messaging/docs/TUzODY3Mjg?platform=flutter)，以游客身份进入服务器，可查询部分信息和接收消息，也可接收部分系统通知。
- 新增 [消息正在输入](https://doc.yunxin.163.com/messaging/docs/DkxODg5MTc?platform=flutter) 功能，支持显示频道消息正在输入。
- SDK 支持查询指定频道中@当前用户的未读消息，同时也支持批量查询消息是否@当前用户。具体请参考 [查询@我的消息](https://doc.yunxin.163.com/messaging/docs/TM0MzgxNzE?platform=flutter)。
- 新增 **[圈组](https://doc.yunxin.163.com/messaging/docs/Dc3OTcyOTY?platform=flutter) 用户资料复用 IM 用户资料** 的能力。

    - 如果某用户未配置自己的 [服务器](https://doc.yunxin.163.com/messaging/docs/zc0ODQ2NDY?platform=flutter) 成员信息，该用户的初始服务器成员信息将直接复用对应的 IM 用户资料（目前仅支持复用昵称和头像）。

    - 如果某用户在未配置自己的服务器成员信息的情况下修改了自己的 IM 用户资料（昵称或头像），系统通知（通知类型 `my_member_info_update`）将触发，通知该用户需要在哪些服务器重新获取自己的资料。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`getMentionedMeMessages`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getMentionedMeMessages.html) | 查询指定频道中@当前用户的未读消息 |
| [`areMentionedMeMessages`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/areMentionedMeMessages.html) | 批量查询消息是否@当前用户 |
| [`QChatServerService#enterAsVisitor`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/enterAsVisitor.html) | 以游客身份进入服务器 |
| [`QChatServerService#leaveAsVisitor`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/leaveAsVisitor.html) | 以游客身份离开服务器 |
| [`QChatChannelService#subscribeAsVisitor`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/subscribeAsVisitor.html) | 以游客身份订阅频道 |
| [`QChatServerService#subscribeAsVisitor`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/subscribeAsVisitor.html) | 以游客身份订阅服务器 |
| [`onReceiveTypingEvent`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatObserver/onReceiveTypingEvent.html) | 监听正在输入事件 |
| [`sendTypingEvent`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/sendTypingEvent.html) | 发送正在输入事件 |
| [`checkpermissions`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/checkPermissions.html) | 查询自己是否拥有某些权限 |

**API 变更**

| <div style="width:150px">API</div> | API 说明 | 变更说明 |
| --- | --- | ---- |
| [`createChannel`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/createChannel.html) | 创建频道 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |
| [`updateChannel`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/updateChannel.html) | 修改频道信息 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |

**数据结构变更**

- 圈组的系统通知类型 [`QChatSystemNotificationType`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatSystemNotificationType.html)中新增枚举 `my_member_info_update`，表示修改 IM 用户资料触发的圈组服务器成员信息的联动修改。该系统通知的具体触发条件、接收者和接收条件，请参考 [圈组系统通知概述](https://doc.yunxin.163.com/messaging/docs/TkxMzc1NDg?platform=server)中对 `USER_INFO_UPDATE(35) ` 的说明。

- 圈组系统通知的投递对象类型 [`QChatSystemMessageToType`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatSystemMessageToType.html) 新增枚举值 `accids`，表示发送给指定的用户。

- [`QChatUnreadInfo`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatUnreadInfo-class.html) 圈组频道未读数类新增 `ackTimeTag`、`lastMsgTime` 和 `time` 属性。

**依赖更新**

- NIMSDK 升级至 9.10.0 版本。
- `nim_core_platform_interface` 升级至 1.6.0。

## <span id="[1.5.0 (2023-03-31"> 1.5.0 (2023-03-31))</span>

**新增特性**

- Android 和 iOS 支持通过接口设置海外节点，具体请参考 [海外数据中心](https://doc.yunxin.163.com/messaging/concept/zA5OTg4Njc?platform=client#4-配置-link-和-lbs-域名)。
- Android 端支持自定义通知栏显示的标题，用户名和头像。
- Android 和 iOS 端消息返回易盾反垃圾结果。

**依赖更新**

- NIMSDK 升级至 9.8.0 版本。
- `nim_core_platform_interface` 升级至 1.5.0。

**问题修复**

修复 iOS 端圈组重发消息 uuid 变化问题。

## <span id="[1.4.8 (2023-03-20"> 1.4.8 (2023-03-20))</span>

修复 [圈组](https://doc.yunxin.163.com/messaging/docs/zMyNjEyOTk?platform=flutter) 的快捷评论信息异常为空的问题。

## <span id="[1.4.6 (2023-02-10"> 1.4.6 (2023-02-10))</span>

`yunxin_alog` 依赖升级到 v1.0.11。

## <span id="[1.4.5 (2023-02-08"> 1.4.5 (2023-02-08))</span>

**API 变更**

- 清除本地消息记录接口 [`clearChattingHistory`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/clearChattingHistory.html)：新增 `ignore` 参数。
- 语音转文本接口 [`voiceToText`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/voiceToText.html)：新增 `mimeType` 和 `sampleRate` 参数。

**依赖更新**

- iOS：支持 NIM SDK v9.6.3 及以上版本。
- `nim_core_platform_interface` 从 v1.4.2 升级至 v1.4.3。
- `nim_core_windows` 从 v1.0.6 升级至 v1.0.7。
- `nim_core_macos` 从 v1.0.6 升级至 v1.0.7。

**问题修复**

iOS、Android 和 PC 已知问题修复。

## <span id="[1.4.4 (2023-01-06"> 1.4.4 (2023-01-06))</span>

**API 变更**

`NOSService` 类的 [`download`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NOSService/download.html) 方法，`path` 参数从可选变为 **必传**。

**问题修复**

修复 `MessageService`、`TeamService`、`SuperTeamService` 和 `ChatroomService` 中部分接口的已知问题。

## <span id="[1.4.3 (2022-12-26"> 1.4.3 (2022-12-26))</span>

修复 iOS 端的圈组自定义消息的回调类型异常。

## <span id="[1.4.2 (2022-12-16"> 1.4.2 (2022-12-16))</span>

修复 iOS 端的如下已知问题：
- 修复 **标记指定类型通知为已读** 接口 `resetSystemMessageUnreadCountByType` 的调用异常问题。
- 修复调用 **创建聊天室自定义消息** 接口 `createChatRoomCustomMessage` 时，传入 `attachment` 不生效的问题。
- 修复 **删除指定类型的系统通知** 接口 `clearSystemMessagesByType` 的调用异常问题。

## <span id="[1.4.1 (2022-12-13"> 1.4.1 (2022-12-13))</span>

**依赖更新**

- dart 版本要求更新至 v2.17.0 及以上。
- ffi 升级至 v2.0.0。
- `nim_core_platform_interface` 从 v1.4.0 升级至 v1.4.1。
- `nim_core_web` 从 v1.0.1 升级至 v1.0.2。

**问题修复**

- 修复 iOS 端的如下已知问题：

    - 修复系统通知未读数查询接口 [`querySystemMessageUnreadCountByType`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SystemMessageServicePlatform/querySystemMessageUnreadCountByType.html) 的调用异常问题。
    - 修复调用自定义消息创建接口 [`createCustomMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createCustomMessage.html) 时，传 `content` 参数未生效的问题。
    - 修复调用群组创建接口 [`createTeam`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/createTeam.html) 时，传入扩展字段 `extension` 未生效的问题。
- 修复其他已知问题。

## <span id="[1.4.0 (2022-11-24"> 1.4.0 (2022-11-24))</span>

::: note notice
当前版本的圈组模块，Android 和 iOS 存在少量的错误码、接口返回值和接口使用逻辑 **不一致** 的情况，具体请参考 [已知问题](https://doc.yunxin.163.com/messaging/docs/jU3OTgwNzY?platform=flutter)。
:::

**新增特性**

- 圈组模块新增特性

    <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
    --- | --- | --- | ---
    1 | 成员封禁管理 | 封禁、解封服务器成员，查询被封禁的成员。 | [成员封禁管理](https://doc.yunxin.163.com/messaging/docs/jc4ODY5MDA?platform=flutter#成员封禁管理)
    2 | 服务器未读数管理 | 获取服务器所有频道的消息未读总数，并可按需清零 | [服务器未读数管理](https://doc.yunxin.163.com/messaging/docs/Dg3NjY3NDM?platform=flutter)
    3 | 频道黑白名单 | 通过频道黑白名单管控频道对服务器成员是否可见 | [频道黑白名单](https://doc.yunxin.163.com/messaging/docs/zQ3MTY4OTg?platform=flutter)
    4 | 用户定制权限 | 为频道成员专门定制权限，管控其在频道维度的操作 | [用户定制权限](https://doc.yunxin.163.com/messaging/docs/TIxNjQyMjc?platform=flutter)
    5 | 查询自己拥有的权限 | 查询自己是否拥有某个权限 | [查询自己的权限](https://doc.yunxin.163.com/messaging/docs/jk0MzU5MjY?platform=flutter#查询自己的权限)
    6 | 会话消息回复（Thread） | 引用接收到的某一条消息进行针对性的回复 | [会话消息回复（Thread）](https://doc.yunxin.163.com/messaging/docs/TMyMDYyOTE?platform=flutter)
    7 | 快捷评论 | 对某条消息进行快捷评论，例如添加表情评论 | [圈组快捷评论](https://doc.yunxin.163.com/messaging/docs/zE1OTY3MDU?platform=flutter)
    8 | 圈组消息缓存 | 获取和清空消息缓存 | [圈组消息缓存](https://doc.yunxin.163.com/messaging/docs/jYzODcyMDk?platform=flutter)
    9 | 搜索消息 | 按照关键字和消息发送者等搜索当前用户所在服务器下的全部频道或单频道的消息 | [圈组消息搜索](https://doc.yunxin.163.com/messaging/docs/TQ0Mzg1MDM?platform=flutter)
    10 | 获取频道最后一条消息 | 获取多个频道的最后一条消息 | [获取频道最后一条消息](https://doc.yunxin.163.com/messaging/docs/jY5NzU1NzY?platform=flutter)
    11 | 圈组离线推送 | <ul><li>多维度（设备、圈组服务器和频道）配置需要离线推送的消息类型（按消息优先级区分）</li><li>推送免打扰、是否展示推送文案详情等其他配置</li></ul> | [圈组离线推送](https://doc.yunxin.163.com/messaging/docs/jQwMDExODc?platform=flutter)

- IM 消息新增特性

    <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
    --- | --- | --- | ---
    1 | 插入本地消息 | 新增 `saveMessageToLocalEx` 方法，用于插入本地消息，且可设置消息的时间戳<note type=notice>仅 Android 和 iOS 支持</note> | [插入本地消息](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/saveMessageToLocalEx.html)

**新增 API**

- QChatChannelService 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`updateChannelBlackWhiteRoles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/updateChannelBlackWhiteRoles.html) | 更新频道黑白名单身份组 |
     [`getChannelBlackWhiteRolesByPage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getChannelBlackWhiteRolesByPage.html) | 分页查询频道黑白名单身份组列表 |
     [`getExistingChannelBlackWhiteRoles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getExistingChannelBlackWhiteRoles.html) | 批量查询频道黑白名单身份组列表 |
     [`updateChannelBlackWhiteMembers`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/updateChannelBlackWhiteMembers.html) | 更新频道黑白名单成员 |
     [`getChannelBlackWhiteMembersByPage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getChannelBlackWhiteMembersByPage.html) | 分页查询频道黑白名单成员列表 |
     [`getExistingChannelBlackWhiteMembers`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getExistingChannelBlackWhiteMembers.html) | 批量查询频道黑白名单成员列表 |
     [`updateUserChannelPushConfig`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/updateUserChannelPushConfig.html) | 更新某个频道的推送配置 |
     [`getUserChannelPushConfigs`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getUserChannelPushConfigs.html) | 获取多个频道的推送配置列表 |

- QChatMessageService 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`replyMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/replyMessage.html) | 引用一条消息进行回复 |
     [`getReferMessages`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getReferMessages.html) | 查询 Thread 中某条消息的父消息和根消息 |
     [`getThreadMessages`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getThreadMessages.html) | 根据某个 Thread 中的任意一条消息分页查询该 Thread 的消息列表 |
     [`getMessageThreadInfos`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getMessageThreadInfos.html) | 批量查询某个频道下的多个 Thread 的根消息的 meta 信息 |
     [`addQuickComment`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/addQuickComment.html) | 对某条消息添加快捷评论 |
     [`removeQuickComment`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/removeQuickComment.html) | 移除快捷评论 |
     [`getQuickComments`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getQuickComments.html) | 查询快捷评论列表 |
     [`getMessageCache`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getMessageCache.html) | 获取消息缓存（异步） |
     [`clearMessageCache`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/clearMessageCache.html) | 清除消息缓存 |
     [`getLastMessageOfChannels`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getLastMessageOfChannels.html) | 获取最多 20 个频道的最后一条消息 |
     [`searchMsgByPage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/searchMsgByPage.html) | 根据关键字和消息发送者搜索消息 |

- QChatRoleService 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`addMemberRole`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/addMemberRole.html) | 创建用户定制权限（注：用户定制权限中包含多个权限项） |
     [`removeMemberRole`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/removeMemberRole.html) | 移除用户定制权限 |
     [`updateMemberRole`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/updateMemberRole.html) | 修改用户定制权限 |
     [`getMemberRoles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/getMemberRoles.html) | 分页查询用户定制权限列表 |
     [`getExistingAccidsOfMemberRoles`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/getExistingAccidsOfMemberRoles.html) | 批量查询用户是否拥有定制权限 |
     [`checkPermission`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/checkPermission.html) | 查询自己是否拥有某个权限项 |

- QChatServerService 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`updateServerMemberInfo`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/updateServerMemberInfo.html) | 修改其他服务器成员的成员信息 |
     [`banServerMember`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/banServerMember.html) | 封禁服务器成员 |
     [`unbanServerMember`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/unbanServerMember.html) | 解封服务器成员 |
     [`getBannedServerMembersByPage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/getBannedServerMembersByPage.html) | 分页查询被封禁的服务器成员列表 |
     [`updateUserServerPushConfig`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/updateUserServerPushConfig.html) | 更新服务器的推送配置 |
     [`getUserServerPushConfigs`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/getUserServerPushConfigs.html) | 获取多个服务器的推送配置列表 |
     [`getServerMembersByPage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/getServerMembersByPage.html) | 分页查询服务器成员列表 |
     [`markRead`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/markRead.html) | 清空服务器所有频道的消息未读数 |
     [`subscribeAllChannel`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/subscribeAllChannel.html) | 一次性订阅服务器下最多 200 个频道 |

- QChatObserver 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`serverUnreadInfoChanged`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatObserver/serverUnreadInfoChanged.html) | 注册或注销 **服务器未读通知接收** 事件流 |

- MessageService 新增 API

     <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
     --- | --- |
     [`saveMessageToLocalEx`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/saveMessageToLocalEx.html) | 保存消息到本地，可设置时间戳<note type="notice">仅 Android 和 iOS 支持</note> |

## <span id="[1.3.3 (2022-11-22"> 1.3.3 (2022-11-22))</span>

修复已知问题：

- iOS：修复第一次查询消息列表时异常报错的问题。
- Web：发送多媒体消息（包括图片、音频、视频和文件）接口增加 `base64` 字段，解决消息发送异常的问题。

## <span id="[1.3.2 (2022-11-17"> 1.3.2 (2022-11-17))</span>

修复 iOS 圈组的查询历史消息接口（`getMessageHistory`）异常。

## <span id="[1.3.1 (2022-11-14"> 1.3.1 (2022-11-14))</span>

修复 iOS 已知问题，包括：

- 修复构建聊天室消息异常报错的问题。
- 修复发送消息时附件异常报错的问题。
- 修复保存本地消息时，`fromAccount` 参数异常报错的问题。

## <span id="[1.3.0 (2022-11-03"> 1.3.0 (2022-11-03))</span>

**新增模块**

网易云信即时通讯服务全新能力 **圈组** 发布（当前版本仅支持 Android 和 iOS）。相关功能介绍和集成指南请分别参考 <a href="https://doc.yunxin.163.com/messaging/docs/zMyNjEyOTk?platform=flutter" target="_blank">圈组功能</a> 和 <a href="https://doc.yunxin.163.com/messaging/docs/zc1MjQ4Mjk?platform=flutter" target="_blank">实现圈组消息收发</a>。

::: note notice
当前版本，可能出现 Android 和 iOS 对于圈组内相同问题或异常操作的报错不一致的情况，具体请参考 <a href="https://doc.yunxin.163.com/messaging/docs/jU3OTgwNzY?platform=flutter" target="_blank">已知问题</a>。强烈建议不要针对错误码进行应用上层的逻辑开发。
:::

**依赖更新**

- 兼容的 NIM iOS SDK 版本更新至 V9.6.3
- 兼容的 NIM Android SDK 版本更新至 V9.6.3
- `nim_core_platform_interface` 从 V1.0.3 升级至 V1.3.0
- `nim_core_windows` 从 V1.0.3 升级至 V1.0.4
- `nim_core_macos` 从 V1.0.3 升级至 V1.0.4

**问题修复**

- 修复 MacOS 和 Windows 偶现的群会话 ID （`sessionId`）异常报错的问题。
- 修复 macOS 和 Windows 偶现的调用群组禁言接口（`muteTeam`）异常报错的问题。

**Android 第三方推送兼容版本**

第三方推送 | 版本
---- | ----
华为 | 6.5.0.300
小米 | 5.1.0
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

## <span id="[1.2.0 (2022-10-13"> 1.2.1 (2022-10-13))</span>

**依赖更新**

更新了 iOS 的 NIM SDK，将其版本从 v9.6.0 升级至 v9.6.1。

## <span id="[1.2.0 (2022-09-30"> 1.2.0 (2022-09-30))</span>

::: note notice
v1.2.1 版本 Flutter SDK 更新了 v1.2.0 版本中可能导致线上崩溃的 iOS 的 NIM SDK 版本。如果您目前使用的是 v1.2.0 版本的 Flutter SDK，强烈建议您升级至 v 1.2.1。
:::

**新增特性**

增加信令功能（Android、iOS）。

**API 新增**

新增的信令相关 API 都挂载在 `AvSignallingService` 模块。

API | 说明
---- | ----
`createChannel` | 创建信令频道
`closeChannel` | 关闭信令频道
`joinChannel` | 加入信令频道
`leaveChannel` | 离开信令频道
`invite` | 邀请他人加入频道
`cancelInvite` | 取消邀请
`rejectInvite` | 拒绝邀请
`acceptInvite` | 接收邀请
`sendControl` | 发送自定义命令
`call` | 直接呼叫，用于用户新开一个频道并邀请对方加入频道
`queryChannelInfo` | 根据频道名称查询频道信息
`onlineNotification` | 在线通知事件回调
`offlineNotification` | 离线通知事件回调
`onMemberUpdateNotification` | 频道成员更新事件回调
`otherClientInviteAckNotification` | 多端同步，其他端响应（接收/拒绝）邀请事件回调，当其他端响应了邀请时触发
`syncChannelListNotification` | 同步未退出频道列表事件回调，在用户登录后 sdk 会去服务器获取当前还未退出的频道列表

**修复**

修复 iOS 初始化问题。

**依赖更新**
- `nim_core_web` 版本从 v1.0.0 升级至 v1.0.1。
- `nim_core_platform_interface` 版本从 v1.0.2 升级至 v1.0.3。
- iOS NIM SDK 从 v8.11.0 升级至 v9.6.0。

## <span id="[1.1.0 - 2022-9-23">1.1.0 (2022-9-23)</span>

1.1.0 版本开始兼容 Web，Web 端集成说明请参考 <a href="https://doc.yunxin.163.com/messaging/docs/DQwNDE4MDM?platform=flutter#%E6%AD%A5%E9%AA%A42%E9%9B%86%E6%88%90-sdk" target="_blank">集成 SDK</a>。

- 部分接口和事件 **暂未支持**，包括：

    - `AudioService` 类的所有接口和事件。
    - `EventSubscribeService` 类的 `observeEventChanged` 事件。
    - `SettingsService` 类中除 `enableMobilePushWhenPCOnline` 和 `isMobilePushEnabledWhenPCOnline` 以外的所有方法。
    - `MessageService` 类中的 `cancelUploadAttachment`、`queryReplyCountInThreadTalkBlock`、`queryTotalUnreadCount` 和 `checkLocalAntiSpam`。
    - `MessageService` 类中的 `onAttachmentProgress` 事件。

- 接口变更：

    - `sendMessage` 接口的 `NIMFileAttachment` 中新增通用的可选参数 `base64`，目前用于 Web 传递文件信息（Web 端发送文件必传）。
    - `searchCloudMessageHistory` 接口新增 `otherAccid`（Web 端必传），表示聊天对象的 IM 账号（`accid`）。
    - `ackAddFriend` 接口新增参数 `idServer`（Web 端必传），表示接收到的好友申请系统通知的 ID。

## <span id="[1.0.11 - 2022-9-15">1.0.11 (2022-9-15)</span>

iOS：

- 修复消息状态问题。
- 兼容的 iOS SDK 更新到 v8.11.0。

## <span id="[1.0.10 - 2022-9-8">1.0.10 (2022-9-8)</span>

**功能新增**

支持 iOS 模拟器。

**API 变更**

- 新增：
    - `MessageService` 中新增 `queryRoamMsgHasMoreTime` 方法，用于获取是否有更多漫游消息标记的时间戳。
    - `MessageService` 中新增 `updateRoamMsgHasMoreTag` 方法，用于更新是否有更多漫游消息的标记。
    - `TeamService` 中新增 `rejectApply` 方法，用于拒绝入群申请。

- 变更
    - `UserService.onMuteListChanged` 返回类型变更为 `NIMMuteListChangedNotify`。
    - `MessageService.onSessionDelete` 返回类型变更为可空。

**依赖更新**

- `nim_core_platform_interface` 从 v1.0.0 更新至 v1.0.1。
- Android NIM SDK 从 v8.11.12 更新至 v8.11.13。

**问题修复**

修复已知问题。

## <span id="[1.0.9 - 2022-9-2">1.0.9 (2022-9-2)</span>

**问题修复**

- iOS：修复无法获取经纬度的问题。

**依赖更新**

- `nim_core_macos` 版本从 v1.0.0 升级至 v1.0.2。
- `nim_core_windows` 版本从 v1.0.0 升级至 v1.0.2。

## <span id="[1.0.8 - 2022-8-29">1.0.8 (2022-8-29)</span>

iOS：修复 `removeManagers` 方法的参数异常问题。

## <span id="[1.0.7 - 2022-8-23">1.0.7 (2022-8-23)</span>

iOS：
- 修复获取置顶信息列表数据为空的问题。
- 修复 `fetchUserInfoList` 方法强制解包导致的崩溃问题。
- 修复 `LastMessage` 文本展示为空问题。

## <span id="[1.0.5 - 2022-8-18">1.0.6 (2022-8-18)</span>

Android：
- `TeamService` 中新增 `updateMyMemberExtension` 方法。
- 修复超大群的 `sendMessage` 方法调用异常。

## <span id="[1.0.5 - 2022-8-17">1.0.5 (2022-8-17)</span>

iOS：修复 `getUserinfo` 的 `ext` 字段信息丢失的问题。

## <span id="[1.0.4 - 2022-8-9">1.0.4 (2022-8-9)</span>

Android：修复初始化状态异常。

## <span id="[1.0.3 - 2022-7-26">1.0.3 (2022-7-26)</span>

Android：修复多通道（Flutter Method Channel）异常。

## <span id="[1.0.2 - 2022-7-22">1.0.2 (2022-7-22)</span>

iOS：修复消息附件丢失的问题。

## <span id="[1.0.1 - 2022-7-20">1.0.1 (2022-7-20)</span>

补充必要日志。

## <span id="[1.0.0 - 2022-7-13">1.0.0 (2022-7-13)</span>

Flutter SDK 正式发布，首个版本号为 1.0.0，支持 Android、iOS、Windows、Mac。

**新增**

- 新增 `MessageService.clearAllSessionUnreadCount` 接口，用于清除所有会话的未读计数。
- 新增超大群接口。
- 在 `TeamService` 中新增 ` declineInvite`。（Android、Macos、Windows）
- 新增自动登录失败 417 错误码回调。（iOS）

**修复**

- 修复转换 `DirCacheFileType` 时丢失 THUMB 问题。（Android）
- 修复 `fromNickname` 为空问题。（iOS）
- 修复音频消息持续问题。（iOS）
- 修复 `searchAllMessage` 接口问题。（Android）
- 适配 Flutter 3.0。
- 修复 `TeamService.muteTeam` 接口调用失败问题。
- 修复 `AudioService` 接口问题。
- 修复 `TeamService#updateTeamFields` 方法调用错误问题。
- 修复 iOS 图片消息 `size` 字段解析错误问题。
- 修复编译错误问题。

## <span id="[1.0.0-rc.15 - 2021-11-09">1.0.0-rc.15 (2021-11-09)</span>

SDK Beta 版本发布，版本号为 1.0.0-rc.15，支持 Android、iOS、Windows、Mac。