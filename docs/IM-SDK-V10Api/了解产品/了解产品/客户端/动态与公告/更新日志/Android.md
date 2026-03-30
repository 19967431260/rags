本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）开发版安卓端 10.x.x 及以上版本的更新日志。

::: note note
- 有关稳定版 9.x.x 及以下版本，请参考《IM 即时通讯 V9》[Android 更新日志](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client)。
- 有关 UI 组件安卓端 10.x.x 及以上版本的更新日志，请参考 [Android UIKit 更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/zMzNDI4MDI?platform=client)。
:::

<style>
table th:first-of-type {
    width: 35%;
}
</style>

## <span id="10.9.80 - 2026-03-20">10.9.80 (2026-03-20)</span>

- 好友逻辑优化。
- 其他内部优化。

## <span id="10.9.77 - 2026-02-27">10.9.77 (2026-02-27)</span>

修复已知问题。

## <span id="10.9.76 - 2026-02-06">10.9.76 (2026-02-06)</span>

**新增特性**

本地插入消息支持配置，使用户可任意插入消息状态。

**API 更新**

方法/回调/类 | 说明
---- | ----
`insertMessageToLocalEx` | 新增方法，用于插入一条本地消息。较 `insertMessageToLocal` 接口新增 `V2NIMMessageInsertParams.lastMessageUpdateEnabled`，表示是否需要更新会话的最后一条信息。

## <span id="10.9.75 - 2026-01-28">10.9.75 (2026-01-28)</span>

**新增特性**

- 支持翻译功能，将原始文本翻译为指定语言。
- 新增历史消息导入/导出能力，支持消息迁移。
- 普通消息的流式输出支持停止取消。

**优化**

优化下载功能，支持安全链接的 URL 下载。

**API 更新**

方法/回调/类 | 说明
---- | ----
`translateText` | 新增方法，用于将原始文本翻译为指定语言。
`V2NIMUtilityService.exportMessagesToPath` | 新增方法，用于导出本地消息到指定文件。
`V2NIMUtilityService.importMessagesFromPath` | 新增方法，用于将指定文件中的消息导入到本地消息。
`V2NIMUtilityService.cancelMigrateMessages` | 新增方法，用于取消当前导入/导出消息的操作。
`stopAIStreamMessage` | 接口更新，同时支持 AI 数字人流式消息和普通流式消息的停止。

## <span id="10.9.71 - 2026-01-05">10.9.71 (2026-01-05)</span>

**优化**

- 支持在初始化时配置聊天室默认 Link 地址。在聊天室中启用 LBS，但 LBS 不可用时，将使用设置的默认 Link 地址（`chatRoomLinkList`）进行连接。具体请参考 [聊天室连接配置最佳实践](https://doc.yunxin.163.com/messaging2/guide/jMyNDg5MzU?platform=client)。
- 优化 IM 快连双栈竞速能力。
- 优化 QUIC 冗余包动态调整。
- 进一步优化网络通信体验。
- 其他内部优化。

## <span id="10.9.70 - 2025-12-05">10.9.70 (2025-12-05)</span>

**新增特性**

支持清空本地历史消息。

<!--
聊天室 lbs 地址提供默认国内外地址。
-->

**优化**

- 优化好友申请功能，当用户离线后再次登录后，同步离线期间的删除好友和清空好友的记录。
- 优化群组申请/邀请记录的云端存储。

**API 更新**

方法/回调/类 | 说明
---- | ----
`clearLocalMessage` | 新增方法，用于清空历史消息。
`V2NIMMessage` | 消息对象新增 `fromClientType`，表示消息发送方的客户端类型。  
`clearAllTeamJoinActionInfoEx` | 新增接口，主要用于清空所有入群申请。较 `clearAllTeamJoinActionInfo` 接口，该接口支持申请记录的云端存储。

## <span id="10.9.60 - 2025-11-05">10.9.60 (2025-11-05)</span>

**新增特性**

- 支持获取自己管理的群组列表。 
- API 普通流式消息支持高级群。
- 超大群消息支持单向删除。

**优化**

- 优化优化单聊会话已读回执数量和时间。
- 优化好友申请逻辑。

**API 更新**

方法/回调/类 | 说明
---- | ----
`getManagerTeamList` | 新增接口，用于获取当前自己为管理员的群组列表（包括自己是群主的群）。
`clearAllAddApplicationEx` | 新增接口，用于清空所有好友申请。较 `clearAllAddApplication` 接口入参新增清除好友申请记录的相关选项参数（包括好友申请类型和申请时间戳）。

## <span id="10.9.52 - 2025-09-26">10.9.52 (2025-09-26)</span>

内部优化。

## <span id="10.9.50 - 2025-09-12">10.9.50 (2025-09-12)</span>

**新增特性**

- 消息流式处理：普通流式消息现支持携带 RAG 信息，增强 AI 交互能力。
- 群组信息全文检索：新增群组信息本地全文检索接口，支持快速查找群组。
- 群成员信息全文检索：新增群成员信息本地全文检索接口，便于快速定位群成员。

**优化**

- 文件附件：优化 `V2NIMMessageAttachmentUtil` 中 `getFileAttachmentThumbPath` 方法，提升文件处理效率。
- AI 用户信息：优化 AI 用户信息字段，提供更丰富的 AI 交互体验。
- 登录安全性：优化登录被踢模式，提升账户安全管理。
- 会话变更通知：收到陌生人消息或用户信息（姓名/头像）变化时，自动通知会话变更，提升用户体验。

**API 更新**

方法/回调/类 | 说明
---- | ----
`searchTeams` | 新增接口，用于根据关键词全文检索本地的符合条件的群组 ID 和群组名称。
`searchTeamMembersEx` | 新增接口，用于根据关键词全文检索本地的符合条件的群成员信息。
`V2NIMMessageSearchExParams` | 搜索配置参数中新增 `tokenize` 字段，用于对输入的关键词进行分词。
`V2NIMAIUser` | AI 用户信息结构体中新增 `aiModelType` 字段，替换原有的 `modelType` 字段，表示大模型类型。
`V2NIMMessageStreamConfig` | 消息体的流式输出相关配置信息中新增 `rag` 字段，表示流式消息中携带的 rag 信息。

## <span id="10.9.45 - 2025-09-09">10.9.45 (2025-09-09)</span>

内部优化。

## <span id="10.9.44 - 2025-08-29">10.9.44 (2025-08-29)</span>

优化消息中会话 ID 获取方式。

## <span id="10.9.43 - 2025-08-27">10.9.43 (2025-08-27)</span>

**API 更新**

方法/回调/类 | 说明
---- | ----
`createConversation` | 新增对应同步接口，用于创建会话。

<!--产品确认不对外
## <span id="10.9.42 - 2025-08-15">10.9.42 (2025-08-15)</span>

**新增特性**

新增批量插入本地消息功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
`importMessagesToLocal` | 新增接口，批量导入本地消息。

## <span id="10.9.41 - 2025-08-14">10.9.41 (2025-08-14)</span>

- 优化会话创建内部逻辑。
- 其他内部优化。
-->

## <span id="10.9.40 - 2025-08-07">10.9.40 (2025-08-07)</span>

**新增特性**

- 新增设置当前聊天账号功能。
- 新增查询本端当前登录用户的所有数据库信息功能。
- 消息新增在线/离线标志。
- 在线提醒支持设置通知优先级。

**优化**

- 优化更新消息内部逻辑，去除权限校验。
- 回调失败的消息支持重新发送。

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMLocalConversationService.setCurrentConversation` | 新增接口，用于设置当前的聊天账号。
`V2NIMStatisticsService.getDatabaseInfos` | 新增接口，用于查询本端当前登录用户的所有数据库信息。
`getConversationListByIds` | 新增对应同步接口，用于根据会话 ID 获取本地会话列表。
`V2NIMMessageSource` | 新增枚举，表示消息来源，用于判断在线/离线状态。

## <span id="10.9.30 - 2025-07-18">10.9.30 (2025-07-18)</span>

**新增特性**

- 支持删除漫游消息功能。
- 支持在登录时设置登录抄送和登录重连配置。
- 支持更新群个人名片和群成员昵称时配置是否通过反垃圾审核。

**API 更新**

方法/回调/类 | 说明
---- | ----
`clearRoamingMessage` | 新增接口，用于删除漫游消息。
`V2NIMLoginOption` | 登录配置参数中新增 `routeConfig` 字段，用于设置登录抄送配置。
`V2NIMChatroomLoginOption` | 聊天室登录配置参数中新增 `routeConfig` 字段，用于设置聊天室登录抄送配置。
`updateSelfTeamMemberInfo` | 更新接口，在更新自己名片时支持设置 `antispamConfig` 字段，用于配置是否通过反垃圾审核。
`updateTeamMemberNickEx` | 新增接口，用于更新群成员昵称。<br>较 `updateTeamMemberNick` 接口，支持在更新时设置 `antispamConfig` 字段，配置是否通过反垃圾审核。

## <span id="10.9.20 - 2025-07-02">10.9.20 (2025-07-02)</span>

**优化**

- 优化好友申请功能。
- 优化入群申请/邀请功能。
- 聊天室支持 LBS 以及 WebSocket 连接。

**API 更新**

方法/回调/类 | 说明
---- | ----
`setTeamJoinActionInfoRead` | 新增接口，用于设置入群申请已读。
`getTeamJoinActionInfoUnreadCount` | 新增接口，用于查询入群申请/邀请的未读数量。
`setAddApplicationReadEx` | 新增接口，用于设置好友申请已读。
`V2NIMLoginOption` | 在初始化参数中新增 `offlineMode` 字段，表示是否启用离线模式，默认不开启。
`V2NIMChatroomEnterParams` | 在进入聊天室配置参数中新增 `enableLbs` 字段，表示是否启用聊天室 LBS，默认为不启用。

<!--下个版本
`aiChatAssist` | 新增接口，用于获取 AI 助聊信息。
`updateSelfTeamMemberInfo` | 新增接口，用于更新自己的群成员信息。
`updateTeamMemberNickEx` | 新增接口，用于修改群成员昵称。
`clearRoamingMessage` | 新增接口，用于清空会话漫游消息。
`getMessageListByServerIds` | 新增接口，根据消息服务器 ID 查询本地消息。
-->

## <span id="10.9.10 - 2025-06-18">10.9.10 (2025-06-18)</span>

**新增特性**

- 全文检索能力支持双向检索。
- 支持普通消息流式显示。

**API 更新**

方法/回调/类 | 说明  
---- | ----
`searchLocalMessages` | 更新方法，新增 `direction` 字段，支持双向检索能力。
`V2NIMMessageStreamStatus` | 消息的流式输出状态。
`V2NIMMessageStreamChunk` | 消息的流式输出最近分片信息。
`V2NIMMessageStreamConfig` | 消息体中的流式输出相关配置信息。若存在该配置信息说明是流式消息，否则是非流式消息。
`getJoinedTeamMembers` | 新增方法，用于查询加入群组的成员列表。
`getAllTeamMessageMuteMode` | 新增方法，用于查询自己所在的所有群组的消息免打扰模式。
`clearHistoryMessage` | 更新方法，新增 `clearMode` 字段，支持配置是否同时删除云端和本地的是历史消息。
`updateLocalMessage` | 新增方法，用于更新本地插入的消息。
`getCloudMessageList` | 新增方法，用于按条件分页获取云端消息。
`getPushMobileOnDesktopOnline` | 新增方法，用于查询桌面端在线时，移动端是否需要推送。
`onPushMobileOnDesktopOnline` | 新增回调，用于监听当桌面端在线时，移动端是否需要推送。

## <span id="10.9.0 - 2025-05-30">10.9.0 (2025-05-30)</span>

**新增特性**

- 支持消息过滤功能。
- 支持查询指定用户是否在黑名单中。
- 新增置顶会话查询能力。

**优化**

- 优化聊天室 Link 获取逻辑。 
- 优化黑名单发送消息失败后漫游消息处理的内部逻辑。

**API 更新**

方法/回调/类 | 说明
---- | ----
`getMessageListEx` | 新增方法，用于查询历史消息列表。分页接口，可以根据参数组合查询各种类型，每次默认 50 条消息。
`checkBlock` | 新增方法，用于查看指定用户是否在黑名单中。
`V2NIMConversationService.getStickTopConversationList` | 新增方法，用于查询当前置顶的全量云端会话列表。
`V2NIMLocalConversationService.getStickTopConversationList` | 新增方法，用于查询当前置顶的全量本地会话列表。
`setMessageFilter` | 新增方法，设置消息过滤器，实现消息过滤。
`V2NIMMessageFilter` | 新增对象，表示消息过滤器，用于实现消息过滤。
`V2NIMConversation` | 会话对象新增 `name`（会话名称）、`avatar`（会话头像）、`mute`（会话静音状态）以及 `lastReadTime`（上一会话已读时间） 字段。
`V2NIMMessageListResult` | 新增查询消息列表返回的数据结构。
`ServerAddresses.chatRoomLbsList` | 新增字段，表示聊天室 LBS 服务器地址。
`EnterChatRoomData.enableLbs` | 新增方法，用于启用聊天室 LBS。默认为 false，不启用。
`enableEnhancedLinkSecurity` | 新增方法，用于启用增强链路安全策略，默认为 YES，启用。

## <span id="10.8.30 - 2025-04-24">10.8.30 (2025-04-24)</span>

**新增特性**

- 新增支持 IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。具体请参考 [与 AI 数字人聊天（SDK）](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。
- 优化全文检索云端历史消息。您可以按照指定条件，全局检索整个应用内的云端历史消息。

**API 更新**

方法/回调/类 | 说明
---- | ----
`searchCloudMessagesEx` | 新增方法，用于全文检索云端历史消息。 
`stopAIStreamMessage` | 新增方法，用于停止 AI 数字人流式输出消息，可以选择直接停止输出，或撤回/更新已输出的 AI 数字人消息。
`regenAIMessage` | 新增方法，用于重新输出 AI 数字人消息，可以选择直接更新覆盖已输出的消息，或者直接创建一条新的 AI 数字人消息。
`stopAIModelStreamCall` | 新增方法，用于向服务器请求停止流式输出 AI 数字人消息。
`onProxyAIModelStreamCall` | 新增 AI 数字人流式输出回调。
`sendMessage` | 接口更新，发送消息的 AI 数字人配置参数中新增输出模式字段（`aiStream`）字段，选择是否使用流式输出 AI 数字人消息。
`proxyAIModelCall` | 接口更新，向 LLM 发起模型调用请求方法的 AI 数字人配置参数中新增输出模式字段（`Stream`），选择是否流式输出 AI 数字人消息。

## <span id="10.8.21 - 2025-03-24">10.8.21 (2025-03-24)</span>

**优化改进**

本地历史消息检索功能支持按消息子类型进行过滤。

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMMessageSearchExParams` | 本地历史消息检索接口的入参中新增 `messageSubtypes` 字段，表示自定义消息子类型。

## <span id="10.8.10 - 2025-03-10">10.8.10 (2025-03-10)</span>

**新增特性**

支持在初始化 SDK 时配置是否开启 [云端会话功能](https://doc.yunxin.163.com/messaging2/guide/zExMDk4ODU?platform=client)，默认不开启，即默认使用本地会话功能。

**优化改进**

- 优化查询群成员信息的内部逻辑。 
- 优化提升连接稳定性。

**API 更新**

方法/回调/类 | 说明
---- | ----
`inviteMemberEx` | 新增方法，用于邀请成员加入群组。
`V2NIMTeamInviteParams` | 新增数据结构，用于定义邀请成员入群的配置参数。
`V2NIMTeamJoinActionInfo` | 入群操作信息中新增 `serverExtension` 字段，用于配置扩展信息。
`enableV2CloudConversation` | 云端会话的配置开关，默认为 `false`，代表不启用云端会话模式（默认使用本地会话模式）。只有设置为 `true` 后，才能正常使用 [`V2NIMConversationService`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#%E6%8E%A5%E5%8F%A3%E7%B1%BB) 服务。

## <span id="10.8.0 - 2025-02-17">10.8.0 (2025-02-17)</span>

**新增特性**

- 新增本地会话功能。详情请参考 [本地会话管理](https://doc.yunxin.163.com/messaging2/guide/zMyODU1OTM?platform=client)。
- 支持清空本地历史消息功能。
- 支持自行填入第三方厂商的推送 token。详情请参考 [实现 Android 离线推送](https://doc.yunxin.163.com/messaging2/guide/TkzMjk1ODg?platform=client#相关参考)。
- SDK 适配 16KB 内存页大小（Page Size），确保可以在使用 4 KB 和 16 KB 内存页大小的设备上无缝运行，提升兼容性并避免崩溃。（加密数据库需要升级至 `net.zetetic:sqlcipher-android:4.6.1`。）

**API 更新**

方法/回调/类 | 说明
---- | ----
[`clearHistoryMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage) | 新增 `clearMode` 入参，可自由选择清空 **本地和云端** 或 **仅本地** 的历史消息。
`V2NIMLocalConversationService` | 新增本地会话服务类，提供创建、删除、更新、获取、置顶本地会话，本地会话消息未读数相关、注册本地会话监听等接口。

## <span id="10.7.0 - 2024-12-27">10.7.0 (2024-12-27)</span>

**新增特性**

- 新增本地消息全文搜索功能。
- 提升网络联通率与稳定性，支持 QUIC 能力。
- 内部多项优化。

**API 更新**

方法/回调/类 | 说明
---- | ----
`searchLocalMessages` | 新增方法，用于全文检索本地历史消息。
`getCollectionListExByOption` | 新增方法，用于按条件分页获取收藏信息，较 `getCollectionListByOption` 方法，回参新增 `totalCount` 字段，表示收藏总数。
<!--不对外
`sendCustomNotification` | 发送自定义系统通知方法的入参 `params.notificationConfig` 中新增 `clientNotificationId` 字段，表示客户端系统通知 ID，便于后续查询系统通知日志。
-->

## <span id="10.6.0 - 2024-11-20">10.6.0 (2024-11-20)</span>

**新增特性**

- 新增 [聊天室队列服务](https://doc.yunxin.163.com/messaging2/guide/Tk1MjYyNDc?platform=client) 功能。
- 新增删除或清空 [好友申请](https://doc.yunxin.163.com/messaging2/guide/DE2MTE1OTg?platform=client) / [入群申请](https://doc.yunxin.163.com/messaging2/guide/TU1NTE1NjU?platform=client#管理入群申请) 功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
`queueOffer` | 新增方法，用于在队列中新增或更新元素。
`queuePoll` | 新增方法，用于取出队列中的头元素或指定的元素。
`queueList` | 新增方法，用于排序列出所有元素。
`queuePeek` | 新增方法，用于查看队列的头元素。
`queueDrop` | 新增方法，用于清空队列。
`queueInit` | 新增方法，用于初始化队列。 
`queueBatchUpdate` | 新增方法，用于批量更新队列元素。 
`addQueueListener` | 新增方法，注册聊天室队列监听器。
`removeQueueListener` | 新增方法，取消注册聊天室队列监听器。
`getChatroomQueueService` | 新增方法，用于获取聊天室队列服务（除 Web 端）。
`clearAllAddApplication` | 新增方法，用于清空所有好友申请。
`deleteAddApplication` | 新增方法，用于删除指定的好友申请。
`clearAllTeamJoinActionInfo` | 新增方法，用于清空所有入群申请。
`deleteTeamJoinActionInfo` | 新增方法，用于删除指定的入群申请。
`getMessageList` | 新增 `onlyQueryLocal` 入参，表示是否只查询本地，默认为 true，只查询本地。

## <span id="10.5.1 - 2024-11-15">10.5.1 (2024-11-15)</span>

修复已知问题。

## <span id="10.5.0 - 2024-10-15">10.5.0 (2024-10-15)</span>

**新增特性**

- 融合存储插件化，优化包体积大小。
- 新增 [群成员特别关注](https://doc.yunxin.163.com/messaging2/guide/jM2MDE1MTc?platform=client#群成员特别关注) 功能。
- 新增自定义消息附件解析器，用于解析自定义消息各种子类型。
- 新增本地登录信息的查询功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
[`addTeamMembersFollow`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#addTeamMembersFollow) | 新增方法，用于添加特别关注群成员列表。 |
[`removeTeamMembersFollow`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#removeTeamMembersFollow) | 新增方法，用于移除特别关注群成员列表。 |
[`createCustomMessageWithAttachment`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessageWithAttachment) | 新增方法，用于构造自定义消息。 |
[`registerCustomAttachmentParser`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#registerCustomAttachmentParser) |新增方法，用于注册自定义消息附件解析器，解析消息类型（`V2NIMMessageType`）为 100 的附件。 |
[`unregisterCustomAttachmentParser`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unregisterCustomAttachmentParser) |新增方法，用于反注册自定义消息附件解析器。 |
[`getCurrentLoginClient`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getCurrentLoginClient) | 新增方法，用于查询本地登录的相关信息。 |
[`V2NIMUpdatedTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMUpdatedTeamInfo) | 新增 `customerExtension` 字段，表示客户自定义扩展信息。 |
[`V2NIMTeamMember`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMTeamMember) | 新增 `followAccountIds` 字段，表示特别关注的群成员账号列表。 |
<!---
[`updateAppKey`]() | 新增方法，动态替换 AppKey。 |
[`init`]() | 新增方法，用于初始化 V2NIM 实例。 |
[`update`]() | 新增方法，用于更新 SDK 相关配置。 |
-->

## <span id="10.4.2 - 2024-09-11">10.4.2 (2024-09-11)</span>

优化聊天室重复进入逻辑。

## <span id="10.4.1 - 2024-09-05">10.4.1 (2024-09-05)</span>

- 优化提升连接稳定性。
- 新增仅查询本地的消息。

## <span id="10.4.0 - 2024-08-21">10.4.0 (2024-08-21)</span>

**新增特性**

- 新增 [用户在线状态事件订阅](https://doc.yunxin.163.com/messaging2/guide/DA0MjM3NTk?platform=client) 功能。
- 新增 [更新消息](https://doc.yunxin.163.com/messaging2/guide/jg1NjE1NDY?platform=client) 功能。
- 新增群定向消息功能。发送群消息时，可以指定接收消息的群成员列表。

**优化改进**

- 全面升级第三方推送。
- 优化 SDK 的初始化。

**适配的第三方推送版本**

V10.4.0 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.12.0.300
小米 | 6.0.1
OPPO | 3.5.1
vivo | 4.0.4.0_504
魅族 | 4.3.0
荣耀 | 7.0.61.303
FCM |firebase-bom:28.4.2<br>具体版本：firebase-messaging：24.0.0，firebase-analytics: 22.0.0

**API 更新**

方法/回调/类 | 说明
---- | ----
[`V2NIMSendMessageParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSendMessageParams)|新增 `targetConfig` 参数，用于实现群定向消息功能。
[`modifyMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#modifyMessage)|新增更新消息接口，用于实现消息的二次编辑能力。
[`addSubscribeListener`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#addSubscribeListener)|新增事件监听，用于监听用户订阅相关事件。
[`removeSubscribeListener`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#removeSubscribeListener)|移除事件监听，移除用户订阅相关事件的监听。
[`publishCustomUserStatus`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#publishCustomUserStatus)|新增接口，用于发布用户自定义状态。
[`subscribeUserStatus`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#subscribeUserStatus)|新增接口，用于订阅用户状态。
[`unsubscribeUserStatus`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#unsubscribeUserStatus)|新增接口，用于取消订阅用户状态。
[`queryUserStatusSubscriptions`](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#queryUserStatusSubscriptions)|新增接口，用于查询用户状态的订阅关系。
[错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client)|新增群定向消息、消息更新、用户订阅相关错误码。

## <span id="10.3.1 - 2024-07-19">10.3.1 (2024-07-19)</span>

- 新增 [新版信令](https://doc.yunxin.163.com/signaling/guide?platform=client) 功能。
- 修复已知问题。

## <span id="10.2.6 - 2024-05-10">10.3.0 (2024-07-04)</span>

**新增特性**

- 新增 AI 数字人功能。详情请参考 [AI 数字人](https://doc.yunxin.163.com/messaging2/guide/zQ1MDEwNzA?platform=client)。
- 新增根据关键字检索群信息和群成员信息功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
[`addAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#addAIListener) | 新增方法，注册 AI 数字人相关监听器。 |
[`removeAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#removeAIListener) | 新增方法，移除 AI 数字人相关监听器。 |
[`getAIUserList`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#getAIUserList) | 新增方法，根据用户账号 ID 列表获取 AI 数字人。 |
[`proxyAIModelCall`](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#proxyAIModelCall) | 新增方法，AI 数字人向 LLM 发起查询请求。 |
[`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | 更新方法，AI 数字人发送消息。 |
[`V2NIMAIUser `](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIUser ) | 新增对象。 |
[`V2NIMAIModelType`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelType) | 新增枚举。 |
[`V2NIMAIModelConfig`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelConfig) | 新增对象。 |
[`V2NIMProxyAIModelCallParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMProxyAIModelCallParams) | 新增对象。 |
[`V2NIMProxyAICallAntispamConfig`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMProxyAICallAntispamConfig) | 新增对象。 |
[`V2NIMAIModelCallContent`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelCallContent) | 新增对象。 |
[`V2NIMAIModelCallMessage`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelCallMessage) | 新增对象。 |
[`V2NIMAIModelRoleType`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelRoleType) | 新增枚举。 |
[`V2NIMAIModelConfigParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelConfigParams) | 新增对象。 |
[`V2NIMSendMessageParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSendMessageParams) | 更新对象。 |
[`V2NIMMessageAIConfigParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageAIConfigParams) | 新增对象。 |
[`V2NIMMessageAIConfig`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageAIConfig) | 新增对象。 |
[`V2NIMMessageAIStatus`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageAIStatus) | 新增枚举。 |
[`V2NIMAIModelCallResult`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIModelCallResult) | 新增对象。 |
[`V2NIMAIListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAIListener) | 新增回调监听对象。 |
[`V2NIMMessage`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessage) | 新增对象。 |

## <span id="10.2.6 - 2024-05-10">10.2.6 (2024-05-10)</span>

**新增特性**

- 新增话单消息类型，用于实现音视频通话功能。
- 新增云端拉取用户信息功能，用于实时感知用户信息的更新。
- 支持生成图片缩略图和视频封面图。
- 新增 Thread 消息查询功能。
- 新增发送消息状态的回调。

**优化改进**

- 优化好友申请相关数据信息，新增申请者账号和被申请者信息和未读状态信息。
- 优化好友监听回调（`V2NIMFriendListener`）。

**API 更新**

方法/回调/类 | 说明
---- | ----
[`createCallMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCallMessage) | 新增该方法，用于创建一条话单消息。 |
[`imageThumbUrl`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#imageThumbUrl) | 新增该方法，用于生成图片缩略图。 |
[`videoCoverUrl`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#videoCoverUrl) | 新增该方法，用于生成视频封面链接。 |
[`getUserListFromCloud`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserListFromCloud) | 新增该方法，用于根据用户账号列表从服务器获取用户信息。 |
[`V2NIMFriendAddApplication`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMFriendAddApplication) | 申请添加好友相关操作信息中，新增 `applicantAccountId`（申请者账号）、`recipientAccountId`（被申请者账号）、`read`（是否已读）字段。
[`V2NIMMessageCallAttachment`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageCallAttachment) | 新增对象，表示话单消息附件。
[`V2NIMMessageCallDuration`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageCallDuration) | 新增数据结构，表示话单消息单人通话时长。
[`V2NIMFriendAddApplicationStatus`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimfriendaddapplicationstatus) | 添加好友申请状态枚举中，新增 `V2NIM_FRIEND_ADD_APPLICATION_STATUS_DIRECT_ADD` 枚举值，表示直接添加为好友。
[`getThreadMessageList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getThreadMessageList) | 分页查询 Thread 历史消息列表。
[`getLocalThreadMessageList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getLocalThreadMessageList) | 查询本地 Thread 历史消息列表。
[`V2NIMThreadMessageListOption`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMThreadMessageListOption) | Thread 消息查询选项。
[`V2NIMThreadMessageListResult`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMThreadMessageListResult) | Thread 消息查询结果。
[`V2NIMMessageListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageListener) | 新增发送消息状态的回调（`onSendMessage`），本端发送消息或插入消息成功后，SDK 会返回该回调。
[`V2NIMChatroomListener`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMChatroomListener) | 新增发送聊天室消息状态的回调（`onSendMessage`），本端发送聊天室消息或插入聊天室消息成功后，SDK 会返回该回调。
[`V2NIMAddCollectionParams`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMAddCollectionParams) | 消息收藏配置参数新增 `uniqueId` 字段，表示去重唯一 ID，如果 ID 相同，则不会新增收藏，只更新之前的收藏内容。
[`V2NIMCollection`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMCollection) | 收藏数据结构新增 `uniqueId` 字段，表示去重唯一 ID，如果 ID 相同，则不会新增收藏，只更新之前的收藏内容。

## <span id="10.2.4 - 2024-04-07">10.2.4 (2024-04-07)</span>

**新增特性**

- 新增获取推送免打扰配置详情功能。
- 新增鸿蒙终端类型的解析。

**API 更新**

方法/回调/类 | 说明
---- | ----
[`getDndConfig`](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getDndConfig) | 新增获取推送免打扰配置详情的方法。
[`V2NIMLoginClientType`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimloginclienttype) | 新增鸿蒙终端类型（`V2NIM_LOGIN_CLIENT_TYPE_HARMONY_OS`）。

## <span id="10.2.3 - 2024-03-27">10.2.3 (2024-03-27)</span>

**新增特性**

- 新增文件下载功能。
- 新增文件 URL 短链接转长链接功能。

**优化改进**

- 登录状态新增 **未登录**。
- 通知消息附件新增 **群信息更新** 字段。

**API 新增**

方法/回调/类 | 说明
---- | ----
[`downloadFile`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#downloadFile) | 新增方法，用于下载文件。
[`shortUrlToLong`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#shortUrlToLong) | 新增方法，用于文件 URL 短链接转长链接。

**API 变更**

方法/回调/类 | 说明
---- | ----
[`V2NIMLoginStatus`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMLoginStatus) | 新增 `V2NIM_LOGIN_STATUS_UNLOGIN` 未登录状态。
[`V2NIMMessageNotificationAttachment`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMMessageNotificationAttachment) | 新增 `updatedTeamInfo` 成员参数，用于获取群信息更新字段。类型为 [`V2NIMUpdatedTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMUpdatedTeamInfo)。

## <span id="10.2.2 - 2024-03-19">10.2.2 (2024-03-19)</span>

**新增特性**

新增用户和好友信息检索功能。

**优化改进**

- 优化会话最后一条信息，新增消息发送者的用户信息。
- 优化通知消息类型，拆分高级群和超大群的通知消息类型。

**API 新增**

方法/回调/类 | 说明
---- | ----
[`searchFriendByOption`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#searchFriendByOption) | 新增方法，根据关键字信息搜索好友信息。
[`searchUserByOption`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#searchUserByOption) | 新增方法，根据关键字信息搜索用户信息。

**API 变更**

方法/回调/类 | 说明
---- | ----
[`V2NIMLastMessage`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMLastMessage) | 新增 `senderName` 成员参数，用于获取消息发送者的名称。
[`V2NIMMessageNotificationType`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimmessagenotificationtype) | 新增超大群（`SUPER_TEAM`）相关的通知消息类型，将高级群和超大群的通知消息类型进行拆分。

## <span id="10.2.1 - 2024-03-01">10.2.1 (2024-03-01)</span>

**新增特性**

- 新增查询未读好友申请数据功能。
- 新增设置好友申请已读功能。

**优化改进**

- 优化群通知附件信息。
- 优化会话名称（[`V2NIMConversation.name`](https://doc.yunxin.163.com/messaging2/docs/DAxNjk0Mzc?platform=client#V2NIMConversation)）的显示规则。

**API 新增**

方法/回调/类 | 说明
---- | ----
[`getAddApplicationUnreadCount`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationUnreadCount) | 新增方法，用于查询未读的好友申请数量。
[`setAddApplicationRead`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setAddApplicationRead) | 新增方法，用于将所有未读的好友申请标记为已读。

**API 变更**

方法/回调/类 | 说明
---- | ----
[`V2NIMFriend`](https://doc.yunxin.163.com/messaging2/docs/DAxNjk0Mzc?platform=client#V2NIMFriend) | 新增 `userProfile` 成员参数，用于获取好友对应的用户信息。
[`V2NIMMessageNotificationAttachment`](https://doc.yunxin.163.com/messaging2/docs/DAxNjk0Mzc?platform=client#V2NIMMessageNotificationAttachment) | 新增 `updateTeamInfo` 成员参数，用于通知消息的群信息更新字段显示。

## <span id="10.2.0 - 2024-01-26">10.2.0 (2024-01-26)</span>

**v10.2.0 版本发布**。平台包括 Android、iOS、Windows/macOS、Web（Web/小程序/uniapp）、Linux。

**新增特性**

- 新增全套新版 API，具体请参考 [API 概览](https://doc.yunxin.163.com/messaging2/docs/DY2Mjk0MjU?platform=client)。

- 新增云端会话功能，支持在不登录 IM 的情况下，通过相关接口获取会话数据。具体请参考 [会话管理](https://doc.yunxin.163.com/messaging2/docs/zExMDk4ODU?platform=client)。

- 新增云端会话分组功能，支持按照自定义维度将会话进行分组，方便用户管理和查询会话。具体请参考 [会话分组管理](https://doc.yunxin.163.com/messaging2/docs/DYzMjEwOTg?platform=client)。

**改进优化**

- 对于圈组功能，新版本采用融合登录策略，用户只需登录一次，则可以完成 IM 登录与圈组登录。
- 对于聊天室登录模式进行各端一致性优化，聊天室连接地址为用户托管，由用户自行选择聊天室连接地址获取方式。具体请参考 [聊天室登录](https://doc.yunxin.163.com/messaging2/docs/DI2NDc1NzQ?platform=client)。
- 优化聊天室成员角色分类与操作逻辑，具体请参考 [聊天室成员管理](https://doc.yunxin.163.com/messaging2/docs/Dc4NTY1ODQ?platform=client#技术原理)：

    V10 | V9 |
    ---- | ---- |
    对聊天室成员执行拉黑/解除拉黑操作，聊天室成员角色不变。 | 黑名单用户为固定成员，移除黑名单后变为游客身份。 |
    对聊天室成员执行禁言/接触禁言操作，聊天室成员角色不变。 | 永久禁言用户为固定成员，解除永久禁言后变为游客身份。 |