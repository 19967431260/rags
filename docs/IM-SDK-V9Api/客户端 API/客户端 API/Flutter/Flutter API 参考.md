网易云信 IM 即时通讯服务基于网易多年的通信服务技术积累，致力于打造最稳定的即时通讯平台。IM Flutter SDK 为 Flutter 应用提供完善的即时通信功能开发框架，屏蔽其内部复杂细节，对外提供较为简洁的 API 接口，方便第三方应用快速集成即时通信功能。NIM Flutter SDK 目前支持 Android 和 iOS。非移动端（包括 Windows、macOS 和 Web）仍为 Beta 版本，处于内测阶段，敬请期待。

::: note note
本文仅列出部分核心类和核心接口。全量的类和接口，请前往 [IM Flutter API 参考](https://pub.dev/documentation/nim_core_platform_interface/latest/nim_core_platform_interface/nim_core_platform_interface-library.html) 进行搜索查阅。
:::

## 核心类

以下为 NIM Flutter SDK 的部分核心类：

- `NimCore` 类主要提供初始化、获取其他子服务的能力。
- `AuthService` 类提供鉴权接口、包括登录和注销。
- `UserService` 类提供用户服务接口。
- `MessageService` 提供消息收发接口。
- `EventSubscribeService` 类提供事件订阅服务接口。
- `SystemMessageService` 类提供系统通知服务接口。
- `TeamService` 类提供群聊服务接口。
- `SuperTeamService` 类提供超大群服务接口。
- `ChatroomService` 类提供聊天室服务接口。
- `NOSService` 类提供 NOS 服务接口。
- `AudioService` 类提供音频服务接口。
- `SettingsService` 类提供设置项相关服务接口。
- `PassThroughService` 类提供透传服务接口。
- `QChatService` 类提供圈组登录登出相关接口（目前仅支持 iOS 和 Android）。
- `QChatServerService` 类提供圈组服务器服务接口（目前仅支持 iOS 和 Android）。
- `QChatChannelService` 类提供圈组频道服务接口（目前仅支持 iOS 和 Android）。
- `QChatMessageService` 类提供圈组消息服务接口（目前仅支持 iOS 和 Android）。
- `QChatRoleService` 类提供圈组身份组服务接口（目前仅支持 iOS 和 Android）。
- `SettingsService` 类提供 SDK 设置类接口，如开启/关闭推送和免打扰等。

在调用 API 过程中，SDK 可能会返回错误码和警告码，请参考 [错误码和警告码](/docs/TM5MzM5Njk/DQzNzc0NzM)。

<style>
table th:first-of-type {
    width: 35%;
}
table th:nth-of-type(2) {
    width: 50%;
}
table th:nth-of-type(3) {
    width: 15%;
}
</style>

## NimCore

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [instance](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/instance.html) | 获取全局 SDK 对象。 | V1.0.0 |
| [initialize](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/initialize.html) | 初始化 SDK | V1.0.0 |
| [authService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/authService.html) | 获取鉴权服务对象 | V1.0.0 |
| [userService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/userService.html) | 获取用户服务对象 | V1.0.0 |
| [messageService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/messageService.html) | 获取消息服务对象 | V1.0.0 |
| [eventSubscribeService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/eventSubscribeService.html) | 获取事件订阅服务对象 | V1.0.0 |
| [chatroomService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/chatroomService.html) | 获取聊天室服务对象 | V1.0.0 |
| [audioService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/audioService.html) | 获取音频服务对象 | V1.0.0 |
| [teamService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/teamService.html) | 获取群聊服务对象 | V1.0.0 |
| [systemMessageService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/systemMessageService.html) | 获取系统消息服务对象 | V1.0.0 |
| [settingsService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/settingsService.html) | 获取设置服务对象 | V1.0.0 |
| [nosService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/nosService.html) | 获取 NOS 服务对象 | V1.0.0 |
| [passThroughService](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/passThroughService.html) | 获取透传服务对象 | V1.0.0 |

## AuthService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [login](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/login.html) | 账号登录 | V1.0.0 |
| [logout](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/logout.html) | 账号注销 | V1.0.0 |
| [kickOutOtherOnlineClient](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/kickOutOtherOnlineClient.html) | 踢掉其他端 | V1.0.0 |
| [authStatus](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/authStatus.html) | 登录状态事件流 | V1.0.0 |
| [onlineClients](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/onlineClients.html) | 多端登录事件流 | V1.0.0 |
| [dynamicTokenProvider](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/dynamicTokenProvider.html) | 设置动态登录 token 提供者 | V1.0.0 |

## UserService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [addFriend](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/UserService/addFriend.html) | 添加好友 | V1.0.0 |
| [deleteFriend](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/UserService/deleteFriend.html) | 删除好友 | V1.0.0 |
| [getFriendList](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/UserService/getFriendList.html) | 获取好友列表 | V1.0.0 |
| [updateMyUserInfo](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/UserService/updateMyUserInfo.html) | 更新个人资料 | V1.0.0 |

## MessageService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [sendMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/sendMessage.html) | 发送消息 | V1.0.0 |
| [searchMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/searchMessage.html) | 查询消息 | V1.0.0 |
| [replyMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/replyMessage.html) | 回复消息 | V1.0.0 |
| [revokeMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/revokeMessage.html) | 撤回消息 | V1.0.0 |
| [pullMessageHistory](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/pullMessageHistory.html) | 拉取消息历史 | V1.0.0 |
| [onMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/onMessage.html) | 接收消息事件流 | V1.0.0 |
| [onMessageStatus](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/onMessageStatus.html) | 消息状态变化事件流 | V1.0.0 |

## TeamService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [createTeam](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/createTeam.html) | 创建群聊 | V1.0.0 |
| [dismissTeam](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/dismissTeam.html) | 解散群聊 | V1.0.0 |
| [queryTeam](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/queryTeam.html) | 查询群资料 | V1.0.0 |
| [applyJoinTeam](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/applyJoinTeam.html) | 申请加入群聊 | V1.0.0 |
| [acceptInvite](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/acceptInvite.html) | 接受入群邀请 | V1.0.0 |
| [quitTeam](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/quitTeam.html) | 退出群聊 | V1.0.0 |
| [passApply](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/passApply.html) | 通过入群申请 | V1.0.0 |
| [removeMembers](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/TeamService/removeMembers.html) | 从群聊移除用户 | V1.0.0 |

## ChatroomService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [enterChatroom](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/enterChatroom.html) | 加入聊天室 | V1.0.0 |
| [exitChatroom](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/exitChatroom.html) | 退出聊天室 | V1.0.0 |
| [fetchChatroomInfo](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/fetchChatroomInfo.html) | 获取聊天室信息 | V1.0.0 |
| [fetchChatroomMembers](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/fetchChatroomMembers.html) | 获取聊天室成员 | V1.0.0 |
| [fetchMessageHistory](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/fetchMessageHistory.html) | 获取聊天室历史消息 | V1.0.0 |
| [sendChatroomMessage](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/sendChatroomMessage.html) | 发送聊天室消息 | V1.0.0 |
| [onMessageReceived](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/ChatroomService/onMessageReceived.html) | 接收聊天室消息事件流 | V1.0.0 |

## EventSubscribeService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [registerEventSubscribe](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/EventSubscribeServicePlatform/registerEventSubscribe.html) | 订阅指定账号的在线状态事件 | V1.0.0 |
| [unregisterEventSubscribe](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/EventSubscribeServicePlatform/unregisterEventSubscribe.html) | 取消订阅指定账号的在线状态事件 | V1.0.0 |
| [publishEvent](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/EventSubscribeServicePlatform/publishEvent.html) | 向订阅者发布事件 | V1.0.0 |
| [eventSubscribeStream](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/EventSubscribeServicePlatform/eventSubscribeStream.html) | 接收到订阅事件流 | V1.0.0 |

## SystemMessageService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [querySystemMessageUnread](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SystemMessageServicePlatform/querySystemMessageUnread.html) | 获取未读系统通知消息 | V1.0.0 |
| [clearSystemMessages](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SystemMessageServicePlatform/clearSystemMessages.html) | 删除所有系统通知 | V1.0.0 |
| [sendCustomNotification](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SystemMessageServicePlatform/sendCustomNotification.html) | 发送自定义系统通知 | V1.0.0 |
| [onCustomNotification](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SystemMessageServicePlatform/onCustomNotification.html) | 接收到系统通知消息 | V1.0.0 |

## NOSService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [upload](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NOSService/upload.html) | 上传附件 | V1.0.0 |
| [onNOSTransferProgress](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NOSService/onNOSTransferProgress.html) | 进度事件流 | V1.0.0 |
| [onNOSTransferStatus](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NOSService/onNOSTransferStatus.html) | 状态事件流 | V1.0.0 |

## AudioService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [startRecord](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AudioService/startRecord.html) | 开始音频录制 | V1.0.0 |
| [stopRecord](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AudioService/stopRecord.html) | 停止音频录制 | V1.0.0 |
| [onAudioRecordStatus](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AudioService/onAudioRecordStatus.html) | 录制状态事件流 | V1.0.0 |

## SettingsService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [enableNotificationAndroid](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/enableNotificationAndroid.html) | 配置消息提醒（Android） | V1.0.0 |
| [enablePushServiceAndroid](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/enablePushServiceAndroid.html) | 开启或关闭消息推送（Android） | V1.0.0 |
| [updateAPNSToken](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/updateAPNSToken.html) | 更新 iOS deviceToken | V1.0.0 |
| [uploadLogs](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/uploadLogs.html) | 日志上传 | V1.0.0 |

更多 `SettingsService` 包含的方法，请参考 <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService-class.html" target="_blank">`SettingsService`</a>。

## PassThroughService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| [httpProxy](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/PassThroughService/httpProxy.html) | 发送 HTTP 代理请求 | V1.0.0 |

## QChatService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatService/kickOtherClients.html" target="_blank">kickOtherClients</a> | 踢掉多端同时圈组在线的其他端 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatService/login.html" target="_blank">login</a> | 登录圈组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatService/logout.html" target="_blank">logout</a> | 登出圈组 | V9.3.0 |

## QChatServerService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/createServer.html" target="_blank">createServer</a> | 创建圈组的服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/deleteServer.html" target="_blank">deleteServer</a> | 删除服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/updateServer.html" target="_blank">updateServer</a> | 修改服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/getServersByPage.html" target="_blank">getServersByPage</a> | 分页查询服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/applyServerJoin.html" target="_blank">applyServerJoin</a> | 申请加入服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/acceptServerApply.html" target="_blank">acceptServerApply</a> | 接受其他用户加入服务器的申请 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/inviteServerMembers.html" target="_blank">inviteServerMembers</a> | 邀请其他用户加入服务器 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/acceptServerInvite.html" target="_blank">acceptServerInvite</a> | 接受其他用户发出的加入服务器邀请 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/generateInviteCode.html" target="_blank">generateInviteCode</a> | 生成邀请码 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService/joinByInviteCode.html" target="_blank">joinByInviteCode</a> | 通过邀请码加入服务器 | V9.3.0 |

更多相关方法，请参考 <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatServerService-class.html" target="_blank">QChatServerService</a>。

## QChatChannelService
| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/createChannel.html" target="_blank">createChannel</a> | 创建频道 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/updateChannel.html" target="_blank">updateChannel</a> | 更细频道 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/deleteChannel.html" target="_blank">deleteChannel</a> | 删除频道 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService/getChannelsByPage.html" target="_blank">getChannelByPage</a> | 分页查询频道列表 | V9.3.0 |

更多相关方法，请参考 <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatChannelService-class.html" target="_blank">QChatChannelService</a>。

## QChatRoleService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/createServerRole.html" target="_blank">createServerRole</a> | 创建服务器身份组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/updateServerRole.html" target="_blank">updateServerRole</a> | 修改服务器身份组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/deleteServerRole.html" target="_blank">deleteServerRole</a> | 删除服务器身份组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/getServerRoles.html" target="_blank">getServerRoles</a> | 查询服务器身份组列表 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/addChannelRole.html" target="_blank">addChannelRole</a> | 创建频道身份组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/updateChannelRole.html" target="_blank">updateChannelRole</a> | 修改频道身份组 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/getChannelRoles.html" target="_blank">getChannelRoles</a> | 查询频道身份组 | V9.3.0 |

更多相关方法，请参考 <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatRoleService/QChatRoleService.html" target="_blank">QChatRoleService</a>。

## QChatMessageService

| 方法/属性 | 功能 | 起始版本 |
| --- | --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/sendMessage.html" target="_blank">sendMessage</a> | 在频道在发送消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/deleteMessage.html" target="_blank">deleteMessage</a> | 删除消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/updateMessage.html" target="_blank">updateMessage</a> | 更新消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/revokeMessage.html" target="_blank">revokeMessage</a> | 撤回消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/getMessageHistory.html" target="_blank">getMessageHistory</a> | 查询历史消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/markMessageRead.html" target="_blank">markMessagRead</a> | 标记圈组的某条消息为已读 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/markSystemNotificationsRead.html" target="_blank">markSystemNotificationsRead</a> | 标记圈组的系统通知为已读 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/resendMessage.html" target="_blank">resendMessage</a> | 重发消息 | V9.3.0 |
| <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService/sendSystemNotification.html" target="_blank">sendSystemNotification</a> | 发送自定义系统通知 | V9.3.0 |

更多相关方法，请参考 <a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/QChatMessageService-class.html" target="_blank">QChatMessageService</a>。
