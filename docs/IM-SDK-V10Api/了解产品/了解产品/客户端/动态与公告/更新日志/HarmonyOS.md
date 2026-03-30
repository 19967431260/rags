本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）开发版鸿蒙端的更新日志。

::: note note
有关 UI 组件的更新日志，请参考 [鸿蒙 UIKit 更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/jE4MTgyNTI?platform=client)。
:::

<style>
table th:first-of-type {
    width: 35%;
}
</style>

## <span id="10.9.80 - 2026-03-20">10.9.80 (2026-03-20)</span>

登录连接优化，提升登录成功率。

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

优化 SDK 多实例能力，具体使用姿势请参考 [多实例使用指南](https://doc.yunxin.163.com/messaging2/guide/DQ0MjQ1NTM?platform=client)。

**API 更新**

方法/回调/类 | 说明
---- | ----
`translateText` | 新增方法，用于将原始文本翻译为指定语言。
`V2NIMUtilityService.exportMessagesToPath` | 新增方法，用于导出本地消息到指定文件。
`V2NIMUtilityService.importMessagesFromPath` | 新增方法，用于将指定文件中的消息导入到本地消息。
`V2NIMUtilityService.cancelMigrateMessages` | 新增方法，用于取消当前导入/导出消息的操作。
`stopAIStreamMessage` | 接口更新，同时支持 AI 数字人流式消息和普通流式消息的停止。

## <span id="10.9.72 - 2025-12-29">10.9.72 (2025-12-29)</span>

- 优化同步时间戳。
- 修复已知问题。

## <span id="10.9.70 - 2025-12-10">10.9.70 (2025-12-10)</span>

**新增特性**

- 支持清空本地历史消息。
- 支持自定义推送文案配置。
- 适配 HarmonyOS 6。
- 支持 TCP 连接。

**优化**

- 优化本地会话未读数以及最后一条消息的内部逻辑。
- 优化好友申请功能，当用户离线后再次登录后，同步离线期间的删除好友和清空好友的记录。
- 优化群组申请/邀请记录的云端存储。

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMMessage` | 消息对象新增 `fromClientType`，表示消息发送方的客户端类型。  
`clearLocalMessage` | 新增方法，用于清空历史消息。
`clearAllTeamJoinActionInfoEx` | 新增接口，主要用于清空所有入群申请。较 clearAllTeamJoinActionInfo 接口，该接口支持申请记录的云端存储。

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

## <span id="10.9.50 - 2025-09-12">10.9.50 (2025-09-12)</span>

**新增特性**

- 消息流式处理：普通流式消息现支持携带 RAG 信息，增强 AI 交互能力。
- 群组信息全文检索：新增群组信息本地全文检索接口，支持快速查找群组。
- 群成员信息全文检索：新增群成员信息本地全文检索接口，便于快速定位群成员。

**优化**

- AI 用户信息：优化 AI 用户信息字段，提供更丰富的 AI 交互体验。
- 登录安全性：优化登录被踢模式，提升账户安全管理。

**API 更新**

方法/回调/类 | 说明
---- | ----
`searchTeams` | 新增接口，用于根据关键词全文检索本地的符合条件的群组 ID 和群组名称。
`searchTeamMembersEx` | 新增接口，用于根据关键词全文检索本地的符合条件的群成员信息。
`V2NIMMessageSearchExParams` | 搜索配置参数中新增 `tokenize` 字段，用于对输入的关键词进行分词。
`V2NIMAIUser` | AI 用户信息结构体中新增 `aiModelType` 字段，替换原有的 `modelType` 字段，表示大模型类型。
`V2NIMMessageStreamConfig` | 消息体的流式输出相关配置信息中新增 `rag` 字段，表示流式消息中携带的 rag 信息。

<!--产品确认不对外
## <span id="10.9.42 - 2025-08-15">10.9.42 (2025-08-15)</span>

**新增特性**

- 新增批量插入本地消息功能。
- 优化会话创建内部逻辑。

**API 更新**

方法/回调/类 | 说明
---- | ----
`importMessagesToLocal` | 新增接口，批量导入本地消息。
-->

## <span id="10.9.40 - 2025-08-07">10.9.40 (2025-08-07)</span>

**新增特性**

- 新增设置当前聊天账号功能。  
- 新增根据消息 ID 列表查询消息功能。    
- 消息新增在线/离线标志。   
<!--不支持
- 新增查询本端当前登录用户的所有数据库信息功能。  
-->

**优化**

- 优化更新消息内部逻辑，去除权限校验。   
- 回调失败的消息支持重新发送。  

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMLocalConversationService.setCurrentConversation` | 新增接口，用于设置当前的聊天账号。   
`getMessageListByServerIds` | 新增接口，用于根据消息 ID 列表查询消息。只查询本地数据库。       
`V2NIMMessageSource` | 新增枚举，表示消息来源，用于判断在线/离线状态。  
<!--不支持
`V2NIMStatisticsService.getDatabaseInfos` | 新增接口，用于查询本端当前登录用户的所有数据库信息。 
-->

## <span id="10.9.30 - 2025-07-18">10.9.30 (2025-07-18)</span>

**新增特性**

- 支持删除漫游消息功能。
- 支持在登录时设置登录抄送配置。
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

**新增特性**

新增群成员特别关注功能。

**优化**

- 优化好友申请功能。
- 优化入群申请/邀请功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
`addTeamMembersFollow` | 新增方法，用于添加特别关注群成员列表。 
`removeTeamMembersFollow` | 新增方法，用于移除特别关注群成员列表。 
`setTeamJoinActionInfoRead` | 新增接口，用于设置入群申请已读。
`getTeamJoinActionInfoUnreadCount` | 新增接口，用于查询入群申请/邀请的未读数量。
`setAddApplicationReadEx` | 新增接口，用于设置好友申请已读。
`V2NIMTeamMember` | 新增 `followAccountIds` 字段，表示特别关注的群成员账号列表。

<!--下个版本
`clearRoamingMessage` | 新增接口，用于清空会话漫游消息。
`getMessageListByServerIds` | 新增接口，根据消息服务器 ID 查询本地消息。
`aiChatAssist` | 新增接口，用于获取 AI 助聊信息。
`updateSelfTeamMemberInfo` | 新增接口，用于更新自己的群成员信息。
`updateTeamMemberNickEx` | 新增接口，用于修改群成员昵称。
`V2NIMLoginOption` | 在初始化参数中新增 `offlineMode` 字段，表示是否启用离线模式，默认不开启。
`V2NIMChatroomEnterParams` | 在进入聊天室配置参数中新增 `enableLbs` 字段，表示是否启用聊天室 LBS，默认为不启用。
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

- 支持查询指定用户是否在黑名单中。
- 新增置顶会话查询能力。

**优化**

优化黑名单发送消息失败后漫游消息处理的内部逻辑。

**API 更新**

方法/回调/类 | 说明
---- | ----
`getMessageListEx` | 新增方法，用于查询历史消息列表。分页接口，可以根据参数组合查询各种类型，每次默认 50 条消息。
`checkBlock` | 新增方法，用于查看指定用户是否在黑名单中。
`V2NIMConversationService.getStickTopConversationList` | 新增方法，用于查询当前置顶的全量云端会话列表。
`V2NIMLocalConversationService.getStickTopConversationList` | 新增方法，用于查询当前置顶的全量本地会话列表。
`V2NIMConversation` | 会话对象新增 `name`（会话名称）、`avatar`（会话头像）、`mute`（会话静音状态）以及 `lastReadTime`（上一会话已读时间） 字段。
`V2NIMMessageListResult` | 新增查询消息列表返回的数据结构。

## <span id="10.8.30 - 2025-04-25">10.8.30 (2025-04-25)</span>

**特性变更**

- 新增支持 IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。<!-- 具体请参考 [与 AI 数字人聊天（SDK）]()。 -->
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

## <span id="10.8.25 - 2025-04-01">10.8.25 (2025-04-01)</span>

**优化改进**

聊天室支持私有化配置。

## <span id="10.8.20 - 2025-03-21">10.8.20 (2025-03-21)</span>

**优化改进**

本地历史消息检索功能支持按消息子类型进行过滤。

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMMessageSearchExParams` | 本地历史消息检索接口的入参中新增 `messageSubtypes` 字段，表示自定义消息子类型。

## <span id="10.8.10 - 2025-03-10">10.8.10 (2025-03-10)</span>

**优化改进**

- 优化查询群成员信息的内部逻辑。
- 优化提升连接稳定性。

**API 更新**

方法/回调/类 | 说明
---- | ----
`inviteMemberEx` | 新增方法，用于邀请成员加入群组。
`V2NIMTeamInviteParams` | 新增数据结构，用于定义邀请成员入群的配置参数。
`V2NIMTeamJoinActionInfo` | 入群操作信息中新增 `serverExtension` 字段，用于配置扩展信息。

<!-- 
`enableV2CloudConversation` | 云端会话的配置开关，默认为 `false`，代表不启用云端会话模式。只有设置为 `true` 后，才能正常使用 [`V2NIMConversationService`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#%E6%8E%A5%E5%8F%A3%E7%B1%BB)。
 -->
## <span id="10.8.5 - 2025-02-20">10.8.5 (2025-02-20)</span>

内部性能优化。

**API 更新**

方法/回调/类 | 说明
---- | ----
`V2NIMMessageStatus` | 消息状态对象中新增 `readReceiptSent` 字段，表示是否已发送过已读回执。<br>当用户开启群消息已读回执时，客户端收到消息后需要发送已读回执请求，为了避免重复发送，需要通过该字段判断是否已发送过已读回执。

## <span id="10.8.0 - 2025-02-17">10.8.0 (2025-02-17)</span>

**新增特性**

支持清空本地历史消息功能。

**API 更新**

方法/回调/类 | 说明
---- | ----
[`clearHistoryMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage) | 新增 `clearMode` 入参，可自由选择清空 **本地和云端** 或 **仅本地** 的历史消息。

## <span id="10.7.0 - 2024-12-27">10.7.0 (2024-12-27)</span>

内部多项优化。

## <span id="10.6.0 - 2024-11-29">10.6.0 (2024-11-29)</span>

- 新增 [本地消息全文搜索](https://doc.yunxin.163.com/messaging2/guide/TI5MTgzNjU?platform=client) 功能。
- 新增 [用户在线状态事件订阅](https://doc.yunxin.163.com/messaging2/guide/DA0MjM3NTk?platform=client) 功能。
- 新增 [聊天室队列服务](https://doc.yunxin.163.com/messaging2/guide/Tk1MjYyNDc?platform=client) 功能。
- 新增删除或清空 [好友申请](https://doc.yunxin.163.com/messaging2/guide/DE2MTE1OTg?platform=client) / [入群申请](https://doc.yunxin.163.com/messaging2/guide/TU1NTE1NjU?platform=client#管理入群申请) 功能。
- 新增自定义消息附件解析器，用于解析自定义消息各种子类型。
- 新增本地登录信息的查询功能。
- 新增 [AI 数字人](https://doc.yunxin.163.com/messaging2/guide/zQ1MDEwNzA?platform=client) 功能。

## <span id="10.0.0 - 2024-10-29">10.0.0 (2024-10-29)</span>

**鸿蒙 SDK 的版本号调整为 v10.0.0，与其他客户端版本对齐。**

- 新增 [消息更新](https://doc.yunxin.163.com/messaging2/guide/jg1NjE1NDY?platform=client) 以及 [消息过滤](https://doc.yunxin.163.com/messaging2/guide/TA4ODQ0NTI?platform=client) 功能。
- 新增消息附件下载功能。
- 新增群定向消息功能。发送群消息时，可以指定接收消息的群成员列表。
- 新增根据关键字检索群信息功能以及根据关键词检索群成员昵称功能。

::: note important
在使用云端会话功能的情况下，不建议使用消息过滤功能。
:::

## <span id="1.4.0 - 2024-09-27">1.4.0 (2024-09-27)</span>

- 性能优化。
- 修复已知问题。

::: note important
HarmonyOS 应用/服务编译时的版本由 4.0.0(10) 升至 5.0.0(12)。请您在升级的 SDK 时同时将鸿蒙系统版本更新为 "compatibleSdkVersion": "5.0.0(12)"。
:::

## <span id="1.3.1 - 2024-09-06">1.3.1 (2024-09-06)</span>

- 修复已知问题。
- 性能优化。

## <span id="1.3.0 - 2024-08-30">1.3.0 (2024-08-30)</span>

- 新增本地会话功能，具体请参考 [本地会话管理](https://doc.yunxin.163.com/messaging2/guide/zMyODU1OTM?platform=client)。
- 支持生成图片缩略图和视频封面图。
- 内部优化。

## <span id="1.2.0 - 2024-07-31">1.2.0 (2024-07-31)</span>

- 新增标记会话消息已读功能。
- 内部优化。

## <span id="1.1.0 - 2024-06-28">1.1.0 (2024-06-28)</span>

- 新增消息发送状态监听能力。
- 优化底层传输逻辑，提升传输效率。
- 修复部分底层问题。

## <span id="1.0.0 - 2024-05-31">1.0.0 (2024-05-31)</span>

- 新增聊天室功能，具体请参考 [聊天室功能概述](https://doc.yunxin.163.com/messaging2/guide/jYyNjkwMDA?platform=client)。
- 优化集成方式，简化集成流程。
- 修复已知问题。

## <span id="0.6.0 - 2024-05-09">0.6.0 (2024-05-09)</span>

- 新增会话分组功能，具体请参考 [会话分组](https://doc.yunxin.163.com/messaging2/guide/DYzMjEwOTg?platform=client)。
- 新增系统设置功能，支持设置免打扰。

## <span id="0.5.0 - 2024-03-29">0.5.0 (2024-03-29)</span>

**网易云信 IM 即时通讯 Harmony SDK 首次发布**，v0.5.0 版本支持以下功能：

- 支持多端登录、单聊/群聊、用户信息以及好友关系功能模块。
- 支持多样化的消息类型。
- 支持群组管理、用户和好友管理能力。
- 支持鸿蒙推送能力，具体请参考 [实现 HarmonyOS 离线推送](https://doc.yunxin.163.com/messaging2/guide/TMzMzE5Mjc?platform=client)。