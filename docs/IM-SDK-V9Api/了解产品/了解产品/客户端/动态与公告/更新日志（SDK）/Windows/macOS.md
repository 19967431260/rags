<!--keywords: 更新日志,新增,修改,更新 -->

本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）稳定版 Windows/macOS 端 v9.x.x 及以下版本的更新日志。有关 v10.x.x 开发版，请参考《IM 即时通讯 V10》[Windows/macOS 更新日志](https://doc.yunxin.163.com/messaging2/concept/zY1NDUxNzc?platform=client)。

## **近期重要更新**

- 新增全文检索能力，提升查询效率，具体请查看 [消息全文检索](https://doc.yunxin.163.com/messaging/guide/DQxNTQ0NDk?platform=pc#消息全文检索)。
- 新增鸿蒙终端类型的解析。
- 支持圈组本地缓存能力，为方便用户按需存储圈组消息草稿，可以向本地数据库插入文本消息，同时可删除和查询该缓存消息，具体请参考 [插入本地圈组消息草稿](https://doc.yunxin.163.com/messaging/docs/zU1NjU5MDY?platform=pc)。

## 9.20.16 (2025-09-28)

优化已知问题。

## 9.19.0 (2024-10-16)

新增 AI 数字人功能。详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。

## 9.18.0 (2024-09-05)

- 提升网络稳定性。
- 内部多项优化。

## <span id="9.16.11 (2024-08-19)">9.16.11 (2024-08-19)</span>

修复在离线期间被拉入群组，修改群名称未生效的问题。

## <span id="9.16.10 (2024-08-14)">9.16.10 (2024-08-14)</span>

优化 Windows 机械硬盘初次登录速度慢的问题。

## <span id="9.16.9 (2024-07-26)">9.16.9 (2024-07-26)</span>

优化群 `valid` 字段的内部更新逻辑。

## <span id="9.16.8 (2024-07-17)">9.16.8 (2024-07-17)</span>

- 将发送 P2P 消息已读回执的时间修改为消息时间，而非服务器时间。
- 修复群成员信息变更通知中群成员对象携带的 `invalid` 属性异常的问题。

## <span id="9.16.7 (2024-07-08)">9.16.7 (2024-07-08)</span>

修复超大群消息未计入未读数的问题。

## <span id="9.16.6 (2024-06-28)">9.16.6 (2024-06-28)</span>

- 修复断网重连失败的问题。
- 修复 `GetMessagesDynamically` 接口在关闭自动下载的情况下仍会自动下载图片缩略图的问题。
- 修复开启融合存储后，相同设备登录多个账号上传凭证复用导致资源被覆盖的问题。
- 修复其他已知问题。

## <span id="9.16.5 (2024-05-22)">9.16.5 (2024-05-22)</span>

修复已知问题。

## <span id="9.16.4 (2024-05-20)">9.16.4 (2024-05-20)</span>

修复已知问题。

## <span id="9.16.3 (2024-05-15)">9.16.3 (2024-05-15)</span>

**新增特性**

新增全文检索能力，提升查询效率，具体请查看 [消息全文检索](https://doc.yunxin.163.com/messaging/guide/DQxNTQ0NDk?platform=pc#消息全文检索)。

**API 变更**

方法/回调/类 | 说明
---- | ----
`QueryMessagesByKeywordAsync` | 根据关键字在本地查询关联消息的内容，本接口使用全文检索引擎进行查询。
`IsMessageIndexEstablished` | 判断是否已经同步完成所有旧消息索引。
`BuildMsglogIndexes` | 构建历史消息索引，以提供全文检索接口快速查询内容。
`CancelMsglogIndexesBuilding` | 停止历史消息的索引构建。

**缺陷修复**

修复超大群通知计入未读数的问题。

## <span id="9.16.1 (2024-04-26)">9.16.1 (2024-04-26)</span>

内部优化。

## <span id="9.16.0 (2024-04-16)">9.16.0 (2024-04-16)</span>

**新增特性**

新增鸿蒙终端类型的解析。

**功能优化**

- 优化 HTTP DNS 模块。
- 升级高可用 SDK 至 V2.4.1 版本。

**API 变更**

方法/回调/类 | 说明
---- | ----
[`NIMClientType`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/nim__client__def_8h.html#ac527fbe48688134f69a107d4b9d3ee89) | 新增 HarmonyOS 客户端，多端登录支持鸿蒙客户端类型的解析。

## <span id="9.15.4 (2024-03-28)">9.15.4 (2024-03-28)</span>

修复已知问题。

## <span id="9.15.1 (2024-03-01)">9.15.1 (2024-03-01)</span>

修复 macOS 升级引起的数据库打开失败的问题。

## <span id="9.15.0 (2024-02-23)">9.15.0 (2024-02-23)</span>

**新增特性**

- 支持圈组本地缓存能力，为方便用户按需存储圈组消息草稿，可以向本地数据库插入文本消息，同时可删除和查询该缓存消息，具体请参考 [插入本地圈组消息草稿](https://doc.yunxin.163.com/messaging/docs/zU1NjU5MDY?platform=pc)。
- 支持将发送失败的消息自动缓存到本地，可通过查询圈组历史消息（[`GetMessages`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_message.html#a367873688ad7911b2ba9210282c9cd33)）时选择是否包含发送失败（`include_local_messages`）的消息实现。
- 支持本地查询 Thread 消息功能。

**功能优化**

优化 `QueryMsgOfSpecifiedTypeInASessionAsync` 接口，优化后，该接口支持在超大群会话中搜索消息。

**API 变更**

方法/类/枚举 | 说明
---- | ----
`InsertOrReplaceTextCache` | 新增接口，用于向本地数据库插入一条缓存数据，如果该频道下已经存在数据，则被新数据覆盖。
`DeleteTextCache` | 新增接口，用于删除圈组本地缓存数据。
`GetTextCache` | 新增接口，用于查询圈组本地缓存数据。
`GetMessages` | 该方法的入参 `QChatGetMessagesParam` 新增 `include_local_messages` 字段，表示是否查询发送失败的圈组消息。
`QueryLocalThreadHistoryMessages` | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息的数量。

<!--私有化分支 未合入

## <span id="9.14.4 (2024-02-02)">9.14.4 (2024-02-02)</span>

**新增特性**

支持在群免打扰状态下设置特别关注的群成员（包括高级群和超大群）。在开启群免打扰时，仍能收到特别关注的成员发送的消息提醒。

**API 变更**

方法/类/枚举 | 说明
:---- | :----
[`nim::Team::AddTeamMembersFollow`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_team.html#a1acf5d53483d1a338b02e89d3454f8ac) | 添加高级群中需要特别关注的成员列表。
[`nim::Team::RemoveTeamMembersFollow`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_team.html#a970f4f8d4d5b4e40ad9e4743024c9920) | 移除高级群中需要特别关注的成员列表。
[`nim::SuperTeam::AddTeamMembersFollow`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_super_team.html#a2d8040e7b43ce52d3092a24ec249d73b) | 添加超大群中需要特别关注的成员列表。
[`nim::SuperTeam::RemoveTeamMembersFollow    `](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_super_team.html#a6e36a6b8da953a5ff63f7400797783d4) | 移除超大群中需要特别关注的成员列表。
[`nim::TeamMemberProperty`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_team_member_property.html) | 群成员属性中新增 [`GetFollowMember`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_team_member_property.html#a833a6f56b1ff54250feed5a7b0868e2d) 和 [`    SetFollowMember`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_team_member_property.html#a529e832030f5708af4c7ec82adc5009d) 方法，表示获取和更新该用户特别关注的群成员列表。
-->

## <span id="9.14.3 (2024-01-19)">9.14.3 (2024-01-19)</span>

**新增特性**

- 支持根据关键字检索超大群成员。
- 支持根据群成员类型查询群成员列表（包括高级群和超大群）。
- 支持在初始化时对未加密的数据库进行补充加密。

**API 变更**

| API/类/枚举名称 | 说明
---- | ---- |
[`nim::SuperTeam#searchTeamMembers`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_super_team.html#a55ecdc687ef64d163bd58f61e530ea71) | 新增该方法，用于根据关键字检索超大群成员信息。
[`nim::SuperTeam#getTeamMemberList`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_super_team.html#a7e4f78418c3962bd2c1d95a9d8d3a2a3) | 新增该方法，用于根据群成员类型查询超大群成员列表。
[`nim::Team#getTeamMemberList`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_team.html#aab0b94bf34cbd69b4681672971144ec6) | 新增该方法，用于根据群成员类型查询高级群成员列表。
[`SDKConfig`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_s_d_k_config.html) | 初始化参数中新增字段：<li>`encrypt_unencrypted_db_`：是否对未加密数据库补充加密，true：补充加密。false（默认）：不补充加密。<li>`encrypt_unencrypted_db_threshold_ `：补充加密的数据库大小阈值，超过该阈值则忽略补充加密，默认为 0，表示无阈值，不限制补充加密的数据库大小。<note type=note>对未加密数据库进行补充加密会非常耗时，若设置补充加密，建议设置补充加密的数据库大小阈值，忽略较大的未加密数据库。

## <span id="9.14.2 (2023-12-21)">9.14.2 (2023-12-21)</span>

- 适配 macOS 10.13 版本。
- 优化文件下载时断网重连的内部逻辑。

## <span id="9.14.1 (2023-12-04)">9.14.1 (2023-12-04)</span>

内部优化。

## <span id="9.14.0 (2023-11-10)">9.14.0 (2023-11-10)</span>

升级融合存储所需 TLS 库的最低支持版本至 TLS 1.2。

## <span id="9.13.0 (2023-10-11)">9.13.0 (2023-10-11)</span>

- 修复会话未读数多端不一致的问题。
- 修复发送自定义消息时，`attachment` 中的中文被转义的问题。
- 修复清理（`Cleanup`）聊天室引起的崩溃问题。

## <span id="9.12.2 (2023-08-17)">9.12.2 (2023-08-17)</span>

优化手动登录的重连效率。

## <span id="9.12.1 (2023-08-01)">9.12.1 (2023-08-01)</span>

**缺陷修复**

- 修复部分设备初始化失败或崩溃问题。
- 修复设备被踢但还自动登录的问题。

## <span id="9.12.0 (2023-07-07)">9.12.0 (2023-07-07)</span>

**新增特性**

圈组订阅机制支持自动订阅。开启自动订阅后，当用户登录到圈组服务器，无需手动订阅服务器或频道，进入服务器或频道时即可收到消息、事件和系统通知，退出时则自动取消订阅。具体请参考 [圈组订阅机制](https://doc.yunxin.163.com/messaging/docs/TA0ODE3MDY?platform=pc)。

**功能优化**

`SetMultiUnreadCountZeroAsync` 方法支持参数校验，当传入会话数量超过 50 则调用失败并返回错误码 10414。

**API 变更**

API | 说明
---- | ----
`QChatInitParam::auto_subscribe` | 新增圈组自动订阅开启/关闭参数。

## <span id="9.11.0 (2023-05-30)">9.11.0 (2023-05-30)</span>

**新增特性**

- 支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动，具体请参考 [接入第三方机器人](https://doc.yunxin.163.com/TM5MzM5Njk/docs/DA5OTY5NDM?platform=pc)。
- 新增第三方回调动态登录模式，具体请参考 [登录 IM](https://doc.yunxin.163.com/TM5MzM5Njk/docs/jQ4NDI2MDI?platform=pc)。

**功能优化**

- 与聊天室建立连接时，调用 `Exit` 接口马上结束登录。
- 优化登录重连机制的内部逻辑。
- 优化 NOS 文件上传前需要确认备份文件是否与源文件匹配，若不匹配则使用源文件上传。

**缺陷修复**

- 修复调用 `QueryMsgAsync` 方法查询群消息的结果中无用户昵称的问题。
- 修复其他已知问题。

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| `Client::RegRequestLoginExtensionCb` | 获取 IM 动态登录扩展信息，用于实现通过第三方回调动态登录 IM |
| `Chatroom::RegRequestLoginTokenCb` | 获取聊天室动态 Token，用于实现通过动态 Token 登录聊天室 |
| `Chatroom::RegRequestLoginExtensionCb` | 获取聊天室动态登录扩展信息，用于实现通过第三方回调动态登录聊天室 |
| `nim::IMMessage` | 消息体中新增机器人信息字段（`robot_info`），用于实现机器人消息功能
| `GetQuickComments` | 调用获取圈组快捷评论接口返回的数据中新增快捷评论的创建时间，即 `QChatQuickCommentDetail` 中新增评论创建时间字段（`create_time`）

## <span id="9.10.0 (2023-04-11)">9.10.0 (2023-04-11)</span>

**功能优化**

- 优化内部拉黑后的消息重发逻辑。
- 内部升级 libcurl。

**问题修复**

- 修复调用 QueryMsgByIDAysnc 接口会将自己发的文件消息路径修改为临时路径的问题。
- 修复调用 TeamMsgQueryUnreadList 接口查询群消息已读/未读的成员列表异常问题。
- 修复转发文件消息异常的问题。
- 修复其他已知问题。

## <span id="9.9.2 (2023-03-09)">9.9.2 (2023-03-09)</span>

**新增特性**

新增 **[圈组](https://doc.yunxin.163.com/messaging/docs/Tc1NTk0NTA?platform=pc) 用户资料复用 IM 用户资料** 的能力。

- 如果某用户未配置自己的服务器成员信息，该用户进入服务器后的初始成员信息将直接复用对应的 IM 用户资料（目前仅支持复用昵称和头像）。

- 如果某用户在未配置自己的服务器成员信息的情况下修改了自己的 IM 用户资料（昵称或头像），系统通知（枚举值 `kNIMQChatSystemNotificationTypeMyMemberInfoUpdated`）将触发，通知当前用户需要在哪些服务器中重新获取自己的成员信息。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| `CreateTeamAsyncEx` | 创建群组的新接口，默认创建高级群，可以选择 type 创建普通群（即讨论组，当前版本 SDK 中讨论组已废弃，不建议使用） <note type=notice>原创建群接口 [`CreateTeamAsync`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_team.html#aa41e4499bae73a818824bbefc7dddf02) 已废弃。</note> |

**数据结构变更**

- [圈组](https://doc.yunxin.163.com/messaging/docs/Tc1NTk0NTA?platform=pc) 的系统通知类型 [`NIMQChatSystemNotificationType`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/nim__qchat__system__notification__def_8h.html#a68eb284bba17219f9f003e57d5ae414b) 中新增枚举 `kNIMQChatSystemNotificationTypeMyMemberInfoUpdated`，表示修改 IM 用户资料触发的圈组服务器成员信息的联动修改。该系统通知的具体触发条件、接收者和接收条件，请参考 [圈组系统通知概述](https://doc.yunxin.163.com/messaging/docs/TkxMzc1NDg?platform=server)中对 `USER_INFO_UPDATE(35) ` 的说明。

- 圈组系统通知的投递对象类型 `NIMQChatSystemNotificationToType` 新增枚举值 `kNIMQChatSystemNotificationToTypeAccids`，表示发送给指定的用户。

**问题修复**

部分已知问题修复与优化。

## <span id="9.9.0 (2023-02-09)">9.9.0 (2023-02-09)</span>

**新增特性**

SDK 支持查询指定频道中@当前用户的未读消息，同时也支持批量查询消息是否@当前用户。具体请参考 [查询@我的消息](https://doc.yunxin.163.com/TM5MzM5Njk/docs/Dk5MTUwMTI?platform=pc)。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| [`Message::GetMentionedMeMessages`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_message.html#ac1e869752436bb1c34d11727d719927a) | 查询指定频道中@当前用户的未读消息 |
| [`Message::AreMentionedMeMessages`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_message.html#a61b279cf91afa049aecf7da68943475a) | 批量查询消息是否@当前用户 |

**功能优化**

- 修复已读/未读状态显示错误问题。
- 修复其他已知问题。

## <span id="9.8.0 (2022-12-27)">9.8.0 (2022-12-27)</span>

该版本的圈组模块新增了游客功能。

**新增特性**

 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
:--- | :--- | :--- | :---
1 | 游客功能 | 以游客身份进入服务器，可查询部分信息和接收消息，也可接收部分系统通知 | [游客功能](https://doc.yunxin.163.com/TM5MzM5Njk/docs/zgyOTY5NTU?platform=pc)
2 | 频道对游客的可见性 | 创建和更新频道时可设置频道是否对游客可见 | [频道管理](https://doc.yunxin.163.com/messaging/docs/jczMzcwOTE?platform=pc)
3 | 频道分组对游客的可见性 | 如果频道对游客可见，则包含该频道的频道分组也对游客可见，且频道分组的查看模式变更可能导致频道对游客的可见性变更 | [频道分组](https://doc.yunxin.163.com/messaging/docs/DUxOTA3NTM?platform=pc)
4 | 频道可见性变更系统通知 | 新增系统通知类型 `CHANNEL_VISIBILITY_TO_VISITOR_UPDATE`，表示频道对游客的可见性发生变更 | [游客可接收的系统通知](https://doc.yunxin.163.com/TM5MzM5Njk/docs/zgyOTY5NTU?platform=pc#可接收的系统通知)

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| [`Server::EnterAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_server.html#a28ad85fc5c0145da781363de4826e628) | 以游客身份进入服务器 |
| [`Server::LeaveAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_server.html#a6a04d962970a75129adc58fd28912afb) | 以游客身份离开服务器 |
| [`Channel::SubscribeAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_channel.html#a990481b02f2726880d6e4e05cd9ce850) | 以游客身份订阅频道 |
| [`Server::SubscribeAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_server.html#ae654bd2c2fd40cd2c81ea69334aff0db) | 以游客身份订阅服务器 |

**API 变更**

| <div style="width:150px">API</div> | API 说明 | 变更说明 |
| :--- | :--- | :---- |
| `Channel::CreateChannel` | 创建频道 | 新增参数 `visitor_mode`，用于设置频道是否对游客可见 |
| `Channel::UpdateChannel` | 修改频道信息 | 新增参数 `visitor_mode`，用于设置频道是否对游客可见 |

## <span id="9.7.0 (2022-12-2)">9.7.0 (2022-12-2)</span>

**新增特性**

IM 新增动态查询连续完整的历史消息功能，具体请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/docs/DQxNTQ0NDk?platform=pc#动态查询某段时间内的历史消息)。

相较于频繁从云端获取，该查询方法在保证历史消息完整的同时，减少了耗时和耗能。

**API 新增**

API | API 说明
:---- | :----
[`GetMessagesDynamically`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_msg_log.html#abee08cf6596997254c09845fb68e452b) | 动态查询连续完整的历史消息

**功能优化**

- 日志文件按照进程分开保存。
- 修复已知问题。

## <span id="9.6.3 (2022-10-27)">9.6.3 (2022-10-27)</span>

**新增特性**

聊天室模块新增根据标签（Tags）查询聊天室历史消息的功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging/docs/DU5ODU2OTA?platform=pc#根据标签查询历史消息" target="_blank">根据标签查询历史消息</a>。

**API 新增**

V9.6.3 的聊天室模块引入了如下 API。

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
| :--- | :--- |
| <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim__chatroom_1_1_chat_room.html#a5f7f4acd3f4e2ca622cc395fe8edba6a" target="_blank">`GetMessageHistoryByTagsOnlineAsync`</a> | 通过聊天室标签（可多个）来检索聊天室历史消息。 |

**缺陷修复**

修复解析非期望的服务器数据包后未重连的问题。

## <span id="9.6.0 (2022-9-26)">9.6.0 (2022-9-26)</span>

**新增特性**

 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
:--- | :--- | :--- | :---
1 | @身份组 | 支持在圈组发送消息时@指定身份组 | <a href="https://doc.yunxin.163.com/messaging/docs/zYzNzc0OTA?platform=pc#%E5%85%B7%E4%BD%93%E6%B5%81%E7%A8%8B" target="_blank">圈组消息收发</a>
2 | 身份组自定义权限 | 支持通过服务端 API 为身份组添加自定义权限项，帮助开发者快速实现符合自身业务需求的权限管控能力 | <a href="https://doc.yunxin.163.com/TM5MzM5Njk/docs/TA2MzAwNTc?platform=pc" target="_blank">自定义权限</a>

**API 变更**

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> | 变更说明 |
| :--- | :--- |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_message.html#a9ea6079f062c4a4d8fce2d9123ed1721" target="_blank">`Send`</a> | 在圈组的频道中发送消息 | 新增参数 `mention_role_ids`，如传入该参数，则表示发送的消息需要@指定的身份组。@身份组需要拥有 **@身份组** 权限（`kPermissionAtRole`） |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#ab47e3a432d56320db6c69f050b442032" target="_blank">`UpdateServerRole`</a> | 修改服务器身份组 | <ul><li>可配置的权限项新增 **@身份组** （`kPermissionAtRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatPermission 中新增自定义权限项（如果已通过服务端 API 创建），键值大于或等于 10000 的 int 型权限项即为自定义权限项</li></ul> |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#aa45706a7bdb818d42f2a7117e4833c8c" target="_blank">`UpdateChannelRole`</a> | 修改频道身份组 | <ul><li>可配置的权限项新增 **@身份组** （`kPermissionAtRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatPermission 中新增自定义权限项（如果已通过服务端 API 创建），键值大于或等于 10000 的 int 型权限项即为自定义权限项</li></ul> |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#ae70ec95311a4089113884d2f05445d69" target="_blank">`UpdateChannelCategoryRole`</a> | 修改频道分组身份组 | <ul><li>可配置的权限项新增 **@身份组** （`kPermissionAtRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatPermission 中新增自定义权限项（如果已通过服务端 API 创建），键值大于或等于 10000 的 int 型权限项即为自定义权限项</li></ul> |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#a78ac14380c314fe74a8be532503bb1bf" target="_blank">`UpdateChannelCategoryMemberRole`</a> | 修改频道分组用户定制权限 | <ul><li>可配置的权限项新增 **@身份组** （`kPermissionAtRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatPermission 中新增自定义权限项（如果已通过服务端 API 创建），键值大于或等于 10000 的 int 型权限项即为自定义权限项</li></ul> |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#adca112ca2d42e824aa4c60fd901be807" target="_blank">`UpdateMemberRole` | 修改(频道下的）用户定制权限 | <ul><li>可配置的权限项新增 **@身份组** （`kPermissionAtRole`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatPermission 中新增自定义权限项（如果已通过服务端 API 创建），键值大于或等于 10000 的 int 型权限项即为自定义权限项</li></ul> |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#a1ba4c80e20acea58e34492314615233e" target="_blank">`CheckPermissions`</a> | 查询自己是否拥有某些权限 | 支持查询自定义权限（如果已通过服务端 API 创建） |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#a1139ee1ed035b47ac3986d7a2f139cdb" target="_blank">`CheckPermission`</a> | 查询自己是否拥有某个权限 | 支持查询自定义权限（如果已通过服务端 API 创建） |

**优化改进**

优化带有附件的消息处理：
- 在根据消息 ID 查询所有消息的场景中，当存在多消息附件时，会进行处理得到默认的消息附件地址，即调用 <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_msg_log.html#a70c9c553f255cbd8ba34ee72d7359a9e" target="_blank">`QueryMsgByIDAysnc`</a> 方法后，带有附件的消息的 `local_res_path` 字段会被赋予路径。
- 创建多媒体转发消息时，若 url 不存在，则自动从数据库中获取。

## <span id="9.5.2 (2022-9-7)">9.5.2 (2022-9-7)</span>

修复断网场景下进行数据上报引起的崩溃问题。

## <span id="9.5.1 (2022-8-31)">9.5.1 (2022-8-31)</span>

更新 wrapper 层的 CMakeLists.txt，修复 cmake configure 失败的问题。

## <span id="9.5.0 (2022-8-29)">9.5.0 (2022-8-29)</span>

**新增特性**

V9.5.0 的圈组模块新增搜索频道成员功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging/docs/DkyNTAzNDc?platform=pc" target="_blank">搜索服务器和频道</a>。

**优化改进**

优化 LBS 策略。

**新增 API**

V9.5.0 的圈组模块引入了如下 API。

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| <a href="https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_channel.html#a6515b3a07ce2c841e4af701405518c73" target="_blank">`ChannelMemberSearch`</a> | 搜索频道成员 |

## <span id="9.4.0 (2022-8-8)">9.4.0 (2022-8-8)</span>

**新增特性**

V9.4.0 的圈组模块新增如下特性：

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| :--- | :--- | :--- | :--- |
| 1 | 批量查询权限 | 支持查询自己是否拥有某些权限 | [查询当前用户是否拥有某些权限](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DM2NTA4ODU?platformId=60227#查询当前用户是否拥有某些权限) |
| 2 | 以圈组服务器维度处理未读消息数 | 支持订阅服务器所有频道的消息，且支持清空服务器未读数 | [服务器未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA5Nzg5OTU?platformId=60227) |
| 3 | 搜索消息 | 支持分页搜索对用户可见的消息。您可通过 `msg_sub_type` 参数进行相应的上层业务开发，实现消息可见性逻辑。支持配置该参数的 API，请参考下文的 **API 变更** 说明 | [搜索消息](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DE4MDgzNDc?platformId=60227#搜索消息) |

**API 变更**

V9.4.0 的圈组模块引入了如下新增 API 和 变更 API。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| [`CheckPermissions`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_role.html#a1ba4c80e20acea58e34492314615233e) | 查询自己是否圈组内的某些（圈组）权限 |
| [`SearchMsgByPage`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_message.html#a8475cfb252f3ab42756bdad40e3aa2ef) | 分页搜索圈组消息 |
| [`SubscribeAllChannel`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#a37ea6ef0e38328899260aacc60a936ac) | 一次性订阅圈组服务器下最多 200 个频道。单次调用可传入的服务器 ID 数量上限为 10 个。即使多次调用，单个服务器下最多仅能订阅 200 个 频道 |
| [`MarkRead`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#ac3173a3f1308609cb25e479b1497f387) | 清空圈组服务器的未读数 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| :--- | :--- |
| `Message::Send` | 新增入参和回参 `msg_sub_type`，表示消息子类型。该参数可以用来做特殊渲染、可见性判断、动画效果展示等。例如，您可通过该参数开发相应的上层业务逻辑，实现发送消息时设置消息对其他用户的可见性 |
| `Message::Reply` | 新增入参和出参 `msg_sub_type`，表示消息子类型 |
| `Message::Update` | 新增入参和出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetMessages` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetMessagesCache` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetLastMessages` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetMessageHistoryByIds` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetReferMessages` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetThreadMessages` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::GetThreadRootMessagesMeta` | 新增出参 `msg_sub_type`，表示消息子类型 |
| `Message::MessageSearchByPage` | 新增出参 `msg_sub_type`，表示消息子类 |
| `Message::RegRecvCb` | 新增出参 `msg_sub_type`，表示消息子类 |
| `Message::RegUpdatedCb` | 新增出参 `msg_sub_type`，表示消息子类 |

## <span id="9.3.0 (2022-7-25)">9.3.0 (2022-7-25)</span>

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| :--- | :--- | :--- | :--- |
| 1 | 获取服务器未读数 | 获取服务器下所有频道的累加消息未读数 | [获取服务器未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA5Nzg5OTU?platformId=60227) |
| 2 | 获取频道最后一条消息 | 获取多个频道的最后一条消息，从而在频道列表展示各频道的最后一条消息 | [获取频道最后一条消息](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DI1Mzk1MTY?platformId=60227) | |
| 3 | 圈组搜索结果自定义排序 | 搜索圈组服务器和频道的匹配结果，可按自定义排序 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DkyNTAzNDc?platformId=60227) |
| 4 | 查询邀请/申请记录 | 查询服务器的邀请和申请记录，以及用户个人被邀请加入服务器和申请加入服务器的记录 | [查询申请/邀请的历史记录](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA3Nzc3MjM?platformId=60227#查询申请/邀请的历史记录) |
| 5 | 生成邀请码 | 拥有 **邀请他人加入服务器的权限** 的用户可生成邀请码，其他用户可通过邀请码加入服务器 | [生成邀请码](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA3Nzc3MjM?platformId=60227#生成邀请码) |
| 6 | 通过邀请码加入服务器 | 获取到邀请码的用户，可通过邀请码加入服务器 | [通过邀请码加入服务器](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA3Nzc3MjM?platformId=60227#通过邀请码加入服务器) |

**优化改进**

新增自动取消订阅逻辑：新增 **频道对当前用户可见性变更** 和 **当前用户进入/退出服务器** 内置系统通知类型。当收到前者时，如存在相应频道的订阅信息，则自动取消订阅该频道的请求。当收到后者（且为退出服务器）时，如存在相应服务器的订阅信息，则自动取消订阅该服务器以及该服务器下所有已订阅频道的请求。圈组的具体订阅机制，请参考 [圈组订阅机制](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TA0ODE3MDY?platformId=60227)。

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
| [`GenerateInviteCode`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#a1f23087f33d128cf1a9be17ec65b1600) | 生成邀请码 |
| [`JoinByInviteCode`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#a62aacd7340736deafb2aab6c53a4dac4) | 通过邀请码加入服务器 |
| [`GetInviteApplyRecordOfServer`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#a260cd4546deec9c9d1488e28754d021f) | 查询服务器下的申请记录和邀请记录 |
| [`GetInviteApplyRecordOfSelf`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#a63734ee537a320797a64733e9b8fd0f7) | 用户查询自己的申请记录和邀请记录 |
| [`RegUnreadCb`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_server.html#ab4be741f8f4c85dc943221df926c896f) | 注册/注销服务器未读数变更回调 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| :--- | :--- |
| `Invite` | 新增 `ttl` 入参（可选），表示加入服务器邀请的有效时长 |
| `Apply` | 新增 `ttl` 入参（可选），表示加入服务器申请的有效时长 |
| `AcceptApply` | 新增 `requestId` 入参（必传），表示加入服务器申请的标识 |
| `RejectApply` | 新增 `request_id` 入参（必传），表示加入服务器申请的标识 |
| `AcceptInvite` | 新增 `request_id` 入参（必传），表示加入服务器邀请的标识 |
| `RejectInvite` | 新增 `request_id` 入参（必传），表示加入服务器邀请的标识 |
| `CreateChannel` | 可创建的频道类型枚举增加枚举值 `kNIMQChatChannelTypeRTC`，表示 实时互动频道。 |
| `UpdateServerRole` | 可修改的服务器身份组权限新增 实时互动频道相关权限、邀请申请管理权限和邀请申请历史记录查看权限 |
| `UpdateChannelRole` | 可修改的频道身份组权限新增 实时互动频道相关权限 |
| `UpdateMemberRole` | 可修改的个人定制权限新增 实时互动频道相关权限 |
| `UpdateChannelCategoryRole` | 可修改的个人定制权限新增 实时互动频道相关权限 |
| `UpdateChannelCategoryMemberRole` | 可修改的频道分组维度的个人定制权限新增 实时互动频道相关权限 |
| `ServerSearchByPage` | 新增入参 `sort`，表示频道的排序条件 |
| `ChannelSearchByPage` | 新增入参 `sort`，表示频道的排序条件 |

## <span id="9.2.8 (2022-7-1)">9.2.8 (2022-7-1)</span>

优化自动重连机制，实现国内外节点平滑迁移。

## <span id="9.2.5 (2022-6-13)">9.2.5 (2022-6-13)</span>

该版本在圈组模块增加了圈组系统通知的类型。

| <div style="width:100px">相关模块</div> | <div style="width:100px">新增特性</div> | <div style="width:60px">相关文档</div> |
| :--- | :--- | :--- |
| 圈组系统通知 | 1. 新增以下 5 种圈组系统通知类型：</br> <ul><li>加入服务器身份组成员</li><li>移除服务器身份组成员</li><li>更新服务器身份组权限</li><li>更新频道身份组权限</li><li>更新频道个人定制权限</li></ul>具体可参考 [`NIMQChatSystemNotificationType`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/nim__qchat__system__notification__def_8h.html#a68eb284bba17219f9f003e57d5ae414b)</br></br>2. 对应新增 5 种圈组系统通知结构体，具体可查看[`QChatSystemNotificationDataBase`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/structnim_1_1_q_chat_system_notification_data_base.html) | [系统通知](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jUwMzY1MDE?platformId=60227) |

## <span id="9.2.1 (2022-5-25)">9.2.1 (2022-5-25)</span>

修复融合存储短链下载无响应的问题。

## <span id="9.2.0 (2022-5-24)">9.2.0 (2022-5-24)</span>

该版本在圈组模块增加了频道分组、消息正在输入状态显示和搜索功能等更新。

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| :--- | :--- | :--- | :--- |
| 1 | 频道分组 | 支持对频道进行分组管理 | [频道分组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DUxOTA3NTM?platformId=60227) |
| 2 | 频道分组黑白名单 | 支持为频道分组设置黑白名单成员/身份组，与频道类型（私密/公开）共同判定频道分组是否对用户可见 | [频道分组黑白名单](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TAxMDc2ODI?platformId=60227) |
| 3 | 频道分组身份组 | 支持在频道分组维度设置身份组和定制权限，增加用户权限控制的层级 | [频道分组身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zc5MDAxNzI?platformId=60227) |
| 4 | 消息正在输入 | 支持显示频道消息正在输入 | [消息正在输入](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DIzODYwNzc?platformId=60227) |
| 5 | 圈组搜索功能 | 支持通过关键字对服务器、频道和服务器成员进行搜索 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DkyNTAzNDc?platformId=60227) |

**API 新增与变更**

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| :--- | :--- |
`CreateChannelCategory` | 创建频道分组 |
`RemoveChannelCategory` | 删除频道分组 |
`UpdateChannelCategory` | 修改频道分组信息 |
`GetChannelCategoriesByID` | 按分组 ID 查询频道分组 |
`GetChannelCategoryChannelsPage` | 分页查询频道分组下频道列表 |
`GetChannelCategoriesPage` | 分页查询频道分组列表 |
`AddChannelCategoryRole` | 创建频道分组身份组。创建后，默认继承服务器身份组的权限。如需更改权限，需调用 `UpdateChannelCategoryRole` |
`RemoveChannelCategoryRole` | 删除频道分组身份组 |
`UpdateChannelCategoryRole` | 更新频道分组身份组。设置频道分组身份组的权限，需调用该方法 |
`GetChannelCategoryRolesPage` | 查询频道分组身份组信息 |
`AddChannelCategoryMemberRole` | 创建频道分组某人的定制权限，创建后还需调用 `UpdateChannelCategoryMemberRole` 才能授予某人权限 |
`RemoveChannelCategoryMemberRole` | 删除频道分组某人的定制权限 |
`UpdateChannelCategoryMemberRole` | 修改频道分组某人的定制权限。创建某人定制权限后，需再调用本方法才能授予某人权限 |
`GetChannelCategoryMemberRolesPage` | 查询频道分组某人的定制权限 |
`UpdateChannelCategoryWhiteBlackRole` | 更新频道分组黑白名单身份组 |
`GetExistingChannelCategoryWhiteBlackRoles` | 根据身份组 ID 查询频道分组白/黑名单身份组列表 |
`GetChannelCategoryWhiteBlackRolesPage` | 分页查询频道分组黑白名单身份组列表 |
`UpdateChannelCategoryWhiteBlackMembers` | 更新频道分组白/黑名单成员 |
`GetExistingChannelCategoryWhiteBlackMembers` | 根据成员 ID 查询频道分组黑白名单列表 |
`GetChannelCategoryWhiteBlackMembersPage` | 分页查询频道分组白/黑名单成员列表 |
`RegRecvTypingEvent` | 监听正在输入事件 |
`SendTypingEvent` | 发送正在输入事件 |
`ServerSearchByPage` | 分页搜索服务器 |
`ServerMemberSearch` | 搜索服务器成员 |
`ChannelSearchByPage` | 搜索频道 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| :--- | :--- |
| [`CreateChannel`](https://doc.yunxin.163.com/messaging/references/pc/doxygen/Latest/zh/classnim_1_1_channel.html#af7457bd81c198bd35e709f69d2e51975) | 新增 `category_id` 和 `sync_mode` 参数，调用时传入 `category_id` 可将频道加入某个频道分组。通过设置 `sync_mode`，可实现频道数据与频道分组数据的同步。具体同步的数据包括查看模式（私密或公开）、黑白名单和身份组权限。 |

## <span id="9.1.0 (2022-4-11)">9.1.0 (2022-4-11)</span>

**新增功能**

- 圈组相关更新
    - 支持 [查询当前登录用户是否拥有特定权限](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DM2NTA4ODU?platformId=60227#查询当前登录用户是否拥有特定权限)。
    - 新增封禁服务器成员功能。
        <!-- - 新增参数 ](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DM2NTA4ODU?platformId=60227#查询当前登录用户是否拥有特定权限)。
        - 支持通过 ](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA3Nzc3MjM?platformId=60227#查询封禁成员)。 -->
    - 新增 Thread 聊天和快捷评论功能。这两个功能的调用方法和示例请参考 [发送消息](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DE4MDgzNDc) 中的相关说明。
    - 新增圈组对安全通（易盾反垃圾）能力的支持。
        - [圈组服务器管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Dk3MzY2MDY?platformId=60227)、[圈组服务器成员管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DA3Nzc3MjM?platformId=60227)、[频道管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jczMzcwOTE?platformId=60227) 和[身份组及特殊权限管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DM2NTA4ODU?platformId=60227) 中新增 ```QChatBusinessAntiSpamInfo``` 参数（结构体）。可通过该参数配置服务器/服务器成员/频道/身份组信息反垃圾。
        - [圈组消息管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DE4MDgzNDc?platformId=60227)中新增 ```QChatMessageAntiSpamInfo``` 参数（结构体）。可通过该参数为消息配置内容安全审核。
    - 新增圈组消息缓存能力。可通过 [初始化](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DcwOTY0MjI?platformId=60227#初始化圈组模块)。
- 其他更新
    - 未读相关操作按会话类型分类能力。可通过 ```sessionType``` 获取、清除相应类型的会话的未读数。

## <span id="9.0.0 (2022-3-14)">9.0.0 (2022-3-14)</span>

**新增功能**

网易云信即时通讯服务全新能力 **圈组** 发布。相关功能介绍和开发集成请分别参考 [什么是圈组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Tc1NTk0NTA)和 [圈组接入流程](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TU1NzExODQ)。

**缺陷修复**

初始化后不登录直接 Cleanup 崩溃。

## 8.11.0 (2022-01-10)

**新增功能**

- 聊天室空间消息 [示例代码](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DU5ODU2OTA?platformId=60227#%E8%81%8A%E5%A4%A9%E5%AE%A4%E5%AE%9A%E5%90%91%E6%B6%88%E6%81%AF)
- 聊天室定向消息 [示例代码](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DU5ODU2OTA?platformId=60227#%E8%81%8A%E5%A4%A9%E5%AE%A4%E5%AE%9A%E5%90%91%E6%B6%88%E6%81%AF)
- 聊天室标签实时更新 [标签介绍](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TQwNDIyNDU?platformId=60227)
- 匿名聊天室和独立聊天室支持第三方 token 鉴权, 进入聊天室时 AuthType 设为 2, 并注册自定义 token 回调(RegCustomTokenCb/nim_chatroom_reg_custom_token_cb)
- 资料反垃圾, 涉及以下接口
  - Enter/nim_chatroom_enter EnterInfo 增加配置反垃圾相关参数
  - IndependentEnter/nim_chatroom_independent_enter EnterInfo 增加配置反垃圾相关参数
  - IndependentEnter2/nim_chatroom_independent_enter2 EnterInfo 增加配置反垃圾相关参数
  - AnonymousEnter/nim_chatroom_enter_with_anoymity EnterInfo 增加配置反垃圾相关参数
  - AnonymousEnter2/nim_chatroom_enter_with_anoymity2 EnterInfo 增加配置反垃圾相关参数
  - UpdateMyUserNameCard/nim_user_update_my_user_name_card 接口 json 扩展增加配置反垃圾相关参数
  - UpdateTeamInfoAsync/nim_team_update_team_info_async 接口 json 扩展增加配置反垃圾相关参数
  - CreateTeamAsync/nim_team_create_team_async 接口 json 扩展增加配置反垃圾相关参数
  - UpdateSuperTeamInfoAsync/nim_super_team_update_team_info_async 接口 json 扩展增加配置反垃圾相关参数
  - UpdateRoomInfoAsync/nim_chatroom_update_room_info_async 接口 json 扩展增加配置反垃圾相关参数
  - UpdateMyRoomRoleAsync/nim_chatroom_update_my_role_async 接口 json 扩展增加配置反垃圾相关参数

## 8.10.0 (2021-12-23)

**缺陷修复**

- QueryLastFewSessionAsync 查询出来的会话都没有未读数

**新增功能**

- 支持 S3 存储

## 8.9.0 (2021-12-03)

**缺陷修复**

- 修复 update msglog 时 SQL 语句错误导致返回 21

**新增功能**

- 从 8.9.0 开始不再支持 xp 系统
- 提升好友数至 1 万

## 8.8.0 (2021-11-04)

**缺陷修复**

- 修复离线消息和漫游消息同步顺序可能导致用旧的消息更新会话
- 在注册回调执行函数之后部分带有指针的回调到用户线程后超出生命周期

**新增功能**

- 新增根据时间排序的全文检索消息接口
- 批量添加聊天室队列元素

## 8.7.2 (2021-09-28)

**新增功能**

 - 安全通增加反垃圾自定义过滤规则和回执 [C](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_C/html/nim__talk__def_8h.html#aef5a6b4b2d2145ddde2499e17e2e2745)/[C++](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/structnim_1_1_message_setting.html#a058f458061eeaaa627be93c413253b89) （2021 年 9 月 28 日前接入安全通（易盾反垃圾）的客户，需要升级到最新版安全通能力才可使用此接口能力，升级请联系商务经理）

**缺陷修复**

 - NOS 短链换长链后下载资源失败

## 8.7.0 (2021-08-25)

**新增功能**

 - 聊天室撤回消息通知，用户可关注聊天室通知 kChatRoomNotificationIdRecallMessage 在业务层删除指定消息
 - 聊天室队列支持指定队列所有人 [C++](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#a96395c0772452d119cdc39678ab8b7ee)

**缺陷修复**

 - 漫游消息会重复下发问题
 - 发送多次已读回执问题
 - 多次调用 Cleanup 死锁
 - 保存时间戳到数据库有溢出问题

## 8.6.2 (2021-08-06)

**缺陷修复**

 - C++ 封装层代码在 VS2013 下无法编译通过

## 8.5.0 (2021-06-17)

**新增功能**

 - 增加服务器全文检索接口 [C](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_C/html/nim__msglog_8h.html#a02a62d2551b096141a2d2a760212c2c7)/
[C++](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a5a0a2c0a901d97f3dea015d9d1eb11df)

 - 增加群组已读回执查询重载接口，支持传入指定 IDs 列表查询 [C++](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/classnim_1_1_team.html#a92a07f3cbb8bce0dac5a2126110e4823)

**缺陷修复**

 - 未调用 Cleanup 直接退出应用场景做进一步保护
 - IDE 调试退出场景 NRTC 模块抛出异常
 - 登录地址非自动解析场景下登录失败
 - Node C++ addon 编译后无法执行异步回调
 - 网络重连成功后没有标记重连状态为 false 导致下次无法重连
 - 断线重连过程中登出无效

## 8.4.0 (2021-04-26)

**新增功能**

- 聊天室设置标签标志加入聊天室及按标签发送消息、查询成员详情及总数、禁言能力
    - 登录设置指定标签 [kNIMChatRoomEnterLoginTags](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom__def_8h.html#a895b42535f3ce945ce40dd4cea8aee57)
    - 登录设置指定通知标签 [kNIMChatRoomEnterNotifyTags](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom__def_8h.html#a3826532c90e33b532522093839eedfe7)
    - 按标签查询指定聊天室成员 [C](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom_8h.html#ae584346f44e389a3ad9407ed88f11804)/[C++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#ab89f8d0f28f70ee3470926e4d8e69157)
    - 按标签查询指定类型成员总数 [C](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom_8h.html#a954a30870d2a1121ef50a79fc3ff1908)/[C++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#a266053b943edbbfababdcff6662f1efa)
    - 根据标签禁言指定成员能力 [C](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom_8h.html#ab1c6b0b420e8819fbda2b5b2b116919b)/[C++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#a97c9dca1e7bbfeef7e4b03c3265d722b)
- 增加本地可读版本号上传至服务器能力
- 删除会话时可以设置是否缓存会话数据，如未读计数等 [C](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__client__def_8h.html#a988b764314617fc0a386f093e162a4b4)/[C++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_s_d_k_config.html#ae0a1d94b1cdb89616586f7727fa398ad)

**功能优化**

- 对 C++ 封装层目录结构及编译方式进行调整，详情请见 [8.4.0 C++ 封装层接入指南](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/index.html)
- 透传高级通知事件 `attach` 字段到应用上层
- 发送图片时若打开文件失败则尝试重新发送图片，最多重试 3 次，失败后上报错误码 [kNIMLocalResMsgFileNotAccess 10403](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__res__code__def_8h.html#a5083ca8fcdb1153b725f6a55e6cbd647a4643c0715bc457cd03598dc8117fab3f)
- 高可用组件稳定性提升
- Windows 及 macOS SDK 功能对齐

**缺陷修复**

- Windows XP 下无法正常加载 SDK 组件
- 聊天室断线重连异常场景崩溃
- 使用 Stick 相关接口置顶会话后查询会话列表返回状态不正确
- 修复群组超过 99 条未读时数据统计不准确问题
- Pin 消息解析 Json 异常崩溃
- 修复 macOS AppDataDir 相对路径 Init 崩溃问题

## 8.3.1 (2021-03-22)

**功能优化**

- 提高 SDK 稳定性

- 优化缺省 lbs 生成规则

**缺陷修复**

- SDK 初始化时对 httpdns 访问过于频繁的问题

## 8.3.0 (2021-03-03)

**新增功能**

- [IM 支持动态登录策略](/docs/TM5MzM5Njk/jQ4NDI2MDI?#动态登录)

- 超大群获取群禁言成员列表 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#a5ca37927e33a5495a99eefc1599a7f05) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a67e3a793a0ed8361fec7edd99c0698fc)

**功能优化**

- 修改日志模块引起的句柄泄露

**缺陷修复**

- 取消消息附件下载操作时可能引起的崩溃

- 上传/下载文件没有进度回调的问题

- 消息已读状态可能不准确的问题

- 邀请已在群内成员(管理员/群主)再次进群后，群成员类型被覆盖为 0 的问题

- 断线重连后消息丢失的问题

- 删除会话最后一条消息后，会话列表中最后一条消息信息不准确的问题

- [nim::Client::Cleanup2](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_client.html#ac43b170258c8f1ce18c4d7b6025f3801)可能假死的问题

## 8.2.5 (2021-02-03)

**功能优化**

- 完善域名高可用策略，提升服务稳定性

**缺陷修复**

- db 加密可能失效的问题

- 非正常场景下卸载 SDK 模块引起的崩溃

## 8.2.0 (2020-12-30)

**新增功能**

- 查询会话列表,可指定最后一条会话消息要排除掉的类型(列表) [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session_8h.html#ae710257c15ab892bac924a42cc05c31e) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#ad930f7237e2d168c59bb781b7ab0cf1a)

- 删除最近联系人,同时指定是否删除漫游消息 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session_8h.html#acf84da1fa9e8d94692636ea3fe1831de) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a8aca6d8913ad3bb59d6969369639aacc)

- 最近联系人项(多条)未读数清零 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session_8h.html#af53d76d4308524c8d7234a7f96efdd15) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a93f4167269e78aee6ca2b6b5b03e5c6d)

- 发送群消息已读回执返回成功/失败/忽略列表 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__team_8h.html#a73b8b33c33948dd9b62d9f3cdfbdc1c3) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_team.html#ae3202918132636fb44b118af4d875dee)

- 查询给定的一组群 ID 详细信息 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__team_8h.html#a69bffc56fc9193a6deb6ce6802ae4547) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_team.html#a0c5423a48d3debf0f1b4f809811d776b)

**功能优化**

- IM 断网及重连检测速度

**缺陷修复**

- SDK 异常退出导致的崩溃

## 8.1.0 (2020-11-13)

**新增功能**

- 调整 IM、聊天室消息去重逻辑
- NOS 下载支持独立 CDN 域名配置
- NOS 下载域名加速支持多域名配置
- 聊天室支持 CDN 消息
- 聊天室新增匿名进入扩展接口, **可传入私有化参数** [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom_8h.html#ac3a6debd92023398e8381e5ac8b465c4)/[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#a578820dd0cf2ff16c1983914363650a5)
- 聊天室新增独立进入扩展接口, **可传入私有化参数** [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__chatroom_8h.html#ab6278cf429a38d7302628eff2c45e049)/[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#a45f7ee53217c51af4ddcc81c372730a8)

**缺陷修复**

- IM、聊天室 SDK 在 windows ucrtbase 版本号为"10.0.10240"时，初始化卡死的问题
- 增加稳定性，排除可能产生的崩溃

## 8.0.0 (2020-09-28)

**新增功能**

- 删除某一会话的云端的历史记录 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#a8cee3b65c1143f2220e1c388660a3639)/[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a8018eb61161b95141017058f66a83bcc)
- 单向删除同一会话多条消息("同时删除本地与云端") [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#ad5abffcc5d5d579289f73a75dcce29fa)/[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#aa6a64cecaae61f4163362bf9a4673135)
- 删除指定会话的漫游消息 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session_8h.html#aa25a79ffa505833f99f65405235a737e)/[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a1c097097f2cd0401ca207eaade6ee358)
- 撤回消息可指定扩展参数 [`extra_params`](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__talk__def_8h.html#a54807611fa5db9fefc7bd7c77492dcea) [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__talk_8h.html#a210102cd50be4d81d86d842721fd5570) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk.html#aaf4562ece6b6e9c98ae7859c0b066371)
- 在线会话列表会话数据添加 [`last_message_type(0 表示普通消息，1 表示消息撤回通知)`](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_session_on_line_service_helper_1_1_session_info.html#a22f6a72035f9983e1961a445f76950b3)定义 [c](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session__online__service__def_8h.html#a78a2d38473922013fea669dd8f27b5a0) /[c++](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_session_on_line_service_helper_1_1_session_info.html)

## 7.8.1 (2020-07-29)

**新增功能**

- [获取聊天室成员列表](/docs/TM5MzM5Njk/zY5NzQzNjU?#%E8%8E%B7%E5%8F%96%E8%81%8A%E5%A4%A9%E5%AE%A4%E5%9C%A8%E7%BA%BF%E6%88%90%E5%91%98)新增两种查询类型
  + [**在线固定成员**](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/nim__chatroom__def_8h.html#a279a05aa063f226803f0c2b12f4b72e5a608e318ec31a700e42d4fba3f760614d),查询时时间戳使用" [update_timetag_](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_member_info.html#ad612c1d1c93025b717f2ea7bcf836592) "
  + [**非固定成员**](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/nim__chatroom__def_8h.html#a279a05aa063f226803f0c2b12f4b72e5a9c13bca47814ec060256da8cd4482379),按时间正序排列,查询时时间戳使用" [enter_timetag_](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWindows%E7%AB%AF/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_member_info.html#a089d0ba3e52c285f9d38c0be6a12c601) "

## 7.8.0 (2020-07-21)

**新增功能**

- IM 和聊天室消息体新增易盾反垃圾字段
[nim::MessageSetting::yidun_anti_cheating_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_message_setting.html#a69af10e5d4774309b5025c21acde28da)
[nim_chatroom::ChatRoomMessageSetting::yidun_anti_cheating_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_message_setting.html#a48e4a3848e281fb9a60496b982eb509e)

- IM 和聊天室消息体自定义消息子类型
[nim::IMMessage::sub_type_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_i_m_message.html#a55c7a12192d8113df10b95c1b69e16dd)
[nim_chatroom::ChatRoomMessage::sub_type_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_message.html#a8ba99fc24a8823b1ba26e3e9b9327da8)

- 查询本地历史消息时可以指定消息子类型
bool [nim::MsgLog::QueryMsgByOptionsAsyncEx](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a27269ddfda24d9381efac62fb3caaca1)(const [QueryMsgByOptionsAsyncParam](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log_1_1_query_msg_by_options_async_param.html)& param, const [QueryMsgCallback](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#abd21b7e2e0632825fcfc6a27ee29a253)& cb);

- 第三方回调回来的自定义扩展字段
[nim::IMMessage::third_party_callback_ext_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_i_m_message.html#ad836dc3c93d36ddd4a4c55f8c6aefaed)
[nim_chatroom::ChatRoomMessage::third_party_callback_ext_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_message.html#ae7fda6797cbed13d4eb6b95b2b80a087)
[nim::SendMessageArc::third_party_callback_ext_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_send_message_arc.html#a9db2ee5348c930eac92ff3507302abe3)

- 被踢下线时返回被踢描述以及自定义终端类型
[nim::KickoutRes::kickout_description_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_kickout_res.html#ad6bb88f0cf9164095669af0d514a6352)
[nim::KickoutRes::custom_client_type_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_kickout_res.html#aa40d22b9ebf8bb93bd7129d28e65949d)

## 7.7.2 (2020-06-12)

**新增功能**

- IM 消息添加易盾反垃圾增强反作弊专属字段
    易盾反垃圾增强反作弊专属字段(可选), json string 格式，长度限制 1024, **需开通易盾反垃圾能力**
    + 定义
     [kNIMMsgKeyYiDunAntiCheating](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__talk__def_8h.html#a5ef851f6e7351e482c7c749d2d0391d0)
    [kNIMChatRoomMsgKeyYiDunAntiCheating](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__chatroom__def_8h.html#a0aef2fbcef0f3efe0320dfa88f40fbab)
    + 相关字段
      [nim::MessageSetting::yidun_anti_cheating_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_message_setting.html#a69af10e5d4774309b5025c21acde28da)
      [nim_chatroom::ChatRoomMessageSetting::yidun_anti_cheating_](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim__chatroom_1_1_chat_room_message_setting.html#a48e4a3848e281fb9a60496b982eb509e)

**缺陷修复**

- 获取黑名单不准确的问题

## 7.7.1 (2020-06-01)

**缺陷修复**

- 退出聊天室时导致应用程序卡死的问题

## 7.6.1 (2020-05-13)

**缺陷修复**

- 用户配置本地缓存加密情况下加密未生效的问题

## 7.6.0 (2020-05-13)

**新增功能**

- 独立进入聊天室接口
    + [nim_chatroom::ChatRoom::IndependentEnter](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim__chatroom_1_1_chat_room.html#ab528c210c47bdd2073e2de4c3f069d72)
- 主动日志上报接口
    + [nim::Global::UploadSDKLog](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_global.html#a64f8af65c1d1eaf1de7cd3606b44eecf)
- 消息回复（thread）
    + [nim::Talk::ReplyMessage](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk.html#af945de69bd31309c6243bd86f9f47fc5)

    + [nim::MsgLog::QueryMessageIsThreadRoot](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a8f067d8e364273646b889b614d309b51)

    + [nim::MsgLog::QueryMessageOnline](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#afbdf9e0d6ef7ca859b653e25e784f068)

    + [nim::MsgLog::QueryThreadHistoryMsg](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a037bb6ea1bdc0de5c763faf12b202c2f)

- 会话置顶功能

    此功能 **支持多端同步** 不同于 [nim::Session::SetSessionTop](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a8c2494eca706e36d4b161cddbf901a7e) (仅保存在本地)

    + [nim::Session::QueryStickTopSessionList](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#aabc4175b7d96b876691beb6613efa2d5)

    + [nim::Session::SetToStickTopSession](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a6093107af35e643f8d6893f22a674221)

    + [nim::Session::UpdateToStickTopSession](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#adc0ffd8aac0849b13a1b647e83d3defd)

    + [nim::Session::CancelToStickTopSession](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a73edbc941406d6f0b90f8847064c9d24)

    + [nim::Session::RegSetToStickTopSessionNotifyCB](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#a23e5fc7e8ce1c1546cd7d44ead852878)

    + [nim::Session::RegCancelStickTopSessionNotifyCB](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#ab39d0bd756f32f82e81d5cf2257f67ca)

    + [nim::Session::RegUpdateStickTopSessionNotifyCB](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session.html#aabda56cdedad78c2ceb0c8446caf20a4)

- [消息快捷评论]
    + [nim::TalkEx::QuickComment](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk_ex_1_1_quick_comment.html)

- 收藏功能
    + [nim::TalkEx::Collect](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk_ex_1_1_collect.html)

- 会话消息 PIN 标记
    + [nim::TalkEx::PinMsg](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk_ex_1_1_pin_msg.html)

## 7.5.0 (2020-03-31)

**缺陷修复**

- 卸载 http 模块时可能引起的崩溃

## 7.4.0 (2020-03-10)

**新增功能**

- 撤回消息支持配置撤回的通知消息的 pushcontent 和 payload 字段

    + c

        [nim_talk_recall_msg2](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__talk_8h.html#a82adb4eac79058faa802f77bea353588)

    + c++

        [RecallMsg2](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk.html#a259d7002eca7bcdd07cf27adb646d14b)

- 单向删除消息(包含漫游与云端历史记录)

    + c

        [nim_msglog_delete_message_self_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#ac3a599c140034122c1fd6ffe06c8b2d2)

    + c++

        [DeleteMessageSelfAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a80a7d046f41250b69c48de8aabafb3fa)

- 删除本地消息可配置是否可以通过查询云端历史记录恢复字段

    增加相应 API 函数的参数"revert_by_online_query" 是否可以通过服务端查询消息记录(QueryMsgOnlineAsync,QueryMsgOnlineAsyncParam::need_save_to_local_ = true)进行恢复,true:是,false:否

    + 删除某个会话的全部聊天记录

        + c

            [nim_msglog_batch_status_delete_async_ex](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#ac476d340ec3bfb43335f5d2e91528ba4)

        + c++

            [BatchStatusDeleteAsyncEx](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a62527081708e77ae08f05838f4d673dd)

    + 删除全部消息历史

        + c

            [nim_msglog_delete_all_async_ex](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#ac98af4b7c150b014ba68cab067706f66)

        + c++

            [DeleteAllAsyncEx](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#a57952cc8a7edfb8b7e281ee8951d4451)

    + 根据时间段删除部分会话的历史消息

        + c

            [nim_msglog_delete_by_time_async_ex](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#a01fa51a2c481585b49bbca2692628898)

        + c++

            [DeleteMsgByTimeAsyncEx](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#ae0760884f19324e4fac2ec455100c1b8)

**缺陷修复**

- 连接代理后,登录失败的问题
- 查询会话列表时，返回结果中 msg_sender 字段缺失的问题

## 7.3.0 (2020-03-02)

**变更**

- SDK 二制文件存放目录由原来的"bin" 改为"libs"

**缺陷修复**

- 登录后马上断网，可能引起的崩溃
- SDK 初始化路径包含中文时，可能引起崩溃
- 修改拼写错误

## 7.2.0 (2020-01-13)

**新增功能**

- 云端按关键字查询消息接口

    + c

        [nim_msglog_query_msg_by_keyword_online_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__msglog_8h.html#ad8045b7425d59345788f6c71523b5564)

    + c++

        [QueryMsgByKeywordOnlineAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_msg_log.html#ab2e714e9a0ef1d656f6dd4732987731c)

- 超大群新增部分 API

    + 按关键字查询群组信息

        + c

            [nim_super_team_query_teams_info_by_keyword_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#aaf8873536523e323be0018739e477e7f)

        + c++

        [QuerySuperTeamsInfoByKeywordAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a6a7395c852085ee72f4575d42f2923fe)

    + 申请入群

        + c

            [nim_super_team_query_teams_info_by_keyword_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#a0edfe1c8e50fb3c2b1baf8320899b288)

        + c++

            [ApplyJoinAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#aff9b55d747e91f92b9a168b13ddc089f)

    + 同意入群申请

        + c

            [nim_super_team_pass_join_apply_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#abec48b6344e5197ab9aba04502623d17)

        + c++

            [PassJoinApplyAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#ab9437666b433ce919f590862181d86d3)

    + 拒绝入群申请

        + c

        [nim_super_team_reject_join_apply_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#a5b142065f89cca36f7770399aee0cca5)

        + c++

        [RejectJoinApplyAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a6774f717c9fda732387729d3beb8e333)

    + 添加管理员

        + c

        [nim_super_team_add_managers_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#a81205e2b9ac5c47d6cad5c991a202d61)

        + c++

        [AddManagersAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a68a00b71ef66ef628c00fa69d4397703)

    + 删除管理员

        + c

        [nim_super_team_remove_managers_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#abd38d409babe40caddc7322cdd8e5820)

        + c++

            [RemoveManagersAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a1ecd10cf9651962753008a106bfee6ad)

    + 移交群主

        + c

            [nim_super_team_transfer_team_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#ab3feb0353b0858e8df1316c753adc354)

        + c++

            [TransferTeamAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a1a816a19343ffabf46f8d7ee345c7a9c)

    + 更新自己的群信息

        + c

            [nim_super_team_update_my_property_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#acb70dcf5008ce91824617985a6455d42)

        + c++

            [UpdateMyPropertyAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a2fe8462889de916937bce63b7101f0b1)

    + 修改群成员昵称

        + c

            [nim_super_team_update_other_nick_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#ace91d66b65467897d253e7421b178e15)

        + c++

            [UpdateOtherNickAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#ab71ff11678bb6ca0238c71f3f5716d5d)

    + 接受入群邀请

        + c

            [nim_super_team_accept_invitation_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#a2c3b67e5344531104ff1cbcd8e06797a)

        + c++

            [AcceptInvitationAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a66977cf1c7645e10d9668b18dc84b76c)

    + 拒绝入群邀请

        + c

            [nim_super_team_reject_invitation_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#ac80a1276277df47623a6e0f262378e8c)

        + c++

            [RejectInvitationAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a536f363d723d7b5665706e9d6a4bb1fb)

    + 设置或解除群成员禁言状态

        + c

            [nim_super_team_mute_member_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#aa2e0d9d5796a08bf3038f88c8aabc96e)

        + c++

            [MuteMemberAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a266560ad35c363409c3493efbf40e698)

    + 设置或解除群禁言状态

        + c

            [nim_super_team_mute_async](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__super__team_8h.html#aefc055eb56429b20be14686c4e4440d8)

        + c++

            [MuteAsync](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_super_team.html#a1766fa10369f918846b9eaac2f2dad9b)

**功能优化**

- cpp_wrapper_util 工程添加到解决方案，不再以编译好的 lib 库引入，您需要根据工程属性选择加载 md/mt 项目到解决方案

## 7.1.0 (2019-12-17)

[sdk 升级 6.6.6 及以上版本引导](/docs/TM5MzM5Njk/DYyOTU1MzE)

**新增功能**

- 对 windows xp(sp3 x86/x64)支持
- 消息过滤配置接口

    + c

        [nim_talk_reg_message_filter_cb](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__talk_8h.html#a8d55c77db4f01b6a86ec15777af41fb9)

        [nim_talk_message_filter_func](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__talk__def_8h.html#a2616f6c21a06e7dd7d5a4cde7c69fe5f)

    + c++

        [RegMessageFilter](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk.html#a9fdd3a9351690b66af1a47ff3a7614f4)

        [MessageFilter](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_talk.html#a443f2b6b9a4ee665eacba556d56d4335)

## 7.0.0 (2019-11-13)

[sdk 升级 6.6.6 及以上版本引导](/docs/TM5MzM5Njk/DYyOTU1MzE)

**新增功能**

- SDK 写缓存数据失败时通知应用层的功能

    + c

        [nim_global_reg_sdk_db_error_cb](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__global_8h.html#a63e0cd809341d1c2c7b4edebc0b01fbc)

        [nim_global_sdk_db_error_cb_func](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__global__def_8h.html#ae1b961d1c2e0f11fd419f5c1327ba38f)

        [NIMDBOperation](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__global__def_8h.html#abc613b95c17309ee71530fee9d6adc03)

    + c++

        [nim::Global::SDKDBErrorInfo](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_global_1_1_s_d_k_d_b_error_info.html)

        [nim::Global::SDKDBErrorInfo::DBOperation](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/structnim_1_1_global_1_1_s_d_k_d_b_error_info.html#a0aee446cb1f49621bcb84454ab6a0926)

        [nim::Global::RegSDKDBError](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_global.html#a516ac94111c0ed602136fd414950ee81)

- 会话列表服务功能

    [nim_session_online_service_helper](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__session__online__service__helper_8h.html)

    [nim::SessionOnLineService](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/classnim_1_1_session_on_line_service.html)

    + c

        [nim_session_online_service](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_C/html/nim__session__online__service_8h.html)

    + c++

        [nim_session_online_service_def](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__session__online__service__def_8h.html)

**功能优化**

- 取消私有化配置项 [kNIMPrivateEnableHttps（"https_enabled"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#ae19b4000c1645689197dbe5a17c38dc4)统一由公共配置[kNIMUseHttps（"use_https"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#a104d26562d50aa6383328d9135122cbe) 来开启与关闭 https 功能

- 取消私有化配置 [kNIMRsaPublicKeyModule（"module"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#a5c0d2aaa447d394ba883e97e2ee68cf6)、[kNIMRsaVersion（"version"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#ae1ed41a4fafbef377e1d68768a20eebc)，改由[kNIMNegoKeyNECAKeyPA（"nego_key_enca_key_parta"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#a3f775052993bcf1fdcab069f6ec6ba4c)、[kNIMNegoKeyNECAKeyPB（"nego_key_enca_key_partb"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#a52846a65a1acb7963779b4fbd1de3fbb)、[kNIMNegoKeyNECAKeyV（"nego_key_enca_key_version"）](https://dev.yunxin.163.com/docs/interface/即时通讯Windows端/NIMSDKAPI_CPP/html/nim__client__def_8h.html#aceb38c366fce51397d86ce880acf5cd2) 来进行配置

## 6.9.0 (2019-09-19)

[sdk 升级 6.6.6 及以上版本引导](/docs/TM5MzM5Njk/DYyOTU1MzE)

**新增功能**

- 超大群增加消息撤回功能
- 超大群支持自定义系统通知
- 超大群增加离线消息处理
- 查询指定数量的最后会话数据

    c 定义如下

    ```C
    /** @fn void nim_session_query_all_recent_session_async(const char *json_extension, nim_session_query_recent_session_cb_func cb, const void *user_data)
    * 查询指定数量的最后会话数据
    * @param[in] limit        要返回的最大数量
    * @param[in] json_extension json 扩展参数（备用，目前不需要）
    * @param[in] cb            查询会话列表的回调函数，nim_session_query_recent_session_cb_func 回调函数定义见 nim_session_def.h
    * @param[in] user_data    App 的自定义用户数据，SDK 只负责传回给回调函数 cb，不做任何处理。
    * @return void 无返回值
    */
    NIM_SDK_DLL_API void nim_session_query_last_few_session_async(int limit, const char *json_extension, nim_session_query_recent_session_cb_func cb, const void *user_data);
    ```

    c++定义如下

    ```C++
    /** @fn static void QueryAllRecentSessionAsync(const QuerySessionListCallabck& cb, const std::string& json_extension = "")
    * 查询指定数量的最后会话数据
    * @param[in] limit        要返回的最大数量
    * @param[in] cb            查询会话列表的回调函数
    * @param[in] json_extension json 扩展参数（备用，目前不需要）
    * @return void 无返回值
    */
    static void QueryLastFewSessionAsync(int limit, const QuerySessionListCallabck& cb, const std::string& json_extension = "");
    ```

- SDKConfig

    新增私有化是否启用 HTTPS 协议

    ```C
    static const char *kPrivateEnableHttps = "https_enabled"; /**< bool，（必填，私有化配置是否启用 HTTPS 协议，启用私有化配置时会覆盖 kNIMUseHttps，为 true 时 kNIMDefaultNosUploadHost 必填） */
    ```
    ```c++
    bool SDKConfig::private_enable_https_; /**< bool，（必填，私有化配置是否启用 HTTPS 协议，启用私有化配置时会覆盖 use_https_，为 true 时 default_nos_upload_host_必填） */
    ```
    在调用 Login 接口后无论成功是否上报历史错误日志到服务器


    ```c
    static const char *kUploadSDKEventsAfterLogin = "upload_sdk_events_after_login"; /**< bool，在调用 Login 接口后无论成功是否上报历史错误日志到服务器（目前支持 408、415、500）默认为 false */
    ```
    ```c++
    bool SDKConfig::upload_sdk_events_after_login_; /**< bool，在调用 Login 接口后无论成功是否上报历史错误日志到服务器（目前支持 408、415、500）默认为 false */
   ```

**功能优化**

IM SDK 改用跨平台的方案实现，不再支持 Windows XP 及以下系统，目前只适配了 win7/win10,后续版本中将会适配 Mac、linux 等系统(以更新说明为准), [6.8.2 版本 branch:6.8.x](https://github.com/netease-im/NIM_PC_SDK-CPP- )继续提供 Windows xp (sp3+) 支持，

## 6.8.1 (2019-08-14)

**缺陷修复**

NOS：修复调用 `StopDownloadResourceEx`（nim_nos_stop_download_ex） 接口时无法停止使用 `DownloadResourceEx`（nim_nos_download_ex）发起的任务。

## 6.7.0 (2019-08-01)

[sdk 升级 6.6.6 及以上版本引导](/docs/TM5MzM5Njk/DYyOTU1MzE)

**新增功能**

- 未接通的音视频通话消息统一计入未读数

    功能通过以下配置来开启或关闭

        bool GlobalConfig::vchat_miss_unread_count_;/**< bool，语音消息未接通消息是否计入未读数，默认 false */
        static const char *kNIMVChatMissUnreadCount = "vchat_miss_unread_count";
- 获取最近会话列表可选是否排除掉某类型消息

  c 定义如下

   ```c
        /** @fn void nim_session_query_all_recent_session_with_last_msg_excluded_type_async(const char *json_extension, nim_session_query_recent_session_cb_func cb, enum NIMMessageType last_msg_excluded_type,const void *user_data)
        * 查询会话列表,可指定最后一条会话消息要排除掉的类型
        * @param[in] json_extension json 扩展参数（备用，目前不需要）
        * @param[in] cb    查询会话列表的回调函数，nim_session_query_recent_session_cb_func 回调函数定义见 nim_session_def.h
        * @param[in] last_msg_excluded_type 最后一条会话消息要排除掉的类型,如果不排除任何消息，参数请传入 NIMMessageType::kNIMMessageTypeUnknown
        * @param[in] user_data    App 的自定义用户数据，SDK 只负责传回给回调函数 cb，不做任何处理。
        * @return void 无返回值
        */
        NIM_SDK_DLL_API void nim_session_query_all_recent_session_with_last_msg_excluded_type_async(const char *json_extension, nim_session_query_recent_session_cb_func cb, enum NIMMessageType last_msg_excluded_type,const void *user_data);
      c++定义如下

   ```
   ```c++
        /** @fn static void nim::Session::QueryAllRecentSessionAsync(NIMMessageType last_msg_excluded_type,const QuerySessionListCallabck& cb, const std::string& json_extension = "");
        * 查询会话列表,可指定最后一条会话消息要排除掉的类型
        * @param[in] last_msg_excluded_type 最后一条会话消息要排除掉的类型,如果不排除任何消息，参数请传入 NIMMessageType::kNIMMessageTypeUnknown
        * @param[in] cb    查询会话列表的回调函数
        * @param[in] json_extension json 扩展参数（备用，目前不需要）
        * @return void 无返回值
        */
        static void nim::Session::QueryAllRecentSessionAsync(NIMMessageType last_msg_excluded_type,const QuerySessionListCallabck& cb, const std::string& json_extension = "");

- 超大群新增 群移交群主、设置/取消管理员、禁言/解除禁言群成员等操作的通知消息
    定义如下

    ```
        kNIMNotificationIdSuperTeamOwnerTransfer = 406,    /**< 超大群移交群主，{"id":"a1","uinfos":["uinfo1", "uinfo2"]}*/
        kNIMNotificationIdSuperTeamAddManager = 407,    /**< 超大群增加管理员，{"ids":["a1","a2"],"uinfos":["uinfo1", "uinfo2"]}*/
        kNIMNotificationIdSuperTeamRemoveManager = 408,    /**< 超大群删除管理员，{"ids":["a1","a2"],"uinfos":["uinfo1", "uinfo2"]}*/
        kNIMNotificationIdSuperTeamMuteMember = 409,    / **< 超大群禁言/解禁群成员，{"uinfos":["uinfo1", "uinfo2"],** tinfo**:tinfo,"id":"a1","mute":1-禁言,0-解禁}*/
    ```

**功能优化**

- 修改本地反垃圾过滤逻辑，在不传入本地反垃圾词库名称时，对于替换规则会进行所有词库的匹配

## 6.6.6 (2019-07-16)

**新增功能**

- 根据时间段删除部分会话的历史消息接口

  * c 定义如下

   ```c
        /** @typedef void (*nim_msglog_modify_res_cb_func)(int res_code, const char *json_extension, const void *user_data)
        * 消息历史操作结果的回调函数定义(只关心 rescode)
        * @param[out] res_code        操作结果，成功 200
        * @param[out] json_extension    json 扩展数据（备用）
        * @param[out] user_data        App 的自定义用户数据，SDK 只负责传回给回调函数，不做任何处理。
        * @return void 无返回值
          */
        typedef void (*nim_msglog_modify_res_cb_func)(int res_code, const char *json_extension, const void *user_data);

        /** @fn void nim_msglog_delete_msg_by_time_async(const char *account_id, enum NIMSessionType to_type, uint64_t from_time, uint64_t to_time, const char *json_extension, nim_msglog_res_cb_func cb, const void *user_data);
        * 根据时间区间删除指定会话指定类型的本地消息
        * @param[in] account_id    会话 ID，对方的 account id 或者群组 tid
        * @param[in] to_type        会话类型
        * @param[in] timestamp1    与 timestamp2 组成一个时间段，SDK 内部会判断大小调整入参顺序
        * @param[in] timestamp2    与 timestamp1 组成一个时间段，SDK 内部会判断大小调整入参顺序
        * @param[in] json_extension json 扩展参数（备用，目前不需要）
        * @param[in] cb            操作结果的回调函数，nim_msglog_modify_res_cb_func 回调函数定义见 nim_msglog_def.h
        * @param[in] user_data    App 的自定义用户数据，SDK 只负责传回给回调函数 cb，不做任何处理。
        * @return void 无返回值
        * @note 错误码    200:成功
        *        0:失败
        */
        NIM_SDK_DLL_API void nim_msglog_delete_by_time_async(const char *account_id, enum NIMSessionType to_type, uint64_t timestamp1, uint64_t timestamp2, const char *json_extension, nim_msglog_modify_res_cb_func cb, const void *user_data);

   ```
  * c++定义如下

   ```c++
        typedef DBFunctionCallback DeleteMsgByTimeCallback;    /**< 根据时间段删除部分消息历史回调模板 */

        /** @fn static bool DeleteMsgByTimeAsync(const std::string& session_id, NIMSessionType to_type, uint64_t from_time, uint64_t to_time, const DeleteMsgByTimeCallback& cb, const std::string& json_extension = = "")
        * 根据时间段删除部分会话的历史消息
        * @param[in] session_id    要删除消息的会话 ID
        * @param[in] to_type    要删除消息的会话类型
        * @param[in] timestamp1    与 timestamp2 组成一个时间段，SDK 内部会判断大小调整入参顺序
        * @param[in] timestamp2    与 timestamp1 组成一个时间段，SDK 内部会判断大小调整入参顺序
        * @param[in] json_extension json 扩展参数（备用，目前不需要）
        * @param[in] cb            操作结果的回调函数
        * @return bool 检查参数如果不符合要求则返回失败
        * @note 错误码    200:成功
                        0:失败
        */
        static bool MsgLog::DeleteMsgByTimeAsync(const std::string& session_id, NIMSessionType to_type, uint64_t timestamp1, uint64_t timestamp2, const DeleteMsgByTimeCallback& cb, const std::string& json_extension = "");
   ```
- 获取当前服务器时间戳
  * c 定义如下

   ```c
        /** @typedef void(*nim_client_get_server_current_time_cb_func)(int rescode, bool calc_local, uint64_t time,const char *json_params, const void *user_data)
        * 多端推送设置/同步回调
        * @param[out] rescode
        * @param[out] calc_local 是否为本地计算
        * @param[out] time 当前服务器时间(ms)
        * @param[out] user_data App 的自定义用户数据，SDK 只负责传回给回调函数，不做任何处理。
        * @return void 无返回值
        */
        typedef void(*nim_client_get_server_current_time_cb_func)(int rescode, bool calc_local, uint64_t time, const void *user_data);

        /** @fn void nim_client_get_server_current_time(bool calc_local,nim_client_get_server_current_time_cb_func cb, const char *json_extension,const void *user_data)
        * 获取当前服务器时间
        * @param[in] calc_local 是否在本地计算，false:直接到服务端查询 ,true:根据上次查询到的服务端时间与本地系统启动时间来计算，不会到服务端查询
        * @param[in] cb 操作结果的回调函数
        * @param[in] json_extension json 扩展参数(备用，目前不需要）
        * @param[in] user_data App 的自定义用户数据，SDK 只负责传回给回调函数 cb，不做任何处理。
        * @return void
        * @note 由于网络上/下行的原因，返回的时间会存在一定误差，
         当 calc_local == false 时,如果跟上次调用该方法的时间间隔小于 2000ms，SDK 会采用 calc_local == true 时的方案以减少服务端的压力，并会在回调中指明返回的时间是由本地计算的。
         如果返回 code != 200,同样会返回一个本地计算结果
        */
        NIM_SDK_DLL_API void nim_client_get_server_current_time(bool calc_local,nim_client_get_server_current_time_cb_func cb, const char *json_extension,const void *user_data);
   ```
  * c++定义如下

   ```c++
        typedef std::function<void(int, bool, uint64_t)> GetCurrentServerTimeCallback;    /**< 查询服务器当前时间回调模板 */

        /** @fn void GetServerCurrentTime(bool calc_local, const Client::GetCurrentServerTimeCallback& cb)
        * 获取当前服务器时间
        * @param[in] cb 操作结果的回调函数
        * @param[in] calc_local 是否在本地计算，false:直接到服务端查询 ,true:根据上次查询到的服务端时间与本地系统启动时间来计算，不会到服务端查询
        * @return void
        * @note 由于网络上/下行的原因，返回的时间会存在一定误差，
        * 当 calc_local == false 时,如果跟上次调用该方法的时间间隔小于 2000ms，SDK 会采用 calc_local == true 时的方案以减少服务端的压力，并会在回调中指明返回的时间是由本地计算的。
        * 如果返回 code != 200,同样会返回一个本地计算结果
        */
        static void nim::Client::GetServerCurrentTime(const Client::GetCurrentServerTimeCallback& cb, bool calc_local = false);
   ```

**变更**

- 对 SDK 目录结构进行了调整，修改说明可参考 [sdk 升级 6.6.6 及以上版本引导](/docs/TM5MzM5Njk/DYyOTU1MzE) 章节

## 6.6.0 (2019-06-25)

**新增功能**

- C 接口新增在线查询消息接口 nim_msglog_query_msg_online_async2，可以参数中传入需要查询的消息类型列表

**缺陷修复**

- 创建高级群时，被邀请人收到两次邀请通知的问题

## 6.5.5 (2019-06-12)

**新增功能**

- 超大群功能，开通功能请联系商务，接口定义文件：C 接口：nim\_super\_team.h CPP 接口:nim\_cpp\_super\_team.h

## 6.5.0 (2019-05-24)

**新增功能**

- 新增查询群成员邀请人的 accid 接口

**变更**

- 再次进入经进入的聊天室时，进入聊天室结果由 step2 改为 step5,rescode 改为 20002

**缺陷修复**

- 同时（几乎）调用进入同一聊天室接口可能引起的崩溃

## 6.4.0 (2019-04-26)

**缺陷修复**

- 邀请群成员不需要被邀请人同意时，群内其他成员无法从"TeamEvent"拿到 attach 字段的问题

**变更**

- Sdk 升级到 vs2017，对于不开启自动更新的 windows 系统，需要追加对应的运行时库。相关的运行时库见 sdk 包中的 **redist\_packages** 文件夹。用户产品发布时将 **redist\_packages** 下的库文件需放到执行目录下。

## 6.3.0 (2019-04-18)

**新增功能**

- 从服务器上清空 P2P 消息的历史和漫游记录接口
- 针对撤回消息的操作是否减少未读数的功能开关
- 删除好友同时可指定是否删除备注信息接口

## 6.2.0 (2019-03-14)

**新增功能**

- 话单消息(有通话时长)支持存云端历史消息、支持漫游
- NOS 资源支持安全链接(短链)功能

**功能优化**

- 群成员同步完成后，无论是否有变化都会通知应用层

## 6.1.1 (2019-02-15)

**功能优化**

- 修复多次对 SDK 进行初始化/清理，可能引起 SDK 卡死的问题

## 6.1.0 (2019-01-22)

**新增功能**

- 导出本地消息记录到云端
- 导入云端消息记录到本地
- 邀请群成员添加输入 attachment 字段接口
- 新增注销与退出 SDK 聚合接口

**功能优化**

- 修改因没有初始化 SDK 调用 SDK 接口导致的崩溃的问题
- 修改登录后立即退出，再次登录时可能会收到重复 IM 消息的问题

## 6.0.0 (2019-01-14)

**功能优化**

- 修改 SDK 清理后再次初始化可能存在的崩溃
- 调整 C++封装层对 VS2015 及其以上版本的支持

## 5.9.0 (2018-11-28)

**新增功能**

- 可配置 IM 消息（图片、视频）的缩略图命名格式（以"{filename}"做为通配符）
- 创建群聊时支持指定该群的群人数上限可配
 1. 创建群聊时支持指定该群的群人数上限（可选参数），默认为该 app 当前整体配置的群人数上限。
 2. 指定的群人数上限不可超过当前 app 配置的群人数上限，否则创建/修改失败，返回相关的错误码。
 3. 群人数达到上限时，无法添加新的成员入群，申请加群/同意进群的操作返回加群失败。
 4. SDK 创建群时支持指定，不支持修改。修改通过服务端 API 来修改。
- IM SDK 按 session id 获取 session data 接口

**功能优化**

- 上传资源（图片、视频、语音、文件）生成的下载链接改为 CDN 域名
- 增加 SDK 回调线程，以防止应用层阻塞 SDK 核心线程

## 5.8.0 (2018-11-13)

**功能优化**

- SDK 全部改为 VS2013 update5 版本编译，运行时库由 VS2010 改为 VS2013

## 5.7.0 (2018-10-12)

**新增功能**

- 登录客户端描述新增自定义信息字段
- 聊天室协议新增批量更新聊天室通用队列元素接口

**功能优化**

- 文件上传支持快传，即上传重复的大文件上传将不不再需要重复传输，相关接口内部优化

## 5.6.0 (2018-08-30)

**新增功能**

- 新增独立的音视频通话代理接口（c 接口：nim\_rts\_set\_proxy），该接口和全局接口优先级一致，当和全局代理不同时可以独立调用修改音视频的代理。该接口只支持 socks5。
- 新增独立的音视频通话代理接口（c 接口：nim\_vchat\_set\_proxy），该接口和全局接口优先级一致，当和全局代理不同时可以独立调用修改音视频的代理。该接口只支持 socks5。

## 5.5.0 (2018-08-07)

**新增功能**

- 文件上传增加 **场景** 信息

    使用 5.5 版本及其以上 SDK（PC 端、移动端、web 端）实现的客户端（简称：5.5+ SDK），向使用 PC5.4 及其以下版本 SDK 实现的客户端（简称：PC 5.4- SDK），发送图片消息且客户端开启下载缩略图功能时(即：5.5+ SDK 向 PC 5.4- SDK(preload_attach_=true),发送图片消息),接收到的缩略图片可能是原图。建议升级 SDK 到 5.5 及其以上版本或者在 UI 层对缩略图做缩放处理。

- 本地数据文件(*.db)备份功能

**缺陷修复**

- Windows x64 下 http 库可能引起的崩溃

## 5.3.0 (2018-06-26)

**新增功能**

- 好友信息新增 server_ex 字段(客户端 sdk 只读，服务端 api 读写)

## 5.1.0 (2018-05-17)

**新增功能**

- 聊天室被踢后可以获取扩展通知内容
- 服务器端批量踢人的客户端通知
- 获取云端历史消息支持类型筛选
- 聊天室增加批量消息上报接口

**缺陷修复**

- 修复偶现初始化崩溃问题

## 5.0.0 (2018-03-29)

**新增功能**

- 客户端反垃圾功能
- SDK 提供缓存管理接口（查询、删除），nim\_global.h
- 群消息已读功能
- 群组禁言功能

## 4.8.0 (2018-02-08)

**新增功能**

- 易盾的客户，可以配置某条消息是否要过反垃圾

**缺陷修复**

- 修复移动端创建群，PC 端同步到的群信息有误导致群无效需要重启的问题
- 不能将群昵称置空的问题
- 同一台电脑两个应用同时匿名登录同一个聊天室后的异常表现
- 偶现群成员获取不全的问题

## 4.6.0 (2018-01-04)

**新增功能**

- 群主或群管理员可以撤回其他群成员发送的消息的功能
- 用户配置的对某单条消息另外的反垃圾的业务 ID 的功能
- 视频消息主动获取封面功能
- NOS 域名迁移
- NOS 加速地址，上传、下载地址等统一配置
- 聊天室历史记录拉取可以按类型筛选功能
- 聊天室队列权限可配置
- 聊天室更新用户信息后，断线重连进入聊天室时，相应信息依旧还在的功能

## 4.4.0 (2017-11-16)

**新增功能**

- 聊天室用户异常掉线或主动退出的时候自动清除队列, nim\_chatroom.h
    - nim\_chatroom\_queue\_offer\_async(...), json_extension = "{\"transient\":true}" 设置此次更新的元素会在特定场景下被自动清除
    - 新增通知类 kNIMChatRoomNotificationIdQueueBatchChanged 用在麦序队列中有批量变更，发生在元素提交者离开聊天室或者从聊天室异常掉线时

**缺陷修复**

- 修复获取最近会话列表时可能导致 CPU 增高的问题

## 4.3.0 (2017-10-13)

**新增功能**

- 群消息支持「只接收管理员消息提醒」的免打扰选项
- 全员广播
- 批量清空所有会话未读数的接口
- 搜索历史记录支持多类型组合
- 聊天室游客模式
- 获取图片缩略图需要支持动图缩略图

**缺陷修复**

- 修复群信息界面 普通成员无法修改群消息通知模式的 bug

## 4.2.0 (2017-09-12)

**新增功能**

- 群通知消息是否计为未读数增加开关配置 nim\_client.h
- 聊天室支持机器人

**缺陷修复**

- 修复某些场景下群成员同步 bug

## 4.1.0 (2017-08-08)

**新增功能**

- 音视频 MP4 录制添加一个，录制全体声音的开关，允许在录制单个画面时录制通话的全体混音声音
- 音视频声卡采集设备改为非限定，允许在非通话的时候开启（需要用户主动关闭）
- 发送群自定义系统通知支持存离线
- 普通成员可以操作聊天室队列
- 新增多端登录时对 Mac 端的支持

**缺陷修复**

- 修复登录时有大量离线消息时导致的掉线等异常情况
- 修复开启 HTTPS 后文件不会续传的问题
- 修复 NOS::StopUploadResourceEx 不能停止非续传任务
- 修复群成员入群后同步到本地的群成员列表存在无效成员的问题

## 4.0.0 (2017-07-06)

**新增功能**

- 机器人模块, nim\_robot.h
- 聊天室消息不存历史记录开关
- 聊天室队列变更通知增加变更内容
- 支持 Https（默认 Http）

**缺陷修复**

- 修复管理后台创建群（不需要用户同意）时，在线客户端无法同步该群信息到本地的问题
- 修复申请加入群（不需要管理员同意）时，本地群列表里没有该群信息的问题

## 3.9.1 (2017-06-29)

**缺陷修复**

- 修复已知问题

**新增功能**

- 在点对点白板发起、点对点音视频发起、多人音视频创建接口中追加 webrtc 兼容模式的参数，用于和 web 的 webrtc 音视频互通，**该 WebRTC 为 beta 版，如果没有 webrtc 客户端参与，不要打开该开关**。

## 3.9.0 (2017-06-23)

**缺陷修复**

- SDK 优化了音视频相关的音频前处理功能，追加一个 nrtc_audio_process.dll 模块，并优化了音频编码

**新增功能**

- 视频通话的发送分辨率等级添加一个 960*540 的分辨率
- 音视频数据监听 nim\_vchat\_set\_audio\_data\_cb\_ex 接口添加一个伴音混音数据监听
- 音视频状态监听回调中 nim\_vchat\_cb\_func 添加一个回调类型 kNIMVideoChatSessionTypeLiveState 通知直播推流的服务器状态
- 添加互动直播时主播可以选择自定义布局，多人 join 的时候主播追加一个参数 kNIMVChatCustomLayout，在 NIMVChatVideoSplitMode 设置为 kNIMVChatSplitCustomLayout 时生效

## 3.8.0 (2017-06-06)

**新增功能**

- 聊天室更新固定成员信息时，支持 nick,avator 和 ext 字段的持久化
- 语音采集模块路径相关参数类型改为宽字符, nim\_audio.h

## 3.6.0 (2017-04-27)

**新增功能**

- 音视频通话时可以录制其他成员的 MP4 文件，在原先的 MP4 发起和结束接口中 json 支持扩展的 kNIMVChatUid,如果是本人和之前一样不填
- 音视频数据监听追加 nim\_vchat\_set\_audio\_data\_cb\_ex 接口用于监听伴音数据
- 音视频原先的动态推流接口 nim\_vchat\_set\_streaming\_mode 废弃，用户如果要互通推流需要在发起时确定
- 音视频追加发送画面裁剪接口 nim\_vchat\_set\_video\_frame\_scale
- 增加事件订阅相关接口

**缺陷修复**

- 修复无法修改好友备注的 bug
- 优化弱网环境下的链接稳定性
- 修复聊天室异常登录状态下发送消息 ack 通知信息不全的问题

## 3.5.0 (2017-03-15)

**新增功能**

- 音视频通话时可以录制 aac 的混音音频文件（自己和对方所有人的混音），同时通过音视频状态回调接口返回录制状态
- 音视频通话和白板通话邀请时追加一个 keepcalling 的功能，默认打开
- 聊天室历史消息拉取接口现在支持正反向一起拉，nim\_chatroom\_get\_msg\_history\_online\_async 第二个参数增加条件配置, nim\_chatroom\_def.h #分获取历史消息条件 Keys
- 新增代理测试接口, nim\_global.h

**缺陷修复**

- 优化麦克风和摄像头的设备遍历接口，防止错误的设备导致接口调用崩溃
- 修复音视频网络探测接口调用失败后导致的 cpu 高占用率的问题
- 优化白板数据接口在高频率调用时的崩溃问题
- 优化麦克风自动调节功能，会较明显的提升麦克风音量过小的问题
- 修复 HTTP 模块发送大文件容易超时的问题
- 优化本地数据持久化方案
- 修复近期反馈的崩溃问题

## 3.4.0 (2017-01-20)

**新增功能**

- 在接口 client init（sdk 初始化）中，追加一个必填的参数 app key，如果用户不填，会导致音视频模块初始化失败
- 添加音视频模块网络探测功能，网络探测会返回探测结果，针对结果可以参考开发手册计算出当前的网络情况
- 点对点白板通话中，白板数据和音频数据的服务器录制开关分离
- 追加互动直播的服务器录制开关
- C 接口支持隐式调用
- 进入聊天室增加账号禁用通知(422)

**缺陷修复**

- 解决伴音采集导致异常崩溃的问题
- 修复 x64 下，打开扬声器导致的崩溃问题
- 优化弱网下的 SDK 的提示，增加本地网络错误的错误号 10010
- 修复发送文件过程中，文件大小有变化导致的接收端无法正常接收文件的问题

## 3.3.0 (2016-12-28)

**新增功能**

- SDK 追加文档转换模块，文档上传和下载复用 nos 模块功能
- SDK 音视频设备中支持修改音频采集时是否开启降噪、人言检查、消回音功能
- SDK 音视频通话支持高清语音模式，3.3.0 之前的版本无法加入已经开启高清语音的多人会议
- SDK 初始化是增加配置登录最大重试次数, nim\_client\_def.h
- SDK IM/聊天室/音视频(C#)提供 64 位编译版本，伴音功能暂不提供 64 位版本。
- nim\_nos.h HTTP 上传下载扩展接口增加支持断点续传和暂停功能 nim\_nos\_def.h
- HTTP 下载扩展接口增加 **另存为** 指定到自定义路径 nim\_nos\_def.h
- HTTP 上传下载扩展接口增加超时时间的自定义设置入口, nim\_nos\_def.h
- nim\_nos.h 增加监听上传任务结果回调全局广播的全局注册接口，您可以通过监听获取多媒体消息的下载地址。
- 聊天室 **进入聊天室** 的聊天室通知增加三个内容：该进入成员是否被禁言，该进入成员是否被临时禁言，该进入成员临时禁言还剩时长, nim\_chatroom\_def.h

**缺陷修复**

- 优化 注销退出流程
- 修复 退出后 cleanup 可能会卡住调用线程的问题

## 3.2.5 (2016-12-19)

**新增功能**

- SDK IM/聊天室/音视频支持 64 位，伴音功能暂时不提供 64 位版本。
- SDK 内容调整，增加 nim\_audio.dll、nim\_tools\_http.dll 对应的 c/c++接口的描述文件和相关定义的头文件，文件夹 nim\_tools\_c\_sdk、文件夹 nim\_tools\_cpp\_sdk。
- 调整 CPP 接口命名：DeleteStatusByTypeAsync(...)调整为 DeleteByTypeAsync(...)，nim\_cpp\_sysmsg.h。
- C/CPP 接口注释增加错误码备注。

## 3.2.0 (2016-11-30)

**缺陷修复**

- 优化音频处理流程
- 优化高清摄像头数据解析，提高高清摄像头采集帧率
- 变更逻辑：关闭麦克风将不认为是静音状态，与伴音功能兼容
- 服务器白板录制，针对 3.2 之后的版本，在每条数据前追加 4 字节长度信息和 4 字节的时间戳，详情看开发手册
- 优化 IM 和聊天室登录流程

**新增功能**

- 新增多人白板功能，通过 nim\_rts\_create\_conf 创建多人白板，再由 nim\_rts\_join\_conf 接口加入多人白板。多人白板不支持视频通道，如果需要上层 App 可以另外开启多人音视频通话。
- 白板的创建及加入等接口将返回白板通道的 channelid，用于和服务器的白板会话抄送对应。
- 新增设备类型 kNIMDeviceTypeAudioHook，用户可采集播放器音频，需要使用 sdk 新增的 nim\_audio\_hook.dll
- 设备监听中可以监听伴音设备，kNIMDeviceTypeAudioHook 开始工作和被顶替（顶替是指伴音只允许有一个，如果有别的进程也使用了 sdk 中的伴音功能，则会被顶替，这时之前的伴音失效），将会通过回调上报。
- 会话消息已读未读状态多端同步
- 会话属性增加设置置顶和扩展数据字段接口, nim_session.h
- IM 和聊天室增加获取当前登录状态的接口, nim_client.h nim_chatroom.h

## 3.1.0 (2016-10-26)

**缺陷修复**

- 修复撤回消息成功后重登会再次受到通知的问题
- 调整 CPP 接口 CreateRoomMessage(...)(nim\_chatroom\_cpp.h),增加结构体 ChatRoomMessageSetting(nim\_chatroom\_helper.h)
- 修改 CPP 封装层结构体定义 TeamInfo,TeamMemberProperty,nim\_team\_helper.h

**新增功能**

- 群组、聊天室增加全员禁言状态,nim\_team\_def.h, nim\_chatroom\_def.h
- 获取群组被禁言成员列表,nim\_team.h
- 撤回消息通知增加所撤回的消息的消息时间戳,nim\_talk\_def.h
- 发送 P2P 消息，群组消息，聊天室消息增加反垃圾字段，nim\_talk\_def.h, nim\_chatroom\_def.h
- 增加查询好友关系同步接口,nim\_friend.h

## 3.0.0 (2016-10-20)

**缺陷修复**

- 优化登录流程。
- 登录后离线消息、同步消息的会话更新通知广播不再每条上报，改为最后一条上报。
- 批量获取消息接口的结果增加 kNIMMsglogQueryKeySource，区分来源(本地或者云端),nim\_msglog\_def.h。
- 登录回调通知里增加 kNIMRetrying，说明当前登录结果后 SDK 是否还在自动尝试登录（针对此次登录失败时),nim\_client\_def.h。
- 修改群成员属性 kNIMTeamUserKeyBits 的注释说明,nim\_team\_def.h。
- 调整 CPP 接口 CreateCustomNotificationMsg(...)(nim\_cpp\_sysmsg.h）,增加结构体 SysMessageSetting(nim\_sysmsg\_helper.h)。

**新增功能**

- 支持实时修改音视频通话的视频发送帧率上限
- 支持实时的音视频通话音频音量回调
- 实现实时修改推流的开始和结束。在发起直播时原先的连麦参数"bypass_rtmp"变成推流开关，主播如果要直接开始推流需要填此参数
- 变更：加入房间时，主播如果要直接开始推流需要填写 kNRTCChatBypassRtmp

## 2.9.0 (2016-09-19)

**缺陷修复**

- 白板通话（不含音视频）的挂断失败问题修复
- 优化消息附件（图片、语音和文件等）的下载
- 优化对高清摄像头的支持
- 优化视频编解码策略
- 优化音视频通话中本地 MP4 录制时声音图像不同步的问题

**新增功能**

- 初始化 SDK 接口新增两个配置项，设置接收图片消息后预下载图片的质量：kPreloadImageQuality, kPreloadImageResize。nim\_client\_def.h
- 音视频通话，全局状态回调添加 kNIMVideoChatSessionTypeInfoNotify 类型，返回实时的音视频数据状态

## 2.8.0 (2016-08-30)

**缺陷修复**

- V2.7.0 版本下载文件暂停继续下载的问题。
- 聊天室接口注册发送消息回执回调接口命名修改：nim\_chatroom\_reg\_send\_msg\_arc\_cb 接口变更为 nim\_chatroom\_reg\_send\_msg\_ack\_cb。nim\_chatroom.h
- 消息历史插入本地 DB 一条消息的接口命名和参数调整：typedef void(\*nim\_msglog\_write\_db\_only\_async)(const char \*account\_id, NIMSessionType to\_type, const char \*msg\_id, const char \*json\_msg, const char \*json\_extension, nim\_msglog\_res\_cb\_func cb, const void \*user\_data); 调整为 typedef void(\*nim\_msglog\_insert\_msglog\_async)(const char \*talk\_id, const char \*json\_msg, bool need\_update\_session, const char \*json\_extension, nim_msglog\_res\_cb\_func cb, const void \*user\_data);。nim\_msglog.h
- 合并错误码：10414 和 10450 统一为 10414，新增错误码 kNIMLocalResMsgNosDownloadCheckError。nim\_res\_code\_def.h
- 群成员收到退群通知后群成员数据不从本地删除，通过标记位标记为无效，具体调用方法请参考 api 文档或开发文档。
- 修复某种情况下 session change 通知时 session id 为空的问题。

**新增功能**

- 撤回消息。<!-- nim_talk.h -->

## 2.7.0 (2016-08-11)

**缺陷修复**

- 优化登录后同步群成员列表。
- 优化 SDK 在登。