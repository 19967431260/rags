<!--keywords: 更新日志,新增,修改,更新 -->

本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）稳定版 iOS 端 v9.x.x 及以下版本的更新日志。有关 v10.x.x 开发版，请参考《IM 即时通讯 V10》[iOS 更新日志](https://doc.yunxin.163.com/messaging2/concept/TIxNTgxOTk)。

:::details 单击展开了解什么是稳定版，以及与开发版的区别。

稳定版基于 [开发版](https://doc.yunxin.163.com/messaging2/concept/TIxNTgxOTk?platform=client)，可满足常见 IM 应用业务场景，但更注重稳定性。开发版则主要是在可商用的基础上，提供新功能与特性。

稳定版相较开发版，在更长周期内获得了更多用户的验证，且修复了多个历史版本的已知问题，稳定性保障更佳。
:::

## 9.21.10 (2026-01-30)

**新增特性**

支持在初始化时配置聊天室默认 Link 地址。在聊天室中启用 LBS，但 LBS 均不可用时，将使用设置的默认 Link 地址进行连接。

::: details 单击查看配置示例
```
- (void)setChatroomLinkList
{
    // 在初始化 SDK 前设置
    NIMServerSetting *setting = [[NIMServerSetting alloc] init];
    // 原来的初始化设置代码
    ...
    // 增加聊天室默认地址设置
    setting.chatroomLinkList = @[
        //国内Link地址
        @"chatlink-cn.yunxinfw.com:443"
        //海外Link地址
        //@"chatlink-sg.yunxinfw.com:443"
    ];
    NIMSDK.sharedSDK.serverSetting = setting;
}
```
:::
  
**接口更新**

| 接口 | 说明 |
| ---- | ---- |
| `NIMServerSetting.chatRoomLinkList` | 新增字段，表示聊天室默认 Link 地址。

**优化**

内部优化。

## 9.21.0 (2025-12-22)

**新增功能**

- API 普通流式消息支持高级群。
- 普通流式消息现支持携带 RAG 信息，增强 AI 交互能力。

**优化**

- 优化群成员更新逻辑。
- 优化解析聊天室通知中的成员信息逻辑。
- 流式过程中查询消息时补齐消息完整内容。
- 搜索消息时限制查询的消息数量，避免消息内存占用过大的问题。

## 9.20.18 (2025-12-02)

全文检索性能优化。

## 9.20.17 (2025-11-14)

修复已知问题。

## 9.20.16 (2025-09-28)

**新增功能**

- 点对点文本支持普通流式消息。
- 底层连接优化以及其他内部优化。

## 9.20.15 (2025-08-26)

**新增功能**

新增消息的二次编辑能力。

**接口变更**

| 接口 | 说明 |
| ---- | ---- |
| [`modifyMessage`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#ad31e48935fc32710405819bb01cf7964) | 新增接口，用于用于实现消息的二次编辑能力。 |

## 9.20.13 (2025-07-24)

优化 NOS 上传 Token 管理机制，解决可能存在的 token 重用问题。频繁发送图片、视频等多媒体内容时，提高文件上传的安全性和稳定性。

## <span id="[9.20.12] - 2025-06-16">9.20.12 (2025-06-16)</span>

内部优化。

## <span id="[9.20.10] - 2025-04-18">9.20.10 (2025-04-18)</span>

- 针对 AI 大模型生成的消息，新增了流式效果输出功能，使消息内容能够逐步展示。
- 同时，新增了 AI 流式代理功能，用于更高效地管理和控制消息流的输出。

## <span id="9.19.14 (2025-04-14)">9.19.14 (2025-04-14)</span>

内部优化。

## <span id="9.19.11 (2025-03-18)">9.19.11 (2025-03-18)</span>

内部优化。

## <span id="9.19.10 (2025-02-20)">9.19.10 (2025-02-20)</span>

内部优化。

## <span id="[9.19.4] - 2024-12-27">9.19.4 (2024-12-27)</span>

修复融合存储相关问题。

## <span id="[9.19.3] - 2024-12-11">9.19.3 (2024-12-11)</span>

提升网络联通率与稳定性，支持 QUIC 能力。

## <span id="[9.19.2] - 2024-11-20">9.19.2 (2024-11-20)</span>

- 提升网络连接稳定性。
- 修复偶现崩溃问题。

## <span id="[9.19.0] - 2024-10-15">9.19.0 (2024-10-15)</span>

新增 AI 数字人功能。详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client) 。

## <span id="[9.18.1] - 2024-09-18">9.18.1 (2024-09-18)</span>

网络链接优化。

## <span id="[9.18.0] - 2024-09-04">9.18.0 (2024-09-04)</span>

- 提升网络稳定性。
- 内部多项优化。

## <span id="[9.17.0 - 2024-07-04">9.17.0 (2024-07-04)</span>

**新增特性**

- 新增圈组临时禁言功能，具体请参考 [圈组临时禁言](https://doc.yunxin.163.com/messaging/guide/DEzMDIyOTk?platform=iOS)。
- 新增圈组频道分组自定义排序能力，具体请参考 [搜索服务器和频道（频道分组）](https://doc.yunxin.163.com/messaging/guide/jI1MzQyMDA?platform=iOS)。
- 新增圈组查询未在频道分组下的频道信息能力，具体请参考 [频道管理](https://doc.yunxin.163.com/messaging/guide/zYxNzM0Nzg?platform=iOS#分页查询未在频道分组下的频道)。

**性能优化**

- 推出最新稳定版，整体性能和稳定性进一步提升。
- 跨平台支持增强，支持 XCFramework 打包。
- 圈组插件化，可根据需求灵活加载，提升应用的定制性和响应速度。

    若需要使用圈组能力，除了需要引入 NIMSDK，还需要单独引入 NIMSDK/QChat，具体请参考 [集成 SDK](https://doc.yunxin.163.com/messaging/guide/TI1NTAzNTk?platform=iOS)。
- 存储上传稳定性提升，显著提高文件传输的稳定性和可靠性。
- 多项内部优化，进一步提升性能。

**API 新增**

方法/回调/类 | 说明
---- | ----
`NIMQChatServerManager.mute ` | 在指定圈组服务器中对指定成员进行临时禁言或解除临时禁言。
`NIMQChatServerManager.getMuteMemberByPage` | 在指定圈组服务器中分页查询被临时禁言的成员列表。
`NIMQChatChannelManager.mute` | 在指定频道中对指定成员进行临时禁言或解除临时禁言。
`NIMQChatChannelManager.getMuteMemberByPage` | 在指定频道中分页查询被临时禁言的成员列表。
`getUncategorizedChannelsByPage` | 分页查询当前服务器中不在频道分组下的频道列表。
`NIMQChatChannelCategory` | 频道分组对象新增 `reorderWeight` 字段，表示自定义排序标识，在分页查询频道分组时可根据该字段进行自定义排序。
`getCategoriesInServerByPage` | 查询频道分组列表接口的入参中新增 `sortType`（排序类型）和 `cursor` （分页）字段，可设置排序类型实现 **按自定义权重排序** 查询频道分组。

## <span id="[9.16.5 - 2024-05-30">9.16.5 (2024-05-30)</span>

优化文件上传逻辑，提升上传稳定性。

## <span id="[9.16.4 - 2024-05-24">9.16.4 (2024-05-24)</span>

修复圈组登录相关问题。

## <span id="[9.16.3 - 2024-05-21">9.16.3 (2024-05-21)</span>

优化 `NIMSDKConfig.shouldCountTeamNotification` 方法，支持配置包括超大群在内的群通知是否计入未读数。

## <span id="[9.16.1 - 2024-04-29">9.16.1 (2024-04-29)</span>

内部优化。

## <span id="[9.16.0 - 2024-04-16">9.16.0 (2024-04-16)</span>

**新增特性**

- 支持按群成员类型分页查询群成员列表。
- 支持添加特别关注群成员列表。
- 新增鸿蒙终端类型的解析。
- 圈组支持根据身份组优先级获取成员身份组列表。
- IM iOS SDK 中新增 PrivacyInfo.xcprivac 隐私文件，兼容苹果公司的隐私更新。

**API 新增**

方法/回调/类 | 说明
---- | ----
`getTeamMemberList` | 根据群成员类型获取成员列表。
`addTeamMembersFollow` | 在群组中添加需要特别关注的群成员。
`removeTeamMembersFollow` | 在群组中移除特别关注的群成员。
`getExistingAccidsInServerRole` | 根据身份组优先级获取成员身份组列表。

**API 变更**

方法/回调/类 | 说明
---- | ----
`NIMLoginClientType` | 新增 HarmonyOS 客户端，多端登录支持鸿蒙客户端类型的解析。

## <span id="[9.15.2 - 2024-04-11">9.15.2 (2024-04-11)</span>

NIM iOS SDK 中新增 PrivacyInfo.xcprivac 隐私文件，兼容苹果公司的隐私更新。具体导入方式请参考 [苹果隐私策略说明](https://doc.yunxin.163.com/messaging/guide/TM5ODM1NDQ?platform=iOS)。

## <span id="[9.15.1 - 2024-03-06">9.15.1 (2024-03-06)</span>

修复已知问题。

## <span id="[9.15.0 - 2024-01-31">9.15.0 (2024-01-31)</span>

**新增特性**

- 支持分页查询指定圈组消息下的某一快捷评论类型的所有用户信息，具体请参考 [圈组快捷评论](https://doc.yunxin.163.com/messaging/guide/TQxODgzNTg?platform=iOS#查询指定快捷评论类型的所有用户信息)。
- 支持圈组本地缓存能力，为方便用户按需存储圈组消息草稿，可以向本地数据库插入文本消息，同时可删除和查询该缓存消息，具体请参考 [插入本地圈组消息草稿](https://doc.yunxin.163.com/messaging/guide/TM3ODI4ODE?platform=iOS)。
- 支持将发送失败的消息自动缓存到本地，可通过查询圈组历史消息（`getMessageHistory`）时选择是否包含发送失败（`includeLocalMessages`）的消息实现，具体请参考 [查询历史消息](https://doc.yunxin.163.com/messaging/guide/DA1NDA5NDk?platform=iOS)。

**API 新增**

方法/类/枚举 | 说明
---- | ----
[`getCommentators`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d9c/protocol_n_i_m_q_chat_message_extend_manager-p.html#a57d51d2ce7307da0b655dbf2ba390398) | 新增接口，用于分页查询指定圈组消息下的某一快捷评论类型的所有用户信息。
[`insertOrReplaceTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a93cd2acf8c2dfb450db838267c450e3e) | 新增接口，用于向本地数据库插入一条缓存数据，如果该频道下已经存在数据，则被新数据覆盖。
[`deleteTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a97ba0878d85bf8e1cad54b45e9d0bada) | 新增接口，用于删除圈组本地缓存数据。
[`getTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#aadc6042ebab626308519b60b0513cd8d) | 新增接口，用于查询圈组本地缓存数据。
[`getMessageHistory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a0f2048e59a206134994e73fbe2e26763) | 该方法的入参 [`NIMQChatGetMessageHistoryParam`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d7/d3e/interface_n_i_m_q_chat_get_message_history_param.html) 新增 `includeLocalMessages` 字段，表示是否查询发送失败的圈组消息。

## <span id="[9.14.2 - 2024-01-15">9.14.2 (2024-01-15)</span>

内部优化。

## <span id="[9.14.1 - 2023-12-06">9.14.1 (2023-12-06)</span>

内部逻辑优化。

## <span id="[9.14.0 - 2023-11-10">9.14.0 (2023-11-10)</span>

登录和消息发送逻辑优化。

## <span id="[9.13.1 - 2023-10-25">9.13.1 (2023-10-25)</span>

内部优化。

## <span id="[9.12.1 - 2023-08-01">9.12.1 (2023-08-01)</span>

- `NIMSDKConfig` 新增 `reportIgnoredMessage` 字段，支持配置是否上报被过滤的消息。
- 修复海外用户发送图片失败的问题。

## <span id="[9.12.0 - 2023-07-07">9.12.0 (2023-07-07)</span>

**新增特性**

圈组订阅机制支持自动订阅。开启自动订阅后，当用户登录到圈组服务器，无需手动订阅服务器或频道，进入服务器或频道时即可收到消息、事件和系统通知，退出时则自动取消订阅。具体请参考 [圈组订阅机制](https://doc.yunxin.163.com/messaging/guide/zAxNjQzMDA?platform=iOS)。

**优化**

优化第三方回调登录内部逻辑，具体请参考 [通过第三方回调登录 IM](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS#通过第三方回调登录)。

**修复**

本次版本修复以下问题：

- 当批量将会话消息未读数清零（标记已读）时，会话数量过大导致报错。
- 当会话未读数为 0 时，调用 `markAllMessagesReadInSession:completion:` 未触发 completion 回调。
- 添加圈组快捷评论时报 syntax error 错误。

**API 变更**

API | 说明
---- | ----
`NIMQChatConfig#autoSubscribe` | 新增圈组自动订阅开启/关闭参数。
`NIMSDKConfig#reconnectInBackgroundStateDisabled` | 废弃该接口，即不支持配置退至后台的重连策略。<note type=note>网易云信使用退至后台仍允许重连的策略。</note>

## <span id="[9.11.2 - 2023-06-20">9.11.2 (2023-06-20)</span>

- 修复使用 NOS 上传文件，取消上传时崩溃的问题。
- 修复 S3 优发送图片消息，长时间无回应的问题。
- 修复上传文件失败重试，延迟时间过大的问题。
- 修复其他已知问题。

## <span id="[9.11.0 - 2023-05-31">9.11.0 (2023-05-31)</span>

**新增特性**

- 支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动，具体请参考 [接入第三方机器人](https://doc.yunxin.163.com/messaging/guide/Tg5NzQ1NTQ?platform=iOS)。

- 新增第三方回调动态登录模式，具体请参考 [登录 IM](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS)。

- 新增数据准备完成的回调，具体请参考 [监听数据准备完成事件](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS#监听数据准备完成事件)。

**修复**

- 修复用户频繁登录时发生报错的问题。
- 修复调用 `udpateStickTopSession` 更新置顶会话扩展信息未生效的问题。
- 修复其他已知问题。

**API 变更**

API | 说明
---- | ----
`onDataReady` | 新增数据准备完成回调接口，当消息数据库开启完成后，通知用户数据已准备完成，可以开始发送消息。
`dynamicLoginExtForAccount:` | 新增获取 IM 动态登录扩展信息，用于实现通过第三方回调动态登录 IM。
`dynamicChatRoomTokenForAccount:` | 新增获取聊天室动态 Token，用于实现通过动态 Token 登录聊天室。
`dynamicChatRoomLoginExtForAccount:` | 新增获取聊天室动态登录扩展信息，用于实现通过第三方回调动态登录聊天室。
`fetchQuickComments:completion:` | 获取圈组快捷评论接口返回的数据中新增快捷评论的创建时间，即 `NIMQChatMessageQuickCommentsDetail` 中新增获取评论创建时间的接口（`createTime`）。
`NIMMessage` | 消息体中新增机器人信息字段（`robotInfo`），用于实现机器人消息功能。

## <span id="[9.10.1 - 2023-04-20">9.10.1 (2023-04-20)</span>

修复已知问题。

## <span id="[9.10.0 - 2023-04-11">9.10.0 (2023-04-11)</span>

**API 变更**

初始化参数 `NIMSDKConfig` 中新增 `fixMsgStatusByBlackList` 配置项，默认关闭。开启后，消息状态是否成功需要结合 `isInBlockList`（通过解析消息体得到该字段）进行判断：
- 同步接收到的消息，如果 `isInBlockList==true`，则消息状态修改为 failed。
- 查询云端历史消息，如果 `isInBlockList==true`，则消息状态修改为 failed。

**优化**

- 优化内部拉黑后的消息重发逻辑，具体请参考 [消息重发](https://doc.yunxin.163.com/messaging/guide/TQzMzM5NTg?platform=iOS#%E9%87%8D%E5%8F%91%E6%B6%88%E6%81%AF%E7%9B%B8%E5%85%B3)。
- 优化定义圈组频道未读信息的 [`NIMQChatUnreadInfo`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d6b/interface_n_i_m_q_chat_unread_info.html) 类，补充缺失字段。
- 优化圈组订阅回调机制。（订阅圈组服务器/频道后，只有未读数变更时才触发回调。）

**问题修复**

- 修复获取本地历史记录传入 order 无效的问题。
- 修复卡顿问题。
- 修复其他已知问题。

## <span id="[9.9.2 - 2023-03-09">9.9.2 (2023-03-09)</span>

**新增特性**

新增 **[圈组](https://doc.yunxin.163.com/messaging/concept/jUyODc1NDM?platform=client) 用户资料复用 IM 用户资料** 的能力。

- 如果某用户未配置自己的 [服务器](https://doc.yunxin.163.com/messaging/guide/DU5NDExNzU?platform=iOS) 成员信息，该用户进入服务器后的初始成员信息将直接复用对应的 IM 用户资料（目前仅支持复用昵称和头像）。

- 如果某用户在未配置自己的服务器成员信息的情况下修改了自己的 IM 用户资料（昵称或头像），系统通知（通知类型 `NIMQChatSystemNotificationTypeMyMemberInfoUpdated`）将触发，通知该用户需要在哪些服务器重新获取资料。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| `createTeam:completion:` | 创建群组的新接口 <note type=notice>原创建群接口 [`createTeam:users:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aa451717d26bc70053da5820453952daa) 已废弃。</note> |

**数据结构变更**

- [圈组](https://doc.yunxin.163.com/messaging/concept/jUyODc1NDM)的系统通知类型 [`NIMQChatSystemNotificationType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/ddd/_n_i_m_q_chat_defs_8h.html#a68eb284bba17219f9f003e57d5ae414b)中新增枚举 `MY_MEMBER_INFO_UPDATED`，表示修改 IM 用户资料触发的圈组服务器成员信息的联动修改。该系统通知的具体触发条件、接收者和接收条件，请参考 [圈组系统通知概述](https://doc.yunxin.163.com/messaging/server-apis/TkxMzc1NDg?platform=server)中对 `USER_INFO_UPDATE(35) ` 的说明。

- 圈组系统通知的投递对象类型 [`NIMQChatSystemNotificationToType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/ddd/_n_i_m_q_chat_defs_8h.html#a8ea996c7fd86ba0b6a997387c63c0aa2) 新增枚举值 `NIMQChatSystemNotificationToTypeAccids`，表示发送给指定的用户。

**问题修复**

部分已知问题修复与优化。

## <span id="[9.9.0 - 2023-02-09">9.9.0 (2023-02-09)</span>

**新增特性**

SDK 支持查询指定频道中@当前用户的未读消息，同时也支持批量查询消息是否@当前用户。具体请参考 [查询@我的消息](https://doc.yunxin.163.com/messaging/guide/Tg5ODExMjE?platform=iOS)。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`getMentionedMeMessages:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#ae2e47b62c3db9b7fbf314b4b64c9953c) | 查询指定频道中@当前用户的未读消息 |
| [`areMentionedMeMessages:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a6fcfec3a53ba2e355d15401d744e01d5) | 批量查询消息是否@当前用户 |

**优化**

- 优化内部索引，解决获取本地历史消息记录查询慢的问题。
- 修复由于聊天室消息收发引起的卡顿问题。
- 修复 [` checkPermissions:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a70d6e567fdea268dd11469751a6da362) 接口在 swift 环境调用产生崩溃的问题。
- 修复其他已知问题。

## <span id="[9.8.0 - 2022-12-27">9.8.0 (2022-12-27)</span>

该版本的圈组模块新增了游客功能。

**新增特性**
 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
--- | --- | --- | ---
1 | 游客功能 | 以游客身份进入服务器，可查询部分信息和接收消息，也可接收部分系统通知 | [游客功能](https://doc.yunxin.163.com/messaging/guide/jMyMTQ2OTU?platform=iOS)
2 | 频道对游客的可见性 | 创建和修改频道时可设置频道是否对游客可见 | [频道管理](https://doc.yunxin.163.com/messaging/guide/zYxNzM0Nzg?platform=iOS)
3 | 频道分组对游客的可见性 | 如果频道对游客可见，则包含该频道的频道分组也对游客可见，且频道分组的查看模式变更可能导致频道对游客的可见性变更 | [频道分组](https://doc.yunxin.163.com/messaging/guide/zY5Mzg5MTA?platform=iOS)
4 | 频道可见性变更系统通知 | 新增系统通知类型 `NIMQChatSystemNotificationTypeVisitorChannelVisibilityUpdate`，表示频道对游客的可见性发生变更 | [游客可接收的系统通知](https://doc.yunxin.163.com/messaging/guide/jMyMTQ2OTU?platform=iOS#可接收的系统通知)

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`enterAsVisitor:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#aea998e3762c6c913270cb3989673299f) | 以游客身份进入服务器 |
| [`leaveAsVisitor:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a7c79f19559990829bbeba14b48d30692) | 以游客身份离开服务器 |
| [`NIMQChatChannelManager#subscribeAsVisitor:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a2d77e785dc8db4f9fa74b8f01a648ae0) | 以游客身份订阅频道 |
| [`NIMQChatServerManager#subscribeAsVisitor:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a27911bcc6be2cb08d894c3503cf99627) | 以游客身份订阅服务器 |

**变更 API**

| <div style="width:150px">API</div> | API 说明 | 变更说明 |
| --- | --- | ---- |
| [`createChannel:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ab496ffeebbeb568bcff924918026075d) | 创建频道 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |
| [`updateChannel:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#aeb8aece70850d5f574d892cbc3be6d12) | 修改频道信息 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |

**问题修复**

修复部分已知问题。

## <span id="[9.7.0 - 2022-12-2">9.7.0 (2022-12-2)</span>

**新增特性**
IM 新增动态查询连续完整的历史消息功能，具体请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS#动态查询某段时间内的历史消息)。

相较于频繁从云端获取，该查询方法在保证历史消息完整的同时，减少了耗时和耗能。

**API 新增**
API | API 说明
---- | ----
[`getMessagesDynamically:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#acdb9b2c4e4c3127c2c2d55728eba4640) | 动态查询连续完整的历史消息

<p hidden="hidden">
API 变更
API | API 说明
---- | ----
`queryCollect` | 入参新增 `allType` 参数，表示查询所有收藏类型，若设为 YES，将忽略已设置的 `type` 属性，返回所有的收藏类型
</p>

**修复**

修复已知问题。

## <span id="[9.6.3 - 2022-10-27">9.6.3 (2022-10-27)</span>

**新增特性**

v9.6.3 的聊天室模块，新增根据标签（Tags）查询聊天室历史消息的功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging/guide/zAzNzk3MTg?platform=iOS#根据标签查询历史消息" target="_blank">根据标签查询历史消息</a>。

**API 新增**

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
| --- | --- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a35290fa5a9b593a070bb8383e6ca2112" target="_blank">`getMessagesByTags`</a> | 通过聊天室标签（可多个）来检索聊天室历史消息 |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d8/d34/protocol_n_i_m_chatroom_manager_delegate-p.html#afa50c2041f1b6ea582b71482182f47e7" target="_blank">`tagsUpdate`</a> | 监听聊天室标签变更事件，回调包含变更标签的聊天室 ID 和变更后的标签信息 |

**API 变更**
| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
| --- | --- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/df3/interface_n_i_m_message.html" target="_blank">`NIMMessage`</a> | 消息结构体中新增 `rawAttachContent` 参数，表示消息附件的字符串内容 |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d21/interface_n_i_m_q_chat_message.html" target="_blank">`NIMQChatMessage`</a> | 圈组消息结构体中新增 `rawAttachContent` 参数，表示圈组消息附件的字符串内容 |

## <span id="[9.6.1 - 2022-10-12">9.6.1 (2022-10-12)</span>
- 修复 `getChannelMembersByPage:` 方法参数校验错误的问题。
- 修复 iOS 进程退出过程中系统 HTTP 请求应答处理过程崩溃的问题。
- 其他已知问题修复。

## <span id="[9.6.0 - 2022-9-26">9.6.0 (2022-9-26)</span>

::: note notice
v9.6.1 修复了 v9.6.0 可能导致线上崩溃的问题。如果您目前使用的是 v9.6.0，强烈建议您升级至 v9.6.1。
:::

**新增特性**

 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
--- | --- | --- | ---
1 | @身份组 | 支持在圈组发送消息时@指定身份组 | <a href="https://doc.yunxin.163.com/messaging/guide/zM0OTk2NDM?platform=iOS" target="_blank">圈组消息收发</a>
2 | 身份组自定义权限 | 支持通过服务端 API 为身份组添加自定义权限项，帮助开发者快速实现符合自身业务需求的权限管控能力 | <a href="https://doc.yunxin.163.com/messaging/guide/TU1NTA4NzM?platform=iOS" target="_blank">自定义权限</a>
3 | 高级群禁言模式 | 新增高级群禁言模式，可以选择是否禁言群主和管理员 | <a href="https://doc.yunxin.163.com/messaging/guide/jc2NzI5MTY?platform=iOS#群组全员禁言" target="_blank">群组全员禁言</a>

**API 变更**

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> | 变更说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a24452d81b713fb77b6704dcf55521b7b" target="_blank">`sendMessage:toSession:error:`</a> | 在圈组的频道中发送消息 | `NIMQChatMessage` 新增参数 `mentionedRoleidList`，可指定消息发出时需要@的身份组
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a15fb23ede995f9695a134a6d38895a02" target="_blank">`sendMessage:toSession:completion:`</a> | 在圈组的频道中发送消息（异步） | `NIMQChatMessage` 新增参数 `mentionedRoleidList`，可指定消息发出时需要@的身份组 |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a45583fc4bfd523b42dad6bfe5841422f" target="_blank">`updateServerRole:completion:`</a> | 修改服务器身份组 | <ul><li>可配置的权限项新增**@身份组**（`NIMQChatPermissionTypeMentionedRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）<li>身份组权限项在 `NIMQChatPermissionStatusInfo` 中定义，新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo`</li></ul> |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa3b921324fcfd5f2c74282b87d1985d0" target="_blank">`updateChannelRole:completion:`</a> | 修改频道身份组 | <ul><li>可配置的权限项新增**@身份组**（`NIMQChatPermissionTypeMentionedRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）<li>身份组权限项在 `NIMQChatPermissionStatusInfo` 中定义，新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo`</li></ul> |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa5c228755b6b39f5abb8f3a69ee1b89a" target="_blank">`updateChannelCategoryRole:completion:`</a> | 修改频道分组身份组 | <ul><li>可配置的权限项新增**@身份组**（`NIMQChatPermissionTypeMentionedRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）<li>身份组权限项在 `NIMQChatPermissionStatusInfo` 中定义，新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo`</li></ul> |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a105aa80f83b29115f06c87f577c6b601" target="_blank">`updateChannelCategoryMemberRole:completion:`</a> | 修改频道分组用户定制权限 | <ul><li>可配置的权限项新增**@身份组**（`NIMQChatPermissionTypeMentionedRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）<li>身份组权限项在 `NIMQChatPermissionStatusInfo` 中定义，新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo`</li></ul> |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#af1cac765662f98ef9b1834d043d981db" target="_blank">`updateMemberRole:completion:` | 修改（频道下的）用户定制权限 | <ul><li>可配置的权限项新增**@身份组**（`NIMQChatPermissionTypeMentionedRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）<li>身份组权限项在 `NIMQChatPermissionStatusInfo` 中定义，新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo`</li></ul> |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a70d6e567fdea268dd11469751a6da362" target="_blank">`checkPermissions:completion:` | 查询自己是否拥有某些权限 | 新增支持查询自定义权限。如果已通过服务端 API 创建自定义权限，则 `NIMQChatPermissionStatusInfo` 权限列表新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo` |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#ab97fabe19389fc714c0d5ce7d32c4d1d" target="_blank">`checkPermission:completion:` | 查询自己是否拥有某个权限 | 新增支持查询自定义权限。如果已通过服务端 API 创建自定义权限，则 `NIMQChatPermissionStatusInfo` 权限列表新增自定义权限项 `customType`（int 类型，value 大于或等于 10000）。`NIMQChatPermissionStatusInfo` 兼容原先的 `NIMQChatPermissionType`，但后者即将废弃，建议将其替换为 `NIMQChatPermissionStatusInfo` |
| `NIMTeamAllMuteMode` | 高级群禁言模式 | 新增高级群配置项，具体请参考 <a href="https://doc.yunxin.163.com/messaging/guide/jc2NzI5MTY?platform=iOS#群组全员禁言" target="_blank">群组全员禁言</a>。

**优化改进**

- 减小 SDK 包体积并优化 SDK 集成流程，具体请参考 <a href="https://doc.yunxin.163.com/messaging/guide/TI1NTAzNTk?platform=iOS" target="_blank">集成</a>。
- 适配 iOS 16 系统。

## <span id="[9.5.2 - 2022-9-7">9.5.2 (2022-9-7)</span>

修复断网场景下进行数据上报引起的崩溃问题。

## <span id="[9.5.0 - 2022-8-29">9.5.0 (2022-8-29)</span>

**新增特性**

- 圈组模块新增搜索频道成员功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging/guide/jI1MzQyMDA?platform=iOS" target="_blank">搜索服务器和频道</a>。
- 支持配置消息缩略图尺寸。

**优化改进**
优化 LBS 策略。

**API 变更**

V9.5.0 引入了如下新增 API 和 变更 API。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a30adc65906c8225daa8fc73d12193eba" target="_blank">`searchServerChannelMember`</a> | 搜索频道成员 |

**变更 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html" target="_blank">`NIMSDKConfig`</a> | 初始化配置接口新增 `thumbnailSize` 参数，用于配置缩略图的尺寸。 |

## <span id="[9.4.0 - 2022-8-8">9.4.0 (2022-8-8)</span>

**新增特性**

V9.4.0 的圈组模块新增如下特性：

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 批量查询权限 | 支持查询自己是否拥有某些权限 | [查询自己是否拥有某些权限](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zg0Nzc3Mzg?platformId=60278#查询自己是否拥有某些权限) |
| 2 | 订阅圈组服务器下所有频道及清空服务器未读消息数 | 支持订阅服务器所有频道的消息，且支持清空服务器未读数 | [获取服务器未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Dc5MzYxNDU?platformId=60278) |
| 3 | 搜索消息 | 支持分页搜索对用户可见的消息。您可通过 `subType` 参数进行相应的上层业务开发，实现消息可见性逻辑。支持配置该参数的 API，请参考下文的 **API 变更** 说明 | [搜索消息](https://doc.yunxin.163.com/messaging/guide/Dg3NDg1Mzg?platform=iOS) |

**API 变更**

V9.4.0 的圈组模块引入了如下新增 API 和 变更 API。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`checkPermissions`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a70d6e567fdea268dd11469751a6da362) | 查询自己是否圈组内的某些（圈组）权限 |
| [`searchMsgByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#aa956630a952de6abb0add8cf0c11cd41) | 分页搜索圈组消息 |
| [`subscribeAllChannel`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a2a363e0217a79ee8c1fc6453a59dfba7) | 一次性订阅圈组服务器下最多 200 个频道。单次调用可传入的服务器 ID 数量上限为 10 个。即使多次调用，单个服务器下最多仅能订阅 200 个 频道 |
| [`markServerRead:completion`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a8acbb09eef92cf983545e9d4c7989cc6) | 清空圈组服务器的未读数 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| --- | --- |
| [`sendMessage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html) | 新增 `subType` 入参，表示消息子类型。该参数可以用来做特殊渲染、可见性判断、动画效果展示等。例如，您可通过该参数开发相应的上层业务逻辑，实现发送消息时设置消息对其他用户的可见性。返回的消息体 `NIMQChatMessage` 新增 `subType` 参数 |
| [`updateMessage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#ae95e6009f2c88a7f123c9f6219e4419c) | 新增 `subType` 入参，表示消息子类型。返回的消息体 `NIMQChatUpdateMessageInfo` 新增 `subType` 参数 |
| `onRecvMessages` | 返回的消息体 `NIMQChatMessage` 新增 `subType` 参数 |
| [`getMessageHistory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a0f2048e59a206134994e73fbe2e26763) | 返回的消息体 `NIMQChatMessage` 新增 `subType` 参数 |
| `onMessageUpdate` | 返回的消息体 `NIMQChatUpdateMessageInfo` 新增 `subType` 参数 |
| [`getMessageHistoryByIds`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a14ca2a6af92bdc7bb739ad4e1f4731ed) | 返回的消息体 `NIMQChatMessage` 新增 `subType` 参数 |
| [`getThreadMessages:completion`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d9c/protocol_n_i_m_q_chat_message_extend_manager-p.html#aff2aaa1f21227b11fcb4a77b2491e98e) | 返回的消息体 `NIMQChatMessage` 新增 `subType` 参数 |
| `getLastMessageOfChannels` | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |

## <span id="[9.3.1 - 2022-8-3">9.3.1 (2022-8-3)</span>

- 修复版本升级后偶现本地会话消失的问题。
- 其他已知问题修复。

## <span id="[9.3.0 - 2022-7-25">9.3.0 (2022-7-25)</span>

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 实时互动频道 | 圈组新增实时互动频道，用户可在实时互动频道进行音视频通话等音视频相关操作 | [实时互动频道](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DYzMDM1MjM?platformId=60278) |
| 2 | 圈组搜索结果自定义排序 | 搜索圈组服务器和频道的匹配结果，可按自定义排序 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jI1MzQyMDA?platformId=60278) |
| 3 | 查询邀请申请记录 | 查询服务器的邀请和申请记录，以及用户个人被邀请加入服务器和申请加入服务器的记录 | [查询申请/邀请的历史记录](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zMyODEwMTg?platformId=60278#查询申请/邀请的历史记录) |
| 4 | 生成邀请码 | 拥有**邀请他人加入服务器的权限**的用户可生成邀请码，其他用户可通过邀请码加入服务器 | [生成邀请码](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zMyODEwMTg?platformId=60278#生成邀请码) |
| 5 | 通过邀请码加入服务器 | 获取到邀请码的用户，可通过邀请码加入服务器 | [圈组服务器成员管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zMyODEwMTg?platformId=60278#根据邀请码加入服务器) |

**优化改进**

- 新增自动取消订阅逻辑：新增 **频道对当前用户可见性变更** 和 **当前用户进入/退出服务器** 内置系统通知类型。当收到前者时，如存在相应频道的订阅信息，则自动取消订阅该频道的请求。当收到后者（且为退出服务器）时，如存在相应服务器的订阅信息，则自动取消订阅该服务器以及该服务器下所有已订阅频道的请求。圈组订阅机制相关说明，请参考 [圈组订阅机制](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zAxNjQzMDA?platformId=60278)。
- 更新的消息体新增 `updateContent` 和 `updateOperatorInfo` 字段，分别表示更新的内容和发起更新操作的用户。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`generateInviteCode:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a9646a5a39bc451de54753527f6e5b3fb) | 生成邀请码 |
| [`joinByInviteCode:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#ae62d71dac4442a753ad77ba29266da1a) | 通过邀请码加入服务器 |
| [`getInviteApplyRecordOfServer:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#ad8c85a14ecb493edd95318fd3f18a7aa) | 查询服务器下的申请记录和邀请记录 |
| [`getInviteApplyRecordOfSelf:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a51f2e969d3a45099109ff33535333175) | 用户查询自己的申请记录和邀请记录 |
| [`initWithCompletion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Classes/NIMQChatMediaKit.html#//api/name/initWithCompletion:) | 初始化实时互动频道模块 |
| [`connectChannel:ofServer:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/connectChannel:ofServer:completion:) | 连接实时互动频道 |
| [`disconnectCompletion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/disconnectCompletion:) | 取消连接实时互动频道 |
| [`addMediaChannelListener:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/addMediaChannelListener:) | 添加实时互动频道事件监听 |
| [`removeMediaChannelListener:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/removeMediaChannelListener:) | 移除实时互动频道监听 |
| [`unmuteMyAudio:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unmuteMyAudio:) | 打开自己的音频 |
| [`muteMyAudio:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/muteMyAudio:) | 关闭自己的音频 |
| [`unmuteMyVideo:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unmuteMyVideo:) | 打开自己的视频 |
| [`muteMyVideo:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/muteMyVideo:) | 关闭自己的视频 |
| [`unmuteAudioWithAccId:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unmuteAudioWithAccId:completion:) | 打开成员音频 |
| [`muteAudioWithAccId:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/muteAudioWithAccId:completion:) | 关闭成员音频 |
| [`muteVideoWithAccId:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/muteVideoWithAccId:completion:) | 关闭成员视频 |
| [`unmuteVideoWithAccId:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unmuteVideoWithAccId:completion:) | 打开成员视频 |
| [`startScreenShareWithCompletion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/startScreenShareWithCompletion:) | 开启本端屏幕共享 |
| [`stopScreenShareWithCompletion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/stopScreenShareWithCompletion:) | 关闭本端屏幕共享 |
| [`stopMemberScreenShareWithAccId:completion:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/stopMemberScreenShareWithAccId:completion:) | 关闭成员屏幕共享 |
| [`subscribeRemoteVideoStreamWithAccId:streamType:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/subscribeRemoteVideoStreamWithAccId:streamType:) | 订阅远端视频流 |
| [`unsubscribeRemoteVideoStreamWithAccId:streamType:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unsubscribeRemoteVideoStreamWithAccId:streamType:) | 取消订阅远端视频流 |
| [`subscribeRemoteVideoSubStreamWithAccId:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/subscribeRemoteVideoSubStreamWithAccId:) | 订阅远端视频辅流 |
| [`unsubscribeRemoteVideoSubStreamWithAccId:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/unsubscribeRemoteVideoSubStreamWithAccId:) | 取消订阅远端视频辅流 |
| [`setupLocalVideoCanvas:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/setupLocalVideoCanvas:) | 设置本地视频画布 |
| [`setupRemoteVideoCanvas:accId:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/setupRemoteVideoCanvas:accId:) | 设置远端视频画布 |
| [`setupRemoteSubStreamVideoCanvas:accId:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/setupRemoteSubStreamVideoCanvas:accId:) | 设置远端视频辅流画布 |
| [`getScreenSharingAccid`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/getScreenSharingAccid) | 获取共享屏幕者 ID |
| [`enableAudioVolumeIndicationWithEnable:interval:`](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html#//api/name/enableAudioVolumeIndicationWithEnable:interval:) | 启用说话者音量提示 |
**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| --- | --- |
| [`inviteServerMembers:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a83f7643421a00e1f722d7a1adb39796c) | 新增 `ttl` 入参（可选），表示加入服务器邀请的有效时长 |
| [`applyServerJoin:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#af5aedc6a8b90f6d3017a74b3625c48a5) | 新增 `ttl` 入参（可选），表示加入服务器申请的有效时长 |
| [`acceptServerApply:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a3b38159dde3c263666b7331820b08335) | 新增 `requestId` 入参（必传），表示加入服务器申请的标识 |
| [`rejectServerApply:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#adc4bc957ca9e61e83d275e92c308d322) | 新增 `requestId` 入参（必传），表示加入服务器申请的标识 |
| [`acceptServerInvite:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a9d9ce6e82adde8212447a57b9c2eb684) | 新增 `requestId` 入参（必传），表示加入服务器邀请的标识 |
| [`rejectServerInvite:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a38cb24208eda9cc6dafce898c93ec550) | 新增 `requestId` 入参（必传），表示加入服务器邀请的标识 |
| [`createChannel:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ab496ffeebbeb568bcff924918026075d) | 可创建的频道类型枚举 [`NIMQChatChannelType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/ddd/_n_i_m_q_chat_defs_8h.html#a305177856fe8469a259c546c08170534) 增加枚举值 `NIMQChatChannelType 实时互动 `，表示 实时互动 频道。 |
| [`updateServerRole:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a45583fc4bfd523b42dad6bfe5841422f) | 可修改的服务器身份组权限 [`NIMQChatPermissionType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/ddd/_n_i_m_q_chat_defs_8h.html#aeee4335aecd193652bc2e7e05679ebb0) 新增 实时互动 频道相关权限、邀请申请管理权限和邀请申请历史记录查看权限 |
| [`updateChannelRole:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa3b921324fcfd5f2c74282b87d1985d0) | 可修改的频道身份组权限新增实时互动频道相关权限 |
| [`updateMemberRole:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#af1cac765662f98ef9b1834d043d981db) | 可修改的个人定制权限新增实时互动频道相关权限 |
| [`updateChannelCategoryRole:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa5c228755b6b39f5abb8f3a69ee1b89a) | 可修改的个人定制权限新增实时互动频道相关权限 |
| [`updateChannelCategoryMemberRole:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a105aa80f83b29115f06c87f577c6b601) | 可修改的频道分组维度的个人定制权限新增实时互动频道相关权限 |
| [`getServersByPage:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a5f0e299283039a65d37928f3c416345c) | 新增入参 `sort`，表示服务器的排序条件 |
| [`getChannelsByPage:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a906f0987d0cd8c3a240cb998599aff6d) | 新增入参 `sort`，表示频道的排序条件 |

## <span id="[9.2.8 - 2022-7-1">9.2.8 (2022-7-1)</span>
优化自动重连机制，实现国内外节点平滑迁移。

## <span id="[9.2.5 - 2022-6-13">9.2.5 (2022-6-13)</span>
该版本在圈组模块增加了圈组系统通知的类型。

| <div style="width:90px">相关模块</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- |
| 圈组系统通知 | 1. 新增以下 5 种圈组系统通知类型：</br> <ul><li>加入服务器身份组成员</li><li>移除服务器身份组成员</li><li>更新服务器身份组权限</li><li>更新频道身份组权限</li><li>更新频道个人定制权限</li></ul>具体可查看 [`NIMQChatSystemNotificationType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/ddd/_n_i_m_q_chat_defs_8h.html#a68eb284bba17219f9f003e57d5ae414b)</br></br>2. 对应新增 5 种圈组系统通知附件协议，具体可查看 `NIMQChatSystemNotificationAttachment` | [系统通知](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Tg0OTEyNjY?platformId=60278) |

## <span id="[9.2.0 - 2022-5-24">9.2.0 (2022-5-24)</span>

该版本在圈组模块增加了频道分组、消息正在输入状态显示和搜索功能等更新。

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 频道分组 | 支持对频道进行分组管理 | [频道分组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY5Mzg5MTA?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C) |
| 2 | 频道分组黑白名单 | 支持为频道分组设置黑白名单成员/身份组，与频道类型（私密/公开）共同判定频道分组是否对用户可见 | [频道分组黑白名单](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TQ1MzMwNDA?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C) |
| 3 | 频道分组身份组 | 支持在频道分组维度设置身份组和定制权限，增加用户权限控制的层级 | [频道分组身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Dg0MTQ1MjM?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C) |
| 4 | 消息正在输入 | 支持显示频道消息正在输入 | [消息正在输入](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TU4NjQ0NDk?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C) |
| 5 | 圈组搜索功能 | 支持通过关键字对服务器、频道和服务器成员进行搜索 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jI1MzQyMDA?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C) |
| 6 | 频道分组推送配置 | 支持在频道分组层级配置推送 | [圈组推送管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zQ0OTI2NjA?platformId=60278#NIMSDK%20%E6%B3%A8%E5%86%8C)

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`createChannelCategory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ad8abd53b70dcfefb28f6332ebd2590ec) | 创建频道分组 |
| [`deleteChannelCategory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a15fd89de57850a54f60189425364071c) | 删除频道分组 |
| [`updateChannelCategory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ae6609e50943b3fe1243ee1a0133024c0) | 修改频道分组信息 |
| [`getChannelCategories`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a0ad77fe55bcb4b8fa72552015c9db71c) | 查询频道分组 |
| [`getChannelsInCategoryByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a7c1970852e939442576f01e18f9cfd43) | 分页查询频道分组下频道列表 |
| [`addChannelCategoryRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a5488d0c1914ac4a090b9f4a884911024) | 创建频道分组身份组 |
| [`removeChannelCategoryRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa6b28285176029a3b986e3f75166c054) | 删除频道分组身份组 |
| [`updateChannelCategoryRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aa5c228755b6b39f5abb8f3a69ee1b89a) | 更新频道分组身份组。设置频道分组身份组的权限，需调用该方法 |
| [`getChannelCategoryRoles`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a227f55e5f96aeb63825a857dee2ea1b0) | 查询频道分组身份组信息 |
| [`addChannelCategoryMemberRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#ab706cc9d80d1b9f7e0cfa45009569b17) | 创建频道分组某人的定制权限 |
| [`removeChannelCategoryMemberRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#aed6542360dba333af47b09a95e9a0d1b) | 删除频道分组某人的定制权限 |
| [`updateChannelCategoryMemberRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a105aa80f83b29115f06c87f577c6b601) | 修改频道分组某人的定制权限。 |
| [`getChannelCategoryMemberRoles`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html#a2ae39f1335eb9546394dcce14680bf32) | 查询频道分组某人的定制权限 |
| [`updateChannelCategoryBlackWhiteRole`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a89579aedc856cc3352bc6c472cb2bea5) | 更新频道分组黑白名单身份组 |
| [`getChannelCategoryBlackWhiteRolesByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#af64e4ea20500928a38c0dcf6cd31f95e) | 分页查询频道分组黑白名单身份组列表 |
| [`updateChannelCategoryBlackWhiteMembers`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a73d461746fa3b7c5944fa9f87e80d887) | 更新频道分组黑白名单成员 |
| [`getChannelCategoryBlackWhiteMembersByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a056f85b8c1853745763ec7d864a80e82) | 分页查询频道分组黑白名单成员列表 |
| [`getExistingChannelCategoryBlackWhiteRoles`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a35f8208a637c8436529bca32fb03b626) | 批量查询频道分组黑白名单身份组列表 |
| [` getExistingChannelCategoryBlackWhiteMembers`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ae6d949f9b50ea79f8aac5f1e3bc86058) | 批量查询频道分组黑白名单成员列表 |
| [`onRecvTypingEvent`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d4/d3f/protocol_n_i_m_q_chat_message_manager_delegate-p.html#adf908db38e4cb7fa268a40b458737070) | 监听频道消息正在输入事件 |
| [`sendMessageTypingEvent`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html#a317f738802abd63f4b5cf3b5bc0dfd69) | 发送频道消息正在输入事件 |
| [`searchServerByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a5e53e2d14fb78426773590109f55bb97) | 分页搜索服务器 |
| [`searchServerMemberByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html#a79239976eba0ac22acc9b17b1e0e0c5e) | 分页搜索服务器成员 |
| [`searchChannelByPage`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#a1a54b00db00479f95c085d821b8908a7) | 分页搜索频道 |
| [`updatePushNotificationProfile:channelCategory`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d4f/protocol_n_i_m_q_chat_apns_manager-p.html#abc12695a5c3875c46c46ea80ba909ff4) | 更新频道分组层级推送配置 |
| [`getUserPushNotificationConfigByChannelCategories`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d4f/protocol_n_i_m_q_chat_apns_manager-p.html#ab18f4608715da672ec8c130bc8a4e4fd) | 获取频道分组层级推送配置 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| --- | --- |
| [`createChannel`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#ab496ffeebbeb568bcff924918026075d) | 新增 `categoryId` 和 `syncMode` 参数，调用时传入 `categoryId` 可将频道加入某个频道分组。通过设置 `syncMode`，可实现频道数据与频道分组数据的同步。具体同步的数据包括查看模式（私密或公开）、黑白名单和身份组权限。 |
| [`updateChannel`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html#aeb8aece70850d5f574d892cbc3be6d12) | 同上

## <span id="[9.1.1 - 2022-4-14">9.1.1 (2022-4-14)</span>
**圈组相关优化**
- 将 ```checkPermission``` 的入参 ```channelId``` 调整为可传参数。如果不传则查服务器权限，传则查频道权限。

**修复**
- 修复遗留问题。

## <span id="[9.1.0 - 2022-4-11">9.1.0 (2022-4-11)</span>
**更新**
- 圈组相关更新：
    - 当用户在服务器维度没有**管理角色**权限，但在频道维度有该权限时，可在 ```getServerRoles``` 方法的 ```NIMQChatGetServerRolesParam``` 中传入 ```channelId``` 参数查询整个服务器的身份组列表，以便对频道进行权限添加。相关详情请参考 [获取服务器身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zg0Nzc3Mzg?platformId=60278#获取服务器身份组)。
    - 新增封禁用户功能。
        - 创建或更新身份组时可配置 ```NIMQChatPermissionTypeManageBanServerMember``` 参数，该参数代表封禁服务器其他成员的权限。相关配置详情请参考 [创建服务器身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zg0Nzc3Mzg?platformId=60278#创建服务器身份组)和[更新服务器身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zg0Nzc3Mzg?platformId=60278#更新服务器身份组)。
        - 拥有封禁其他成员权限的服务器成员可封禁或解封其他成员。相关方法调用详情请参考 [封禁服务器成员相关](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zMyODEwMTg?platformId=60278#封禁服务器成员相关)。
    - 新增 Thread 聊天和快捷评论功能。相关方法调用详情请参考 [消息扩展](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TY1NDI3MTQ?platformId=60278)。
    - 新增圈组反垃圾功能。
        - 支持通过 ```NIMQChatMessageAntispamSetting``` 配置消息内容反垃圾。相关配置详情请参考 [圈组消息内容审核](https://doc.yunxin.163.com/messaging/guide/zMxMTQxMDc?platform=iOS)。
        - 支持传入 ```antispamBusinessId``` 参数为服务器、频道和身份组的创建和更新操作配置反垃圾业务 ID。
    - 更新圈组推送逻辑。新的推送逻辑详情请参考 [圈组推送](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jc5OTQ2OTk?platformId=60278#推送)。相关方法调用请参考 [圈组推送消息等级类型解释及定义](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zQ0OTI2NjA?platformId=60278#%E5%9C%88%E7%BB%84%E6%8E%A8%E9%80%81%E6%B6%88%E6%81%AF%E7%AD%89%E7%BA%A7%E7%B1%BB%E5%9E%8B%E8%A7%A3%E9%87%8A%E5%8F%8A%E5%AE%9A%E4%B9%89%20%20NIMPushNotificationProfile)、[更新服务器推送消息等级配置](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zQ0OTI2NjA?platformId=60278#更新服务器推送消息等级配置)和[频道推送消息等级配置](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zQ0OTI2NjA?platformId=60278#更新频道推送消息等级配置) 等。
    - 支持 [圈组消息缓存设置](https://doc.yunxin.163.com/messaging/guide/TY0MDEzMDQ?platform=iOS)。
- 其他更新：
    - 未读相关操作按会话类型分类能力。可通过 sessiontype [获取指定会话类型的总未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TE0NzkwMzE?platformId=60278#获取未读数)、[重置未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TE0NzkwMzE?platformId=60278#重置未读数)。

**修复**
- 修复了终端用户开启消息漫游后在不同手机登录时收到的消息发送结果不一致的问题（一台手机上显示消息发送成功，另一台上显示消息发送失败）。
- 其他问题修复及优化

## <span id="[9.0.1 - 2022-3-10">9.0.1 (2022-3-10)</span>
**修复**
1. 修复向圈组小服务器内的频道发送消息，接收方没有回调未读数变化的问题。

## <span id="[9.0.0 - 2022-2-24">9.0.0 (2022-2-24)</span>
**新增**
1. 网易云信即时通讯服务全新能力**圈组**发布。相关功能介绍和开发集成请分别参考 [什么是圈组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TMzMzgwOTU)和[圈组接入流程](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TczMjQyMTA)。
## <span id="[8.11.0 - 2022-01-10">8.11.0 (2022-01-10)</span>
**新增**
1. 支持聊天室空间消息功能。[进入聊天室](/docs/TM5MzM5Njk/jQ0MjQ0NDI#进入聊天室)和[发送聊天室消息](/docs/TM5MzM5Njk/zg1NjkwNjg#功能概述) 支持配置 x, y, z 坐标
2. 支持聊天室定向消息功能。[发送聊天室消息](/docs/TM5MzM5Njk/zg1NjkwNjg#功能概述) 支持消息接受者列表
3. [支持聊天室标签实时更新 ](/docs/TM5MzM5Njk/jQ0MjQ0NDI#更新标签)
4. [匿名聊天室和独立聊天室支持第三方 token 鉴权](/docs/TM5MzM5Njk/jQ0MjQ0NDI#进入聊天室)
5. 支持业务反垃圾。涉及 [进入聊天室](/docs/TM5MzM5Njk/jQ0MjQ0NDI#进入聊天室)、[更新我的用户资料](/docs/TM5MzM5Njk/DI3NjcxMDU#编辑用户资料)、[创建群](/docs/TM5MzM5Njk/jM3Mzk1NzE#创建群组)、[更新群信息](/docs/TM5MzM5Njk/jM3Mzk1NzE#修改群信息)、[更新超大群信息](/docs/TM5MzM5Njk/TEzMTgwNTg#修改群信息)、[更新聊天室信息](/docs/TM5MzM5Njk/jQ0MjQ0NDI#修改聊天室信息) 和[更新我的聊天室资料](/docs/TM5MzM5Njk/jQ0MjQ0NDI#修改自身信息)

## <span id="[8.10.1 - 2021-12-31">8.10.1 (2021-12-31)</span>
**新增**
1. [支持 S3 存储](/docs/TM5MzM5Njk/DQ5MTA5ODQ#NIMSDKConfig)

## <span id="[8.9.0 - 2021-12-03">8.9.0 (2021-12-03)</span>
**新增**
1. 最大支持好友数至 1 万

## <span id="[8.8.0 - 2021-11-04">8.8.0 (2021-11-04)</span>
**新增**
1. [支持批量添加聊天室队列元素（由服务端发起）](/docs/TM5MzM5Njk/jQ0MjQ0NDI#聊天室通知消息)
2. [增加全文云端消息检索（按消息时间排序）接口](/docs/TM5MzM5Njk/DYzOTY1NDc#全文云端消息检索(按消息时间排列))

## <span id="[8.7.2 - 2021-09-28">8.7.2 (2021-09-28)</span>

<div style="display:none">
**新增**

1. 新增 [获取指定会话未读消息列表](/docs/TM5MzM5Njk/TE0NzkwMzE#获取指定会话未读消息列表) 接口
</div>

**变更**

1. 优化创建会话逻辑

## <span id="[8.7.0 - 2021-08-25">8.7.0 (2021-08-25)</span>

**新增**

1. 支持 [聊天室撤回消息](/docs/TM5MzM5Njk/jQ0MjQ0NDI#聊天室通知消息) （服务端接口）
2. 聊天室 [加入或者更新队列元素](/docs/TM5MzM5Njk/jQ0MjQ0NDI#加入或者更新队列元素) 时，支持配置队列元素所属账号
3. 支持[配置聊天室接收消息通知的时间间隔](/docs/TM5MzM5Njk/DQ5MTA5ODQ#NIMSDKConfig)
4. [消息体新增易盾反垃圾扩展字段和结果字段](/docs/TM5MzM5Njk/zg1NjkwNjg#功能概述)
5. 支持[异步获取指定会话某消息之前的若干条消息](/docs/TM5MzM5Njk/DYzOTY1NDc#本地历史消息查询)

## <span id="[8.6.2 - 2021-08-06">8.6.2 (2021-08-06)</span>

**新增**

1. 支持数据库备份功能，配置开关为 [NIMSDKConfig](/docs/TM5MzM5Njk/DQ5MTA5ODQ#NIMSDKConfig) #sessionDatabaseBackupEnabled

## <span id="[8.5.0 - 2021-06-22">8.5.0 (2021-06-22)</span>

**新增**

1. [支持云端历史消息全文检索](/docs/TM5MzM5Njk/DYzOTY1NDc#全文云端消息检索)
2. [查询指定群消息的已读回执，支持指定群成员列表](/docs/TM5MzM5Njk/zg1NjkwNjg#群聊消息已读回执)

**变更**

1. [支持撤回自己给自己发送的消息](/docs/TM5MzM5Njk/zg1NjkwNjg#消息撤回)

## <span id="[8.4.4 - 2021-05-31">8.4.4 (2021-05-31)</span>

**优化**

1. 提升高可用服务稳定性

## <span id="[8.4.0 - 2021-04-29">8.4.0 (2021-04-29)</span>

**新增**

1. [创建会话支持配置是否通过消息数据库设置最后一条消息](/docs/TM5MzM5Njk/TE0NzkwMzE#创建最近会话)
2. [支持从本地数据库查询群已读回执内容](/docs/TM5MzM5Njk/zg1NjkwNjg#群聊消息已读回执)
3. [删除本地会话支持配置是否视为已读](/docs/TM5MzM5Njk/TE0NzkwMzE#删除最近会话)
4. [聊天室设置标签标志加入聊天室及按标签发送消息、查询成员详情及总数、禁言能力](/docs/TM5MzM5Njk/jg5MzQ5Nzk)
5. 登录抄送新增 SDK 外部版本号
6. 上传 nos 的 token 过期时，可以自动更新 token

## 8.3.1 (2021-03-22)

**优化**

1. 提高 SDK 稳定性
2. 优化缺省 lbs 生成规则

**修复**

1. SDK 初始化对 httpdns 访问过于频繁的问题

## 8.3.0 (2021-03-03)

**新增**

- [新增动态登录功能](/docs/TM5MzM5Njk/DQ5MTA5ODQ#动态登录)
- [重置未读数接口新增带回调版本](/docs/TM5MzM5Njk/TE0NzkwMzE#重置未读数)

**修正**

- IM 触发访问局域网权限弹窗问题优化

## 8.2.5 (2021-02-04)

**优化**

- 完善域名高可用策略，提升服务稳定性

## 8.2.0 (2020-12-30)

**新增**

- 新增批量查询群组信息功能。
- 新增批量处理会话未读数接口。
- 删除会话支持配置是否删除漫游。
- 消息撤回支持扩展字段。

**修正**

- iOS 14 相册适配（NIMKit 依赖的 TZImagePickerController 升级版本）。
- iOS 退后台时，打印下当前的总未读数及回话对应未读数。
- 清理未读数后，打印会话对象的 unread 与 sessionid。

## 8.1.5 (2020-12-21)

**优化**

- 修复极端网络情况下，低概率漫游消息丢失问题;
- 优化了 SDK 调用 NIMHTTPDNSService 时偶现的卡顿现象;
- 修复超大群获取属性字段值多端同步问题;
- SDK 调用 searchMessages:接口，查询结果都按照旧消息到新消息的顺序排列;

## 8.1.4 (2020-12-18)

**优化**
- SDK 调用 NIMHTTPDNSService 的卡顿问题规避

## 8.1.3 (2020-12-9)

**优化**
- 修复偶现闪退问题

## 8.1.0 (2020-11-13)

**新增**
- 文件下载支持配置 CDN 域名
- 聊天室 CDN 弹幕功能
- 新增 G2 音视频话单消息类型
- 增加配置开关，使得同步云端消息到本地时能够自动创建同步消息所对应的会话

## 8.0.1 (2020-10-23)

**优化**

- 修复私有化环境文件上传失败问题
- 修复群成员偶现丢失问题

## 8.0.0 (2020-09-28)

**新增**

- [增加批量删除云端历史消息功能](/docs/TM5MzM5Njk/DYzOTY1NDc#批量删除云端历史消息)

- [增加清空单个会话的云端历史消息功能](/docs/TM5MzM5Njk/DYzOTY1NDc#清空单个会话的云端历史消息)

- 消息撤回接口增加附言字段。NIMRevokeMessageOption 增加 postscript 字段，用于设置附言

- [云端最近会话最后一条消息增加撤回通知类型。NIMRecentSession 增加 lastMessageType 和 lastRevokeNotification 字段。](/docs/TM5MzM5Njk/DYzOTY1NDc#清空单个会话的云端历史消息)

- 标记会话已读接口。增加清空结果回调。参考 NIMConversationManagerDelegate#onMarkMessageReadCompleteInSession

- [增加云端会话自定义过滤。](/docs/TM5MzM5Njk/jY2MzAxMTQ#获取会话列表)

**优化**

- 远程拉取的消息如果本地数据库存在允许撤回
- 修复大文件上传失败的问题
- 修复新旧版本覆盖安装时出现的数据库错误
## 7.9.1 (2020-09-11)

**优化**

- 增加最近会话的相关日志

## 7.8.5 (2020-08-20)

**优化**

- 修复 IOS9 上开启录音出现的 crash

## 7.8.4 (2020-08-14)

**优化**

- 修复群成员丢失问题
- 修复大量会话数据同步时造成卡顿的问题

## 7.8.3 (2020-07-31)

**优化**

- 修复上传附件请求的 Content-Type 类型错误的问题

## 7.8.1 (2020-07-29)

**新增**

 * [增加反向查询聊天成员列表](/docs/TM5MzM5Njk/jQ0MjQ0NDI#分页获取聊天室成员)，NIMChatroomFetchMemberType 新增 NIMChatroomFetchMemberTypeUnRegularReversedOrder, [API](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d7a/_n_i_m_chatroom_member_request_8h.html#a8248f82865727fcc4deb4fffde77e901)

**优化**

 * 修复更新自己的群成员信息出现的异常

## 7.8.0 (2020-07-21)

**新增**

 * 登录可配置自定义客户端类型，用于自定义互踢功能
 * 支持为消息配置子类型
 * 删除单条消息支持配置是否记录操作

**优化**

 * 消息查询效率优化，解决因消息数量过多产生搜索卡顿的问题

## 7.7.4 (2020-06-22)

**优化**

 * 修复启用 Data Protection 下的一个崩溃问题

## 7.7.2 (2020-06-12)

**新增**

 * 消息增加易盾反垃圾增强反作弊专属字段（请参考易盾反垃圾接口文档反垃圾防刷版专属字段）

**优化**

 * 修复多人会议后注销用户出现的崩溃问题
 * 修复聊天室消息 remoteExt 字段为空的问题

## 7.7.0 (2020-05-27)

**新增**
 * 第三方回调支持消息变更。NIMMessage 中增加第三方回调回来的自定义扩展字段，支持第三方服务器变更该字段。
 * 踢出登录接口增加自定义字段信息。NIMLoginManagerDelegate 中增加如下回调。

```objc
/**
 * 被踢(服务器/其他端)回调
 *
 * @param result        被踢原因
 */
- (void)onKickout:(NIMLoginKickoutResult *)result;
```

## 7.6.0 (2020-05-13)

**新增**

 * [消息回复](/docs/TM5MzM5Njk/TQ0OTI4MDY#会话消息回复)
 * [会话置顶功能](/docs/TM5MzM5Njk/TQ0OTI4MDY#会话置顶)
 * [消息快捷评论](/docs/TM5MzM5Njk/TQ0OTI4MDY#消息快捷评论)
 * [收藏功能](/docs/TM5MzM5Njk/TQ0OTI4MDY#收藏夹)
 * [会话消息 PIN 标记](/docs/TM5MzM5Njk/TQ0OTI4MDY#PIN 标记)

**变更**

 * 未接通的音视频通话话单通知存离线，漫游和云端历史
 * 新增主动停止播放音频回调，与原先的播放完成回调区分。

优化

## 7.4.2 (2020-3-20)

**新增**
 *    新增漫游未完整会话相关 API 接口、回调

```objc
/**
 * 会话管理器回调
 */
@protocol NIMConversationManagerDelegate <NSObject>

@optional
/**
 * 未漫游完整会话列表回调
 * @param infos 未漫游完整的会话信息
 */
- (void)onRecvIncompleteSessionInfos:(nullable NSArray<NIMIncompleteSessionInfo *> *)infos;
@end
```

接口原型

```objc
/**
 * 会话管理器
 */
@protocol NIMConversationManager <NSObject>

/**
 查询漫游消息未完整会话信息

 @param session 目标会话
 @param completion 结果完成回调
 */
- (void)incompleteSessionInfoBySession:(NIMSession *)session
                            completion:(nullable NIMIncompleteSessionsBlock)completion;
/**
 查询所有漫游消息未漫游完整会话信息

 @param completion 结果完成回调
 */
- (void)allIncompleteSessionInfos:(NIMIncompleteSessionsBlock)completion;

/**
 更新未漫游完整会话列表

 @param messages 消息对象，使用 NIMMessage 的会话、severId、timestamp、from 等去更新 b
 @param completion 结果完成回调
 */
- (void)updateIncompleteSessions:(NSArray<NIMMessage *> *)messages
                      completion:(nullable NIMUpdateIncompleteSessionsBlock)completion;

/**
 根据会话移除未漫游完整会话信息

 @param session 目标会话
 */
- (void)removeIncompleteSessionInfoBySession:(NIMSession *)session;

/**
 移除所有未完整会话信息
 */
- (void)removeAllIncompleteSessionInfos;
@end
```

## 7.4.0 (2020-3-11)
**新增**
 * 支持单向删除消息
 * 撤回消息支持配置未读数是否加 1，支持撤回通知的 pushcontent 和 payload 字段

```objc
NSDictionary *payload = @{
        @"apns-collapse-id": message.messageId,
    };

    [[NIMSDK sharedSDK].chatManager revokeMessage:message
                                      apnsContent:@ **撤回一条消息**
                                      apnsPayload:payload
                                  shouldBeCounted:![[NTESBundleSetting sharedConfig] isIgnoreRevokeMessageCount]
                                         completion:^(NSError * _Nullable error)
    {
    }];

```
**变更**
 * 消息推送：iOS 10 及以上系统支持 payload 配置 'apns-collapse-id', 实现后面推送内容覆盖

```objc
+ (void)setupMessage:(NIMMessage *)message
{
    message.apnsPayload = @{
        @"apns-collapse-id": message.messageId,
    };

    NIMMessageSetting *setting = [[NIMMessageSetting alloc] init];
    setting.scene = NIMNOSSceneTypeMessage;
    message.setting = setting;
}
```

**修复**
 * 修复更新消息、最近会话时，多线程下访问出现的崩溃。
 * 修复[[NIMSDK sharedSDK] setSceneDict:dict]; 设置有效期过大的问题。
 * 优化一些内部逻辑。

## 7.2.0 (2020-1-13)
**新增**

 * 服务端消息关键字检索

```objc
/**
 * 会话管理器
 */
@protocol NIMConversationManager <NSObject>
    /**
     * 根据关键字从服务器上检索消息
     *
     * @param session 消息所属的会话
     * @param option 检索选项
     * @param result 读取的消息列表结果
     * @discussion    检索消息内容，大小写不敏感。此接口不支持查询聊天室消息，聊天室请参考 NIMChatroomManagerProtocol 中的消息接口。
     *
     */
    - (void)retrieveServerMessages:(NIMSession *)session
                            option:(NIMMessageServerRetrieveOption *)option
                            result:(nullable NIMRetrieveServerMessagesBlock)result;
@end
```

 * 联系人搜索

```objc
@protocol NIMUserManagerProtocol <NSObject>
/**
 * 查找成员
 *
 * @param option      查询条件
 * @param completion 完成回调
 */
- (void)searchUserWithOption:(NIMUserSearchOption *)option
                  completion:(nullable NIMUserInfoBlock)completion;
```

 * 超大群增加移交群主、增加群管理员、移除群管理员
 * 超大群增加群禁言、群成员禁言
 * 超大群资料修改细化群名称修改，群头像修改，群组验证方式修改，群组被邀请人验证方式修改，群介绍修改，群公告修改，群自定义信息修改几个接口
 * 超大群增加同意邀请入群和拒绝邀请入群
 * 超大群增加增加申请入群，批准入群和拒绝入群申请
 * 超大群增加修改群员昵称

**变更**
 * 多端登录增加具体上下线类型
 * 云端历史消息本地入库
 * 增加 P2P 与群聊单向撤回

## 7.0.3 (2019-12-4)
**新增**
 *    消息过滤配置接口

```objc
@protocol NIMSDKConfigDelegate <NSObject>
/**
 * 是否忽略某条消息
 */
 - (BOOL)shouldIgnoreMessage:(NIMMessage *)message;
@end
```

**修复**
 * 修复最近会话未读数为 0 的问题
 * 修复由于断网没有发送成功的群消息已读回执，重连后再发送也不会成功的问题

## 7.0.0 (2019-11-13)

**新增**

 * allRecentSessions 增加异步加载完成回调。

```
@protocol NIMConversationManagerDelegate <NSObject>
/**
 * 最近会话数据库读取完成
 *
 * @discussion 所有最近会话读取完成。设置 NIMSDKConfig 中的 asyncLoadRecentSessionEnabled 属性为 YES 时，此回调会执行。
 * 该回调执行表示最近会话全部加载完毕可以通过 allRecentSessions 来取全部对话。
 */
- (void)didLoadAllRecentSessionCompletion;

@end
```

 * NIMSDKConfig 中增加异步读取最近会话选项。

```
/**
 * NIM SDK 配置项目
 */
@interface NIMSDKConfig : NSObject

/**
 * 是否开启异步读取最近会话，默认 NO，不开启
 * @discussion 对于最近会话比较多的用户，初始读取数据库时，可能影响到启动速度，用户可以选择开启该选项，开启异步读取最近会话，
 * allRecentSessions 会优先返回一部分最近会话，等到全部读取完成时，通过回调通知用户刷新 UI。
 */
@property (nonatomic, assign) BOOL asyncLoadRecentSessionEnabled;

@end

```

 * 获取服务端会话列表

```objc
@protocol NIMConversationManager <NSObject>
/**
 * 从服务端分页获取历史会话列表
 *
 * @param option 分页查询选项，可为空，空时默认全量获取
 *
 * @param completion 完成回调
 */
- (void)fetchServerSessions:(nullable NIMFetchServerSessionOption *)option
                 completion:(nullable NIMFetchRecentSessionsHistoryBlock)completion;
@end

```

 * 获取服务端会话信息

```objc
@protocol NIMConversationManager <NSObject>
/**
 * 从服务端获取会话信息
 *
 * @param session 目标会话
 *
 * @param completion 完成回调
 */
- (void)fetchServerSessionBySession:(NIMSession *)session
                         completion:(nullable NIMFetchRecentSessionHistoryBlock)completion;
@end

```

 * 更新服务端会话扩展

```objc
@protocol NIMConversationManager <NSObject>
/**
 * 更新服务端获取会话扩展信息
 *
 * @param ext        扩展信息
 *
 * @param session    目标最近会话
 *
 * @param completion 完成回调
 */
- (void)updateServerSessionExt:(NSString *)ext
                       session:(NIMSession *)session
                    completion:(nullable NIMRemoteRecentSessionBlock)completion;
@end

```

 * 删除服务端会话

```objc
@protocol NIMConversationManager <NSObject>
/**
 * 删除服务端会话
 *
 * @param sessions 目标会话
 *
 * @param completion 完成回调
 */
- (void)deleteServerSessions:(NSArray<NIMSession *> *)sessions
                  completion:(nullable NIMRemoteRecentSessionBlock)completion;
@end

```

 * 自定义推送文档配置

```objc
@interface NIMSDK : NSObject
/**
 * 更新 APNS Token
 *
 * @param token APNS Token
 * @param key 自定义本端推送内容, 设置 key 可对应业务服务器自定义推送文案; 传@"" 清空配置, nil 则不更改
 */
- (void)updateApnsToken:(NSData *)token
       customContentKey:(nullable NSString *)key;
 @end

```

 * 本地数据库异常上抛

```objc
/**
 * 数据库异常信息
 */
@interface NIMDatabaseException : NSObject
/**
 * 注册数据库异常处理对象
 * @param handler 用户自定义处理对象
 */
+ (void)registerExceptionHandler:(id<NIMDatabaseHandleExceptionProtocol>)handler;

@end
```

**优化**
 * 暴露消息的服务端 ID

```objc
@interface NIMMessage : NSObject
/**
 * 消息服务端 ID
 */
@property (nonatomic,copy,readonly)   NSString * serverID;
@end
```
 * allRecentSessions 增加异步加载方式，在最近会话量特别大（万级）的情况下防止卡主线程。

```
/**
 * 获取所有最近会话。
 * @return 最近会话列表
 * @discussion SDK 以 map 的形式保存 sessions，调用这个方法时将进行排序，数据量较大 (上万) 时会比较耗时。
 * 该方法默认是同步查询所有 sessions，当数据量较大（上万）会比较耗时，可能会卡主线程，这种情况下
 * 用户可以配置 NIMSDKConfig 中的 asyncLoadRecentSessionEnabled 属性为 YES，此时该接口可以先返回
 * 100 条最近会话，等全部加载完会回调 didLoadAllRecentSessionCompletion，此后再调用该接口可以全量返回
 * 所有会话，用户需要在 didLoadAllRecentSessionCompletion 回调中及时更新 UI 展示。
 */
- (nullable NSArray<NIMRecentSession *> *)allRecentSessions;
```

**修改**
 * 删除少量获取会话接口(最近 100 个会话) mostRecentSessions 接口
 * 修复获取最近会话偶现的崩溃

## 6.10.0 (2019-10-29)

**修改**
 * 获取会话偶现崩溃修复

## 6.9.1 (2019-09-25)

**新增**
 * iOS13 推送（Pushkit）适配

## 6.9.0 (2019-09-17)

**新增**
 * 少量获取会话接口(最近 100 个会话)

```objc
@protocol NIMConversationManager <NSObject>
/**
 * 获取所有最近 100 条会话
 * @return 最近会话列表
 * @discussion 用该接口在 SDK 启动时快速先获取
 */
- (nullable NSArray<NIMRecentSession *> *)mostRecentSessions;
@end

```

 * 点对点音视频通话记录接口

```objc
@protocol NIMNetCallManager <NSObject>
/**
 * 获取点对点通话记录
 *
 * @param option 本地查询可选项, nil 返回所有
 * @param completion 查询结果回调
 */
- (void)recordsWithOption:(NIMNetCallRecordsSearchOption * _Nullable)option
               completion:(NIMNetCallSearchRecordsHandler)completion;

/**
 * 清空点对点通话记录
 */
- (void)deleteAllRecords;
@end
```

- 超大群增加消息撤回功能
- 超大群支持自定义通知
- 超大群增加离线消息处理
- iOS 13 适配：APNs token、视频渲染等

**变更**
 * 添加支持独立聊天室日志上传
 * 聊天室优化
 * 群通知类型增加线程保护

## 6.7.0 (2019-08-01)

**新增**

 * 增加超大群群通知状态接口

```objc
@protocol NIMSuperTeamManager
/**
 * 修改群通知状态
 *
 * @param state        群通知状态
 * @param teamId       群组 ID
 * @param completion   完成后的回调
 */
- (void)updateNotifyState:(NIMTeamNotifyState)state
                   inTeam:(NSString *)teamId
               completion:(nullable NIMSuperTeamHandler)completion;
@end
```

 * 增加超大群群通知状态查询接口

```objc
@protocol NIMSuperTeamManager
/**
 * 群通知状态
 *
 * @param teamId 群 ID
 *
 * @return 群通知状态
 */
- (NIMTeamNotifyState)notifyStateForNewMsg:(NSString *)teamId;
@end
```

 * 增加所有最近会话接口（临时生成的会话用于过滤最后一条消息）

```objc
/**
 * 获取所有最近会话
 * @return 最近会话列表
 * @discussion SDK 以 map 的形式保存 sessions，调用这个方法时将进行排序，数据量较大 (上万) 时会比较耗时。
 * 通过该接口获取的最近会话列表与 allRecentSessions 接口不同，是基于 allRecentSessions 接口筛选类型之后重新生成的新对象
 * 需要用户自行在外部管理，所有回调不回回调该接口查询的任何会话
 */
- (nullable NSArray<NIMRecentSession *> *)allRecentSessionsWithOption:(NIMRecentSessionOption *)option;
```

 * 超大群新增管理员角色，添加和移除管理员需要调用服务端 API
 * 超大群增加群组静音、个人禁言

 * SDK 配置项新增是否允许重置 AVAudioSession

```objc
@interface NIMSDKConfig : NSObject

/**
 * 是否允许重置 AVAudioSession 默认 YES，允许重置
 * @discussion 默认在播放、Seek 等操作下会内部重置 AVAudioSession，设置为 NO 后，将不再重置
 */
@property (nonatomic, assign) BOOL audioSessionResetEnabled;

@end
```

**变更**
 * 客户端反垃圾针对关键字特殊字符优化：增加特殊字符转义
 * 聊天室批量更新通知（317 类型）内容解析异常问题修复
 * 点对点音、视频通话未读数逻辑优化

## 6.6.6 (2019-07-19)

**新增**

 * 增加删除时间范围内的本地消息接口

```objc
@protocol NIMConversationManager

@end
/**
 * 删除指定时间范围内的
 *
 * @param session 目标会话
 * @param option 删除消息选项
 * @param block 完成回调
 */
- (void)deleteMessagesInSession:(NIMSession *)session
                         option:(nullable NIMBatchDeleteMessagesOption *)option
                     completion:(nullable NIMDeleteMessagesBlock)block;

@end

```

## 6.5.5 (2019-06-12)
**新增**
超大群是针对大规模群聊场景的功能。目前支持不超过 5000 人的群聊。由于超大群场景较为特殊，并不能支持所有高级群提供的管理功能。目前超大群仅支持群主与普通成员两种身份（开通超大群功能请联系商务）。
目前支持的功能：

 * 基本群操作：拉人入群、踢人、退出、修改群信息,（创建群需要通过服务端 API）;
 * 基本群消息收发、漫游消息、多端同步等;

## 6.5.0 (2019-05-24)
**新增**
 * 群成员邀请人查询

```objc

@protocol NIMTeamManager <NSObject>
/**
 * 获取群成员邀请人 Accid
 * @param teamId      群组 ID
 * @param memberIDs   查询的成员 ID，数目不允许大于 200
 * @param completion 完成后的回调
 */
- (void)fetchInviterAccids:(NSString *)teamID
         withTargetMembers:(NSArray<NSString *> *)memberIDs
                completion:(nullable NIMTeamFetchInviterAccidsHandler)completion;
@end

```

**变更**
 * 群消息转发推送相关设置优化
 * 本地消息搜索优化
 * 删除好友备注时多端设备同步删除场景优化

## 6.3.0 (2019-04-18)
**新增**
 * 清空点对点历史消息

```objc
@protocol NIMConversationManager <NSObject>

/**
 * 清空点对点会话对应本地和服务端的消息
 *
 * @param sessions 目标会话列表
 * @param option 清空消息选项
 * @param completion 完成回调
 * @discussion 只支持点对点，清空本用户的服务端历史消息，不影响对方。如果不设置清空选项，服务端默认会同时清空漫游消息。
 */
- (void)deleteSelfRemoteSession:(NIMSession *)session
                         option:(nullable NIMClearMessagesOption *)option
                     completion:(nullable NIMRemoveRemoteSessionBlock)completion;
@end

```

 * 删除好友同时是否删除备注

```
/**
 * 好友协议
 */
@protocol NIMUserManager <NSObject>

/**
 * 删除好友
 *
 * @param userId      好友 ID
 * @param remove      是否同时删除备注
 * @param completion 完成回调
 */
- (void)deleteFriend:(NSString *)userId
         removeAlias:(BOOL)remove
          completion:(nullable NIMUserBlock)completion;
@end

```

**变更**
 * 修复登出时本地缓存保存路径异常
 * 修复音视频点对点加入房间超时未通知对端挂断异常
 * 修复音频设备获取时数组越界
 * NIMKit 更新 SDWebImage 版本

## 6.2.0 (2019-03-14)
**新增**
 * 使用短链换长链接口

```objc

@interface NIMResourceManager : NSObject
/**
 * 使用短链换源链
 *
 * @param sho 实时互动 ode    短链
 * @param completion   完成回调
 * @discussion 当用户后台配置了 NOS 文件安全，文件上传的 URL 为短链，无法直接下载，
 * 可通过该接口换取源链
 */
- (void)fetchNOSURLWithURL:(NSString *)sho 实时互动 ode
              completion:(NIMFetchURLCompletion)completion;

@end
```
 * 群列表同步完成时回调

```
@protocol NIMLoginManagerDelegate <NSObject>
@optional
/**
 * 群用户同步完成通知
 * @param success 群用户信息同步是否成功
 */
- (void)onTeamUsersSyncFinished:(BOOL)success;

@end
```
**变更**
 * NOS 文件上传、下载接口支持短链
 * 话单消息支持存云端、从历史消息获取
 * 黑名单消息在漫游、多端同步、历史消息获取时包含是否在黑名单状态
 * 修复异步发送消息接口发送自定义消息或者普通消息导致发送失败的问题

## 6.1.0 (2019-01-22)
**新增**
 * 历史消息迁移备份相关操作。导出备份，更新备份，获取备份，导入备份，取消操作

```
 /**
 导出历史消息到本地文件

 @param delegate 自定义消息的处理 delegate
 @param progress 导出进度更新回调
 @param completion 导出完成回调
 */
- (void)exportMeessageInfosWithDelegate:(id<NIMExportMessageDelegate>)delegate
                               progress:(NIMExportMessageProgress)progress
                             completion:(NIMExportMessageComletion)completion;

/**
 导入历史消息

 @param infoFilePath 已解码并序列化了的本地历史消息文件路径
 @param delegate 自定义消息的处理 delegate
 @param progress 导入进度更新回调
 @param completion 导入完成回调
 */
- (void)importMessageInfosAtPath:(NSString *)infoFilePath
                        delegate:(id<NIMImportMessageDelegate>)delegate
                        progress:(NIMImportMessageProgress)progress
                      completion:(NIMImportMessageCompletion)completion;

/**
 取消 导出/导入 历史消息操作
 */
- (void)cancelMigrateMessages;

/**
 更新历史消息备份信息

 @param URL 历史消息备份的 URL
 @param key 历史消息备份的加密 key
 @param completion 更新信息的完成回调
 */
- (void)updateMigrateMessageInfoWithURL:(NSString *)URL key:(NSString *)key completion:(NIMUpdateMigrateMessageCompletion)completion;

/**
 获取历史消息备份信息

 @param completion 获取历史消息备份的完成回调
 */
- (void)fetchMigrateMessageInfo:(NIMFetchMigrateMessageCompletion)completion;

```

 * 撤回消息通知增加属性。是否属于漫游消息撤回，消息附带的附言

```

/**
 * 撤回通知
 */
@interface NIMRevokeMessageNotification : NSObject

/**
 * 撤回操作是否属于漫游消息
 */
@property (nonatomic, readonly, getter=isRoaming) BOOL roaming;

/**
 * 撤回的附言
 */
@property(nullable, nonatomic, copy) NSString *postscript;

```

 * 异步发送消息

```
/**
 * 异步发送消息
 *
 * @param message 消息
 * @param session 接收方
 * @param completion 发送完成后的回调，这里的回调完成只表示当前这个函数调用完成，需要后续的回调才能判断消息是否已经发送至服务器
 */
- (void)sendMessage:(NIMMessage *)message
          toSession:(NIMSession *)session
         completion:(nullable void(^)(NSError * __nullable error))completion;
```
 * 取消发送消息

```
/**
 * 取消正在发送的消息
 *
 * @param message 目标消息
 *
 * @param completion 完成回调
 *
 * @return 是否调用成功
 */
- (BOOL)cancelSendingMessage:(NIMMessage *)message;
```

**变更**

```
/**
 * 邀请用户入群
 *
 * @param users       用户 ID 列表
 * @param teamId      群组 ID
 * @param postscript 邀请附言
 * @param attach      扩展消息
 * @param completion 完成后的回调
 */
- (void)addUsers:(NSArray<NSString *> *)users
          toTeam:(NSString *)teamId
      postscript:(NSString *)postscript
          attach:(NSString *)attach
      completion:(nullable NIMTeamMemberHandler)completion;
```

## 5.9.0 (2018-11-28)
**新增**
 * 信令 SDK 频道相关操作。创建频道、加入频道、离开频道、关闭频道

```
/**
 创建频道

 @param request 创建频道请求
 @param completion 完成回调
 @discussion 该接口用户创建频道，同一时刻频道名互斥，不能重复创建。但如果频道名缺省，服务器会自动分配频道 ID。对于频道在创建后如果没人加入，有效期 2 小时，当有成员加入后会自动延续频道有效期。当主动关闭频道或者最后一个成员退出后 2 小时后频道销毁。
 @discussion 错误码 200:成功 10405:房间已存在
 */
- (void)signalingCreateChannel:(NIMSignalingCreateChannelRequest *)request
                    completion:(nullable NIMSignalingCreateChannelBlock)completion;

/**
 关闭频道

 @param request 关闭频道请求
 @param completion 完成回调
 @discussion 该接口可以由创建者和频道内所有成员调用，无权限限制。调用该接口成功后，其他所有频道内的成员都回收到频道结束的通知，被动离开频道。此时其他成员需要调用离开接口，也不会收到别人的离开通知。
 @discussion 错误码 200:成功 10406:不在房间内
 */
- (void)signalingCloseChannel:(NIMSignalingCloseChannelRequest *)request
                   completion:(nullable NIMSignalingOperationBlock)completion;

/**
 加入频道

 @param request 加入频道请求
 @param completion 完成回调
 @discussion 错误码 200:成功 10407:已经房间内 10420:已经在房间内（自己的其他端） 10419:房间人数超限 10417:uid 冲突
 */
- (void)signalingJoinChannel:(NIMSignalingJoinChannelRequest *)request
                  completion:(nullable NIMSignalingJoinChannelBlock)completion;

/**
 离开频道

 @param request 离开频道请求
 @param completion 完成回调
 @discussion 该接口用于自己退出频道，但不对频道进行销毁
 @discussion 错误码 200:成功 10406:不在房间内
 */
- (void)signalingLeaveChannel:(NIMSignalingLeaveChannelRequest *)request
                   completion:(nullable NIMSignalingOperationBlock)completion;

```

**新增**

 * 独立呼叫信令邀请加入频道、取消邀请、接受邀请、拒绝邀请相关接口

```
/**
 邀请加入频道

 @param request 邀请加入频道请求
 @param completion 完成回调
 @discussion 该接口用于邀请对方加入频道，邀请者必须是创建者或者是频道中成员。如果需要对离线成员邀请，可以打开离线邀请开关并填写推送信息。被邀请者在线后通过离线通知接收到该邀请，并通过房间信息中的 invalid_字段判断房间的有效性，也可以对所有离线消息处理后判断该邀请是否被取消。
 @discussion 错误码 200:成功 10404:房间不存在 10406:不在房间内（自己）10407:已经房间内（对方）10419:房间人数超限 10201:对方网易云信不在线 10202:对方推送不可达
 */
- (void)signalingInvite:(NIMSignalingInviteRequest *)request
             completion:(nullable NIMSignalingOperationBlock)completion;

/**
 取消邀请

 @param request 取消邀请请求
 @param completion 完成回调
 @discussion 错误码 200:成功 10404:房间不存在 10408:邀请不存在或已过期 10409:邀请已经拒绝 10410:邀请已经接受
 */
- (void)signalingCancelInvite:(NIMSignalingCancelInviteRequest *)request
                   completion:(nullable NIMSignalingOperationBlock)completion;

/**
 拒绝邀请

 @param request 拒绝邀请请求
 @param completion 完成回调
 @discussion 拒绝邀请后用户也可以通过加入频道接口加入频道，接口的使用由用户的业务决定
 @discussion 错误码 200:成功 10404:房间不存在 10408:邀请不存在或已过期 10409:邀请已经拒绝 10410:邀请已经接受
 */
- (void)signalingReject:(NIMSignalingRejectRequest *)request
             completion:(nullable NIMSignalingOperationBlock)completion;

/**
 接受邀请

 @param request 接受邀请请求
 @param completion 完成回调
 @discussion 接受频道接口
 不开自动加入开关：该接口只接受邀请并告知邀请者，并同步通知自己的其他在线设备，但不会主动加入频道，需要单独调用加入接口
 打开自动加入开关：该接口为组合接口，等同于先调用接受邀请，成功后再加入房间。
 @discussion 错误码 200:成功 10404:房间不存在 10408:邀请不存在或已过期 10409:邀请已经拒绝 10410:邀请已经接受 10407:已经房间内 10420:已经在房间内（自己的其他端） 10419:房间人数超限 10417:uid 冲突
 */
- (void)signalingAccept:(NIMSignalingAcceptRequest *)request
             completion:(nullable NIMSignalingAcceptBlock)completion;
```

**新增**

 * 独立呼叫信令自定义控制指令

```
/**
 自定义控制指令

 @param request 自定义控制指令请求
 @param completion 完成回调
 @discussion 该接口用于在频道中透传一些自定义指令，协助频道管理。该接口允许非频道内成员调用，但接收者必须是频道内成员或创建者
 @discussion 错误码 200:成功 10404:房间不存在 10406:不在房间内（自己或者对方）
 */
- (void)signalingControl:(NIMSignalingControlRequest *)request
              completion:(nullable NIMSignalingOperationBlock)completion;
```

**新增**
 * 创建高级群时可以设置自定义群人数上限

```objc

@interface NIMCreateTeamOption : NSObject

/**
 * 设置群最大人数上限
 * @discussion 默认为 0，表示使用默认人数上限
 */
@property (nonatomic,assign)    NSUInteger maxMemberCountLimitation;

@end

```

**变更**
 * 撤回消息支持 apns 推送通知

```objc

@interface NIMMessage : NSObject

@property (nullable,nonatomic,copy) NSString *apnsContent;

@property (nullable,nonatomic,copy) NSDictionary *apnsPayload;

@end

```

## 5.7.0 (2018-10-11)
**新增**
 * 登录客户端描述新增自定义信息字段

```objc

@interface NIMLoginClient : NSObject

/**
 * 自定义信息，最大 32 个字符。目前 android 多端登录，TV 端和手表端，可以通过该字段区分
 */
@property (nullable,nonatomic,copy,readonly)     NSString *customTag;

@end

```

**新增**
 * NIM SDK 配置项目 新增自定义信息字段

```objc

@interface NIMSDKConfig : NSObject

/**
 客户端自定义信息，用于多端登录时同步该信息
 */
@property (nonatomic,copy) NSString *customTag;

@end

```

**新增**
 * 聊天室协议新增批量更新聊天室通用队列元素接口

```objc

@protocol NIMChatroomManager <NSObject>
/**
 * 批量更新聊天室通用队列元素，权限由 NIMChatroom 的 queueModificationLevel 决定
 *
 * @param request    聊天室队列批量请求
 * @param completion 请求回调
 */
- (void)batchUpdateChatroomQueueObject:(NIMChatroomQueueBatchUpdateRequest *)request
                       completion:(nullable NIMChatroomQueueBatchUpdateHandler)completion;
@end

```
**优化**
 * 文件上传支持快传，即上传重复的大文件上传将不不再需要重复传输，相关接口内部优化

**新增**
 * 增加某个最近的空白对话

```objc

@protocol NIMConversationManager <NSObject>
/**
 * 增加某个最近空白会话
 *
 * @param recentSession 待增加的最近空白会话
 * @discussion 异步方法
 */
- (void)addEmptyRecentSessionBySession:(NIMSession *)session;
@end

```

**变更**
 * apns 推送文案字数限制在 500 字

::: note note
V5.5.0 及其他历史版本，请参考 [历史版本更新日志](/docs/TM5MzM5Njk/jUzNjU2MjQ)。
:::

::: details 单击展开 8.9.109 (2022-12-15) ~ 8.9.128 (2024-04-11) 版本 NIM SDK 的更新日志。

⭐<span style="font-size:16px;"><b><span id="[8.9.128 - 2024-04-11">8.9.128 (2024-04-11)</span></b></span>

NIM iOS SDK 中新增 PrivacyInfo.xcprivac 隐私文件，兼容苹果公司的隐私更新。具体导入方式请参考 [苹果隐私策略说明](https://doc.yunxin.163.com/messaging/concept/TM5ODM1NDQ?platform=iOS)。

⭐<span style="font-size:16px;"><b><span id="[8.9.127 - 2024-03-28">8.9.127 (2024-03-28)</span></b></span>

修复已知问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.126 - 2024-03-20">8.9.126 (2024-03-20)</span></b></span>

- 优化信令模块（呼叫功能）。
- 其他内部优化。

⭐<span style="font-size:16px;"><b><span id="[8.9.125 - 2024-03-07">8.9.125 (2024-03-07)</span></b></span>

修复已知问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.124 - 2024-02-02">8.9.124 (2024-02-02)</span></b></span>

**新增特性**

新增动态查询连续完整的历史消息功能，具体请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS#动态查询某段时间内的历史消息)。

相较于频繁从云端获取，该查询方法在保证历史消息完整的同时，减少了耗时和耗能。

<!--私有化分支 未合入
- 支持在群免打扰状态下设置特别关注的群成员（包括高级群和超大群）。在开启群免打扰时，仍能收到特别关注的成员发送的消息提醒。
-->

**API 变更**

方法/类/枚举 | 说明
---- | ----
`getMessagesDynamically` | 动态查询连续完整的历史消息。
<!--
`NIMTeamManager.addTeamMembersFollow` | 添加高级群中需要特别关注的成员列表。
`NIMTeamManager.removeTeamMembersFollow` | 移除高级群中需要特别关注的成员列表。
`NIMSuperTeamManager.addTeamMembersFollow` | 添加超大群中需要特别关注的成员列表。
`NIMSuperTeamManager.removeTeamMembersFollow` | 移除超大群中需要特别关注的成员列表。
`NIMTeamMember` | 群成员属性中新增 `followAccountIds` 字段，表示该用户特别关注的群成员列表。
-->

⭐<span style="font-size:16px;"><b><span id="[8.9.123 - 2024-01-12">8.9.123 (2024-01-19)</span></b></span>

**新增特性**

- 支持按照群成员类型查询成员列表信息。（高级群和超大群）
- 支持按照关键字检索成员。（仅超大群）

**API 新增**

- 新增 `NIMSuperTeamManager.searchTeamMember` 方法按照关键字检索超大群成员。

    ```Objective-C
    - (void)searchTeamMembers:(NIMTeamMemberKeywordSearchOption *)option
                completion:(nullable NIMTeamMemberSearchResultHandler)completion;
    ```

    `NIMTeamMemberKeywordSearchOption` 参数说明：

   - `teamId`：高级群 ID。
   - `keyword`：查询使用的关键字。
   - `offset`：查询偏移，首次传 0，下一次调用传入上一次返回的 `offset`。
   - `order`：[`NIMMessageSearchOrder`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/dc9/_n_i_m_message_search_option_8h.html#a3d8891c421b5dfabf77872e4e9bd39c0)，查询方向，即返回结果按照 `joinTime`（进群时间）升序或降序排序。
   - `limit`：本次查询最大数量，默认为 10。

- 新增 `NIMTeamManager.getTeamMemberList` 和 `NIMSuperTeamManager.getTeamMemberList` 方法按照群成员类型查询高级群和超大群成员。

    ```Objective-C
    - (void)getTeamMemberList:(NSString *)teamId
                    option:(NIMTeamMemberRoleTypeSearchOption *)option
                completion:(nullable NIMTeamMemberSearchResultHandler)completion;
    ```
    `NIMTeamMemberRoleTypeSearchOption` 参数说明：

    - `teamId`：群组 ID
    - `roleTypes`：[`NIMTeamMemberType`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d9b/_n_i_m_team_defs_8h.html#a0ad00add7dc1ed3cd62072968dd1788d)，群成员角色类型。
    - `offset`：查询偏移，首次传 0，下一次调用传入上一次返回的 `offset`。
    - `order`：[`NIMMessageSearchOrder`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/dc9/_n_i_m_message_search_option_8h.html#a3d8891c421b5dfabf77872e4e9bd39c0)，查询方向，即返回结果按照 `joinTime`（进群时间）升序或降序排序。
    - `limit`：本次查询最大数量，默认为 10。

⭐<span style="font-size:16px;"><b><span id="[8.9.122 - 2023-12-27">8.9.122 (2023-12-27)</span></b></span>

**新增特性**

- 支持按会话类型批量清理未读数和查询未读数，具体请参考 [最近会话](https://doc.yunxin.163.com/messaging/guide/TE0NzkwMzE?platform=iOS)。
- 优化蓝牙音频录制与播放功能。
- 优化短时间内发送群消息已读回执过多而导致报错的问题。

**API 新增**

API | 描述
---- | ----
[`markMessagesReadOfType::`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#abc89bc3c87a258139d8541604d763f98) | 将会话类型批量清理未读数（标记已读）。
[`messagesReadOfType:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/dfa/protocol_n_i_m_conversation_manager_delegate-p.html#adcb0b150dd2d2ccc7a4bf92995a29b4e) | 会话消息已读的回调。
[`unreadCountOfType:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#ad793fdc223d31f6b501b927b0ee41cac) | 按会话类型获取未读消息数。

⭐<span style="font-size:16px;"><b><span id="[8.9.121 - 2023-12-08">8.9.121 (2023-12-08)</span></b></span>

新增 `queryRecentSessionsWithLimit:` 方法，用于查询指定数量的最近会话列表，主要适用于当前最近会话数量较多的场景。

⭐<span style="font-size:16px;"><b><span id="[8.9.119 - 2023-10-19">8.9.119 (2023-10-19)</span></b></span>

优化第三方回调动态 Token 登录内部逻辑，具体请参考 [通过第三方回调登录 IM](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS#通过第三方回调登录)。

⭐<span style="font-size:16px;"><b><span id="[8.9.118 - 2023-09-19">8.9.118 (2023-09-19)</span></b></span>

- 优化日志打印逻辑。
- 修复日志模块崩溃问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.116 - 2023-07-18">8.9.116 (2023-07-18)</span></b></span>

修复日志模块偶现的崩溃问题。

<!--由于安卓还未上线，后续和安卓一起展示
- `SDKConfig` 新增 `disableReport` 字段，支持配置是否上报数据。
-->

⭐<span style="font-size:16px;"><b><span id="[8.9.115 - 2023-06-15">8.9.115 (2023-06-15)</span></b></span>

优化内部逻辑。

⭐<span style="font-size:16px;"><b><span id="[8.9.114 - 2023-05-16">8.9.114 (2023-05-16)</span></b></span>

- 新增 `TeamById2` 接口，用于根据群组 ID 在本地缓存中查询具体的群组信息。该接口解决了历史接口（`TeamById`）频繁调用而引起的问题，因此建议使用新接口。
- 优化加载头像的日志打印占日志文件过多的问题。
- 调整 NOS 上传分片大小。
- 修复 SDK 打包上传时提示警告信息的问题。
- 修复 `decodeMessageFromData` 方法没有反序列化 `remoteExt` 属性的问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.113 - 2023-04-23">8.9.113 (2023-04-23)</span></b></span>

- IM & 聊天室登录支持采用动态 Token 鉴权 & 动态 LoginExt 鉴权的场景。
- 修复获取本地历史记录传入 order 无效的问题。
- 修复清除过云端消息的会话无法收到漫游消息的问题。
- 修复由于数据库备份引起的多线程访问冲突问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.111 - 2023-03-31">8.9.111 (2023-03-31)</span></b></span>

- 引入 NIM SDK 时，支持去除 NIMFtsDB 这个 framework 包。

    开发者引入时可自行选择是否去除 NIMFtsDB，如去除可缩减包体积大小。

- [第三方回调登录](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS#通过第三方回调登录)支持第三方服务器采用动态 token 鉴权的场景。

    如果用户登录 IM 时 token 已过期，网易云信服务端会重新向第三方服务器发起登录回调请求，并获取新的 token。

⭐<span style="font-size:16px;"><b><span id="[8.9.110 - 2023-02-13">8.9.110 (2023-02-13)</span></b></span>

修复部分已知问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.109 - 2022-12-15">8.9.109 (2022-12-15)</span></b></span>

**SDK 包体积增量大小对比**

架构 | IPA 解压并安装后的增量大小 ||
^^ | 稳定版（v8.9.109） | 开发版（v9.7.0）
---- | ---- | ----
arm64 | 6.7MB | 10.5MB

**新增特性**

支持聊天室定向消息功能。[发送聊天室消息](https://doc.yunxin.163.com/messaging/guide/jQ0MjQ0NDI?platform=iOS#%E8%81%8A%E5%A4%A9%E5%AE%A4%E6%B6%88%E6%81%AF%E6%94%B6%E5%8F%91) 支持消息接收者列表。

**问题修复**

修复已知问题。

⭐<span style="font-size:16px;"><b><span id="[8.9.108 - 2022-11-08">8.9.108 (2022-11-08)</span></b></span>

**SDK 包体积增量大小对比**

架构 | IPA 解压并安装后的增量大小 ||
^^ | 稳定版（v8.9.108） | 开发版（v9.6.3）
---- | ---- | ----
arm64 | 9.4MB | 11.4MB

**新增特性**

支持聊天室动态登录。

**问题修复**

- 修复 Thread 消息查询结果包含已撤回和删除消息的问题。
- 修复独立模式登录聊天室异常报错的问题。
- 修复自己发出消息的回调中发送者昵称信息为空的问题。
- 修复其他已知问题。
:::