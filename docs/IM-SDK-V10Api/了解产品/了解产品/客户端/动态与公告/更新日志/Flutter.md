本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）开发版适配 Flutter 开发框架 10.x.x 及以上版本的更新日志。

::: note note
- 有关稳定版 9.x.x 及以下版本，请参考《IM 即时通讯 V9》[Flutter 更新日志](https://doc.yunxin.163.com/messaging/concept/DM3MjM5NjA?platform=client)。
- 有关 UI 组件 10.x.x 及以上版本的更新日志，请参考 [Flutter UIKit 更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/jY4MjM0NDc?platform=client)。
:::

<style>
table th:first-of-type {width: 35%;}
</style>

## <span id="10.9.5+1 - 2026-02-09">10.9.5+1 (2026-02-09)</span>

**新增特性**

- Android 和 iOS 平台支持普通消息流式输出（`V2NIMMessage.streamConfig`）。
- Android 平台支持手动提供推送 Token 回调（`registerManuallyProvidePushTokenCallback`），允许 Flutter 层自定义推送 Token 获取逻辑。
- Android 平台新增 `onMixPushToken` 事件回调，用于监听推送 Token 变化。
- Android 平台支持控制台日志输出（`NIMAndroidSDKOptions.consoleLogEnabled`）。

**修复**

修复 iOS 平台重发消息失败的问题。

**兼容版本**

- 底层 Android NIM SDK 升级至 v10.9.75。
- 底层 iOS NIM SDK 升级至 v10.9.75。

## <span id="10.9.5 - 2026-01-14">10.9.5 (2026-01-14)</span>

**新增特性**

- macOS 和 Windows 平台新增群定向消息功能。
- macOS 和 Windows 平台支持查询消息返回更新信息。

**修复**

- macOS 和 Windows 平台修复消息过滤问题。
- macOS 和 Windows 平台修复 `TeamService` 中 `antispamConfig` 的兼容性问题。
- macOS 和 Windows 平台修复消息序列化和反序列化问题。
- macOS 兼容 M 系列芯片，编译 universal 版本。

**兼容版本**

- 底层 Android NIM SDK 升级至 v10.9.70。
- 底层 iOS NIM SDK 升级至 v10.9.70。
- 底层 macOS/Windows NIM SDK 升级至 v10.9.70。

## <span id="10.9.4 - 2025-11-06">10.9.4 (2025-11-06)</span>

**新增特性**

Android 和 iOS 平台支持圈组功能，包括圈组服务、圈组频道、圈组聊天等。

## <span id="10.9.3 - 2025-09-09">10.9.3 (2025-09-09)</span>

**新增特性**

- 支持删除历史漫游消息功能。
- 新增当前聊天账号设置功能。
- Android 平台支持设置消息提醒的类型。
- Android 平台支持设置通知的自定义通道。

**API 更新**

方法/回调/类 | 说明 | 兼容平台
--- | --- | ---
`clearRoamingMessage` | 新增接口，用于删除历史漫游消息。  | Android、iOS、macOS、Windows
`setCurrentConversation` | 新增接口，用于设置当前的聊天账号。|  Android、iOS、macOS、Window
`V2NIMLoginOption` | 在登录参数中新增 `offlineMode` 字段，表示是否启用离线模式，默认不开启。 | Android、iOS
`notificationChannelProvider` | 新增接口，用于设置通知的自定义通道。 | Android
`makeCategory` | 新增接口，用于设置消息提醒的类型。 | Android

**兼容版本**

- 底层 Android NIM SDK 升级至 v10.9.45。
- 底层 iOS NIM SDK 升级至 v10.9.40。
- 底层 macOS/Windows NIM SDK 升级至 v10.9.40。

## <span id="10.9.2 - 2025-08-25">10.9.2 (2025-08-25)</span>

**版本说明：**

该版本适配鸿蒙操作系统（HarmonyOS），为 Beta 版本。

**环境要求：**

使用该版本需要满足以下条件：

- 已配置 Flutter 鸿蒙开发环境（ 参考 [鸿蒙官方文档](https://gitcode.com/openharmony-tpc/flutter_flutter/tree/master)）。
- Flutter 版本：**3.27.5-ohos-0.0.2**。

**引入方式：**

该版本接入方式采用 **git 依赖**，暂未上传至 pub。

在项目的 `pubspec.yaml` 中添加以下 git 依赖，然后执行 `flutter pub get`。

```yaml
dependencies:
nim_core_v2:
    git:
    url: "https://github.com/netease-kit/NIM-Flutter-SDK-OHOS.git"
```

## <span id="10.9.1 - 2025-07-23">10.9.1 (2025-07-23)</span>

macOS 和 Windows 平台功能对齐移动端。

## <span id="10.9.0 - 2025-06-25">10.9.0 (2025-06-25)</span>

**新增特性**

- 新增群成员特别关注功能。
- 新增本地登录信息的查询功能。
- 新增删除或清空好友申请/入群申请功能。
- 新增本地消息全文搜索功能。
- 新增置顶会话查询能力。
- 支持查询指定用户是否在黑名单中。
- 支持消息过滤功能。
- 支持在初始化时配置 NIM SDK 的通知栏回调（Android）。
    - 支持配置是否启用 NIM SDK 的用户信息。
    - 支持配置是否开启定制通知栏消息提醒的文案。
- 支持设置自定义推送 Token（Android）。
- 优化全文检索云端历史消息。您可以按照指定条件，全局检索整个应用内的云端历史消息。

**API 更新**

方法/回调/类 | 说明
---- | ----
`addTeamMembersFollow` | 新增方法，用于添加特别关注群成员列表。
`removeTeamMembersFollow` | 新增方法，用于移除特别关注群成员列表。
`getCurrentLoginClient` | 新增方法，用于查询本地登录的相关信息。
`clearAllAddApplication` | 新增方法，用于清空所有好友申请。
`deleteAddApplication` |　新增方法，用于删除指定的好友申请。
`clearAllTeamJoinActionInfo` | 新增方法，用于清空所有入群申请。
`deleteTeamJoinActionInfo` | 新增方法，用于清空所有入群申请。
`clearHistoryMessage` | 新增 `clearMode` 入参，可自由选择清空 **本地和云端** 或 **仅本地** 的历史消息。
`getOwnerTeamList` | 新增方法，用于获取当前自己的群组列表。
`searchCloudMessagesEx` | 新增方法，用于全文检索云端历史消息。
`getMessageListEx` | 新增方法，用于查询历史消息列表。分页接口，可以根据参数组合查询各种类型，每次默认 50 条消息。
`checkBlock` |　新增方法，用于查看指定用户是否在黑名单中。
`getStickTopConversationList` | 新增方法，用于查询当前置顶的全量会话列表。
`searchLocalMessages` | 新增方法，用于全文检索本地历史消息。
`updateLocalMessage` | 新增方法，用于更新本地插入的消息。
`getPushMobileOnDesktopOnline` | 新增方法，用于查询桌面端在线时，移动端是否需要推送。
`getCollectionListExByOption` | 新增方法，用于按条件分页获取收藏信息，较 `getCollectionListByOption` 方法，回参新增 `totalCount` 字段，表示收藏总数。
`inviteMemberEx` |　新增方法，用于邀请成员加入群组。

**兼容版本**

- 底层 Android NIM SDK 升级至 v10.9.10。
- 底层 iOS NIM SDK 升级至 v10.9.10。

## <span id="10.8.0 - 2025-05-26">10.8.0 (2025-05-26)</span>

**特性变更**

支持 IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。<!--具体请参考 [与 AI 数字人聊天（SDK）](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。 -->

**API 更新**

方法/回调/类 | 说明
---- | ----
`clearUnreadCountByGroupId` | 新增方法，用于根据会话分组 ID 清除分组内所有会话的消息总未读数。
`stopAIStreamMessage` | 新增方法，用于停止 AI 数字人流式输出消息，可以选择直接停止输出，或撤回/更新已输出的 AI 数字人消息。
`regenAIMessage` | 新增方法，用于重新输出 AI 数字人消息，可以选择直接更新覆盖已输出的消息，或者直接创建一条新的 AI 数字人消息。
`stopAIModelStreamCall` | 新增方法，用于向服务器请求停止流式输出 AI 数字人消息。
`onProxyAIModelStreamCall` | 新增 AI 数字人流式输出回调。
`sendMessage` | 接口更新，发送消息的 AI 数字人配置参数中新增输出模式字段（`aiStream`）字段，选择是否使用流式输出 AI 数字人消息。
`proxyAIModelCall` | 接口更新，向 LLM 发起模型调用请求方法的 AI 数字人配置参数中新增输出模式字段（`aiStream`），选择是否流式输出 AI 数字人消息。


## <span id="10.6.1 - 2025-05-08">10.6.1 (2025-05-08)</span>

**新增特性**

支持聊天室队列功能。具体请参考 [聊天室队列管理](https://doc.yunxin.163.com/messaging2/guide/Tk1MjYyNDc?platform=client)。

**API 变更**

方法/回调/类 | 说明
--- | ---
`V2NIMChatroomQueueService` | 新增聊天室队列服务类，提供注册/注销聊天室队列监听器、初始化队列、清空队列、管理队列元素等接口。

## <span id="10.6.0 - 2025-04-18">10.6.0 (2025-04-18)</span>

**新增特性**

- 新增云端会话分组功能，支持按照自定义维度将会话进行分组，方便用户管理和查询会话。具体请参考 [会话分组管理](https://doc.yunxin.163.com/messaging2/docs/DYzMjEwOTg?platform=client)。
- 新增本地会话功能。详情请参考 [本地会话管理](https://doc.yunxin.163.com/messaging2/guide/zMyODU1OTM?platform=client)。
- 新增群定向消息功能。发送群消息时，可以指定接收消息的群成员列表。

**修复**

- 修复 Android 端更新本地消息本地扩展问题 `updateMessageLocalExtension`。
- 修复 iOS 端角标配置问题。
- 修复 iOS 端登录回调 `loginExtension` 问题。

**API 变更**

方法/回调/类 | 说明
--- | ---
[`V2NIMLocalConversationService`](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#%E6%8E%A5%E5%8F%A3%E7%B1%BB) | 新增本地会话服务类，提供创建、删除、更新、获取、置顶本地会话，本地会话消息未读数相关、注册本地会话监听等接口。
`V2NIMConversationGroupService` | 新增云端会话分组服务类，提供创建、删除、更新、获取云端会话分组，注册云端会话分组监听等接口。
`NIMSendMessageParams` | 新增 `targetConfig` 参数，用于实现群定向消息功能。

## <span id="10.5.1 - 2025-04-14">10.5.1 (2025-04-14)</span>

在 Android 项目中，NIM Flutter SDK 编译时使用 JDK 8 (JDK 1.8)，提高 JDK 8 环境的兼容性。

## <span id="10.5.0 - 2025-03-25">10.5.0 (2025-03-25)</span>

**新增特性**

- 新增聊天室服务功能。详情请参考 [聊天室](https://doc.yunxin.163.com/messaging2/guide/DI2NDc1NzQ?platform=client) 相关集成参考。
- 新增消息更新功能。
- 新增消息序列化和反序列化功能。
- 新增清空所有好友申请功能。
- 新增 Android 端的通知配置。

**API 更新**

相关 API 请参考 [聊天室](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client) 相关 API。

方法/回调/类 | 说明
--- | ---
`V2NIMChatroomClient` | 聊天室接口类，包括注册/注销聊天室实例监听，创建、进入、退出、销毁聊天室等接口。
`V2NIMChatroomMessageCreator` | 聊天室消息构建接口类，支持构建多种类型的聊天室消息。
`V2NIMChatroomService` | 聊天室服务接口类，包括注册/注销聊天室监听器、收发聊天室消息、管理聊天室成员、维护聊天室信息等接口。
`modifyMessage` | 更新消息，实现消息的二次编辑能力。
`messageSerialization` | 消息序列化为字符串。
`messageDeserialization` | 消息字符串转换为消息。
`clearAllAddApplication` | 清空所有好友申请。
`updateNotificationConfigAndroid` | 更新通知栏设置，仅支持 Android 平台。
`enableNotificationAndroid` | 配置消息提醒，仅支持 Android 平台，iOS平台请关闭通知权限。

**兼容版本**

- 底层 Android NIM SDK 升级至 v10.8.21。
- 底层 iOS NIM SDK 升级至 v10.8.20。

## <span id="10.4.0 - 2025-01-20">10.4.0 (2025-01-20)</span>

**新增特性**

- 新增 [新版信令](https://doc.yunxin.163.com/signaling/guide?platform=client) 功能。
- Android 平台支持 AGP8（Android Gradle Plugin）。

**兼容版本**

底层 NIM SDK 升级至 v10.7.0。

## <span id="10.3.5 - 2025-01-07">10.3.5 (2025-01-07)</span>

修复获取历史消息报错的问题。

## <span id="10.3.4 - 2024-12-24">10.3.4 (2024-12-24)</span>

新增 [用户在线状态事件订阅](https://doc.yunxin.163.com/messaging2/guide/DA0MjM3NTk?platform=client) 功能。

## <span id="10.3.3 - 2024-11-22">10.3.3 (2024-11-22)</span>

修复 iOS 端无法拉取群组更新属性的问题。

## <span id="10.3.1 - 2024-09-02">10.3.1 (2024-09-02)</span>

优化 PC 端部分已知问题。

## <span id="10.3.0 - 2024-08-23">10.3.0 (2024-08-23)</span>

**网易云信即时通讯首次发布适配 Flutter 开发框架的 V10 系列 SDK**，NIM Flutter SDK 已发布到 pub 库，您可以通过配置 `pubspec.yaml` 自动下载更新，详情请参考 [集成 Flutter SDK](https://doc.yunxin.163.com/messaging2/guide/DIyNzI1MDA?platform=client)。

10.3.0 版本支持以下功能：

- 支持多端登录、单聊/群聊、用户信息以及好友关系功能模块。
- 支持多样化的消息类型。
- 支持群组管理、用户和好友管理能力。