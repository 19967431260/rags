<!--keywords: 更新日志,新增,修改,更新 -->

本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）稳定版安卓端 9.x.x 及以下版本的更新日志。有关 10.x.x 开发版，请参考《IM 即时通讯 V10》[Android 更新日志](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client)。

:::details 单击展开了解什么是稳定版、与开发版的区别、以及开发环境要求。

稳定版基于 [开发版](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client)，可满足常见 IM 应用业务场景，但更注重稳定性。开发版则主要是在可商用的基础上，提供新功能与特性。

稳定版与开发版的主要差异点如下：

- 稳定版相较开发版，在更长周期内获得了更多用户的验证，且修复了多个历史版本的已知问题，稳定性保障更佳。
- **稳定版要求项目开发环境满足至少以下条件**：

    环境要求 | 说明
    ---- | ----
    JDK 版本 | 1.8.0 及以上版本
    Android API 版本 | API 21、Android 5.0 及以上版本
    CPU 架构 | ARM 64、ARM V7
    IDE：Android Studio | 4.0 及以上
    其他 | 依赖 Androidx，不支持 support 库<br>请使用 Android 系统 5.0 或以上版本的移动设备
:::

## 9.21.11 (2026-03-06)

修复已知问题。

## 9.21.10 (2026-01-30)

**新增特性**

支持在初始化时配置聊天室默认 Link 地址。在聊天室中启用 LBS，但 LBS 不可用时，将使用设置的默认 Link 地址进行连接。


::: details 单击查看配置示例
```java
SDKOptions option = SDKOptions.DEFAULT;
//原有的初始化配置代码
...
//新增的初始化配置
ServerAddresses addresses = new ServerAddresses();
//国内为chatlink-cn.yunxinfw.com:443，若需要海外，请替换为chatlink-sg.yunxinfw.com:443
addresses.chatRoomLinkList = new ArrayList<>(Arrays.asList("chatlink-cn.yunxinfw.com:443"));
option.serverConfig=addresses;
……
```
:::
  

**接口更新**

| 接口 | 说明 |
| ---- | ---- |
| `ServerAddresses.chatRoomLinkList` | 新增字段，表示聊天室默认 Link 地址。

**优化**

- 优化聊天室连接。
- 其他内部优化。

## 9.21.0 (2025-12-22)

**新增功能**

- API 普通流式消息支持高级群。
- 普通流式消息现支持携带 RAG 信息，增强 AI 交互能力。

**优化**

- 优化群成员更新逻辑。
- 流式过程中查询消息时补齐消息完整内容。

## 9.20.17 (2025-10-17)

**新增功能**

- 点对点文本支持普通流式消息。
- 底层连接优化。

**问题修复**

修复 arm-v7a 架构偶现崩溃问题。

## 9.20.15 (2025-08-26)

**新增功能**

新增消息的二次编辑能力。

**接口变更**

| 接口 | 说明 |
| ---- | ---- |
| `modifyMessage` | 新增接口，用于用于实现消息的二次编辑能力。 |

## 9.20.14 (2025-08-13)

内部优化。

## 9.20.13 (2025-07-24)

**新增功能**

- 升级加密方案，将 AES 加密密钥长度从 128 位升级到 256 位，提供更强的安全保障。
- FCSNext 功能优化上线，提升文件传输速度和稳定性。

**功能优化**

- 优化 NOS 上传 Token 缓存机制，减少网络请求次数，提升消息发送和文件上传速度。
- 改进了 `getMessagesDynamically` 方法，解决在同时使用 **云端补充** 和 **消息过滤** 功能时可能导致的消息显示不连贯问题，保证消息记录完整性。

**缺陷修复**

- 修复 Google 控制台报告的应用崩溃(crash)和无响应(ANR)问题，提升应用整体稳定性。
- 修复 Android 6.0 系统上的高可用性兼容问题，确保在旧设备上也能流畅运行。适用于使用较早版本 Android 系统的用户。

**接口变更**

| 接口/功能变更 | 影响及兼容性说明 |
| ---- | ---- |
| [`getMessagesDynamically`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a7e04c64027ab59d214642531141f33d4) | 已优化处理 **云端补充** + **消息过滤** 场景，旧版本可能出现消息不连贯情况。 |

## <span id="[9.20.12] - 2025-06-16">9.20.12 (2025-06-16)</span>

内部优化。

## <span id="[9.20.10] - 2025-04-18">9.20.10 (2025-04-18)</span>

- 针对 AI 大模型生成的消息，新增了流式效果输出功能，使消息内容能够逐步展示。
- 同时，新增了 AI 流式代理功能，用于更高效地管理和控制消息流的输出。

## <span id="9.19.14 (2025-04-14)">9.19.14 (2025-04-14)</span>

内部优化。

## <span id="9.19.11 (2025-03-13)">9.19.11 (2025-03-13)</span>

- 优化提升连接稳定性。
- 修复已知问题。

## <span id="9.19.10 (2025-02-20)">9.19.10 (2025-02-20)</span>

内部优化。

## <span id="9.19.4 (2024-12-17)">9.19.4 (2024-12-17)</span>

- SDK 编译版本优化适配。

- 提升网络联通率与稳定性，支持 QUIC（Quick UDP Internet Connections）传输层网络协议，您可以自主选择集成。

- SDK 适配 16K Page Size。（加密数据库需要升级至 net.zetetic:sqlcipher-android:4.6.1。）

## <span id="9.19.2 (2024-11-12)">9.19.2 (2024-11-12)</span>

提升网络连接稳定性。

## <span id="9.19.0 (2024-10-15)">9.19.0 (2024-10-15)</span>

- 新增 AI 数字人功能。详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。
- 新增第三方推送 token 共享能力。

## <span id="9.18.1 (2024-09-18)">9.18.1 (2024-09-18)</span>

网络链接优化。

## <span id="9.18.0 (2024-09-03)">9.18.0 (2024-09-03)</span>

- 提升网络稳定性。
- 内部多项优化。

## <span id="9.17.2 (2024-08-16)">9.17.2 (2024-08-16)</span>

内部优化。

## <span id="9.17.1 (2024-07-16)">9.17.1 (2024-07-16)</span>

优化获取消息附件时返回的 URL 拼接规则。

## <span id="9.17.0 (2024-07-04)">9.17.0 (2024-07-04)</span>

**新增特性**

- 新增圈组临时禁言功能，具体请参考 [圈组临时禁言](https://doc.yunxin.163.com/messaging/guide/jUyNzM0MTI?platform=android)。
- 新增圈组频道分组自定义排序能力，具体请参考 [搜索服务器和频道（频道分组）](https://doc.yunxin.163.com/messaging/guide/TUzMTY5OTQ?platform=android)。
- 新增圈组查询未在频道分组下的频道信息能力，具体请参考 [频道管理](https://doc.yunxin.163.com/messaging/guide/TgwMjk5NDY?platform=android#分页查询未在频道分组下的频道)。

**性能优化**

- 推出最新稳定版，整体性能和稳定性进一步提升。
- 存储上传稳定性提升，显著提高文件传输的稳定性和可靠性。
- 多项内部优化，进一步提升性能。

**API 新增**

方法/回调/类 | 说明
---- | ----
`QChatServerService.mute` | 在指定圈组服务器中对指定成员进行临时禁言或解除临时禁言。
`QChatServerService.getMuteMemberByPage` | 在指定圈组服务器中分页查询被临时禁言的成员列表。
`QChatChannelService.mute` | 在指定频道中对指定成员进行临时禁言或解除临时禁言。
`QChatChannelService.getMuteMemberByPage` | 在指定频道中分页查询被临时禁言的成员列表。
`getUncategorizedChannelsByPage` | 分页查询当前服务器中不在频道分组下的频道列表。
`QChatChannelCategory` | 频道分组对象新增 `reorderWeight` 字段，表示自定义排序标识，在分页查询频道分组时可根据该字段进行自定义排序。
`getChannelCategoriesByPage` | 查询频道分组列表接口的入参中新增 `sortType`（排序类型）和 `cursor` （分页）字段，可设置排序类型实现 **按自定义权重排序** 查询频道分组。

## <span id="9.16.4 - 2024-05-30">9.16.4 (2024-05-30)</span>

优化文件上传逻辑，提升上传稳定性。

## <span id="9.16.3 - 2024-05-21">9.16.3 (2024-05-21)</span>

- 将 NOS LBS 默认请求地址变更为 HTTPS。
- 升级第三方推送，具体兼容版本请参考以下表格。

9.16.3 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.12.0.300
小米 | 6.0.1
OPPO | 3.5.1
VIVO | 4.0.0.0_500
魅族 | 4.3.0
荣耀 | 7.0.61.303
FCM | firebase-bom:32.3.1，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

## <span id="9.16.1 - 2024-04-26">9.16.1 (2024-04-26)</span>

超大群中发消息支持强制推送功能。

## <span id="9.16.0 - 2024-04-16">9.16.0 (2024-04-16)</span>

**新增特性**

- 支持按群成员类型分页查询群成员列表。
- 支持添加、移除特别关注群成员列表。（高级群和超大群）
- 新增鸿蒙终端类型的解析。

**优化改进**

适配升级 OPPO 推送 SDK 至 3.4.0 版本。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`TeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#adc25264df4186ac99d4768d21307abaa) | 按群成员类型分页查询群成员列表。（高级群） |
| [`TeamService.addTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a838a890dfa5b3c389578c7ca612d43a2) | 添加特别关注群成员列表。（高级群） |
| [`TeamService.removeTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#af8191da24c5b90a3c387cb59cbaebb3e) | 移除特别关注群成员列表。（高级群） |
| [`SuperTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a5d0d677e7a9fea2c2b9bfc3e2ac68ea4) | 按群成员类型分页查询群成员列表。（超大群） |
| [`SuperTeamService.addTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a2c36b51df6b3e39bb05f7bf440316904) | 添加特别关注群成员列表。（超大群） |
| [`SuperTeamService.removeTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a1ce398fda27d40962324946d8dcc4aff) | 移除特别关注群成员列表。（超大群） |

**API 变更**

方法/回调/类 | 说明
---- | ----
[`ClientType`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_client_type.html) | 新增 `Harmony` 成员参数，多端登录支持鸿蒙客户端类型。

## <span id="9.15.2 - 2024-03-28">9.15.2 (2024-03-28)</span>

升级数据库加密套件（SQLCipher）至 4.5.4 版本。

## <span id="9.15.1 - 2024-03-22">9.15.1 (2024-03-22)</span>

圈组连接优化。

## <span id="9.15.0 - 2024-01-31">9.15.0 (2024-01-31)</span>

**新增特性**

圈组模块新增支持以下功能：

- 支持分页获取评论者列表，具体请参考 [圈组快捷评论](https://doc.yunxin.163.com/messaging/docs/jcwODc1OTQ?platform=android##分页获取评论者列表)。

- 为方便用户按需存储圈组消息草稿，支持按圈组频道向本地数据库插入圈组消息草稿，同时可以删除和查询该消息草稿。具体请参考 [插入本地圈组消息草稿](https://doc.yunxin.163.com/messaging/docs/jAyNDk5ODg?platform=android)。

- 支持发送失败的消息自动缓存到本地，并可以通过查询历史消息方法（`getMessageHistory`）获取发送失败的本地消息。具体请参考 [查询历史消息](https://doc.yunxin.163.com/messaging/docs/TM4NDAxMTA?platform=android)。

**API 变更**

方法/回调/类 | 说明
---- | ----
[`insertOrReplaceTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#ae2ce2bd93b134babb1bc0390e00d962f) | 新增接口，用于向本地数据库插入一条缓存数据，如果该频道下已经存在数据，则被新数据覆盖。
[`deleteTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#a99a3ac791f7148dbe013d7d2b375c014) | 新增接口，用于删除指定缓存数据。
[`getTextCache`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#a2ec9edb920b911497803676769681122) | 新增接口，用于获取指定缓存数据。
[`getCommentators`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#a38c57f8cf0d96866712fedd8e4ffcb85) | 新增接口，用于分页获取指定消息的快捷评论者列表。
[`QChatGetMessageHistoryParam`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1param_1_1_q_chat_get_message_history_param.html) | 新增 `isIncludeLocalMessages()` 成员函数，用于指定查询结果是否包含本地圈组消息。

## <span id="9.14.2 - 2024-01-15">9.14.2 (2024-01-15)</span>

**优化**

- 圈组多线程处理优化。
- 获取运营商信息缓存优化。
- 已读回执发送逻辑优化。

## <span id="9.14.1 - 2023-12-04">9.14.1 (2023-12-04)</span>

**新增特性**

支持查询指定时间段内的服务端 Thread 历史消息，具体请参考 [历史消息文档](https://doc.yunxin.163.com/messaging/docs/TI3NTU1NDA?platform=android#查询云端-thread-历史消息)。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`queryThreadTalkHistory`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a602ebe389234f22b65d42e4aee2a26e8) | 分页查询指定时间段内的云端 Thread 历史消息（单聊、群/超大群）。 |

**优化**

内部优化。

## <span id="9.14.0 - 2023-11-10">9.14.0 (2023-11-10)</span>

登录和消息发送逻辑优化。

## <span id="9.13.1 - 2023-10-25">9.13.1 (2023-10-25)</span>

内部优化。

## <span id="9.13.0 - 2023-08-29">9.13.0 (2023-08-29)</span>

**新增特性**

支持配置消息提醒（本地通知消息）的类型，具体请参考 [消息提醒类型](https://doc.yunxin.163.com/messaging/docs/jU3NzgxOTk?platform=android)。

**修复**

- 发送视频消息时，缩略图本地路径（`thumbPath`） 后缀名受视频文件后缀名影响而不规范。
- 用户被踢登出后，在子线程取消下载任务导致崩溃。

## <span id="9.12.2 - 2023-08-21">9.12.2 (2023-08-21)</span>

- 优化动态查询历史消息接口的参数类型。
- 修复 IPV6 URL 转换错误的问题。
- 修复重复收到自定义系统通知离线同步的问题。
- 修复 android 12 后台调用 `startForegroundService` 失败导致的崩溃问题。

## <span id="9.12.1 - 2023-08-01">9.12.1 (2023-08-01)</span>

`SDKOptions` 新增 `reportIgnoredMessage` 字段，支持配置是否上报被过滤的消息。

## <span id="9.12.0 - 2023-07-07">9.12.0 (2023-07-07)</span>

**新增特性**

圈组订阅机制支持自动订阅。开启自动订阅后，当用户登录到圈组服务器，无需手动订阅服务器或频道，进入服务器或频道时即可收到消息、事件和系统通知，退出时则自动取消订阅。具体请参考 [圈组订阅机制](https://doc.yunxin.163.com/messaging/docs/zgwMzQ5MDk?platform=android)。

**优化**

- 优化第三方回调登录内部逻辑，具体请参考 [通过第三方回调登录 IM](https://doc.yunxin.163.com/messaging/docs/TI1MTU1NDc?platform=android#通过第三方回调登录)。
- 优化高级群和超大群的同步逻辑，并新增关闭同步高级群和超大群成员信息的配置项。

**修复**

本次版本修复以下问题：

- 当批量将会话消息未读数清零(标记已读)时，会话数量过大导致报错。
- 下载附件后重新进入 app，文件下载状态未更新。
- 切换 `appkey` 后 `deviceId` 未缓存导致自动登录被踢出。

**API 变更**

API | 说明
---- | ----
`SDKOptions#auto_subscribe` | 新增圈组自动订阅开启/关闭参数。
`SDKOptions#syncConfig` | 新增同步配置参数，可设置是否在初始化时同步高级群/超大群的成员信息，默认为 true（同步）。

## <span id="9.11.2 - 2023-06-20">9.11.2 (2023-06-20)</span>

优化内部逻辑。

## 9.11.1 (2023-06-02)

修复开启数据库加密异常的问题。

## <span id="9.11.0 - 2023-05-30">9.11.0 (2023-05-30)</span>

**新增特性**

- 支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动，具体请参考 [接入第三方机器人](https://doc.yunxin.163.com/messaging/docs/zM4MzA2ODA?platform=android)。
- 新增第三方回调动态登录模式，具体请参考 [登录 IM](https://doc.yunxin.163.com/messaging/docs/TI1MTU1NDc?platform=android)。
- 新增数据准备成功的回调，具体请参考 [监听数据准备完成回调](https://doc.yunxin.163.com/messaging/docs/TI1MTU1NDc?platform=android#监听数据准备完成回调)。
- 支持用户在初始化之后，登录 SDK 之前获取推送 Token，具体请参考 [实现离线推送](https://doc.yunxin.163.com/messaging/docs/zc1OTI2MTM?platform=android#步骤-3初始化-nim-sdk)。

**修复**

- 修复断网重连后进入聊天室又退出的问题。
- 修复锁屏之后 `observeOnlineStatus` 回调过于频繁的问题。
- 修复其他已知问题。

**第三方推送兼容版本**

9.11.0 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.9.0.300
小米 | 5.6.2
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.2.3
荣耀 | 7.0.41.301
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

**API 变更**

API | 说明
---- | ----
`observeDataReady` | 新增数据准备成功回调接口，当消息数据库开启完成后，通知用户数据已准备完成，可以开始发送消息。
`SDKOptions#loginExtProvider` | 新增获取 IM 动态登录扩展信息，用于实现通过第三方回调动态登录 IM。
`chatroomAuthProvider` | 新增获取聊天室动态 Token，用于实现通过动态 Token 登录聊天室。
`chatroomLoginExtProvider` | 新增获取聊天室动态登录扩展信息，用于实现通过第三方回调动态登录聊天室。
`getQuickComments` | 获取圈组快捷评论接口返回的数据中新增快捷评论的创建时间，即 `QChatQuickCommentDetail` 中新增获取评论创建时间的接口（`getCreateTime`）。
`getRobotInfo` | `IMMessage` 消息体中新增获取机器人信息的方法，用于实现机器人消息功能。
`setRobotInfo` | `IMMessage` 消息体中新增设置机器人信息的方法，用于实现机器人消息功能。
`getRealMsgObj` | `IMMessage` 消息体中新增获取消息本身的方法，可通过获取到的消息对象判断是否为圈组消息。
`FileAttachment#setUri` | 发送消息时，消息附件支持设置文件 uri，仅支持 `ContentResolver.SCHEME_FILE` 类型和 `ContentResolver.SCHEME_CONTENT` 类型的 uri
`registerPush` | 新增获取推送 Token 接口。在初始化之后，无论是否登录，可以调用该方法获取推送 Token（Token 通过 `observeMixPushToken` 回调得到）。

## <span id="9.10.1 - 2023-04-18">9.10.1 (2023-04-18)</span>

修复已知问题。

<!--
修复数据上报异常的问题。
-->

## <span id="9.10.0 - 2023-04-11">9.10.0 (2023-04-11)</span>

**API 变更**

初始化参数 `SDKOptions` 中新增 `fixMsgStatusByBlackList` 配置项，默认关闭。开启后，消息状态是否成功需要结合 `isInBlockList`（通过解析消息体得到该字段）进行判断：
- 同步接收到的消息，如果 `isInBlockList==true`，则消息状态修改为 failed。
- 查询云端历史消息，如果 `isInBlockList==true`，则消息状态修改为 failed。

**优化**

- 优化内部拉黑后的消息重发逻辑，具体请参考 [消息重发](https://doc.yunxin.163.com/messaging/docs/DY2MTE1Mzg?platform=android#%E9%87%8D%E5%8F%91%E6%B6%88%E6%81%AF)。
- 优化圈组订阅回调机制。（订阅圈组服务器/频道后，只有未读数变更时才触发回调。）

**修复**

- 修复锁屏之后 observeOnlineStatus 回调过于频繁的问题。
- 修复已登录情况下数据库打开异常的问题。
- 修复其他已知问题。

## <span id="9.9.3 - 2023-03-14">9.9.3 (2023-03-14)</span>

优化动态查询历史消息接口（[`getMessagesDynamically`](https://doc.yunxin.163.com/messaging/api-refer/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a7e04c64027ab59d214642531141f33d4)），主要修复当本地消息后没有云端消息时，本地消息无法被查询到的问题。

## <span id="9.9.2 - 2023-03-07">9.9.2 (2023-03-07)</span>

**新增特性**

- 新增 **[圈组](https://doc.yunxin.163.com/messaging/docs/jUyODc1NDM?platform=android) 用户资料复用 IM 用户资料** 的能力。

    - 如果某用户未配置自己的 [服务器](https://doc.yunxin.163.com/messaging/docs/Tg1NzUyNDQ?platform=android) 成员信息，该用户的初始服务器成员信息将直接复用对应的 IM 用户资料（目前仅支持复用昵称和头像）。

    - 如果某用户在未配置自己的服务器成员信息的情况下修改了自己的 IM 用户资料（昵称或头像），系统通知（通知类型 `MY_MEMBER_INFO_UPDATED`）将触发，通知该用户需要在哪些服务器重新获取自己的资料。

- 在线消息通知栏的 **新消息** 提醒，支持多语言配置。

**数据结构变更**

- [圈组](https://doc.yunxin.163.com/messaging/docs/jUyODc1NDM?platform=android)的系统通知类型 [`QChatSystemNotificationType`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1enums_1_1_q_chat_system_notification_type.html)中新增枚举 `MY_MEMBER_INFO_UPDATED`，表示修改 IM 用户资料触发的圈组服务器成员信息的联动修改。该系统通知的具体触发条件、接收者和接收条件，请参考 [圈组系统通知概述](https://doc.yunxin.163.com/messaging/docs/TkxMzc1NDg?platform=server)中对 `USER_INFO_UPDATE(35)` 的说明。

- 圈组系统通知的投递对象类型 [`QChatSystemMessageToType`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1enums_1_1_q_chat_system_message_to_type.html#details) 新增枚举值 `ACCIDS`，表示发送给指定的用户。

**修复**

部分已知问题修复与优化。

## <span id="9.9.0 - 2023-02-09">9.9.0 (2023-02-09)</span>

**新增特性**

SDK 支持查询指定频道中@当前用户的未读消息，同时也支持批量查询消息是否@当前用户。具体请参考 [查询@我的消息](https://doc.yunxin.163.com/TM5MzM5Njk/docs/DM2MjI1NTU?platform=android)。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`getMentionedMeMessages`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#ae303c54e4f0de99e82e49a990a09cd34) | 查询指定频道中@当前用户的未读消息 |
| [`areMentionedMeMessages`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html#acbe5ff1e0080a24f0475dc6f2a5ca3c4) | 批量查询消息是否@当前用户 |
| [`queryMessageListByTypesV2`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a5423b3a2b038d0e9988d199fd2f95333) | 查询指定消息类型的历史消息<br/>该接口相较于 [`queryMessageListByTypes`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a54b25c6ec34d980a7595f7366bb9f90c) 接口，优化了内部的查询逻辑，请优先使用 `queryMessageListByTypesV2`

**优化**

优化登录超时后的重连机制。

**修复**

- 修复会话状态更新错误问题。
- 修复同一用户在多个群中群昵称不同而被覆盖的问题。
- 修复下载附件完成后主线程操作数据库可能 ANR（Application Not Responding）的问题。
- 修复 NOS 下载过程中取消下载后无法再次下载的问题。
- 修复其他已知问题。

## <span id="9.8.0 - 2022-12-27">9.8.0 (2022-12-27)</span>

该版本的圈组模块新增了游客功能，离线推送模块新增支持荣耀的离线推送。

**新增特性**

 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
--- | --- | --- | ---
1 | 游客功能 | 以游客身份进入服务器，可查询部分信息和接收消息，也可接收部分系统通知 | [游客功能](https://doc.yunxin.163.com/messaging/docs/TA4MjY2NzA?platform=android)
2 | 频道对游客的可见性 | 创建和修改频道时可设置频道是否对游客可见 | [频道管理](https://doc.yunxin.163.com/messaging/docs/TgwMjk5NDY?platform=android)
3 | 频道分组对游客的可见性 | 如果频道对游客可见，则包含该频道的频道分组也对游客可见，且频道分组的查看模式变更可能导致频道对游客的可见性变更 | [频道分组](https://doc.yunxin.163.com/messaging/docs/jUxNTE5MTY?platform=android)
4 | 频道可见性变更系统通知 | 新增系统通知类型 `CHANNEL_VISIBILITY_TO_VISITOR_UPDATE`，表示频道对游客的可见性发生变更 | [游客可接收的系统通知](https://doc.yunxin.163.com/messaging/docs/TA4MjY2NzA?platform=android#可接收的系统通知)
5 | 荣耀推送 | 支持荣耀的推送服务 | [荣耀推送](https://doc.yunxin.163.com/messaging/docs/zc1OTI2MTM?platform=android#荣耀推送)

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`QChatServerService#enterAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_server_service.html#a52cb8e81babeb96ce5bd8af0789c26b3) | 以游客身份进入服务器 |
| [`QChatServerService#leaveAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_server_service.html#aa2d757742f7191a1b5af5bf30ddce458) | 以游客身份离开服务器 |
| [`QChatChannelService#subscribeAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_channel_service.html#aa0b4f940e5c0c58a81211490f9d66181) | 以游客身份订阅频道 |
| [`QChatServerService#subscribeAsVisitor`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_server_service.html#aa62c3f0c126f5fddf3fbbe3616fe5eff) | 以游客身份订阅服务器 |

**变更 API**

| <div style="width:150px">API</div> | API 说明 | 变更说明 |
| --- | --- | ---- |
| [`createChannel`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_channel_service.html#a0bd54c91aadefe261414e2150c4f7b8a) | 创建频道 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |
| [`updateChannel`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_channel_service.html#a74a7649e4171bc58ea75f41b427ce65f) | 修改频道信息 | 新增参数 `visitorMode`，用于设置频道是否对游客可见 |

**优化**

IM SDK 适配 Android 13.0.0。

**修复**

修复部分已知问题。

## <span id="9.7.0 - 2022-12-2">9.7.0 (2022-12-02)</span>

**新增特性**

IM 新增动态查询连续完整的历史消息功能，具体请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/docs/TI3NTU1NDA?platform=android#动态查询历史消息)。

相较于频繁从云端获取，该查询方法在保证历史消息完整的同时，减少了耗时和耗能。

**API 新增**

API | API 说明
---- | ----
[`getMessagesDynamically`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/msg/MsgService.html#getMessagesDynamically-com.netease.nimlib.sdk.msg.model.GetMessagesDynamicallyParam-) | 动态查询连续完整的历史消息

## <span id="9.6.3 - 2022-10-27">9.6.3 (2022-10-27)</span>

**新增特性**

9.6.3 的聊天室模块，新增根据标签（Tags）查询聊天室历史消息的功能，具体请参考 [根据标签查询历史消息](https://doc.yunxin.163.com/messaging/docs/zY5NzQzNjU?platform=android#根据标签查询历史消息)。

**API 新增**

API | API 说明
---- | ----
| [`getMessagesByTags`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/chatroom/ChatRoomService.html#getMessagesByTags-com.netease.nimlib.sdk.chatroom.model.GetMessagesByTagsParam-) | 通过聊天室标签（可多个）来检索聊天室历史消息 |
| [`observeTagsUpdate`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/chatroom/ChatRoomServiceObserver.html#observeTagsUpdate-com.netease.nimlib.sdk.Observer-boolean-) | 监听聊天室标签变更事件，回调包含变更标签的聊天室 ID 和变更后的标签信息 |

**优化**

- 优化同步消息过程中的去重逻辑，减少同步时间。
    - **原逻辑**：按每条消息进行数据库查重，数据库查询次数过多。
    - **现逻辑**：通过批量查询消息进行数据库查重，减少数据库查询次数，减少耗时。
- 修复其他已知问题。

**第三方推送 SDK 兼容版本**

9.6.3 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.5.0.300
小米 | 5.1.0
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

## <span id="9.6.2 - 2022-10-14">9.6.2 (2022-10-14)</span>

修复已知问题。

## <span id="9.6.1 - 2022-10-12">9.6.1 (2022-10-12)</span>

修复同步过程中去重失效，导致数据库可能存在多个相同消息的问题。

## <span id="9.6.0 - 2022-09-26">9.6.0 (2022-09-26)</span>

::: note notice
9.6.1 修复了 9.6.0 可能导致数据库存在相同消息的问题。如果您的应用目前使用的是 9.6.0，强烈建议您升级至 9.6.1。
:::

**新增特性**

 <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div>
--- | --- | --- | ---
1 | @身份组 | 支持在圈组发送消息时@指定身份组 | [圈组消息收发](https://doc.yunxin.163.com/messaging/docs/TE1MjI2MDI?platform=android)
2 | 身份组自定义权限 | 支持通过服务端 API 为身份组添加自定义权限项，帮助开发者快速实现符合自身业务需求的权限管控能力 | [自定义权限](https://doc.yunxin.163.com/messaging/docs/DAyNjkzMjI?platform=android)

**API 变更**

| <div style="width:150px">API</div> | API 说明 | 变更说明 |
| --- | --- |
| [`sendMessage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#sendMessage-com.netease.nimlib.sdk.qchat.param.QChatSendMessageParam-) | 在圈组的频道中发送消息 | <ul><li>参数结构 `QChatSendMessageParam` 新增 `setMentionedRoleidList` 接口，用于发送圈组消息时@指定的身份组。@身份组需要拥有 **@身份组** 权限（`MENTIONED_ROLE`）</li><li>返回的消息体 `QChatMessage` 新增 `getMentionedRoleIdList` 接口，用于获取消息需要@的身份组</li></ul> |
| [`updateServerRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateServerRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateServerRoleParam-) | 修改服务器身份组 | <ul><li> 可配置的权限项新增 **@身份组**（`MENTIONED_ROLE`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项</li></ul> |
| [`updateChannelRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelRoleParam-) | 修改频道身份组 | <ul><li> 可配置的权限项新增 **@身份组**（`MENTIONED_ROLE`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项</li></ul> |
| [`updateChannelCategoryRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryRoleParam-) | 修改频道分组身份组 | <ul><li> 可配置的权限项新增 **@身份组**（`MENTIONED_ROLE`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项</li></ul> |
| [`updateChannelCategoryMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryMemberRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryMemberRoleParam-) | 修改频道分组的用户定制权限 | <ul><li> 可配置的权限项新增 **@身份组**（`MENTIONED_ROLE`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项</li></ul> |
| <a href="https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateMemberRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateMemberRoleParam-" target="_blank">`updateMemberRole` | 修改（频道维度）的用户定制权限 | <ul><li> 可配置的权限项新增 **@身份组**（`MENTIONED_ROLE`）。拥有该权限的成员可在圈组发送消息时@指定身份组（最多 10 个）</li><li>定义身份组权限项的 QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项</li></ul> |
| [`checkPermission`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#checkPermission-com.netease.nimlib.sdk.qchat.param.QChatCheckPermissionParam-) | 查询自己是否拥有某个权限 | 支持查询自定义权限（如果已通过服务端 API 创建自定义权限）。QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项
| [`checkPermissions`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#checkPermissions-com.netease.nimlib.sdk.qchat.param.QChatCheckPermissionsParam-) | 查询自己是否拥有某些权限 | 支持查询自定义权限（如果已通过服务端 API 创建自定义权限）。QChatRoleResource 中新增自定义权限项（如果已通过服务端 API 创建），value 大于或等于 10000 的权限项即为自定义权限项
| <a href="https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/SDKOptions.html" target="_blank">`SDKOptions` | SDK 的初始化配置 | 初始化配置参数中新增 `recentContactContentSource`，用于设置最近会话的消息内容来源。 |

**优化**

<div hidden="hidden">
- 优化登录成功后同步消息的内部逻辑，减少同步时间。
</div>

- 华为推送获取到的网易云信消息体 `pushPayload` 中新增 `data` 字段。
- 解决隐私合规问题。

## <span id="9.5.2 - 2022-09-7">9.5.2 (2022-09-07)</span>

修复断网场景下进行数据上报引起的崩溃问题。

## <span id="9.5.0 - 2022-08-29">9.5.0 (2022-08-29)</span>

**升级必看**

消息发送完成回调与状态实现顺序变更，即将 [`sendMessage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/msg/MsgService.html#sendMessage-com.netease.nimlib.sdk.msg.model.IMMessage-boolean-) 消息发送接口的回调触发，调整到了 [`observeMessageStatus`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/msg/MsgServiceObserve.html#observeMsgStatus-com.netease.nimlib.sdk.Observer-boolean-) 消息状态变化观察者回调触发之后。该变更优化了消息发送完成通知和消息发送状态修改的时序逻辑，具体为：

- **原逻辑**：先通知消息发送完成，再修改消息发送状态。
- **新逻辑**：先修改消息发送状态，再通知消息发送完成。

::: note notice
如果您的应用与该逻辑存在相关依赖，请进行相应调整。
:::

**新增特性**

9.5.0 的圈组模块新增搜索频道成员功能，具体请参考 [搜索服务器和频道](https://doc.yunxin.163.com/messaging/docs/TUzMTY5OTQ?platform=android)。

**优化**

优化 LBS 策略。

**新增 API**

9.5.0 的圈组模块引入了如下 API。

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`searchChannelMembers`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#searchChannelMembers-com.netease.nimlib.sdk.qchat.param.QChatSearchChannelMembersParam-) | 搜索频道成员 |

## <span id="9.4.0 - 2022-08-8">9.4.0 (2022-08-08)</span>

**新增特性**

9.4.0 的圈组模块新增如下特性：

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 批量查询权限 | 支持查询自己是否拥有某些权限 | [查询自己是否拥有某些权限](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DMwODc0Njg?platformId=60002#查询自己是否拥有某些权限) |
| 2 | 以圈组服务器维度处理未读消息数 | 支持订阅服务器所有频道的消息，且支持清空服务器未读数 | [服务器未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DYwNDQ4Nzg?platformId=60002) |
| 3 | 搜索消息 | 支持分页搜索对用户可见的消息。您可通过 `subType` 参数进行相应的上层业务开发，实现消息可见性逻辑。支持配置该参数的 API，请参考下文的 **API 变更** 说明 | [搜索消息](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQ0NDg5MzY?platformId=60002#搜索消息) |

**API 变更**

9.4.0 的圈组模块引入了如下新增 API 和 变更 API。

- **新增 API**

    <div style="width:150px">API</div> | API 说明 |
    --- | --- |
    [`checkPermissions`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#checkPermissions-com.netease.nimlib.sdk.qchat.param.QChatCheckPermissionsParam-) | 查询自己是否圈组内的某些（圈组）权限 |
    [`searchMsgByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#searchMsgByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchMsgByPageParam-) | 分页搜索圈组消息 |
    [`subscribeAllChannel`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#subscribeAllChannel-com.netease.nimlib.sdk.qchat.param.QChatSubscribeAllChannelParam-) | 一次性订阅圈组服务器下最多 200 个频道。单次调用可传入的服务器 ID 数量上限为 10 个。即使多次调用，单个服务器下最多仅能订阅 200 个 频道 |
    [`markRead`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#markRead-com.netease.nimlib.sdk.qchat.param.QChatServerMarkReadParam-) | 清空圈组服务器的未读数 |

- **变更 API**

    <div style="width:150px">API</div> | 变更说明 |
    --- | --- |
    [`sendMessage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#sendMessage-com.netease.nimlib.sdk.qchat.param.QChatSendMessageParam-) | `QChatSendMessageParam` 新增 `subType` 入参，表示消息子类型。该参数可以用来做特殊渲染、可见性判断、动画效果展示等。例如，您可通过该参数开发相应的上层业务逻辑，实现发送消息时设置消息对其他用户的可见性 |
    [`updateMessage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#updateMessage-com.netease.nimlib.sdk.qchat.param.QChatUpdateMessageParam-) | `QChatUpdateMessageParam` 新增 `subType` 入参 |
    [`observeReceiveMessage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServiceObserver.html#observeReceiveMessage-com.netease.nimlib.sdk.Observer-boolean-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |
    [`getMessageHistory`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#getMessageHistory-com.netease.nimlib.sdk.qchat.param.QChatGetMessageHistoryParam-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |
    [`observeMessageUpdate`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServiceObserver.html#observeMessageUpdate-com.netease.nimlib.sdk.Observer-boolean-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |
    [`getMessageHistoryByIds`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#getMessageHistoryByIds-com.netease.nimlib.sdk.qchat.param.QChatGetMessageHistoryByIdsParam-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |
    [`getThreadMessages`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#getThreadMessages-com.netease.nimlib.sdk.qchat.param.QChatGetThreadMessagesParam-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |
    [`getLastMessageOfChannels`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#getLastMessageOfChannels-com.netease.nimlib.sdk.qchat.param.QChatGetLastMessageOfChannelsParam-) | 返回的消息体 `QChatMessage` 新增 `subType` 参数 |

**第三方推送 SDK 兼容版本**

9.4.0 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.5.0.300
小米 | 4.5.0
OPPO | 3.0.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics:20.0.0</li></ul>

## <span id="9.3.0 - 2022-07-25">9.3.0 (2022-07-25)</span>

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 实时互动频道 | 圈组新增实时互动频道，用户可在实时互动频道进行音视频通话等音视频相关操作 | [实时互动频道](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zU0OTczMTQ?platformId=60002) |
| 2 | 获取服务器未读数 | 获取服务器下所有频道的累加消息未读数 | [获取服务器未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DYwNDQ4Nzg?platformId=60002) |
| 3 | 圈组搜索结果自定义排序 | 搜索圈组服务器和频道的匹配结果，可按自定义排序 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUzMTY5OTQ?platformId=60002) |
| 4 | 下载消息附件 | 正常情况收到消息后附件会自动下载。如果下载失败，可调用 API 重新下载 | [下载附件](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQ0NDg5MzY?platformId=60002#下载附件) |
| 5 | 查询邀请/申请记录 | 查询服务器的邀请和申请记录，以及用户个人被邀请加入服务器和申请加入服务器的记录 | [查询申请/邀请的历史记录](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#查询申请/邀请的历史记录) |
| 6 | 生成邀请码 | 拥有 **邀请他人加入服务器的权限** 的用户可生成邀请码，其他用户可通过邀请码加入服务器 | [生成邀请码](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#生成邀请码) |
| 7 | 通过邀请码加入服务器 | 获取到邀请码的用户，可通过邀请码加入服务器 | [通过邀请码加入服务器](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#根据邀请码加入服务器) |

**优化**

新增自动取消订阅逻辑：新增 **频道对当前用户可见性变更** 和 **当前用户进入/退出服务器** 内置系统通知类型。当收到前者时，如存在相应频道的订阅信息，则自动取消订阅该频道的请求。当收到后者（且为退出服务器）时，如存在相应服务器的订阅信息，则自动取消订阅该服务器以及该服务器下所有已订阅频道的请求。圈组订阅机制相关说明，请参考 [圈组订阅机制](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zgwMzQ5MDk?platformId=60002)。

**第三方推送兼容版本**

华为推送兼容版本号更新为 6.5.0.300。

当前版本各第三方推送 SDK 的兼容版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.5.0.300
小米 | 4.5.0
OPPO | 3.0.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics:20.0.0</li></ul>

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`generateInviteCode`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#generateInviteCode-com.netease.nimlib.sdk.qchat.param.QChatGenerateInviteCodeParam-) | 生成邀请码 |
| [`joinByInviteCode`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#joinByInviteCode-com.netease.nimlib.sdk.qchat.param.QChatJoinByInviteCodeParam-) | 通过邀请码加入服务器 |
| [`getInviteApplyRecordOfServer`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#getInviteApplyRecordOfServer-com.netease.nimlib.sdk.qchat.param.QChatGetInviteApplyRecordOfServerParam-) | 查询服务器下的申请记录和邀请记录 |
| [`getInviteApplyRecordOfSelf`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#getInviteApplyRecordOfSelf-com.netease.nimlib.sdk.qchat.param.QChatGetInviteApplyRecordOfSelfParam-) | 用户查询自己的申请记录和邀请记录 |
| [`initialize`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html#aba504ade9abd628adbc7a224b36ac9db) | 初始化实时互动频道模块 |
| [`isInitialized`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html#a34b487ab6664f55f439b3b03a111b577) | 查询初始化状态 |
| [`connect`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html#a1a0832cc7555314ae98641a2659d215f) | 连接实时互动频道 |
| [`disConnect`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html#ad6d7ee0a7f102294265babbbe5bd7807) | 取消连接实时互动频道 |
| [`isConnected`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html#a34b487ab6664f55f439b3b03a111b577) | 查询当前连接状态
| [`addRTCChannelListener`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#a8c2d135cca4ab0194e0496c1dbbf1e26) | 添加实时互动频道事件监听 |
| [`removeRTCChannelListener`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#a79abf492c0301f477350ef4a41a82751) | 移除实时互动频道监听 |
| [`unMuteAudio`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#af0f0fa131a1ea4d9cea120293a7618be) | 打开成员音频 |
| [`muteAudio`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#ad562d746fec00fb2f284b9e3472003f4) | 关闭成员音频 |
| [`startScreenShare`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#ad8a8948aaf3df65aa515811854c70c9b) | 开启本端屏幕共享 |
| [`stopScreenShare`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html#a96aca464449ad0bafb7416fc82a9d80a) | 关闭本端屏幕共享 |
| [`onMemberScreenShareStateChanged`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_listener.html#a4ffd33824bb46a7e92892c5bdd9a8050) | 成员屏幕共享状态回调 |
| [`onMemberAudioMuteChanged`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_listener.html#aaff3fb278c72819fb56fe043b8de962d) | 成员音频状态回调 |
| [`onMemberVideoMuteChanged`](https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_listener.html#a1d7a925d761aebc85156d0bc6328e846) | 成员视频状态回调 |
| [`downloadAttachment`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/chatroom/ChatRoomService.html#downloadAttachment-com.netease.nimlib.sdk.chatroom.model.ChatRoomMessage-boolean-) | 正常情况收到消息后附件会自动下载。如果下载失败，可调用该方法重新下载 |
| [`observeServerUnreadInfoChanged`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServiceObserver.html#observeServerUnreadInfoChanged-com.netease.nimlib.sdk.Observer-boolean-) | 注册/注销服务器未读通知接收观察者 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| --- | --- |
| [`inviteServerMembers`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#inviteServerMembers-com.netease.nimlib.sdk.qchat.param.QChatInviteServerMembersParam-) | 入参新增 `ttl`（可选），表示加入服务器邀请的有效时长。回参新增 `requestId` 和 `expireTime`，分别表示邀请的标识和邀请的到期时间戳 |
| [`applyServerJoin`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#applyServerJoin-com.netease.nimlib.sdk.qchat.param.QChatApplyServerJoinParam-) | 入参新增 `ttl`（可选），表示加入服务器申请的有效时长。回参新增 `requestId` 和 `expireTime`，分别表示申请的标识和申请的到期时间戳 |
| [`acceptServerApply`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#acceptServerApply-com.netease.nimlib.sdk.qchat.param.QChatAcceptServerApplyParam-) | 新增 `requestId` 入参（必传），表示加入服务器申请的标识 |
| [`rejectServerApply`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#rejectServerApply-com.netease.nimlib.sdk.qchat.param.QChatRejectServerApplyParam-) | 新增 `requestId` 入参（必传），表示加入服务器申请的标识 |
| [`acceptServerInvite`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#rejectServerApply-com.netease.nimlib.sdk.qchat.param.QChatRejectServerApplyParam-) | 新增 `requestId` 入参（必传），表示加入服务器邀请的标识 |
| [`rejectServerInvite`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#rejectServerInvite-com.netease.nimlib.sdk.qchat.param.QChatRejectServerInviteParam-) | 新增 `requestId` 入参（必传），表示加入服务器邀请的标识 |
| [`createChannel`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#createChannel-com.netease.nimlib.sdk.qchat.param.QChatCreateChannelParam-) | 可创建的频道类型枚举 [`QChatChannelType`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/enums/QChatChannelType.html) 增加枚举值 `RTCChannel`，表示实时互动频道。 |
| [`updateServerRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateServerRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateServerRoleParam-) | 可修改的服务器身份组权限 [`QChatRoleResource`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/enums/QChatRoleResource.html) 新增实时互动相关权限、邀请申请管理权限和邀请申请历史记录查看权限 |
| [`updateChannelRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelRoleParam-) | 可修改的频道身份组权限新增实时互动频道相关权限 |
| [`updateChannelRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelRoleParam-) | 可修改的频道身份组权限新增实时互动频道相关权限 |
| [`updateMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateMemberRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateMemberRoleParam-) | 可修改的个人定制权限新增实时互动频道相关权限 |
| [`updateChannelCategoryRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryRoleParam-) | 可修改的个人定制权限新增实时互动频道相关权限 |
| [`updateChannelCategoryMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryMemberRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryMemberRoleParam-) | 可修改的频道分组维度的个人定制权限新增实时互动频道相关权限 |
| [`searchServerByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#searchServerByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchServerByPageParam-) | 新增入参 `sort`，表示频道的排序条件 |
| [`searchChannelByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#searchChannelByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchChannelByPageParam-) | 新增入参 `sort`，表示频道的排序条件 |

## <span id="9.2.8 - 2022-07-1">9.2.8 (2022-07-01)</span>

优化自动重连机制，实现国内外节点平滑迁移。

## <span id="9.2.5 - 2022-06-13">9.2.5 (2022-06-13)</span>

该版本在圈组模块增加了圈组系统通知的类型。

| <div style="width:90px">相关模块</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- |
| 圈组系统通知 | 1. 新增以下 5 种圈组系统通知类型：</br> <ul><li>加入服务器身份组成员</li><li>移除服务器身份组成员</li><li>更新服务器身份组权限</li><li>更新频道身份组权限</li><li>更新频道个人定制权限</li></ul>具体可查看 [`QChatSystemNotificationType`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/enums/QChatSystemNotificationType.html)</br></br>2. 对应新增 5 种圈组系统通知附件结构类型，具体可查看[`QChatSystemNotificationAttachment`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/model/systemnotification/QChatSystemNotificationAttachment.html) | [系统通知](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TA4NjcwNTc?platformId=60002) |

## <span id="9.2.1 - 2022-05-26">9.2.1 (2022-05-26)</span>

解决 [`NIMClient.config`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/NIMClient.html#config-Context-com.netease.nimlib.sdk.auth.LoginInfo-com.netease.nimlib.sdk.SDKOptions-) 方法极低概率下会获取设备当前进程的问题。

## <span id="9.2.0 - 2022-05-24">9.2.0 (2022-05-24)</span>

该版本在圈组模块增加了频道分组、消息正在输入状态显示和搜索功能等更新。

::: note notice :::
NIM SDK 9.2.1 版本修复了 9.2.0 版本中 `NIMClient.config` 方法有概率获取设备当前进程的问题。如您当前使用的是 9.2.0 版本，强烈建议您升级至 9.2.1。
:::

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> | <div style="width:100px">相关文档</div> |
| --- | --- | --- | --- |
| 1 | 频道分组 | 支持对频道进行分组管理 | [频道分组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jUxNTE5MTY?platformId=60002) |
| 2 | 频道分组黑白名单 | 支持为频道分组设置黑白名单成员/身份组，与频道类型（私密/公开）共同判定频道分组是否对用户可见 | [频道分组黑白名单](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jA3NjE4Mjc?platformId=60002   ) |
| 3 | 频道分组身份组 | 支持在频道分组维度设置身份组和定制权限，增加用户权限控制的层级 | [频道分组身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQwMzEwNzI?platformId=60002) |
| 4 | 消息正在输入 | 支持显示频道消息正在输入 | [消息正在输入](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jA4OTU0ODc?platformId=60002) |
| 5 | 圈组搜索功能 | 支持通过关键字对服务器、频道和服务器成员进行搜索 | [圈组搜索功能](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUzMTY5OTQ?platformId=60002) |
| 6 | 频道分组推送配置 | 支持在频道分组层级配置推送 | [推送管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQyMzk0MDQ?platformId=60002)

**新增 API**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`createChannelCategory`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#createChannelCategory-com.netease.nimlib.sdk.qchat.param.QChatCreateChannelCategoryParam-) | 创建频道分组 |
| [`deleteChannelCategory`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#deleteChannelCategory-com.netease.nimlib.sdk.qchat.param.QChatDeleteChannelCategoryParam-) | 删除频道分组 |
| [`updateChannelCategory`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#updateChannelCategory-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryParam-) | 修改频道分组信息 |
| [`getChannelCategories`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getChannelCategories-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoriesParam-) | 查询频道分组 |
| [`getChannelCategoriesByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getChannelCategoriesByPage-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoriesByPageParam-) | 分页查询服务器下的频道分组列表 |
| [`getChannelsInCategoryByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getChannelsInCategoryByPage-com.netease.nimlib.sdk.qchat.param.QChatGetChannelsInCategoryByPageParam-) | 分页查询频道分组下频道列表 |
| [`addChannelCategoryRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#addChannelCategoryRole-com.netease.nimlib.sdk.qchat.param.QChatAddChannelCategoryRoleParam-) | 创建频道分组身份组 |
| [`removeChannelCategoryRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#removeChannelCategoryRole-com.netease.nimlib.sdk.qchat.param.QChatRemoveChannelCategoryRoleParam-) | 删除频道分组身份组 |
| [`updateChannelCategoryRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryRoleParam-) | 更新频道分组身份组。设置频道分组身份组的权限，需调用该方法 |
| [`getChannelCategoryRoles`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#getChannelCategoryRoles-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoryRolesParam-) | 查询频道分组身份组信息 |
| [`addChannelCategoryMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#addChannelCategoryMemberRole-com.netease.nimlib.sdk.qchat.param.QChatAddChannelCategoryMemberRoleParam-) | 创建频道分组某人的定制权限 |
| [`removeChannelCategoryMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#removeChannelCategoryMemberRole-com.netease.nimlib.sdk.qchat.param.QChatRemoveChannelCategoryMemberRoleParam-) | 删除频道分组某人的定制权限 |
| [`updateChannelCategoryMemberRole`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#updateChannelCategoryMemberRole-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryMemberRoleParam-) | 修改频道分组某人的定制权限。 |
| [`getChannelCategoryMemberRoles`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatRoleService.html#getChannelCategoryMemberRoles-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoryMemberRolesParam-) | 查询频道分组某人的定制权限 |
| [`updateChannelCategoryBlackWhiteRoles`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#updateChannelBlackWhiteRoles-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelBlackWhiteRolesParam-) | 更新频道分组黑白名单身份组 |
| [`getChannelCategoryBlackWhiteRolesByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getChannelCategoryBlackWhiteRolesByPage-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoryBlackWhiteRolesByPageParam-) | 分页查询频道分组黑白名单身份组列表 |
| [`updateChannelCategoryBlackWhiteMembers`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#updateChannelCategoryBlackWhiteMembers-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelCategoryBlackWhiteMembersParam-) | 更新频道分组黑白名单成员 |
| [`getChannelCategoryBlackWhiteMembersByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getChannelCategoryBlackWhiteMembersByPage-com.netease.nimlib.sdk.qchat.param.QChatGetChannelCategoryBlackWhiteMembersByPageParam-) | 分页查询频道分组黑白名单成员列表 |
| [`getExistingChannelCategoryBlackWhiteRoles`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getExistingChannelCategoryBlackWhiteRoles-com.netease.nimlib.sdk.qchat.param.QChatGetExistingChannelCategoryBlackWhiteRolesParam-) | 批量查询频道分组黑白名单身份组列表 |
| [` getExistingChannelCategoryBlackWhiteMembers`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getExistingChannelCategoryBlackWhiteMembers-com.netease.nimlib.sdk.qchat.param.QChatGetExistingChannelCategoryBlackWhiteMembersParam-) | 批量查询频道分组黑白名单成员列表 |
| [`observeReceiveTypingEvent`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServiceObserver.html#observeReceiveTypingEvent-com.netease.nimlib.sdk.Observer-boolean-) | 监听正在输入事件 |
| [`sendTypingEvent`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatMessageService.html#sendTypingEvent-com.netease.nimlib.sdk.qchat.param.QChatSendTypingEventParam-) | 发送正在输入事件 |
| [`searchServerByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#searchServerByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchServerByPageParam-) | 分页搜索服务器 |
| [`searchServerMemberByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatServerService.html#searchServerMemberByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchServerMemberByPageParam-) | 分页搜索服务器成员 |
| [`searchChannelByPage`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#searchChannelByPage-com.netease.nimlib.sdk.qchat.param.QChatSearchChannelByPageParam-) | 分页搜索频道 |
| [`updateUserChannelCategoryPushConfig`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#updateUserChannelCategoryPushConfig-com.netease.nimlib.sdk.qchat.param.QChatUpdateUserChannelCategoryPushConfigParam-) | 更新用户频道分组推送配置 |
| [`getUserChannelCategoryPushConfigs`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#getUserChannelCategoryPushConfigs-com.netease.nimlib.sdk.qchat.param.QChatGetUserChannelCategoryPushConfigsParam-) | 获取用户频道分组推送配置列表 |

**变更 API**

| <div style="width:150px">API</div> | 变更说明 |
| --- | --- |
| [`createChannel`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#createChannel-com.netease.nimlib.sdk.qchat.param.QChatCreateChannelParam-) | 新增 `categoryId` 和 `syncMode` 参数，调用时传入 `categoryId` 可将频道加入某个频道分组。通过设置 `syncMode`，可实现频道数据与频道分组数据的同步。具体同步的数据包括查看模式（私密或公开）、黑白名单和身份组权限。 |
| [`updateChannel`](https://dev.yunxin.163.com/docs/interface/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFAndroid%E7%AB%AF/IM_Android/com/netease/nimlib/sdk/qchat/QChatChannelService.html#updateChannel-com.netease.nimlib.sdk.qchat.param.QChatUpdateChannelParam-) | 同上

## <span id="9.1.1 - 2022-04-14">9.1.1 (2022-04-14)</span>

修复了 Gradle 集成时提示 R 文件重复导致的不能打包的问题。

## <span id="9.1.0 - 2022-04-11">9.1.0 (2022-04-11)</span>

::: note notice
如您当前使用 9.1.0 版本的 SDK，强烈建议您将其升级至 9.1.1 版本。9.1.1 版本修复了 9.1.0 版本中存在的打包报错问题。
:::

**新增特性**

- **圈组相关更新**：
    - 当用户在服务器维度没有 **管理角色** 权限，但在频道维度有该权限时，可在 `getServerRoles` 方法的 `QChatGetServerRolesParam` 中传入 `channelId` 参数查询整个服务器的身份组列表，以便对频道进行权限添加。相关详情请参考 [查询某服务器下身份组列表](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DMwODc0Njg?platformId=60002#查询某服务器下身份组列表)。
    - 新增封禁用户功能。
        - 创建或更新身份组时可配置 `BAN_SERVER_MEMBER()` 参数为身份组成员授予封禁其他成员的权限。相关详情请参考 [创建服务器身份组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DMwODc0Njg?platformId=60002#创建服务器身份组)。
        - 拥有封禁其他成员权限的服务器成员可封禁或解封其他成员。相关方法调用详情请参考 [封禁服务器成员](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#封禁服务器成员)、[解禁服务器成员](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#解禁服务器成员) 和 [分页查询服务器封禁成员列表](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zY3MjQzMTc?platformId=60002#分页查询服务器封禁成员列表)。
    - 新增 Thread 聊天和快捷评论功能。
    - 新增圈组反垃圾功能。
        - 支持通过 `getAntiSpamOption()` 获取消息反垃圾选项，通过 `getAntiSpamOption()` 获取消息反垃圾结果（仅对文本和图片有效）。相关调用详情请参考 [消息管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DMwODc0Njg?platformId=60002#创建服务器身份组)。
        - 支持为服务器、频道和身份组的创建和更新操作配置反垃圾 `QChatAntiSpamConfig`。
    - 更新圈组推送逻辑。新的推送逻辑详情请参考 [圈组推送](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUwNDkwODc)。相关的方法调用请参考 [更新服务器推送配置
](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zA1OTMxNjY?platformId=60002#更新服务器推送配置)、[更新频道推送配置](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jk5NTM1NTc?platformId=60002#更新频道推送配置)和[推送管理](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQyMzk0MDQ)。
    - 支持在 IM SDK 初始化时配置消息缓存。相关详情请参考 [圈组消息缓存](https://doc.yunxin.163.com/messaging/guide/jE3NTUxOTM?platform=android) 的 `enabledQChatMessageCache` 参数说明。
- **各厂家推送兼容更新**：
    - 兼容 Vivo push SDK 3.0.0.4_484 且兼容 Android 12.0.0。
    - 兼容 OPPO PUSH SDK 3.0.0。
    - 兼容华为推送 SDK 6.3.0.302。
- **其他更新**：
    - 新增未读相关操作按会话类型分类的能力。可通过 sessiontype [获取指定会话类型的总未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TgyOTE3MDI/获取指定会话类型的总未读数)、[清除未读数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TgyOTE3MDI#重置未读数)。

**改进优化**

- 修复了终端用户开启消息漫游后在不同手机登录时收到的消息发送结果不一致的问题（一台手机上显示消息发送成功，另一台上显示消息发送失败）。
- 其他问题修复及优化。

## <span id="9.0.1 - 2022-03-10">9.0.1 (2022-03-10)</span>

**修复**

修复因圈组 SDK bug 导致的成员管理界面的成员头像显示不全的问题。

**优化**

优化消息未读数更新逻辑：

- 如果 `isHistoryEnable` 或 `isNeedBadge` 为 `false`，消息未读数不更新。
- 删除未读消息时更新未读数，且同步更新 `mentionedCount`。
- 删除已读消息时不更新未读数。
- 自己的消息不更新未读数。

## <span id="9.0.0 - 2022-02-24">9.0.0 (2022-02-24)</span>

**新增**

- 网易云信即时通讯服务全新能力 **圈组** 发布。相关功能介绍和开发集成请分别参考 [什么是圈组](https://doc.yunxin.163.com/docs/TM5MzM5Njk/jUyODc1NDM) 和 [圈组接入流程](https://doc.yunxin.163.com/docs/TM5MzM5Njk/Tk3NzY0OTM)。

## <span id="8.11.1 - 2022-01-17">8.11.1 (2022-01-17)</span>

**修复**

- 修复推送被异常关闭问题

## <span id="8.11.0 - 2022-01-10">8.11.0 (2022-01-10)</span>

::: note notice
如果您当前使用的是 8.11.0 版本的 SDK，强烈推荐您将 SDK 版本升级到 8.11.1 或以上版本。8.11.1 版本修复了 8.11.0 版本中存在的推送异常关闭问题。该问题具体为：融合存储关闭后，Android 系统推送开启与否都无法推送成功。
:::

**新增**

- 支持聊天室空间消息功能。[进入聊天室](/docs/TM5MzM5Njk/zY5NzQzNjU#支持聊天室空间消息) 和 [发送聊天室消息](/docs/TM5MzM5Njk/zY5NzQzNjU#发送带位置信息的消息) 支持配置 x, y, z 坐标，支持 [坐标位置实时更新](/docs/TM5MzM5Njk/zY5NzQzNjU#更新位置信息)
- 支持聊天室定向消息功能。[发送聊天室消息支持消息接受者列表](/docs/TM5MzM5Njk/zY5NzQzNjU#发送定向消息)
- 支持[聊天室标签实时更新](/docs/TM5MzM5Njk/zY5NzQzNjU#更新聊天室标签)
- 匿名聊天室和独立聊天室[支持第三方 token 鉴权](/docs/TM5MzM5Njk/zY5NzQzNjU#鉴权方式)
- 支持业务反垃圾。涉及 [进入聊天室](/docs/TM5MzM5Njk/zY5NzQzNjU#进入聊天室)、[更新我的用户资料](/docs/TM5MzM5Njk/zg1NDIzNzI#编辑用户资料)、[创建群](/docs/TM5MzM5Njk/DE2MjM2MTE#创建群组)、[更新群信息](/docs/TM5MzM5Njk/DE2MjM2MTE#编辑多个资料)、[更新超大群信息](/docs/TM5MzM5Njk/jM5MTgzNzA#编辑多个资料)、[更新聊天室信息](/docs/TM5MzM5Njk/zY5NzQzNjU#修改聊天室信息) 和[更新我的聊天室资料](/docs/TM5MzM5Njk/zY5NzQzNjU#修改自身信息)

**修复**

- 修复注销异常导致导致上次的数据库没有关闭问题
- 修改被踢出后又自动登录问题

## <span id="8.10.0 - 2021-12-23">8.10.0 (2021-12-23)</span>

**新增**

- 支持 s3 存储

**修复**

- 修复历史消息可能再次漫游下发问题
- 修改部分异常场景下错误日志记录崩溃问题

**变更**

- SDK 最低支持 android 5.0

## <span id="8.9.0 - 2021-12-03">8.9.0 (2021-12-03)</span>

**新增**

- [支持自定义配置在线通知的通道](/docs/TM5MzM5Njk/zU4NzUxNjI#初始化配置参数)
- [获取到离线推送 token 的统一回调](/docs/TM5MzM5Njk/zc1OTI2MTM#token回调)
- 最大支持好友数至 1 万
- 适配 Android 12 PendingIntent

**变更**

- [FCS 推送升级，firebase:28.4.2 (firebase-messaging:23.0.0, firebase-analytics:20.0.0)](/docs/TM5MzM5Njk/zc1OTI2MTM#谷歌推送)

## <span id="8.8.0 - 2021-10-28">8.8.0 (2021-10-28)</span>

**新增**

- [支持批量添加聊天室队列元素（由服务端发起）](/docs/TM5MzM5Njk/zY5NzQzNjU#聊天室通知消息)
- [增加全文云端消息检索（按消息时间排序）接口](/docs/TM5MzM5Njk/TI3NTU1NDA#全文云端消息检索(按消息时间排列))

**修复**

- 修复连续开启推送报错的问题

## <span id="8.7.2 - 2021-09-27">8.7.2 (2021-09-27)</span>

<div style="display:none">

**新增**

- 新增 [获取指定会话未读消息列表](/docs/TM5MzM5Njk/TgyOTE3MDI#获取指定会话未读消息列表) 接口
</div>

**变更**

- Android9 之后版本避免 getRunningAppProcesses 调用

## <span id="8.7.0 - 2021-08-25">8.7.0 (2021-08-25)</span>

**新增**

- 支持 [聊天室撤回消息](/docs/TM5MzM5Njk/zY5NzQzNjU#聊天室通知消息) （撤回动作由服务端发起）
- 聊天室 [加入或者更新队列元素](/docs/TM5MzM5Njk/zY5NzQzNjU#加入或者更新队列元素) 时，支持配置队列元素所属账号
- 支持[分页获取最近会话列表](/docs/TM5MzM5Njk/TgyOTE3MDI#分页获取最近会话列表)
- 消息体新增易盾反垃圾扩展字段 `yidunAntiSpamExt` 和结果字段 `yidunAntiSpamRes`，具体参考 [消息重要参数](https://doc.yunxin.163.com/docs/TM5MzM5Njk/zU5ODg2NDU?platformId=60002#%E6%B6%88%E6%81%AF%E7%BB%93%E6%9E%84%E4%B8%AD%E7%9A%84%E9%87%8D%E8%A6%81%E5%8F%82%E6%95%B0)。

**变更**

- [小米推送版本升级至 4.5.0](/docs/TM5MzM5Njk/zc1OTI2MTM#小米推送)
- [魅族推送版本升级至 4.1.0](/docs/TM5MzM5Njk/zc1OTI2MTM#魅族推送)

**修复**

- 修复 MixPushService 的 enable 接口异常情况下可能没有回调问题
- 修复 Https 使用了不安全的 HostNameVerifier 导致在 Google play 无法上架问题、
- 修复后台频繁获取正在运行应用信息问题

## <span id="8.6.2 - 2021-08-06">8.6.2 (2021-08-06)</span>

**修复**

- 提高上传文件时 SDK 的稳定性
- 修复删除不需要未读的消息时未读数也减少的问题

## <span id="8.6.1 - 2021-07-27">8.6.1 (2021-07-27)</span>

**新增**

- [支持 FCM 推送配置自定义字段 `fcmField`](/docs/TM5MzM5Njk/zc1OTI2MTM#推送渠道的选择)
- [支持根据免打扰状态获取总未读数](/docs/TM5MzM5Njk/TgyOTE3MDI#支持根据免打扰状态获取总未读数)
- [发消息支持设置第二段等待时间](/docs/TM5MzM5Njk/zU4NzUxNjI#初始化)

**变更**

- [支持通过 token 的获取情况选择推送渠道](/docs/TM5MzM5Njk/zc1OTI2MTM#推送渠道的选择)
- [华为推送升级 5.3.0.304](/docs/TM5MzM5Njk/zc1OTI2MTM#华为推送)
- [Vivo 升级 3.0.0](/docs/TM5MzM5Njk/zc1OTI2MTM#VIVO 推送)

**修复**

- 修复退出登录时会取消所有 Job 的问题，修复后只会取消网易云信 SDK 的 Job
- 修复频控场景下，频控包被转为心跳包的问题
- 修复 Android11 上没有电话权限导致发送文件失败的问题
- 修复批量删除消息不成功的问题
- 修复未读情况下撤回他人消息时，未读数不变更的问题

## <span id="8.5.0 - 2021-06-22">8.5.0 (2021-06-22)</span>

**新增**

- [支持云端历史消息全文检索](/docs/TM5MzM5Njk/TI3NTU1NDA#全文云端消息检索)
- [本地检索](/docs/TM5MzM5Njk/TI3NTU1NDA#本地消息检索) 功能就 [单会话检索](/docs/TM5MzM5Njk/TI3NTU1NDA#单会话检索(新)) 和 [全局检索](/docs/TM5MzM5Njk/TI3NTU1NDA#全局检索(新)) 分别新增支持更多种配置项的接口
- [查询指定群消息的已读回执，支持指定群成员列表](/docs/TM5MzM5Njk/Tg1MDU1OTE#群聊消息已读回执)

**变更**

- [支持撤回自己给自己发送的消息](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息撤回)

**修复**

- 修复通过 [openLocalCache](/docs/TM5MzM5Njk/zU4NzUxNjI#其他辅助方法) 初始化数据库时，绕开了部分本地缓存初始化步骤的问题

## <span id="8.4.6 - 2021-06-02">8.4.6 (2021-06-02)</span>

**变更**

- 提升高可用服务稳定性
- 录音时不再强制检测存储权限
- 打印日志时如果日志模块尚未初始化，不再直接抛出异常

## <span id="8.4.0 - 2021-04-29">8.4.0 (2021-04-29)</span>

**新增**

- [创建会话支持配置是否通过消息数据库设置最后一条消息](/docs/TM5MzM5Njk/TgyOTE3MDI#创建最近会话)
- [支持从本地数据库查询群已读回执内容](/docs/TM5MzM5Njk/Tg1MDU1OTE#群聊消息已读回执)
- [聊天室设置标签标志加入聊天室及按标签发送消息、查询成员详情及总数、禁言能力](/docs/TM5MzM5Njk/TMxOTI0MDA)
- [支持通过设置过滤器来调控收到撤回通知时否弹出通知栏](/docs/TM5MzM5Njk/Tg1MDU1OTE#撤回是否展示通知的过滤器设置)
- 登录抄送新增 SDK 外部版本号

**变更**

- **前面版本覆盖安装当前版本，可以正常自动登录**
- [批量删除本地消息](/docs/TM5MzM5Njk/TI3NTU1NDA#删除多条消息)和 [批量单向删除消息](/docs/TM5MzM5Njk/TI3NTU1NDA#单向删除多条云端历史消息) 会更新未读数
- [通知栏合并方式](/docs/TM5MzM5Njk/zc1OTI2MTM#消息提醒配置)为 **按会话折叠** 或 **全部不折叠** 时收到已读 ack，清理对应会话的通知栏

**修复**

- [修复更新消息状态时，附件包含单引号就会失败的问题](/docs/TM5MzM5Njk/Tg1MDU1OTE#扩展字段更新)

- [删除本地会话配置 sendAck 标记除了发送 ack 告诉其他端已读外，本端也设置消息已读](/docs/TM5MzM5Njk/TgyOTE3MDI#删除最近会话)

    :::note note
    未读数变化后会触发 [observeRecentContact](/docs/TM5MzM5Njk/TgyOTE3MDI#更新最近会话)回调，并且不保证和删除回调之间的时序，8.5.0 起不再触发[observeRecentContact](/docs/TM5MzM5Njk/TgyOTE3MDI#更新最近会话) 回调。
    :::

## <span id="8.3.1 - 2021-03-22">8.3.1 (2021-03-22)</span>

**变更**

- 提高 SDK 稳定性
- 优化缺省 lbs 生成规则

**修复**

- SDK 初始化对 httpdns 访问过于频繁的问题

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.3.0 - 2021-03-03">8.3.0 (2021-03-03)</span>

**变更**

- [清空未读数接口 `clearUnreadCount` 支持接收 ack 请求结果的回调](/docs/TM5MzM5Njk/TgyOTE3MDI#重置未读数)
- 支持通过配置 [LoginInfo](/docs/TM5MzM5Njk/zU4NzUxNjI#手动登录) 进行动态登录

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.2.5 - 2021-02-04">8.2.5 (2021-02-04)</span>

**变更**

- 完善域名高可用策略，提升服务稳定性
- [单击通知栏支持回调字符串](/docs/TM5MzM5Njk/zc1OTI2MTM#消息提醒配置)，修改 NotificationExtraTypeEnum#notificationExtraType 的默认值为 MESSAGE。如果本来没有显式配置此参数，**8.2.0 及之后** 的版本升级到当前版本需要显式配置此参数为 JSON_ARR_STR，来维持原有逻辑。**8.2.0 之前（不含）** 的版本不需要做额外工作来维持原有逻辑

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.2.2 - 2021-01-19">8.2.2 (2021-01-19)</span>

**新增**

- 数据库新增恢复能力

**变更**

- 优化前后台切换逻辑，减少卡顿
- 根据手机品牌的不同优化前台进程被杀死的处理逻辑

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.2.0 - 2020-12-30">8.2.0 (2020-12-30)</span>

**新增**

- [支持批量查询群组信息](/docs/TM5MzM5Njk/DE2MjM2MTE#从云端获取指定群组)
- OnePlus 和 RealMe 手机支持通过 [OPPO 推送](/docs/TM5MzM5Njk/zc1OTI2MTM#OPPO推送) 下发消息推送
- [删除会话支持配置删除范围](/docs/TM5MzM5Njk/TgyOTE3MDI#删除最近会话)
- [撤回消息支持扩展字段](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息撤回)
- [单击通知栏支持回调字符串](/docs/TM5MzM5Njk/zc1OTI2MTM#消息提醒配置)，**维持原有逻辑，需要配置 NotificationExtraTypeEnum#notificationExtraType 为 MESSAGE**
- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败**

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.1.3 - 2020-11-27">8.1.3 (2020-11-27)</span>

**新增**

- [支持批量清除会话的未读数](/docs/TM5MzM5Njk/TgyOTE3MDI#重置未读数)

**变更**

- [小米推送升级 3.8.5](/docs/TM5MzM5Njk/zc1OTI2MTM#小米推送)

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.1.0 - 2020-11-13">8.1.0 (2020-11-13)</span>

**新增**

- NOS 下载支持独立 CDN 域名配置
- NOS 下载域名加速支持多域名配置
- 聊天室支持 CDN 消息机制

**注意**

- **不使用 IMEI 作为 deviceID，从 8.0.1 及以下升级到此版本及以后会产生 deviceID 的变更，导致第一次自动登录失败。8.4.0 起不再受此限制，可以顺畅自动登录**

## <span id="8.0.1 - 2020-10-23">8.0.1 (2020-10-23)</span>

**变更**

- [华为推送兼容性配置](/docs/TM5MzM5Njk/zc1OTI2MTM#华为推送)中的 action 配置内容调整
- [数据库加密库 Sqlcipher 升级 3.5.9](/docs/TM5MzM5Njk/zU4NzUxNjI#SDK 集成)
- [支持注册初始化状态监听](/docs/TM5MzM5Njk/zU4NzUxNjI#初始化状态监听)

## <span id="8.0.0 - 2020-09-28">8.0.0 (2020-09-28)</span>

**新增**

- 数据库支持加密，通过 [初始化配置参数](/docs/TM5MzM5Njk/zU4NzUxNjI#初始化配置参数)中的 `databaseEncryptKey` 参数控制。[StatusCode](/docs/TM5MzM5Njk/zU4NzUxNjI#登录状态监听) 增加一个新状态值 `DATA_UPGRADE`，表明当前数据库需要迁移到加密状态。
- [单向删除](/docs/TM5MzM5Njk/Tg1MDU1OTE#单向删除)消息支持删除单条、多条、和会话，同时支持多端同步
- [撤回消息支持配置附言](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息撤回)
- [云端最近会话最后一条消息增加撤回通知类型](/docs/TM5MzM5Njk/jcwMDc4MTY#RecentSession接口说明)
- [拉取云端消息支持配置过滤规则](/docs/TM5MzM5Njk/TI3NTU1NDA#云端历史消息查询)
- [Oppo 推送升级 2.1.0](/docs/TM5MzM5Njk/zc1OTI2MTM#OPPO推送)
- [魅族推送升级 3.9.7](/docs/TM5MzM5Njk/zc1OTI2MTM#魅族推送)

**变更**

- 'SDK 集成'时需要 [在 `AndroidManifest.xml` 中增加 `PreferenceContentProvider` 的声明](/docs/TM5MzM5Njk/zU4NzUxNjI#权限与组件)。

## <span id="7.8.1 - 2020-07-29">7.8.1 (2020-07-29)</span>

**新增**

- [获取聊天室成员列表支持按进入时间排序](/docs/TM5MzM5Njk/zY5NzQzNjU#分页获取聊天室成员)，[MemberQueryType 新增 GUEST_DESC 和 GUEST_ASC](/docs/TM5MzM5Njk/zY5NzQzNjU#聊天室成员概述)，[API](/docs/interface/即时通讯 Android 端/IM_Android/com/netease/nimlib/sdk/chatroom/ChatRoomService.html#fetchRoomMembers-java.lang.String-com.netease.nimlib.sdk.chatroom.constant.MemberQueryType-long-int-)

## <span id="7.8.0- (2020-07-21)">7.8.0 (2020-07-21)</span>

**新增**

- [登录可配置自定义客户端类型，用于自定义互踢功能](/docs/TM5MzM5Njk/zU4NzUxNjI#登录)
- [支持为消息配置子类型](/docs/TM5MzM5Njk/Tg1MDU1OTE#功能概述)
- [华为推送升级 4.0.4.301](/docs/TM5MzM5Njk/zc1OTI2MTM#华为推送)
- [删除单条消息支持配置是否记录操作](/docs/TM5MzM5Njk/TI3NTU1NDA#删除单条消息)

**变更**

- 调整断网重连的退避策略，加快重连节奏
- 私有化环境更新时更新 nos 缓存

## <span id="7.7.2- (2020-06-12)">7.7.2 (2020-06-12)</span>

**新增**

- [IM 和聊天室消息体新增易盾反垃圾字段](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息功能概述)
- Android 8.0 起，SDK 调用 startForeground 均会有通知栏提示

## <span id="7.7.0- (2020-05-27)">7.7.0 (2020-05-27)</span>

**新增**

- [IMMessage 新增 getCallbackExtension() 函数，获取第三方回调自定义扩展字段](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息功能概述)
- StatusCode 新增描述字段，服务端踢人如果附加描述，可以通过此字段获取

## <span id="7.6.0- (2020-05-13)">7.6.0 (2020-05-13)</span>

**新增**

- [消息回复](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息回复)
- [快捷评论](/docs/TM5MzM5Njk/Tg1MDU1OTE#快捷评论)
- [收藏](/docs/TM5MzM5Njk/Tg1MDU1OTE#收藏)
- [消息 PIN](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息PIN)
- [会话置顶](/docs/TM5MzM5Njk/Tg1MDU1OTE#会话置顶)
- 主动上传日志消息
- 自定义通知回调按到达顺序

**变更**

- 未接通的音视频通话话单通知存离线，漫游和云端历史

## <span id="7.4.0- (2020-03-09)">7.4.0 (2020-03-09)</span>

**新增**

- [消息单向删除](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息单向删除)
- [撤回消息支持配置撤回通知是否算未读](/docs/TM5MzM5Njk/Tg1MDU1OTE#消息撤回)
- [清空本地会话消息支持配置是否记录此次清除操作](/docs/TM5MzM5Njk/Tg1MDU1OTE#本地会话消息清除)
- [拉取云端消息支持配置是否忽略清除记录](/docs/TM5MzM5Njk/Tg1MDU1OTE#可配置是否入库被清除消息)

**变更**

- 提升强推的优先级，免打扰对强推无效
- 对于离线情况下被推送过的消息，在线时不会触发消息提醒通知栏

**修复**

- 修复按会话合并通知栏时，只有第一栏有单击事件的问题

## <span id="7.2.0- (2020-01-13)">7.2.0 (2020-01-13)</span>

**新增**

- 超大群增加功能
- 通过关键字搜索云端消息
- 本地反查群 ID、用户账号
- 单向撤回
- 按类型获取云端历史消息支持入库
- 推送版本升级
- 通知栏支持按会话合并

**变更**

- 用户拉取云端消息时，被本地删除或者清除的消息会被过滤掉

**修复**

- 修复阿拉伯语下，未读数更新异常的问题
- 修复 observeMemberRemove 回调多次的问题

## <span id="7.0.3- (2019-12-04)">7.0.3 (2019-12-04)</span>

**新增**

- 新增 nos token 过期自动更新逻辑
- 优化通知栏昵称显示

## <span id="7.0.0] - (2019-11-13)">7.0.0 (2019-11-13)</span>

**新增**

- 不显示推送详情时，可自定义离线推送的文案
- 暴露消息的服务端 ID
- 会话列表获取服务
- 插入本地消息支持设置发送方
- 本地历史消息自定义消息字段支持搜索

## <span id="6.9.1] - (2019-09-24)">6.9.1 (2019-09-24)</span>

**新增**

- SDK 适配 Android Q

**变更**

- 升级 FCM 推送版本

## <span id="6.9.0] - (2019-09-17)">6.9.0 (2019-09-17)</span>

**新增**

- 改用 AndroidX 支持库。升级 Target API 到 28，不再支持 support 库
- 超大群优化
- 握手协议升级替换
- IM 日志上报。在 408，415，500 时记录。
- 批量获取音视频通话信息
- 支持会话新增少量获取会话
- NOS 文件优化
- 拉日志支持独立聊天室模式
- 内置通知栏提醒响铃及振动
10. 聊天室支持独立配置

## <span id="6.7.0] - (2019-08-01)">6.7.0 (2019-08-01)</span>

**新增**

- 未接通的音视频通话消息统一计入未读数

- 超大群 Demo 和 UIKit 适配

- 新增接口，获取每个会话的最近一条非过滤消息

- 高级群与超大群入群通知消息中，支持获取用户资料

- 客户端反垃圾词库配置，特殊支持识别检测

- oppo 推送接入

## <span id="6.6.6] - (2019-07-10)">6.6.6 (2019-07-10)</span>

**新增**

- 根据时间范围批量删除本地历史消息

## <span id="6.5.5] - (2019-06-12)">6.5.5 (2019-06-12)</span>

**新增**

- 新增超大群功能

## <span id="6.5.0] - (2019-05-24)">6.5.0 (2019-05-24)</span>

**新增**

- AOS 设置免打扰时间段，支持配置消息推送是否显示通知栏

- SDK 提供方法查询群成员是由谁邀请入群 TeamService#getMemberInvitor

**修复**

- 修复重复注册观察者

- 魅族系统权限问题

## <span id="6.3.0] - (2019-04-18)">6.3.0 (2019-04-18)</span>

**新增**

- vivo 推送支持

- 清空点对点历史消息 MsgService#clearServerHistory

- 删除好友同时删除备注信息 FriendService#deleteFriend

- UI 唤醒添加开关

**修复**

- 推送通知栏跳转报错，无法跳转到 app

**变更**

- Demo 下线波特机器人

## <span id="6.2.0] - (2019-03-13)">6.2.0 (2019-03-14)</span>

**新增**

- 音视频话单消息携带发起呼叫的扩展字段 AVChatAttachment#getExtendMessage

- 增加群成员信息同步完成通知 AuthServiceObserver#observeLoginSyncTeamMembersCompleteResult

- 音视频话单消息支持漫游及历史

**修复**

- 音视频话单消息状态统一

- 删除会话后，被移出群，或者群被解散，收到群组通知，重构该会话并通知

## <span id="6.1.1] - (2019-01-29)">6.1.1 (2019-01-29)</span>

**修复**

- 小米手机 App 内推送有时不展示的问题

## <span id="6.1.0] - (2019-01-22)">6.1.0 (2019-01-22)</span>

**新增**

- **支持本地消息牵移**：MsgService#exportAllMessage、MsgService#importAllMessage

- **支持带文件附件类型消息取消发送**：MsgService#cancelUploadAttachment

- **撤回消息通知区分漫游与同步**：RevokeMsgNotification#getNotificationType

- **撤回消息读取服务端设置的 msg 字段**：RevokeMsgNotification#getCustomInfo

- **拉人入群支持设置邀请附言和自定义扩展字段***：TeamService#addMembersEx

**修复**

- App 推送通知栏撤回消息 bug

- 更正 App 推送免打扰通知 channel 的设置

- 修复短时间内收到大量 App 内通知的 bug

## <span id="5.9.0] - (2018-11-28)">5.9.0 (2018-11-28)</span>

**新增**

- 创建群时指定人数上限：TeamFieldEnum#MaxMemberCount

- 指定消息撤回时是否要 App 内的推送通知：NIMClient#toggleRevokeMessageNotification

- 指定消息撤回时是否要三方推送：MsgService#revokeMessageEx

- 音视频信令系统

**变更**

- 音视频通话的话单通知时间放到通话结束时

## <span id="5.7.0] - (2018-10-11)">5.7.0 (2018-10-11)</span>

**新增**

- 不发消息，创建一个会话项：MsgService#createEmptyRecentContact

- 查询单个会话：MsgService#queryRecentContact

- 文件上传默认支持秒传

- 聊天室批量更新元素：ChatRoomService#batchUpdateQueue

- 登录增加自定义字段：SDKOptions#loginCustomTag

- 更新 NosTokenSceneConfig 配置：NIMClient#updateTokenSceneConfig()

**修复**

- 在 8.0 及以上的系统，StatusBarNotificationConfig ring/vibrate 不起作用

- 不活跃聊天室重复登录收不到消息

## <span id="5.6.1] - 2018-09-13">5.6.1 (2018-09-13)</span>

**变更**

- 修复群组成员数量不对的问题

- 删除 uikit 中的 avchat jar 包

- 删除 sdk 清单文件中关于第三方推送的配置

- 修复反垃圾词典校验时空指针的异常

- 兼容 IMMessage fromAccount 为空的场景

- 修复 VideoAction 序列化问题

## <span id="5.5.0] - 2018-08-7">5.5.0 (2018-08-07)</span>

**新增**

- NOS 场景配置

- 发送消息时可以指定 NOS 场景

- 上传文件时可以指定 NOS 场景

## <span id="5.3.0] - 2018-06-26">5.3.0 (2018-06-26)</span>

**新增**

- 好友信息设置添加仅供服务器设置的扩展字段

## <span id="5.1.1] - 2018-05-21">5.1.1 (2018-05-21)</span>

**变更**

- 解决在独立使用 basesdk.jar 不依赖 push.jar 时，登录返回 500 的问题。

## <span id="5.1.0] - 2018-05-17">5.1.0 (2018-05-17)</span>

**新增**

- 华为推送升级到 2.6.0 版本，小米推送升级到 3.6.2 版本。

- 端内推送支持撤回消息时未读数减一，配置接口：SDKOptions#shouldConsiderRevokedMessageUnreadCount

- 发送消息时可以配置是否离线：配置接口：CustomMessageConfig#enablePersist

- 从服务器拉取消息历史记录，可以指定查询的消息类型：MsgService#pullMessageHistoryExType

- 第三方推送模块独立，输出 push.jar，开发者按需使用

## <span id="5.0.0] - 2018-03-29">5.0.0 (2018-03-29)</span>

**新增**

- 添加群组已读功能，新增接口:
 - TeamService#sendTeamMessageReceipt: (消息接收方)发送群消息已读回执
 - TeamService#refreshTeamMessageReceipt: (消息发送方)刷新群消息已读未读数量
 - TeamService#fetchTeamMessageReceiptDetail: (消息发送方)获取群消息已读未读账号列表
 - MsgServiceObserve#observeTeamMessageReceipt: (消息发送方)监听群消息已读未读数量变更
 - IMMessage#setMsgAck: (消息发送方)构造需要已读回执的消息

- 群组整体禁言: TeamService#muteAllTeamMember。

- 添加客户端反垃圾功能：MsgService#checkLocalAntiSpam。

- 添加日志导出接口: MiscService#zipLogs。

- 添加客户端删除缓存接口:
- MiscService#getSizeOfDirCache : 获取缓存大小
- MiscService#clearDirCache : 删除缓存

- 添加聊天室高优先级消息判断接口：ChatRoomMessage#isHighPriorityMessage。

- 添加在任意位置初始化 SDK 的接口:
- NIMClient#config, 在 Application#onCreate()中配置 SDK（仅仅是配置，不影响性能）
- NIMClient#initSDK, 在 UI 进程主线程上按需使用的初始化 SDK

- 匿名推送功能: MixPushService#setPushShowNoDetail。

## <span id="4.8.0] - 2018-02-08">4.8.0 (2018-02-08)</span>

**新增**

- 对于已经接了易盾的应用，支持配置某条消息是否过易盾反垃圾。

- 新增批量导入最近会话接口。

**变更**

- 修复下载图片、视频等拼接 url 参数的问题。

- 升级小米推送 SDK 至 3.6.0，升级华为推送 SDK 至 2.5.3.302。

- 修复其他已知问题。

## <span id="4.6.0] - 2018-01-04">4.6.0 (2018-01-04)</span>

**新增**

- 易盾反垃圾支持对单条消息配置对应的反垃圾业务规则。

- 新增支持海外推送 FCM 以及魅族推送。

- 支持配置聊天室队列管理权限。

- 支持群管理员撤销其他人消息。

- 支持视频消息获取远程缩略图 url。

- 聊天室历史记录拉取可按类型筛选。

**变更**

- 修复酷派偶现崩溃问题。

- 接口变更：

    ```Java
    List<NimRobotInfo> getRobotInfo(List<String> accounts);
    ```

    改为

    ```Java
    List<NimRobotInfo> getRobotInfoList(List<String> accounts);
    ```

- `MessageNotifierCustomization` 新增消息撤回通知文案自定义接口：

    ```Java
    /**
    * 定制消息撤回提醒文案
    * @param revokeAccount 撤回操作者账号
    * @param item 被撤回的消息
    * @return
    */
    String makeRevokeMsgTip(String revokeAccount, IMMessage item);
    ```

- `ChatRoomPartClearAttachment` 附件内容变更

- `getContentMap()` 返回由 `Map<String,Object>` 变为 `Map<String, String>`

- `getChatRoomQueueChangeType()` 返回 `ChatRoomQueueChangeType.PARTCLEAR`

## <span id="4.4.0] - 2017-11-16">4.4.0 (2017-11-16)</span>

**新增**

- 添加聊天室用户异常掉线或主动退出的时候自动清除队列：ChatRoomService#updateQueueEx。影响类和接口：

- 添加通知类型：NotificationType#CHATROOM_QUEUE_BATCH_CHANGE，表示队列批量变更。
- 添加附件类型：ChatRoomPartClearAttachment，包含清除队列的内容。

- NOS 资源下载添加 CDN 支持，添加两种可配置模板，见 SDKOptions#ServerAddress#nosAccess。

- 适配 Android O 版本通知栏，增加网易云信即时消息通道、消息免打扰通道，解决 target 指向 26 通知栏无法弹出的问题。

- 适配 Android O 版本后台运行机制，开发者请务必在清单文件里面配置:

    ```XML
        <service android:name="com.netease.nimlib.service.ResponseService" />
    ```

- 适配 Android O+ 版本，解决 target 指向 27 InvalidKeySpecException 导致的 SDK 无法登录的问题。

- 添加新的 IPC 数据共享机制，替换不安全的多进程读写 SharedPreference，开发者请务必在清单文件里配置:

    ```XML
        <provider
            android:name="com.netease.nimlib.ipc.NIMContentProvider"
            android:authorities="{App 包名}.ipc.provider"
            android:exported="false"
            android:process=":core" />
    ```

- 添加 SDKOptions#asyncInitSDK 支持异步 SDK 初始化，降低 Application#onCreate 中 SDK 初始化函数的同步响应时间。

- 添加 SDKOptions#reducedIM 支持弱 IM 场景。如果您的 App 仅在部分场景按需使用 IM 能力(不需要在应用启动时就做自动登录)，并不需要保证消息通知、数据的实时性，那么这里可以填 true。弱 IM 场景下，push 进程采用懒启动策略(延迟到用户登录阶段)，启动后其生命周期将跟随 UI 进程，降低弱 IM 场景的 App 的后台功耗开销。

- 添加 SDKOptions.checkManifestConfig，自动检查 SDK 配置是否完全，如果不完全将抛出异常提示。强烈建议开发者在开发阶段开启检查，检查通过后，线上环境关闭。

- API 调用框架增强：
    - 支持带 Looper 的非 UI 线程发起的异步 API 调用，直接回调到调用者线程。老版本会默认回调到 UI 线程。
    - 提供异步强制转成同步的接口：NIMClient#syncRequest,允许设置最大同步等待时间，支持非 UI 线程里需要同步调用网易云信 API 的场景。
    - 添加自动生成的 NIMSDK 类，您可以直接采用 NIMSDK#getXXXService 方法获取服务接口，不再需要传递 XXXService.class，简化 API 调用方式。其他插件自动生成的调用入口类为：NIMChatRoomSDK、NIMLuceneSDK。例如采用 `NIMSDK.getAuthService().login()` 替换 `NIMClient.getService(AuthService.class).login()`。

- 添加 NIMClient#getSDKVersion 接口，运行时获取当前集成的 SDK 版本号。

**变更**

- 类变更：com.netease.nimlib.sdk.uinfo.UserInfoProvider#UserInfo 包名变更为 com.netease.nimlib.sdk.uinfo.model.UserInfo，开发者升级到此版本时，请统一修改 UserInfo import 的包名。

- 类成员函数变更：UserInfoProvider 移除 getDefaultIconResId、getAvatarForMessageNotifier、getTeamIcon 三个函数，统一替换为新增的函数，根据会话类型、会话 ID 返回消息提醒需要的头像位图：getAvatarForMessageNotifier(sessionType, sessionId)，请参考最新 Demo 源码中 NimUserInfoProvider 类中提供的替换方案。

- 添加 NIMUitl#isMainProcess 接口，保证 SDK 初始化及 App 初始化进程判断方式统一，请开发者替换 Application#onCreate 中主进程判断方法为此方法。

- 移除 SDKOptions#enableSDKBackgroundReconnectStrategy 后台自动重连开关，请采用弱 IM 模式替换。

- 修复 Push 进程自动登录被踢出后，部分机器进程被系统反复调度重启时依然发起连接的问题。

- 针对 SDKOptions#sdkStorageRootPath 配置的外置存储缓存根目录，如果开发者配置在 Context#getExternalCacheDir 及 Context#getExternalFilesDir 等应用扩展存储缓存目录下（即/sdcard/Android/data/{package}），SDK 内部将不再检查写权限。值得注意的是，改缓存目录下的的文件会随着 App 卸载而被删除，也可以由用户手动在设置界面里面清除。

- 优化唤醒策略，减少不必要的唤醒。优化 Push 进程无法唤醒 UI 时将采用的 **自杀机制**，先切断所有唤醒路径后再安全退出。

- 修复匿名聊天室断网重连过程中如果出现回调 1001 的错误码时(SDK 无法通过回调获取聊天室 IP)时，SDK 无法继续重连的问题。

- 修复聊天室调用 ChatRoomSerivce#updateMyRoomRole 后，在断网重连过程中，丢失角色信息更新的问题。

## <span id="4.3.0] - 2017-10-12">4.3.0 (2017-10-12)</span>

**新增**

- 添加聊天室独立登录模式：EnterChatRoomData#setIndependentMode。

- 添加批量清空所有会话未读数接口：MsgService#clearAllUnreadCount。

- 添加支持多类型的本地消息历史搜索接口：MsgService#queryMessageListByTypes。

- 添加大群清理逻辑。

- 添加全员广播消息，通过注册观察者接口接收广播消息：MsgServiceObserve#observeBroadcastMessage。

- 群消息支持 **只接收管理员消息提醒** 的免打扰选项。影响类和接口：

- 添加枚举类型：TeamMessageNotifyTypeEnum，用于表示群消息提醒类型，包含全部提醒、仅管理员提醒、全部不提醒。
- 变更接口：TeamService#muteTeam，参数类型从 boolean 更改为 TeamMessageNotifyTypeEnum。
- 添加方法：Team#getMessageNotifyType，此外 Team#mute 方法废弃。

- 添加动图缩略图下载选项：SDKOptions#animatedImageThumbnailEnabled，支持下载原图或者第一帧图像(默认)。

- 添加聊天室获取机器人列表接口：ChatRoomService#pullAllRobots。

- 添加后台自动断网重连策略可选开关 SDKOptions#enableSDKBackgroundReconnectStrategy。

## <span id="4.2.0] - 2017-09-12">4.2.0 (2017-09-12)</span>

**新增**

- 添加聊天室 bot 机器人功能，添加机器人上行消息构建接口：ChatRoomMessageBuilder#createRobotMessage。

- 登录选项添加群通知消息是否计入未读数开关：SDKOptions#teamNotificationMessageMarkUnread。

**变更**

- 对单个用户所在群的数量添加限制，影响到接口：

- TeamService#createTeam，返回结果 CreateTeamResult，包含邀请失败账号列表
- TeamService#addMembers，返回结果 List<String>，即邀请失败账号列表

如果邀请成员中有群数量超过限制，返回码仍然是成功，并且同时返回这部分超限的账号。

- 解决登录偶现登录 417 问题。

- 添加登录同步失败情况处理。

- 添加 IPC ACK 机制，解决极端情况下群消息丢失的问题。

- 解决 HttpDownload 安全警告问题。

## <span id="4.1.0] - 2017-08-08">4.1.0 (2017-08-08)</span>

**新增**

- SDK 发送群自定义通知支持离线。

- 多端登录客户端类型 ClientType 添加 Mac 端。

**变更**

- SDK 后台运行机制调整，避免由于系统后台限制导致 push 进程消息队列无法消化引发的各种问题，减少不必要的系统资源开销。

- 针对系统 Binder 状态异常导致 IPC 无法建立的问题，添加重置机制。

- 华为推送添加通知栏清理回调接口 MixPushMessageHandler#cleanHuaWeiNotifications，您可自行决定通知栏的清除行为。

- SDK 唤醒方式调整以适配即将发布的 Android O 版本，强烈建议开发者在清单配置文件中加上 <ResponseService> 项，具体配置信息请参考开发者文档。

- NOS https 上传资源过程中如果发生证书认证失败，将切换成默认域名进行上传。

- SDK 切换 LBS Link 地址时机调整，当从未登录成功时，采用前台策略。

## <span id="4.0.0] - 2017-07-06">4.0.0 (2017-07-06)</span>

**新增**

- 接入华为推送服务。

- 接入网易 `Bot`（智能机器人）功能，增加 `RobotService`、`RobotServiceObserve` 接口。

- 新增聊天室发消息是否存历史记录的开关，发送聊天室消息时可以选择是否存入历史记录。

- 聊天室连麦队列变更后数据同步。

**变更**

- 被叫语音、视频通话未接听计入未读数。

- 修复接收聊天室 tip 消息获取 content 为空的问题。

## <span id="3.9.0] - 2017-06-23">3.9.0 (2017-06-23)</span>

**变更**

- 添加 NOS 请求频率控制。

- 断网重连策略调整，修复 App 长时间在后台网络受限，回到前台无法立即重连的问题。

## <span id="3.8.0] - 2017-06-06">3.8.0 (2017-06-06)</span>

**新增**

- 聊天室针对固定成员，支持 nick, avatar 和 extension 字段的持久化。

**变更**

- 针对 oppo 手机 IPC 异常问题添加容错处理。

- 修复全文检索偶现的 InternalError 问题。

- 针对解包出错的极端情况添加容错处理。

## <span id="3.6.0] - 2017-04-27">3.6.0 (2017-04-27)</span>

**新增**

- 事件订阅服务：EventSubscribeService，提供如下接口：

- publishEvent 发布事件
- subscribeEvent 订阅指定账号、指定类型的事件
- unSubscribeEvent 取消指定账号、指定事件类型的订阅关系
- batchUnSubscribeEvent 取消指定事件类型的全部的订阅关系
- querySubscribeEvent 查询指定指定账号、指定类型的订阅关系

- 事件订阅监听：EventSubscribeServiceObserver，提供接口 observeEventChanged 监听事件变化

- IM Demo 实现在线状态展示。

- 支持设置消息提醒通知栏 smallIcon 背景颜色，StatusBarNotificationConfig#notificationColor。

- 本地消息清空后，别人再撤回消息，可收到消息撤回的通知

**变更**

- 小米推送升级 3.2.2 版本，解决部分小米手机升级到 Android 7.0 之后初始化推送崩溃、收不到推送的问题。

- IM Demo 更换通知栏透明 smallIcon。

## <span id="3.5.0] - 2017-03-15">3.5.0 (2017-03-15)</span>

**新增**

- 聊天室历史记录拉取接口: pullMessageHistoryEx，支持查询方向按时间点向前或者向后。

**变更**

- AudioRecorder 高清语音录音组件异步化，使用子线程开始、结束录音，UIKit 同时修改适配。

- 通知栏样式变更：
- 展开样式的通知栏单击跳转更改为进入对应联系人的聊天界面
- 折叠样式的通知栏在多联系人时将应用 icon 设置为通知栏大图

- SDK 心跳机制优化，缩短弱网环境下连接失效时上层的感知时间。

- LBS 机制优化，避免应用在后台受到网络限制时耗尽可用的 Link 地址。

## <span id="3.4.0] - 2017-01-20">3.4.0 (2017-01-20)</span>

**变更**

- 文件断点续传优化。

- 修复文件下载过程中调用 cancel 接口后无状态回调的问题。

- 登录优化，解决特殊场景下出现的服务异常的情况。

- SDKOptions 添加是否提高 SDK 进程优先级可选项，用户可根据例外机型或例外系统版本停用此进程保护方式。

- SDK 内部 http 地址替换为 https 地址。

## <span id="3.3.0] - 2016-12-28">3.3.0 (2016-12-28)</span>

**新增**

- UIKit 优化，降低接入复杂度。

- UIKit 基于强推消息实现群组 @ 功能。

- 进入聊天室接口支持可配置重试次数：ChatRoomService#enterChatRoomEx。

- 添加消息通知栏展示样式配置（折叠或者展开）：StatusBarNotificationConfig#notificationFolded。默认是折叠，即网易云信消息端内消息提醒最多之占一栏。也可以设置为展开，达到端内、端外通知栏提醒一致的表现。

- 聊天室通知消息中加入新的附件类型：ChatRoomTempMuteAddAttachment 可获取临时禁言时长，ChatRoomTempMuteRemoveAttachment 可获取解禁提前的时长，ChatRoomRoomMemberInAttachment 可获取进入聊天室的用户是否被禁言，是否被临时禁言以及临时禁言时长。

- 添加文档转码：
- 文档分页查询, DocumentManager#queryDocumentDataList
- 单个文档查询, DocumentManager#querySingleDocumentData
- 单个文档删除, DocumentManager#delete

**变更**

- SDK IPC 唤醒方式修改。

- SDK HTTP 网络库更新。

- NOS 资源传输支持 HTTPS。

- NOS 上传优化，修复文件传输过程中出现断网，偶现重连后无法继续上传的问题。

- 聊天室断网重连机制优化。

- SDK 初始化异常问题优化。

- SDK 网络层偶现的空指针问题修复。

- SDK 多线程问题优化。

- 手动登录返回 408,415 时进行网络检测并输出到日志。

- SDK 收到新消息后不再发送 Action 为 ACTION_RECEIVE_MSG 的广播通知。若开发者依赖此广播实现接收消息，在升级 SDK 请改为使用 Observer 监听的方式接收消息。

## <span id="3.2.0] - 2016-11-30">3.2.0 (2016-11-30)</span>

**新增**

- 添加第三方推送服务：NIMPushClient,MixPushService，目前已接入小米推送。

- 添加会话未读数多端同步功能，开关为 SDKOptions#sessionReadAck，默认关闭。

- 添加第三方推送免打扰设置：MixPushService#setPushNoDisturbConfig。

- 添加本地消息拉取扩展接口：MsgService#queryMessageListExTime，支持时间和条数共同限定结果集。

**变更**

- 最低支持版本变更为 Android 4.0 (Ice Cream Sandwich)，其中音视频通话最低支持版本为 Android 4.4 (KitKat)。

- 登录优化。

- 消息撤回优化，针对离线时对方发送消息并撤回的场景，下次登录时会收到 MsgServiceObserve#observeRevokeMessage 通知，可以获得被撤回消息的时间，便于在 UI 上展现离线期间消息撤回的提示。

## <span id="3.1.0] - 2016-10-26">3.1.0 (2016-10-26)</span>

**新增**

- 添加发送消息时的反垃圾配置 IMMessage#setNIMAntiSpamOption。

- 添加查询被禁言群成员列表接口 TeamService#queryMutedTeamMembers。

- 添加群全员禁言通知。

- 添加聊天室全员禁言通知。

- 文件传输添加动态分块策略。

**变更**

- SDK 网络库精简及优化。

- 修正部分手机 UI 进程被 Kill , push 进程无法感知导致下次 UI 重启时没有同步在线状态的问题。

- 修正联想某型号手机退后台长时间后回到前台无法重连成功的问题。

- 修正 MsgService#saveMessageToLocalEx 接口发送第一条消息，最近联系人列表收不到通知的问题。

- MsgService#queryMessageListByUuidBlock 接口支持 sending 状态的返回。

- 引入 JobScheduler, Android 5.0+ 能起到一定的保活效果。修改提高 push 进程优先级保活方案的适用版本。

## <span id="3.0.0] - 2016-10-20">3.0.0 (2016-10-20)</span>

**变更**

- 修改多端登录获取登录时间为空的问题。

## <span id="2.9.0] - 2016-09-19">2.9.0 (2016-09-19)</span>

**新增**

- 添加聊天室成员是否被临时禁言和临时禁言解除时长字段：ChatRoomMember#isTempMuted, ChatRoomMember#getTempMuteDuration。

**变更**

- 聊天室断线重连时间优化。

- 聊天室发包频控优化。

- MsgService#saveMessageToLocal(IMMessage, boolean, long) 改名为 MsgService#saveMessageToLocalEx(IMMessage, boolean, long)。

## <span id="2.8.0] - 2016-08-30">2.8.0 (2016-08-30)</span>

**新增**

- 添加消息撤回功能：MsgService#revokeMessage, MsgServiceObserve#observeRevokeMessage。

- 添加删除指定会话的漫游消息接口：MsgService#deleteRoamingRecentContact。

- 新增保存消息到本地接口：MsgService#saveMessageToLocal 可以设置消息存储的时间点。

- 消息中添加获取消息发送方类型接口：IMMessage#getFromClientType。

**变更**

- 精简全文检索插件包大小。

- 清空会话本地消息记录 MsgService#clearChattingHistory 接口保留 RecentContact 中的 tag, extension, time 属性。

## <span id="2.7.0] - 2016-08-11">2.7.0 (2016-08-11)</span>

**新增**

- 添加全文检索插件，目前支持消息全文检索及高亮，支持分页查询，接口为 LuceneService。此外，MsgService 中也提供基于 SQL Like 方式的实现。

- 添加 SDK 发包频控控制。

- 添加聊天室队列服务（针对直播连麦场景使用）。

- 添加指定成员强制推送功能（主要针对群）：IMMessage#memberPushOption。

- 添加 PC/Web 端在线时可配置是否推送的开关 SettingService。

- 添加获取群邀请和群踢人通知附件的扩展字段：MemberChangeAttachment#getExtension。

- 添加更新聊天室信息接口 ChatRoomService#updateRoomInfo，更新本人聊天室成员信息接口 ChatRoomService#updateMyRoomRole。

- 添加登录时同步本人所在的所有群的本人群成员资料信息。

- 优化 SDK 登录同步流程。

## <span id="2.5.0] - 2016-07-08">2.5.0 (2016-07-08)</span>

**新增**

- 添加文本消息的全局搜索接口：MsgService#searchAllMessageHistory。

- 添加消息转发功能：MessageBuilder#createForwardMessage，支持除通知消息和音视频消息以外的消息类型。

- 添加聊天室临时禁言接口：ChatRoomService#markChatRoomTempMute，支持设置临时禁言时长。

**变更**

- 将注册群通知消息过滤接口移动到 MsgService 中：MsgService#registerIMMessageFilter，并支持单聊和群聊的通知类型消息过滤，不再限于群通知消息，同时支持音视频类型消息过滤。

- 聊天室架构调整，聊天室业务仅在 UI 进程处理。

- SDK 输出 jar 包按模块分离：nim-sdk.jar（必须）、nim-chatroom.jar（可选聊天室模块）、nim-rts.jar（可选实时会话白板模块）、nim-avchat.jar（可选实时音视频模块）、nrtc-sdk.jar（实时会话、实时音视频基础库），供开发者按需组合使用。

## <span id="2.4.0] - 2016-06-02">2.4.0 (2016-06-02)</span>

**新增**

- 升级群组功能：添加群邀请模式、被邀请模式、群资料修改模式、群资料扩展字段修改模式、群头像、群成员是否被禁言、群成员扩展字段等属性。

- 添加群禁言功能 TeamService#muteTeamMember，禁言后，群成员都会收到一条通知类消息，附件为 MuteMemberAttachment。

- 添加修改自己的群成员扩展字段接口 TeamService#updateMyMemberExtension。

- 添加发送消息配置项：消息是否支持路由（抄送） CustomMessageConfig#enableRoute。

- 添加群通知消息过滤接口：MsgService#registerTeamNotificationFilter，支持由上层决定群通知消息是否需要持久化。

- 添加漫游消息通知接收消息监听接口。

- 通知栏提醒支持呼吸灯配置：StatusBarNotificationConfig#ledARGB、StatusBarNotificationConfig#ledOnMs、StatusBarNotificationConfig#ledOffMs。

- 添加静音列表变更通知：FriendServiceObserve#observeMuteListChangedNotify。

**变更**

- 优化网络心跳唤醒方式。

- 提高网易云信服务进程系统优先级，降低被系统杀死的概率。

- 适配 Android M+ 外部存储读写权限开启后，日志写入无法立即生效的问题。

- UserService#fetchUserInfo 添加单次请求账号数量上限 150，超过 150 需要上层做分批请求，否则抛出 IllegalArgumentException。

- MsgService#searchMessageHistory 接口去掉文本消息类型限制，参照 content 字段进行关键字匹配。

- 完善 AuthService#openLocalCache 接口逻辑。

## <span id="2.3.0] - 2016-05-18">2.3.0 (2016-05-18)</span>

**变更**

- 修正日志超过 8M 未裁剪的问题。

- 修正 SDK 初始化过程中部分机型偶现空指针的问题。

## <span id="2.2.0] - 2016-04-28">2.2.0 (2016-04-28)</span>

**新增**

- LoginInfo 中添加可选属性 AppKey，支持在登录时设置 AppKey。

- 消息中添加获取发送者昵称接口：IMMessage#getFromNick。

- 进入聊天室前，如果 IM 未成功登录，将上报错误码 1000。

- 群组添加批量移除群成员接口：TeamService#removeMembers。

- 扩展字段支持 Map、List、JsonObject、JsonArray 的嵌套。在解析扩展字段时，如果 JSON 解析成 Map 失败将原字符串返回（放入返回的 Map 中，key 为 ext）。

- 添加获取 SDK 数据缓存目录接口：NimClient#getSdkStorageDirPath。

- 聊天室断线重连机制优化。

- 聊天室添加获取断线重连（自动登录）失败的错误码接口：ChatRoomService#getEnterErrorCode。

## <span id="2.1.2] - 2016-04-06">2.1.2 (2016-04-06)</span>

**新增**

- 进入聊天室时支持设置通知的扩展字段 notifyExtension，设置后，在收到聊天室通知消息时，通过 ChatRoomNotificationAttachment 获取此扩展字段。

## <span id="2.1.1] - 2016-03-28">2.1.1 (2016-03-28)</span>

**新增**

- 聊天室 ChatRoomMessageBuilder 支持更丰富的消息类型。

- 进入不存在的聊天室返回错误码 404。

## <span id="2.1.0] - 2016-03-24">2.1.0 (2016-03-24)</span>

**新增**

- MsgService 添加已读回执功能。

- 添加 RTSNotifyOption、AVChatNotifyOption，可自定义音视频、白板的 iOS 推送通知。

**变更**

- 创建 Tip 消息接口变更：MessageBuilder#createTipMessage 去掉最后一个参数 Map<String, Object> content，早期版本请根据该接口返回的 IMMessage 对象来 setRemoteExtension。

- RTSOptions 去掉 pushContent、extra 字段，新版本使用 RTSNotifyOption。

- 优化 App 从后台切到前台时断网重连机制。

- 修复部分系统偶现后台进程活着但 UI 进程收不到消息提醒的问题。

## <span id="2.0.1] - 2016-02-29">2.0.1 (2016-02-29)</span>

**变更**

- RTSManager 去掉铃声配置接口，铃声交由上层自定义实现。

- MsgService#updateRecent 接口改成同步接口。

## <span id="2.0.0] - 2016-02-22">2.0.0 (2016-02-22)</span>

**新增**

- 添加聊天室功能 SDK：ChatRoomService。

- 去掉 libs 下 netty-4.0.23-for-yx.final.jar。

## <span id="1.8.0] - 2016-01-18">1.8.0 (2016-01-18)</span>

**新增**

- RecentContact 类添加扩展字段（本地使用）。

- SDKOption 类添加消息提醒（通知栏提醒）内容定制接口：MessageNotifierCustomization。

- 添加未登录时访问 SDK 本地数据接口：AuthService.openLocalCache。

- IMMessage 和 CustomNotification 的扩展字段支持嵌套。

- 添加更新本地扩展字段接口：MsgService.updateIMMessage。

- 保存消息到本地接口：MsgService.saveMessageToLocal 支持设置是否计入最近联系人未读计数。

**变更**

- 断网后立即上报状态（去掉延时上报机制），上层感知到的网络状态变更更加灵敏供开发者自由发挥。

## <span id="1.7.1] - 2015-12-05">1.7.1 (2015-12-05)</span>

**变更**

- 修复断网时登录无响应的问题（影响版本 1.6.0 及 1.7.0）。

- 修复被拉进群后，收到第一条群消息时，通知栏无法显示昵称的问题。

- UserService.getUserInfo(List<String> accounts) 接口名称更改为 UserService.getUserInfoList(List<String> accounts)。

## <span id="1.7.0] - 2015-12-01">1.7.0 (2015-12-01)</span>

**新增**

- IMMessage 类添加扩展字段（服务器扩展字段和本地扩展字段）。

- IMMessage 类添加推送文案、自定义推送属性。

- IMMessage 类添加消息配置选项，发送消息时可以指定该消息是否计入未读数。

- IMMessage 类添加消息配置选项，发送消息时可以指定该消息是否需要推送（消息提醒）。

- IMMessage 类添加消息配置选项，发送消息时可以指定该消息是否推送昵称（接收方针对 iOS 有效）。

- CustomNotification 类添加通知配置选项，发送通知时可以指定该通知是否需要推送（消息提醒）。

- CustomNotification 类添加通知配置选项，发送通知时可以指定该通知是否推送昵称（接收方针对 iOS 有效）。

- CustomNotification 类添加通知配置选项，发送通知时可以指定该通知是否计入未读数。

- CustomNotification 类添加自定义推送属性。

- 添加通过消息 ID 批量获取 IMMessage 接口：MsgService.queryMessageListByUuidBlock 和 MsgService.queryMessageListByUuid。

- 添加通过消息类型查询消息历史接口：MsgService.queryMessageListByType。

- 添加更新好友备注名、好友关系扩展字段接口：FriendService.updateFriendFields。Friend 类添加获取好友备注名、好友关系扩展字段方法。

- 添加根据类型查询系统通知列表接口：SystemMessageService.querySystemMessageByType。

- 添加查询指定类型的系统通知未读数总和接口：SystemMessageService.querySystemMessageUnreadCountByType。

- 添加将指定类型的系统通知设为已读接口：SystemMessageService.resetSystemMessageUnreadCountByType。

- 添加清空指定类型的系统通知接口：SystemMessageService.clearSystemMessagesByType。

- AudioRecorder 类添加获取当前录音时最大振幅接口：AudioRecorder.getCurrentRecordMaxAmplitude。

- UserInfoProvider 类添加自定义通知栏消息提醒发送者显示名称接口：UserInfoProvider.getDisplayNameForMessageNotifier。

- 添加新的消息类型 Tip：MessageBuilder.createTipMessage，主要用于会话内的通知提醒的场景。

- TeamMember 类添加判断该成员是否有效（是否还在群中）的接口：TeamMember.isInTeam，当群成员退出或被移除后，SDK 通知群成员变化时会将 isInTeam 置为 false。

**变更**

- SystemMessageType 去掉 DeleteFriend，由 SDK 内部处理好友删除，该系统通知不再上报。

- 修复群成员退出或者被移除后 TeamServiceObserver.observeMemberRemove 监听没有回调的问题。

## <span id="1.6.0] - 2015-11-02">1.6.0 (2015-11-02)</span>

**新增**

- 添加查询系统通知列表（同步版本）接口：SystemMessageService.querySystemMessagesBlock。

- 添加登录同步数据状态通知接口：AuthServiceObserver.observeLoginSyncDataStatus。

- 添加查询未读消息总数接口：MsgService.getTotalUnreadCount。

- 添加设置单条系统消息为已读接口：SystemMessageService.setSystemMessageRead。

- AudioPlayer 支持听筒/扬声器播放。

**变更**

- 修改 FriendChangedNotify 类，在好友关系变更通知中批量返回增加、更新、被删除的的好友关系。

- 修改 BlackListChangedNotify 类，在黑名单变更通知中批量返回被拉黑、移出黑名单的帐号列表。

## <span id="1.5.0] - 2015-09-29">1.5.0 (2015-09-29)</span>

**新增**

- 用户资料托管。

- 数据通道服务，基于数据通道服务实现白板功能。

- UI 组件新增：通讯录列表、联系人选择器、群名片。

## <span id="1.4.0] - 2015-09-02">1.4.0 (2015-09-02)</span>

**新增**

- 好友系统托管。

- 黑名单设置。

- 消息提醒开关设置。

- 开源 UI 组件，集成更方便。

- SDK 调用接口回调增加 RequestCallbackWrapper 类，将 RequestCallback 的 3 个回调函数合并为 1 个，方便开发者调用。

- MsgService 增加 saveMessageToLocal 接口，用于开发者保存一些 tips 类的本地消息，同时 IMMessage 放开更多设置接口。

- MsgService 增加单独清空最近联系人未读数接口：clearUnreadCount。

- 给部分不需要网络请求的接口增加了同步调用版本，这些同步调用接口以 \*Block 结尾。

- 增加 UserInfoProvider 接口，并在 SDKOptions 中增加设置，用于网易云信内建的状态栏通知显示用户头像和自定义名字。

**变更**

- 因为架构调整，需要在 AndroidManifest 文件中增加组件申明：

    ```XML
    <!-- 网易云信进程间通信 receiver -->
    <receiver android:name="com.netease.nimlib.service.ResponseReceiver"/>
    ```

- SDK 架构调整，SDK 主要业务逻辑改为工作在 UI 进程，push 进程更轻量，占用资源更少，收到消息后就启动 UI 进程，用户打开 App 更快速。

- 收到新消息，新系统消息，新自定义通知后，UI 进程会被唤起，因此除了使用 Receiver 外，也可以直接使用 observer 接口监听。

- 网易云信 appKey 除了在 AndroidManifest 中配置外，也可以在 SDKOptions 中进行设置，并优先采用 SDKOptions 中的设置。
​
## <span id="1.3.0] - 2015-07-31">1.3.0 (2015-07-31)</span>

**新增**

- 增加搜索本地消息历史纪录的接口：MsgService.searchMessageHistory。

- 新增一个更方便使用，更灵活的批量获取本地消息历史纪录的接口: MsgService.queryMessageListEx。

- 增加语音转文字的接口：MsgService.transVoiceToText。

- 增加了一个后台保活的 jar 包，增强程序健壮性。

- 自定义消息增加生命周期和推送参数的自主配置：CustomMessageConfig。

**变更**

- 发送消息的回掉函数改为到最终发送完成时才回调了，如果发送失败，您可以清楚的知道错误码是什么。

- 修改群组资料改为可以同时修改多个字段了。

- 因为架构调整，需要在 AndroidManifest 文件中增加组件申明：

    ```XML
    <!-- 运行后台辅助服务 -->
    <service
        android:name="com.netease.nimlib.service.NimService$Aux"
        android:process=":core"/>
    ```

**bug 修复**

- 修改服务进程在后台时可能会被系统杀掉导致 UI 上自定义消息无法解析，新消息提醒设置失效的 bug。

## <span id="1.2.0] - 2015-06-23">1.2.0 (2015-06-23)</span>

**新增**

- 群组增加消息提醒开关设置。

- 有多端同时在线时，可以给其他端发送消息，可以踢其他端下线。

- 增加设置消息推送内容的接口。

**bug 修复**

- 修正多个进程调用 SDK 接口时，回调可能混乱的问题。

## <span id="1.1.0] - 2015-05-25">1.1.0 (2015-05-25)</span>

**新增**

- 支持的 android 系统版本由 2.2 升级到 2.3。

- 消息数据库去掉加密选项，去掉对 sqlcipher 的依赖。

- 整合透传指令和自定义系统通知，使接口更方便，概念更清晰。

- 增加从服务器拉取消息记录功能。

- 增加文件消息类型。

- 新消息通知栏提醒的文案改为可自定义。

- 增加语音消息播放 API (AudioPlayer)。

- 增加多端登录状态接口。

- 高级群增加两个扩展字段，可第三方应用自由定义和使用。

**变更**

- CommandMessage 和 CustomSystemNotification 统一改为 CustomNotification，对应 MsgService 的 sendCommandMessage 接口改为 sendCustomNotification，AndroidManifest 文件中 Receiver 声明的 Action 对应改为 `.ACTION.RECEIVE_CUSTOM_NOTIFICATION`。

- IMMessage 的接口精简，去掉大部分 setter 接口，去掉了用于内部使用的 getter 接口。去掉的 getter 接口包括：getMessageId (可改用 getUuid)，getServerId，getAttachStr。

- MsgAttachment 不再需要实现 formJson 接口。

- RecentContact 去掉 getSortTag 和 getSortTime 接口（以前没有实现），增加 getTag 和 setTag 接口。

- MsgTypeEnum.picture -\> MsgTypeEnum.image。

## <span id="1.0.0] - 2015-03-27">1.0.0 (2015-03-27)</span>

网易云信即时通讯 IM SDK 首版发布。

<!-- *云信发布了！* -->


::: details 单击展开 8.9.100 (2022-07-15) ~ 8.9.130 (2024-05-15) 版本 NIM SDK 的更新日志。
⭐<span style="font-size:16px;"><b><span id="8.9.130 - 2024-05-15">8.9.130 (2024-05-15)</span></b></span>

修复已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.129 - 2024-04-07">8.9.129 (2024-04-07)</span></b></span>

新增 `logout(long timeout)` 接口，在内部处理完成登出后回调登出成功的通知。

接口原型如下：

```Java
/**
 * @param timeout 登出允许的最大等待时间，单位毫秒。如 3 * 1000L
 * @return InvocationFuture 可设置回调函数，监听操作结果。
 */
public InvocationFuture<Void> logout(long timeout);
```

⭐<span style="font-size:16px;"><b><span id="8.9.128 - 2024-03-27">8.9.128 (2024-03-27)</span></b></span>

升级数据库加密套件（SQLCipher）至 4.5.4 版本。

⭐<span style="font-size:16px;"><b><span id="8.9.127 - 2024-03-20">8.9.127 (2024-03-20)</span></b></span>

**改进优化**

- 优化未登录情况下消息发送逻辑。
- 优化信令模块（呼叫功能）。
- 其他内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.126 - 2024-02-23">8.9.126 (2024-02-23)</span></b></span>

**新增特性**

支持根据 Thread 根消息查询本地 Thread 子消息。

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| `queryLocalThreadTalkHistory` | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息。 |

⭐<span style="font-size:16px;"><b><span id="8.9.125 - 2024-02-02">8.9.125 (2024-02-02)</span></b></span>

**新增特性**

新增动态查询连续完整的历史消息功能，具体请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/guide/TI3NTU1NDA?platform=android#动态查询历史消息)。

相较于频繁从云端获取，该查询方法在保证历史消息完整的同时，减少了耗时和耗能。

<!--私有化分支，未合入
- 支持在群免打扰状态下设置特别关注的群成员（包括高级群和超大群）。在开启群免打扰时，仍能收到特别关注的成员发送的消息提醒。
-->

**API 变更**

方法/类/枚举 | 说明
---- | ----
[`getMessagesDynamically`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a7e04c64027ab59d214642531141f33d4) | 动态查询连续完整的历史消息。

<!--
`TeamService#addTeamMembersFollow` | 添加高级群中需要特别关注的成员列表。
`TeamService#removeTeamMembersFollow` | 移除高级群中需要特别关注的成员列表。
`TeamMember` | 群成员属性中新增 `getfollowAccountIds` 成员函数，用于获取特别关注的群成员列表。
`SuperTeamService#addTeamMembersFollow` | 添加超大群中需要特别关注的成员列表。
`SuperTeamService#removeTeamMembersFollow` | 移除超大群中需要特别关注的成员列表。
`SuperTeamMember` | 超大群成员属性中新增 `getFollowAccountIds` 成员函数，用于获取特别关注的超大群成员列表。
-->

⭐<span style="font-size:16px;"><b><span id="8.9.124 - 2024-01-12">8.9.124 (2024-01-19)</span></b></span>

**新增特性**

- 支持按照群成员类型查询成员列表信息。（高级群和超大群）
- 支持按照关键字检索群成员。（仅超大群）

**API 新增**

| API | API 说明 |
| --- | --- |
| `TeamService.getTeamMemberList`/`SuperTeamService.getTeamMemberList` | 按照群成员类型查询成员列表信息。<br><b>API 原型：</b>`getTeamMemberList(String teamId, NIMTeamMemberRoleTypeSearchOption option);`<li>`teamId`：群组 ID<br><b>NIMTeamMemberRoleTypeSearchOption 参数说明：</b><li>`roleTypes`：[`TeamMemberType`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1constant_1_1_team_member_type.html)，群成员角色类型 <li>`offset`：查询偏移，首次传 0，下一次调用传入上一次返回的 `offset`。<li>`order`：[`SearchOrderEnum`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1model_1_1_search_order_enum.html)，查询方向，即返回结果按照 `joinTime`（进群时间）升序或降序排序。默认为时间降序。<li>`limit`：本次查询最大数量，默认为 10。 |
| `SuperTeamService.searchTeamMember` | 按照关键字检索群成员。<br><b>API 原型：</b>`searchTeamMembers(NIMTeamMemberKeywordSearchOption option);`<br><b>NIMTeamMemberKeywordSearchOption 参数说明：</b><li>`teamId`：群组 ID <li>`keyword`：查询使用的关键字 <li>`offset`：查询偏移，首次传 0，下一次调用传入上一次返回的 `offset`。<li>`order`：[`SearchOrderEnum`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1model_1_1_search_order_enum.html)，查询方向，即返回结果按照 `joinTime`（进群时间）升序或降序排序。默认为时间降序。<li>`limit`：本次查询最大数量，默认为 10。 |

⭐<span style="font-size:16px;"><b><span id="8.9.123 - 2024-01-12">8.9.123 (2024-01-12)</span></b></span>

内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.122 - 2023-12-27">8.9.122 (2023-12-27)</span></b></span>

**新增特性**

- 支持按会话类型批量清理未读数功能，具体请参考 [指定类型的会话未读数清零](https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android#将指定类型的会话的未读数清零标记已读)。
- 支持获取指定类型的会话的消息未读数，具体请参考 [获取指定类型的会话的消息未读数](https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android#获取指定类型的会话的消息未读数)。

- 支持自行填入第三方厂商的推送 token。实现步骤如下：

    1. `com.netease.nimlib.sdk.mixpush.IManualProvidePushTokenCallback` 提供了自行传入推送 token 的回调类型，需要实现方法 `Pair<MixPushTypeEnum, String> onToken(MixPushTypeEnum suggestedPushType)`。方法中提供当前设备的 **推荐推送类型**，用户可参考推荐类型，并返 **推送类型** + **token** 的键值对交由 SDK 处理。
    2. 通过调用 `com.netease.nimlib.sdk.mixpush.NIMPushClient` 的 `registerManuallyProvidePushTokenCallback` 方法注册 `IManualProvidePushTokenCallback`。

**API 新增**

| API | API 说明 |
| --- | --- |
| [`clearUnreadCount`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a9bab6e3ebb5918f3560ded979826b9b1) | 将指定类型的会话未读数清零（标记已读）。 |
| [`getUnreadCountBySessionType`](https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android#获取指定类型的会话的消息未读数) | 获取指定类型的会话的消息未读数。 |
| `com.netease.nimlib.sdk.mixpush.MixPushConfig` 类新增 `manualProvidePushToken` 配置项 | 自行传入推送 token：<li>true：开启。需要用户自行传入厂商推送 token （Demo 在 `DemoManualProvidePushTokenCallback` 中已实现）。<li>false：（默认）关闭。由 NIM SDK 获取厂商推送 token。 |
| 新增 `com.netease.nimlib.sdk.mixpush.IManualProvidePushTokenCallback` 回调 | 提供自行传入推送 token 的回调。 |

⭐<span style="font-size:16px;"><b><span id="8.9.121 - 2023-12-08">8.9.121 (2023-12-08)</span></b></span>

**新增特性**

- 支持查询指定时间段内的服务端 Thread 历史消息，具体请参考 [历史消息文档](https://doc.yunxin.163.com/messaging/guide/TI3NTU1NDA?platform=android#查询云端-thread-历史消息)。

- 为适配 vivo 推送升级，新增初始化参数，在获得用户隐私许可（agreePrivacyStatement）后才可开启并获取 vivo push token。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`queryThreadTalkHistory`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a602ebe389234f22b65d42e4aee2a26e8) | 分页查询指定时间段内的云端 Thread 历史消息（单聊、群/超大群）。 |
| `MixPushConfig` 新增 `vivoAgreePrivacyStatement` | 设置用户是否同意 vivo 推送隐私声明 agreePrivacyStatement。 |

`vivoAgreePrivacyStatement` 原型：

```Java
/**
 * 设置用户是否同意 vivo 推送隐私声明 agreePrivacyStatement：
 *   true：用户同意了隐私声明。
 *   false:未同意隐私声明，默认不同意。
 */
public boolean vivoAgreePrivacyStatement = false;
```

**改进优化**

第三方推送升级至最新版本。

**第三方推送兼容版本**

8.9.121 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.12.0.300
小米 | 5.9.9
OPPO | 3.4.0
vivo | 3.0.0.7_488
魅族 | 4.3.0
荣耀 | 7.0.61.303
FCM | <ul><li>firebase-messaging：23.2.1</li><li>firebase-analytics: 21.3.0</li></ul>

⭐<span style="font-size:16px;"><b><span id="8.9.119 - 2023-10-19">8.9.119 (2023-10-19)</span></b></span>

- 优化第三方回调动态 Token 登录内部逻辑，具体请参考 [通过第三方回调登录 IM](https://doc.yunxin.163.com/messaging/guide/TI1MTU1NDc?platform=android#通过第三方回调登录)。
- 修复数据库中群成员信息与服务端不一致的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.118 - 2023-08-29">8.9.118 (2023-08-29)</span></b></span>

- 支持配置消息提醒（本地通知消息）的类型，具体请参考 [消息提醒类型](https://doc.yunxin.163.com/messaging/guide/jU3NzgxOTk?platform=android#消息提醒类型)。
- 修复 IPV6 URL 转换错误的问题。
- 修复 NOS 文件上传失败的问题。
- Android API 最低版本升级至 21（原 19）。

⭐<span style="font-size:16px;"><b><span id="8.9.117 - 2023-07-20">8.9.117 (2023-07-20)</span></b></span>

- 支持在应用级别配置 SDK 日志打印的开关，减少 SDK 本地查询数据库的操作。
- 取消未登录状态下发送消息的超时机制，直接返回未登录错误码。
- deviceID 和 AppKey 以健值对的方案存储，传入 AppKey 即可获取 device ID。
- 修复文件下载完成后，文件状态异常的问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.116 - 2023-06-14">8.9.116 (2023-06-14)</span></b></span>

优化内部逻辑。

⭐<span style="font-size:16px;"><b><span id="8.9.115 - 2023-05-15">8.9.115 (2023-05-15)</span></b></span>

- 推送升级。
- 修复其他已知问题。

**第三方推送兼容版本**

8.9.115 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.9.0.300
小米 | 5.6.2
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.2.3
荣耀 | 7.0.41.301
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

⭐<span style="font-size:16px;"><b><span id="8.9.114 - 2023-04-27">8.9.114 (2023-04-27)</span></b></span>

- IM & 聊天室登录支持采用动态 Token 鉴权 & 动态 LoginExt 鉴权的场景。
- 解决隐私合规问题。
- 修复已登录场景下，数据库打开异常的问题。
- 修复锁屏之后 `observeOnlineStatus` 回调过于频繁的问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.113 - 2023-03-31">8.9.113 (2023-03-31)</span></b></span>

- [第三方回调登录](https://doc.yunxin.163.com/messaging/guide/TI1MTU1NDc?platform=android#通过第三方回调登录)支持第三方服务器采用动态 token 鉴权的场景。

    如果用户登录 IM 时 token 已过期，IM 服务端会重新向第三方服务器发起登录回调请求，并获取新的 token。

- 部分已知问题修复与优化。

⭐<span style="font-size:16px;"><b><span id="8.9.112 - 2023-02-17">8.9.112 (2023-02-17)</span></b></span>

- 修复会话状态更新异常。
- 修复登录超时后的重连机制异常。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.111 - 2023-01-31">8.9.111 (2023-01-31)</span></b></span>

修复数据上报完成后，在主线程中操作数据库时，可能导致卡顿或者应用程序无响应对话框
（ANR）的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.109 - 2022-12-15">8.9.109 (2022-12-15)</span></b></span>

**新增特性**
- 支持聊天室定向消息功能。[发送聊天室消息](https://doc.yunxin.163.com/messaging/guide/zY5NzQzNjU?platform=android#%E5%8F%91%E9%80%81%E5%AE%9A%E5%90%91%E6%B6%88%E6%81%AF) 支持消息接收者列表
- 适配 Android 13.0.0
- 解决隐私合规问题

**问题修复**

- 修复发送文件消息时文件上传失败但消息发送成功的问题
- 修复获取群昵称异常问题
- 修复偶现的所在高级群被提示已退出的问题
- 修复其他已知问题

**第三方推送兼容版本**

8.9.109 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.5.0.300
小米 | 5.1.0
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

⭐<span style="font-size:16px;"><b><span id="8.9.108 - 2022-11-28">8.9.108 (2022-11-28)</span></b></span>

优化 SDK 内部判断当前所在进程的逻辑。

⭐<span style="font-size:16px;"><b><span id="8.9.107 - 2022-11-08">8.9.107 (2022-11-08)</span></b></span>

**SDK 包体积增量大小对比**

架构 | 稳定版（8.9.107） | 开发版（9.6.3）
---- | ---- | ----
arm64-v8a | 9.73MB | 23.64MB
armeabi-v7a | 7.38MB | 17.66MB

**新增特性**
- 适配 Android 12.0.0
- 支持数据上报（查看实时监控数据的基础）
- 支持根据用户登录的 App Key 进行数据采集并上报
- 支持聊天室动态登录

**问题修复**

- 去除 ssid 获取
- 去除自启动和关联启动的行为
- 修复 AES 加密问题
- 去除用户未同意隐私条款前的调用逻辑
- 修复超大群消息开启免打扰失效的问题
- 修复应用启动时偶现的无法启动 NimService 问题
- 修复聊天室偶现的无法收到消息的问题
- 修复插入本地消息是否计未读数和主体未读数判断逻辑不一致的问题
- 修复 Thread 的回复消息数与实际不符的问题
- 修复偶现的日志崩溃问题
- 修复其他已知问题

**第三方推送兼容版本**

8.9.107 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.3.0.302
小米 | 4.5.0
OPPO | 3.1.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>

**已知问题**

该版本 SDK 中未包含 **全文检索插件** （`nim-lucene-x.x.x.jar`）。

⭐<span style="font-size:16px;"><b><span id="8.9.100 - 2022-07-15">8.9.100 (2022-07-15)</span></b></span>

NIM SDK 稳定版首次发布。

8.9.100 兼容的第三方推送 SDK 版本信息如下：

第三方推送 | 版本
---- | ----
华为 | 6.3.0.302
小米 | 4.5.0
OPPO | 3.0.0
VIVO | 3.0.0.4_484
魅族 | 4.1.0
FCM | firebase-bom:28.4.2，具体版本：<br><ul><li>firebase-messaging：23.0.0</li><li>firebase-analytics: 20.0.0</li></ul>
:::