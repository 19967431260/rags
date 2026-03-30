本文介绍网易云信即时通讯（简称 NIM）服务端 10.x.x 及以上版本的更新日志。有关 9.x.x 版本及更低版本，请参考《IM 即时通讯 V9 版本》[更新日志](https://doc.yunxin.163.com/messaging/server-apis/DI5ODYxMTg?platform=server)。

<style>
table th:first-of-type {
    width: 40%;
}
</style>

## <span id="10.10.15 - 2026-22-10">10.10.15 (2026-02-10)</span>

**新增特性**

支持根据用户账号和会话分组 ID 查询会话列表。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
[分页查询指定账号的指定会话分组的会话列表](https://doc.yunxin.163.com/messaging2/server-apis/jM0MjQ2MzQ?platform=server) | 新增接口，主要用于查询指定账号的指定会话分组的会话列表。

## <span id="10.10.13 - 2025-12-10">10.10.13 (2025-12-10)</span>

**新增特性**

- 查询好友时支持查询总的好友数量。
- 新增聊天室踢人功能，在聊天室踢人时允许其他成员加入。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [分页查询好友列表](https://doc.yunxin.163.com/messaging2/server-apis/DUyNzA2OTc?platform=server) | 更新接口，返回体参数中新增 `total` 字段，表示总的好友数量。
| [聊天室踢人](https://doc.yunxin.163.com/messaging2/server-apis/DE1ODkwMDA?platform=server) | 新增接口，主要用于将聊天室成员踢出聊天室。

## <span id="10.10.12.5 - 2025-10-31">10.10.12.5 (2025-10-31)</span>

**新增特性**

普通流式消息支持高级群。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [发送流式消息](https://doc.yunxin.163.com/messaging2/server-apis/TgyMTY2NzE?platform=server) | 更新接口，请求体参数中新增 `team_option`（高级群消息功能配置项）、`target_option`（群定向消息配置项）、`thread_config`（Thread 消息配置项）字段。

## <span id="10.10.12 - 2025-10-29">10.10.12 (2025-10-29)</span>

**新增特性**

<!--客户端功能还未实现
- 新增全量用户推送功能。具体请参见 [发送全量用户推送](https://doc.yunxin.163.com/messaging2/server-apis/TcwMDA0MjU?platform=server)。
-->
- 聊天室队列抄送事件新增操作时间戳（`operationTime`）。
- 优化好友申请内部逻辑。

<!--客户端功能还未实现
**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [发送全量用户推送](https://doc.yunxin.163.com/messaging2/server-apis/TcwMDA0MjU?platform=server) | 新增接口，用于对应用内的所有用户发送系统推送。
| [查询单条系统推送](https://doc.yunxin.163.com/messaging2/server-apis/DA3MTYxMDI?platform=server) | 新增接口，用于查询单条系统推送。
| [分页查询系统推送](https://doc.yunxin.163.com/messaging2/server-apis/DQyMDE5MDE?platform=server) | 新增接口，用于批量查询系统推送。
-->

## <span id="10.10.11 - 2025-09-19">10.10.11 (2025-09-19)</span>

**新增特性**

- 支持用户信息的特殊字符校验。
- 普通流式消息现支持携带 RAG 信息。
- 优化安全通检测的内部逻辑。
- 优化查询聊天室在线固定成员功能。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [注册 IM 账号](https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server) | 更新接口，请求体中新增 `email_validation_mode` 字段，表示用户信息校验模式。0（默认）：标准校验模式；1：扩展校验模式（支持特殊字符和拉丁字符）；2：关闭校验（不推荐，可能导致显示异常）。
| [更新用户名片](https://doc.yunxin.163.com/messaging2/server-apis/TA0NzYzNjk?platform=server) | 更新接口，请求体中新增 `email_validation_mode` 字段，表示用户信息校验模式。0（默认）：标准校验模式；1：扩展校验模式（支持特殊字符和拉丁字符）；2：关闭校验（不推荐，可能导致显示异常）。
| [发送流式消息](https://doc.yunxin.163.com/messaging2/server-apis/TgyMTY2NzE?platform=server) | 更新接口，请求体参数中新增 `rag_info_list` 字段，表示流式消息中携带的 RAG 信息。

## <span id="10.10.8.5 - 2025-08-07">10.10.8.5 (2025-08-07)</span>

**升级说明**

为保证用户使用姿势不变，并持续扩展新能力，本次提供 V2.1 版本接口，在保持原有调用方式的同时，优化了返回数据结构：

- ✅ **无缝升级**：新接口在返回的 JSON 数据中扩展了部分字段，原有字段结构保持不变。
- ✅ **完全兼容**：历史 V2 接口仍可继续使用，但 **强烈建议** 迁移到新接口。
- ✅ **功能增强**：新接口提供了更丰富的数据支持，满足更多业务场景需求。

::: note note
随着业务迭代，接口返回的 JSON 数据会持续新增字段（不影响原有字段结构）。为保障接口兼容性与业务扩展性，请务必 **采用标准 JSON 解析方式**（通过字段名直接访问，而非依赖字段顺序遍历），以免因新增字段导致解析逻辑异常。标准解析方式可确保：

- 新增字段不影响现有解析逻辑。
- 无需因字段顺序变化调整代码。
- 兼容未来所有合理的字段扩展。
:::
<br>

**API 变更**

| 接口名称 | 新接口 
| --- | --- 
| [添加好友](https://doc.yunxin.163.com/messaging2/server-apis/TU5NDMzMjM?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/friends` 
| [更新好友信息](https://doc.yunxin.163.com/messaging2/server-apis/TcxMjIxMTg?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/friends/{account_id}` 
| [同意/拒绝添加好友](https://doc.yunxin.163.com/messaging2/server-apis/zAwMzgwNTU?platform=server) | `POST https://{endpoint}/im/v2.1/friends/actions/handle_friend_addition`
| [查询好友信息](https://doc.yunxin.163.com/messaging2/server-apis/DYwOTk2NjQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/friends/{account_id}` 
| [分页查询好友信息](https://doc.yunxin.163.com/messaging2/server-apis/DUyNzA2OTc?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/friends`
| [查询单条消息](https://doc.yunxin.163.com/messaging2/server-apis/DEzNTMwNTY?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/messages/{message_server_id}`
| [搜索历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zQ1MzM5NjM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/messages/actions/search_messages`
| [分页查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jcwNDA0Nzg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/messages` 
| [分页查询聊天室历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jQxNDU2MTM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/chatrooms/{room_id}/messages` 
| [根据消息 ID 查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jczMzMzMjg?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/batch_messages`
| [查询 Thread 消息](https://doc.yunxin.163.com/messaging2/server-apis/zE0MzA0NzM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/messages/actions/thread_messages`
| [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging2/server-apis/DQyMDY2MzQ?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/broadcast_notification/actions/chatroom`
| [创建会话](https://doc.yunxin.163.com/messaging2/server-apis/DgwMjAzMjM?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/conversations` 
| [查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/jUyOTA0NjM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}` 
| [批量查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/DAwNDQ0NTU?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/actions/conversation_ids`
| [分页查询用户的所有会话列表](https://doc.yunxin.163.com/messaging2/server-apis/DI2NDczOTg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations`
| [创建群组](https://doc.yunxin.163.com/messaging2/server-apis/DIwODUwMTE?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/teams` 
| [更新群组信息](https://doc.yunxin.163.com/messaging2/server-apis/jE2MTc1Mjk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/teams/{team_id}`
| [查询群组信息](https://doc.yunxin.163.com/messaging2/server-apis/DI1Nzc3MDY?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams/{team_id}` 
| [解散群组](https://doc.yunxin.163.com/messaging2/server-apis/zk0NDkwOTc?platform=server) | `DELETE https://open.yunxinapi.com/im/v2.1/teams/{team_id}`
| [批量查询群组信息列表](https://doc.yunxin.163.com/messaging2/server-apis/DAyODY4ODE?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams` 
| [分页查询群成员列表](https://doc.yunxin.163.com/messaging2/server-apis/zIxNTk1Mzc?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams/{team_id}/actions/list_members`
| [更新群成员信息](https://doc.yunxin.163.com/messaging2/server-apis/TQ4MzM2NTk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/team_members/{account_id}` 
| [分页查询指定账号已加入的群组信息](https://doc.yunxin.163.com/messaging2/server-apis/TkwODkwNTQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/team_members/{account_id}/actions/joined_teams` 
| [查询聊天室禁言列表](https://doc.yunxin.163.com/messaging2/server-apis/DE1NTg2NzQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/{room_id}/actions/chat_banned`
| [查询聊天室黑名单列表](https://doc.yunxin.163.com/messaging2/server-apis/zY2MTI1MTI?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/{room_id}/actions/blocked` 
| [查询聊天室虚构用户](https://doc.yunxin.163.com/messaging2/server-apis/TI1OTg2NDg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/actions/virtual_members`

## <span id="10.10.8 - 2025-07-17">10.10.8 (2025-07-17)</span>

**新增特性**

- 支持更新群成员信息（昵称）时配置是否通过反垃圾审核。
- 发送普通流式消息时支持配置扩展参数。
- 全文检索能力支持检索超大群消息。
<!--仅服务端支持，没上控制台
- 适配魅族消息推送分类新规则，具体请参见 [魅族消息推送分类](https://doc.yunxin.163.com/messaging/guide/DcwMjI1MTI?platform=android#消息推送分类)。
-->
<!--客户端相关
- 支持客户端删除漫游消息操作。
- 支持客户端登录时设置的环境抄送配置。
-->

**优化**

- 优化推送逻辑，相同推送 token 时，默认不重复推送。 
- 优化 OPPO 推送 `channel_id` 参数的内部逻辑。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [发送流式消息](https://doc.yunxin.163.com/messaging2/server-apis/TgyMTY2NzE?platform=server) | 更新接口，请求体中新增 `extension` 扩展参数字段。
| [更新群成员信息](https://doc.yunxin.163.com/messaging2/server-apis/TQ4MzM2NTk?platform=server)<!--V9接口<li>[修改高级群成员昵称](https://doc.yunxin.163.com/messaging/server-apis/TM0MjM1NTQ?platform=server)<li>[更新超大群成员信息](https://doc.yunxin.163.com/messaging/server-apis/TgzNTY2MjE?platform=server)<li>[修改超大群成员昵称](https://doc.yunxin.163.com/messaging/server-apis/TA0Nzc5OTg?platform=server)--> | 更新接口，请求体中新增 `antispam_config` 安全通相关配置项。

## <span id="10.10.7 - 2025-06-18">10.10.7 (2025-06-18)</span>

**新增特性**

全文检索能力支持设置检索方向。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [检索历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zQ1MzM5NjM?platform=server) | 更新接口，请求体参数中新增 `diretion` 字段，支持设置检索方向。0（默认）：从新到旧；1：从旧到新。

## <span id="10.10.6 - 2025-06-05">10.10.6 (2025-06-05)</span>

**新增特性**

- 支持消息的流式输出，通过实时分片传输内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
- 优化推送 payload 配置能力。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [发送流式消息](https://doc.yunxin.163.com/messaging2/server-apis/TgyMTY2NzE?platform=server) | 新增接口，用于发送流式消息。
| [推送 payload 配置](https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server) | 更新接口，payload 中新增 `notifyId` 字段，支持灵活选择推送通知。

<!--接口未发布，等AI产品通知
## <span id="10.10.5 - 2025-05-16">10.10.5 (2025-05-16)</span>

**新增特性**

- 支持云信 IM AI 陪聊功能。
- 支持优化提示词，创建自定义的 AI 角色。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [AI 陪聊](https://doc.yunxin.163.com/messaging2/server-apis/Dg5MzU3OTQ?platform=server) | 新增接口，用于与云信 AI 助手进行对话交互。
| [提示词优化](https://doc.yunxin.163.com/messaging2/server-apis/DYxNjA4NjY?platform=server) | 新增接口，用于优化提示词，创建自定义 AI 角色。
-->

## <span id="10.10.0 - 2025-04-18">10.10.0 (2025-04-18)</span>

**新增特性**

- 文本翻译接口适配 V10。
- 支持 AI 数字人消息的流式输出功能。
- iOS 推送支持选择推送方式（APNs 或 PushKit）。
- IM 安全通支持传递用户信息扩展字段，具体字段请参考 [网易易盾业务扩展参数](https://support.dun.163.com/documents/588434200783982592?docId=476559002902757376)。

**优化**

- 优化更新消息接口的内部逻辑。
- 优化鸿蒙推送的内部逻辑。
- 优化自定义消息反垃圾，支持视频/音频/图文类型的检测。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [文本翻译](https://doc.yunxin.163.com/messaging2/server-apis/DYxNjA4NjY?platform=server) | 新增接口，用于翻译文本消息内容。
| [设置聊天室成员角色](https://doc.yunxin.163.com/messaging2/server-apis/Dk0ODQ1NDU?platform=server) | 更新接口，将请求参数中的 `room_nick` 改为可选参数。
| [推送 payload 配置](https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server) | 更新接口，payload 中新增 `pushkitFirst` 字段，支持选择推送方式。
| [撤回/删除消息](https://doc.yunxin.163.com/messaging2/server-apis/jAwNTEzODQ?platform=server) | 更新接口，请求参数中新增 `ingore_revoke_time` 字段，表示是否忽略撤回消息的时间检测。
| [批量发送单聊消息](https://doc.yunxin.163.com/messaging2/server-apis/zgzOTE1MTI?platform=server) | 更新接口，请求参数中新增 `need_message_detail` 字段，表示是否返回消息详情。
| [设置会话置顶](https://doc.yunxin.163.com/messaging2/server-apis/jEzMTE5NTI?platform=server) | 更新接口，`top_type` 参数由查询参数变更为请求体参数。
| <li>[发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server)<li>[更新消息](https://doc.yunxin.163.com/messaging2/server-apis/DA2ODM5NTU?platform=server)<li>[发送聊天室消息](https://doc.yunxin.163.com/messaging2/server-apis/TAwMzc0NzE?platform=server)<li>[批量发送聊天室消息](https://doc.yunxin.163.com/messaging2/server-apis/TA1NTM3NzM?platform=server)<li>[发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging2/server-apis/DQyMDY2MzQ?platform=server) | 更新接口，`antispam_custom_message` 参数中新增自定义安全通检测类型新增视频/音频/图文类型（对应 type 3、4、5）的检测。
| <li>[创建会话](https://doc.yunxin.163.com/messaging2/server-apis/DgwMjAzMjM?platform=server)<li>[更新会话](https://doc.yunxin.163.com/messaging2/server-apis/zMwOTAzMTI?platform=server)<li>[查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/jUyOTA0NjM?platform=server)<li>[批量查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/DAwNDQ0NTU?platform=server)<li>[分页查询账号的所有会话列表](https://doc.yunxin.163.com/messaging2/server-apis/DI2NDczOTg?platform=server) | 更新接口，返回参数中新增 `last_read_time` 字段，表示会话最近已读时间。

## <span id="10.6.0 - 2025-03-05">10.6.0 (2025-03-05)</span>

**新增特性**

- 新增聊天室队列接口。
- 新增历史消息检索接口。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [初始化聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/TQ2NTA1Mzk?platform=server) | 新增接口，用于在指定聊天室中初始化一个队列。
| [更新聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/TY1NDI5NjI?platform=server) | 新增接口，用于在聊天室队列中添加或更新元素。
| [删除聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/DAzNjQ0NTQ?platform=server) | 新增接口，用于删除聊天室队列。
| [查询聊天室队列元素](https://doc.yunxin.163.com/messaging2/server-apis/DY4NzAwMjE?platform=server) | 新增接口，用于查询聊天室队列元素。
| [从聊天室队列中取出元素](https://doc.yunxin.163.com/messaging2/server-apis/DUwNzI2NjY?platform=server) | 新增接口，用于从聊天室队列中取出指定的元素或取出队列第一个元素。
| [检索历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zQ1MzM5NjM?platform=server) | 新增接口，用于搜索历史消息。

<!--不对外
为优化部分群组接口，本次新增以下三个接口，分别对应旧接口，旧接口已废弃，请及时进行替换。

**API 变更**

| 接口名称 | 新接口 | 原接口 |
| --- | --- | ---
| [创建群组](https://doc.yunxin.163.com/messaging2/server-apis/DIwODUwMTE?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/teams` | `POST https://open.yunxinapi.com/im/v2/teams`
| [更新群组信息](https://doc.yunxin.163.com/messaging2/server-apis/jE2MTc1Mjk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/teams/{team_id}` | `PATCH https://open.yunxinapi.com/im/v2/teams/{team_id}`
| [查询群组信息](https://doc.yunxin.163.com/messaging2/server-apis/DI1Nzc3MDY?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams/{team_id}` | `GET https://open.yunxinapi.com/im/v2/teams/{team_id}`
-->

## <span id="10.5.0 - 2025-01-17">10.5.0 (2025-01-17)</span>

**新增特性**

- 新增批量查询用户在线状态功能。
- 根据 OPPO 推送新的 [分类规则](https://open.oppomobile.com/new/developmentDoc/info?id=13189) 升级推送规则。

    OPPO 推送消息中的 Message 参数，可参考 [OPPO 推送消息示例](https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server#oppo推送消息)。

**功能优化**

优化推送内容展示规则。在群组会话中，消息的推送内容优化为：`nick+content`（消息发送者的昵称+消息内容）。

<!--bug 不对外
- 优化设置聊天室成员角色接口内部逻辑。
    禁止操作聊天室创建者角色，即不能将其他角色成员设置为创建者，也不允许将创建者设置为其他成员角色。
-->

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [批量查询用户在线状态](https://doc.yunxin.163.com/messaging2/server-apis/jU3NDkwNzY?platform=server) | 新增接口，用于批量查询指定账号的在线状态。 |
| [推送 payload 配置](https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server) | `oppoField` 中新增 `category`、`notify_level` 字段，表示 OPPO 通道类别名称和通知栏消息提醒类型。具体请参考 [OPPO 推送服务分类细则](https://open.oppomobile.com/new/developmentDoc/info?id=13189)。 |

## <span id="10.4.6 - 2025-01-08">10.4.6 (2025-01-08)</span>

**新增特性**

- 新增强制账号退出登录功能。
- 新增清空指定会话消息未读数功能。
- 新增会话置顶功能。
- 支持在发送/更新/撤回/删除消息时，配置是否验证群成员身份。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
| [强制账号退出登录](https://doc.yunxin.163.com/messaging2/server-apis/TkwNjgzNTk?platform=server) | 新增接口，用于将指定账号的登录设备强制踢下线（退出登录）。 |
| [清空指定会话未读数](https://doc.yunxin.163.com/messaging2/server-apis/Dk1OTM4MjY?platform=server) | 新增接口，用于清空指定会话的消息未读数，将指定会话的未读消息数清零。 |
| [设置会话置顶](https://doc.yunxin.163.com/messaging2/server-apis/jEzMTE5NTI?platform=server) | 新增接口，用于将指定的会话置顶。
| [发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server) | <li>请求体和响应体中新增 `message_client_id` 字段，表示消息的客户端 ID。<li>请求体中新增 `check_team_member_valid` 字段，用于配置是否在发消息时验证群成员身份。 |
| [更新消息](https://doc.yunxin.163.com/messaging2/server-apis/DA2ODM5NTU?platform=server) | 请求体中新增 `check_team_member_valid` 字段，用于配置是否在更新消息时验证群成员身份。
| [撤回/删除消息](https://doc.yunxin.163.com/messaging2/server-apis/jAwNTEzODQ?platform=server) | 请求体中新增 `check_team_member_valid` 字段，用于配置是否在撤回/删除消息时验证群成员身份。

## <span id="10.4.5 - 2024-12-18">10.4.5 (2024-12-18)</span>

**新增特性**

- 新增 Thread 消息查询功能。
- 新增快捷评论功能。

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
[查询 Thread 消息](https://doc.yunxin.163.com/messaging2/server-apis/zE0MzA0NzM?platform=server) | 新增接口，用于根据 Thread 根消息分页查询 Thread 消息列表。 |
[添加快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/zg1ODU4ODc?platform=server) | 新增接口，用于对指定的消息添加一条快捷评论。 |
[删除快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/jU4MjMwMTE?platform=server) | 新增接口，用于对指定的消息删除一条快捷评论。 |
[查询快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/DYwMTA5MTI?platform=server) | 新增接口，用于查询指定消息的快捷评论。 |
[根据消息 ID 查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zk4MTcxNDg?platform=server) | 新增接口，用于根据消息 ID 批量查询历史消息。 |
[发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server) | 请求体中新增 `thread_config` 字段，用于实现 Thread 功能。 |
[查询单条消息](https://doc.yunxin.163.com/messaging2/server-apis/DA2NjA2OTk?platform=server) | 响应体中新增 `thread_config` 字段，返回 Thread 消息相关信息。 |
[分页查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zMyNzU2MjA?platform=server) | 响应体中新增 `thread_config` 字段，返回 Thread 消息相关信息。 |

## <span id="10.4.0 - 2024-08-21">10.4.0 (2024-08-21)</span>

**新增特性**

- 新增群定向消息功能。发送群消息时，可以指定接收消息的群成员列表。
- 新增更新消息功能。
- 发布订阅接口适配 V10。
- 新增清空会话历史和漫游消息功能。
- 快捷回复和进出聊天室事件抄送类型增加抄送字段。

<!--内部不对外
- 新增获取文件上传账号功能，根据文件地址反查原始上传的用户账号。
-->

**API 更新**

| 接口 | 变更 |
| ---- | ---- |
[更新消息](https://doc.yunxin.163.com/messaging2/server-apis/DA2ODM5NTU?platform=server) | 新增更新消息接口，用于实现消息的二次编辑能力。 |
[订阅在线状态事件](https://doc.yunxin.163.com/messaging2/server-apis/zI4NjY1NzA?platform=server) | 新增接口，用于订阅指定用户的在线状态事件。 |
[取消在线状态事件的订阅](https://doc.yunxin.163.com/messaging2/server-apis/zUwMTY3Mzg?platform=server) | 新增接口，用于取消在线状态事件的订阅。 |
[查询订阅的在线状态事件](https://doc.yunxin.163.com/messaging2/server-apis/jU4MjMwMTE?platform=server) | 新增接口，用于查询指定用户订阅的有效在线状态事件。 |
[清空会话中的漫游和历史消息](https://doc.yunxin.163.com/messaging2/server-apis/Tc1MTIyMDg?platform=server) | 更新接口，新增清空会话历史消息功能。 |
[圈组快捷评论抄送](https://doc.yunxin.163.com/messaging/server-apis/zQ0NTQ4NTk?platform=server#80-圈组快捷评论抄送) | 抄送字段新增：`msgType`（消息类型），`Integer` 类型。默认不开通，需要单独申请。 |
[聊天室成员进出聊天室事件抄送](https://doc.yunxin.163.com/messaging/server-apis/TcxNzU4NzU?platform=server#聊天室成员进出聊天室事件抄送) | 抄送新增字段：`ext`（扩展字段），`String` 类型。新应用（AppKey）默认开通，历史应用（AppKey）需要单独申请。 |
[发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server) | 新增 `target_option` 字段，用于实现群定向消息功能，并新增定向消息相关错误码。 |

<!--内部不对外
[获取文件上传账号]() | 新增接口，通过文件地址反差原始上传文件的用户账号。 |
-->

## <span id="10.3.1 - 2024-07-31">10.3.1 (2024-07-31)</span>

新增聊天室 AI 数字人相关 API。

| 接口 | 变更 |
| ---- | ---- |
[发送聊天室消息](https://doc.yunxin.163.com/messaging2/server-apis/TAwMzc0NzE?platform=server) | 新增 `ai_params` 字段。 |

## <span id="10.2.3 - 2024-03-20">10.3.0 (2024-07-04)</span>

新增 AI 数字人相关接口设定。数字人配置请参考 [开通和添加数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。

| 接口 | 变更 |
| ---- | ---- |
[发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server) | 新增 `ignore_member_chat_banned`、`ignore_member_chat_banned`、`ai_params` 字段。 |
[IM 会话相关抄送](https://doc.yunxin.163.com/messaging/server-apis/DI3OTg5Mjg?platform=server) | 新增 `aiParams` 数字人消息相关回执。 |
[消息抄送服务概述](https://doc.yunxin.163.com/messaging/server-apis/jQ4ODE0NTY?platform=server#IM%20%E4%BC%9A%E8%AF%9D%E6%B6%88%E6%81%AF) | 新增数字人会话消息抄送和回调 `eventType`。 |

## <span id="10.2.3 - 2024-03-20">10.2.3 (2024-03-20)</span>

- 华为推送升级至 V3 版本。
- 优化安全通关于同步检测超大图的超时逻辑，超时后发起异步检测请求。

## <span id="10.2.0 - 2024-01-26">10.2.0 (2024-01-26)</span>

发布全新的网易云信 IM 服务端开放 API 接口，适配 10.x.x 系列 IM 服务端接口和客户端接口。

**新版 OpenAPI 架构全新升级：**

- 采用 Restfull API 规范，所有接口遵循规范实现，详细调用请参考 [API 调用方式](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server)。
- OpenAPI 与 SDK 端的数据名称定义保持一致。
- 新增云端会话功能和云端会话分组功能。

    - **云端会话功能**：会话状态云端管理，保障客户端的一致性，随时获取会话状态。
    - **云端会话分组**：会话可以按需分组，重点会话特别分组关注。

- 新版 API 移除不合理的接口，或调整对应实现，使接口更通用。

    - 合并部分接口。
    - 老版本单个接口对多个场景的使用，拆分为多个接口。

- 相较于 [9.x.x 系列版本 API](https://doc.yunxin.163.com/messaging/server-apis/DI5ODYxMTg?platform=server)，新版本接口功能基本一致。新旧版本 API 的对应关系请参考 [API 概览](https://doc.yunxin.163.com/messaging2/server-apis/DUzNjAzMTc?platform=server)。

**新旧版本接口变更：**

新旧版本接口在聊天室成员角色分类与操作逻辑上有以下区别，

旧版 | 新版
---- | ----
黑名单用户为固定成员，移除黑名单后变为游客身份。 | 对聊天室成员执行拉黑/解除拉黑操作，聊天室成员角色不变。
永久禁言用户为固定成员，解除永久禁言后变为游客身份。 | 对聊天室成员执行禁言/接触禁言操作，聊天室成员角色不变。
创建的虚构用户（聊天室机器人）默认为游客身份。 | 创建的虚构用户的身份单独为一类，角色身份中新增虚构用户类。

:::note note
- 客户端与服务器建议使用同版本，SDK 2.0（V10）接口配套 API 2.0 接口。
- 关于聊天室成员角色分类与操作的接口，避免新老接口的混用。
:::