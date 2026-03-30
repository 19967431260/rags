本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）LTS 版 Web/uni-app/小程序/RN 端 v9.x.x 及以下版本的更新日志，您可以直接通过 NPM 引入最新的 NIM SDK，详情请参考 [集成 SDK](https://doc.yunxin.163.com/messaging/guide/jMyNTU0ODI?platform=web)。有关 10\.x\.x+ 推荐版，请参考《IM 即时通讯 V10》[Web/uni-app/小程序/RN 更新日志](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)。

:::details 单击展开了解什么是 LTS 版，以及与推荐版的区别。

LTS 版基于 [推荐版](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)，可满足常见 IM 应用业务场景，但更注重稳定性。推荐版则主要是在可商用的基础上，提供新功能与特性。

LTS 版相较推荐版，在更长周期内获得了更多用户的验证，且修复了多个历史版本的已知问题，稳定性保障更佳。

<!--
- LTS 版不支持海外节点存储以及其他最新功能。

    具体功能差异如下：

    功能 | 简介 | <div style="width:80px">LTS 版</div> | <div style="width:80px">推荐版</div>
    ---- | ---- | ---- | ----
    融合存储 | 将数据存储于海外节点<note type=notice>如果您的应用涉及海外业务，请选择推荐版。</note> | <font color=red>✘</font> | <font color=green>✔️ </font>
    聊天室空间消息 | 用于在基于空间坐标的场景下给指定范围内的用户发送消息，如某游戏地图指定区域内的玩家 | <font color=red>✘</font> | <font color=green>✔️ </font>
    聊天室定向消息 | 将消息发送给聊天室内指定的用户 | <font color=red>✘</font> | <font color=green>✔️ </font>
    聊天室标签实时更新 | 实时更新聊天室的用户标签 | <font color=red>✘</font> | <font color=green>✔️ </font>
-->
:::

## 9.21.10 (2026-01-30)

内部优化。

## 9.21.0 (2025-12-22)

**新增功能**

- API 普通流式消息支持高级群。
- 普通流式消息现支持携带 RAG 信息，增强 AI 交互能力。

**优化**

- 优化重连机制。
- 流式过程中查询消息时补齐消息完整内容。

## 9.20.17 (2025-09-28)

**新增功能**

- 点对点文本支持普通流式消息。
- 底层连接优化以及其他内部优化。

## 9.20.15 (2025-08-26)

**新增功能**

新增消息的二次编辑能力。

**接口变更**

| 接口 | 说明 |
| ---- | ---- |
| [`modifyMessage`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#modifyMessage) | 新增接口，用于用于实现消息的二次编辑能力。 |

## <span id="9.20.14 (2025-08-20)">9.20.14 (2025-08-20)</span>

修复微信小程序接收图片消息异常问题。

## <span id="9.20.12 (2025-06-16)">9.20.12 (2025-06-16)</span>

- `resetAllSessionUnread` 和 `setCurrSession` 方法新增 done 回调，预防调用接口姿势错误。
- 其他内部优化。

## <span id="9.20.10 (2025-04-18)">9.20.10 (2025-04-18)</span>

- 针对 AI 大模型生成的消息，新增了流式效果输出功能，使消息内容能够逐步展示。
- 同时，新增了 AI 流式代理功能，用于更高效地管理和控制消息流的输出。

## <span id="9.19.13 (2025-03-21)">9.19.13 (2025-03-21)</span>

优化数据库状态管理，数据库异常断开后自动重连。

## <span id="9.19.12 (2025-03-11)">9.19.12 (2025-03-11)</span>

优化内部传输策略。

## <span id="9.19.11 (2025-02-19)">9.19.11 (2025-02-19)</span>

- 缩小 NIM SDK 包体积 30～50 KB。
- 将 NIM SDK 的微信小程序产物体积从 756 KB 降低为 705 KB。

## <span id="9.19.10 (2024-12-24)">9.19.10 (2024-12-24)</span>

内部优化。

## <span id="9.19.3 (2024-12-18)">9.19.3 (2024-12-18)</span>

- 提升网络联通率与稳定性。
- 内部多项优化。

## <span id="9.19.2 (2024-11-15)">9.19.2 (2024-11-15)</span>

提升网络连接稳定性。

## <span id="9.19.0 (2024-10-15)">9.19.0 (2024-10-15)</span>

新增 AI 数字人功能。详情请参考 [实现与 AI 数字人聊天](https://doc.yunxin.163.com/aiagents/guide/DgyNDI0NTk?platform=client)。

## 9.18.1 (2024-10-10)

- 新增 [`updatePushToken`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_PushInterface.PushInterface.html#updatePushToken) 接口支持第三方厂商推送 token 的外部设置。
- 优化内部连接稳定性。

## 9.18.0 (2024-08-30)

- 提升网络稳定性。
- 内部多项优化。

:::note note
- 9.18.0 版本的小程序支持上传多个备份域名。
- 由于小程序上传地址变更，您需要新增小程序上传域名白名单配置，白名单配置中需要增加关于上传文件（uploadFile）的域名：
    - `https://fileup.chatnos.com`
    - `https://oss.chatnos.com`
- 原来使用的上传域名（`https://nos.netease.com`）也可以继续保留。
:::

## 9.17.5 (2024-08-08)

优化连接问题。

## 9.17.4 (2024-08-07)

兼容优化 [音视频通话 1.0 产品（已停止迭代）](https://doc.yunxin.163.com/rtc1/concept?platform=android) 依赖的信令协议。

## 9.17.3 (2024-08-05)

内部优化。

## <span id="9.17.2 - 2024-07-16">9.17.2 (2024-07-16)</span>

优化附件上传的内部逻辑。

## <span id="9.17.1 - 2024-07-03">9.17.1 (2024-07-03)</span>

- 增强编译产物 ES6 语法的兼容性。
- 内部优化。

## <span id="9.17.0 - 2024-06-28">9.17.0 (2024-06-28)</span>

- 提升了数据库连接的稳定性。
- 修复了 indexedDB 插入键（add key）的错误。

## <span id="9.16.2 - 2024-05-22">9.16.2 (2024-05-22)</span>

- 多项底层优化。
- 优化数据库打开失败异常处理。

## <span id="9.16.1 - 2024-04-24">9.16.1 (2024-04-24)</span>

优化数据包体积，较大程度节省传输流量，提升传输效率。

## <span id="9.16.0 - 2024-04-16">9.16.0 (2024-04-16)</span>

**新增特性**

- 支持添加、移除特别关注群成员列表。
- 新增鸿蒙终端类型的解析。

**优化改进**

- 文件消息支持文件断点续传。
- 融合存储支持直传地址。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`addTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#addTeamMembersFollow) | 添加特别关注群成员列表。（高级群） |
| [`removeTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#removeTeamMembersFollow) | 移除特别关注群成员列表。（高级群） |
| [`addSuperTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#addSuperTeamMembersFollow) | 添加特别关注群成员列表。（超大群） |
| [`removeSuperTeamMembersFollow`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#removeSuperTeamMembersFollow) | 移除特别关注群成员列表。（超大群） |

**API 变更**

方法/回调/类 | 说明
---- | ----
[`NIMEnumClientType`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/enums/nim_types.NIMEnumClientType.html) | 新增 `HarmonyOS`，多端登录支持鸿蒙客户端类型。

## <span id="9.14.4 - 2024-02-23">9.14.4 (2024-02-23)</span>

**新增特性**

- 支持根据 Thread 根消息查询本地 Thread 子消息。
- 支持根据 Thread 根消息查询本地 Thread 子消息的数量。

**API 新增**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`subMessages`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#subMessages) | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息。 |
| [`subMessagesCount`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#subMessagesCount) | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息的数量。 |

## <span id="9.14.3 - 2024-01-24">9.14.3 (2024-01-24)</span>

内部优化。

## <span id="9.14.1 - 2023-12-04">9.14.1 (2023-12-04)</span>

内部优化。

## <span id="9.13.0 - 2023-09-05">9.13.0 (2023-09-05)</span>

**修复**

- IM 连接断开后，未触发 `ondisconnect` 回调。
- 调用 `getLocalSessions` 返回会话中包含已删除的会话。

**API 变更**

API | 说明
---- | ----
`onUpdateTeamManagers` | `members` 新增参数 `account`：用户账号（accid）

## <span id="9.12.2 - 2023-08-04">9.12.2 (2023-08-04)</span>

- 支持 safari 10 以上版本开启数据库功能。
- 优化 NOS 上传图片的内部逻辑。
- 修复撤回群消息后，实际群成员仍能看到撤回消息的问题。

## <span id="9.12.1 - 2023-07-26">9.12.1 (2023-07-26)</span>

修复严格模式下报错的问题。

## <span id="9.12.0 - 2023-07-07">9.12.0 (2023-07-07)</span>

**修复**

本次版本修复以下问题：

- 当批量将会话消息未读数清零(标记已读)时，会话数量过大导致报错。
- 弱网场景下，重连异常问题。
- 同步数据异常问题。
- 调用 `destroy` 销毁实例后，仍进行连接的问题。

**API 变更**

API | 说明
---- | ----
`NIMGetInstanceOptions.socketConcurrent` | 新增初始化参数：Socket 并发连接数上限。如果您需要加快 Socket 连接，建议您设置该参数。请参考 [API 参考文档](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html)。
`NIMGetInstanceOptions.rollbackDelMsgUnread` | <font color=red>废弃</font>初始化参数。

## <span id="9.11.0 - 2023-05-30">9.11.0 (2023-05-30)</span>

**新增特性**

支持接入第三方机器人，在一对一（P2P）和群组（高级群，Team）场景中与机器人进行互动，具体请参考 [接入第三方机器人](https://doc.yunxin.163.com/messaging/docs/DU5MzA2MDQ?platform=web)。

**优化**

- 优化文件发送的流程。
- 对同步前调用部分接口添加日志警告。

**修复**

- 修复调用 `deleteLocalSession` 后未读数数量异常的问题。
- 修复调用 `getThreadMsgs` 获取 thread 消息列表会将 `idClient` 为空的不同消息去重的问题。
- 修复微信小程序启动后报错的问题。
- 修复其他已知问题。

**API 变更**

在发送消息的相关接口的入参中新增机器人信息字段（`robotInfo`），用于实现机器人消息功能。

## <span id="9.10.1 - 2023-04-14">9.10.1 (2023-04-14)</span>

**问题修复**

- 修复聊天室登录的回调缺失回参的问题。
- 修复部分场景下本端操作群时，本端可能不会收到 onmsg 消息事件的问题。
- 修复转让群并退出群时，本端会抛出异常的问题。
- 修复部分场景下，调用 getTeamMsgReadAccounts 接口获取群消息已读账号时，会异常的试图处理数据库的问题。

## <span id="9.10.0 - 2023-04-11">9.10.0 (2023-04-11)</span>

:::note notice
当前版本存在部分问题，已在 9.10.1 版本紧急修复，升级请选择 9.10.1 版本。
:::

**新增特性**

- 新增 [onMyTeamMembers](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onMyTeamMembers) 和 [onMySuperTeamMembers](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onMySuperTeamMembers) 初始化回调函数，在初始化可获取个人在所有群组（高级群和超大群）中的成员信息的回调。
- 新增 [onMsgReceipts](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onMsgReceipts) 初始化回调函数，可通过该回调查看某消息是否已读。

**优化**

- 优化内部拉黑后的消息重发逻辑，具体请参考 [重发消息](https://doc.yunxin.163.com/messaging/docs/zcyOTYyMTU?platform=web#%E9%87%8D%E5%8F%91%E6%B6%88%E6%81%AF)。
- 兼容 ES5 语法，支持 SDK 在低版本 android webview 中运行。

**问题修复**

- 修复登录后未同步到存离线的信令通知的问题。
- 修复内存中的 session 对象逻辑异常问题。
- 修复自定义断网后收到的消息回包字段丢失问题。
- 修复调用 deleteMsgSelfBatch 接口报错的问题。
- 修复离线已读回执中未更新 session 的回执时间（onOfflineMsgReceipts）的问题。
- 修复超时包后给响应，可能造成代码执行错误的问题。
- 修复其他已知问题。

## <span id="9.9.0 - 2023-02-10">9.9.0 (2023-02-10)</span>

**优化改进**

- 规范 `ondisconnect` 提供的回调（NIMOnDisconnectResultOffline）的 code。
    - 主动断开，触发 `ondisconnect` 回调，code 为 `alreadyDisconnected`。
    - 设置 `reconnectAttempts`，重连次数达到最大触发 `ondisconnect` 回调，code 为 `allAttemptsFailed`。
    - 侦测断开网络，触发 `ondisconnect` 回调，code 为 `offlineListener`。

- 在 `onClearServerHistoryMsgs` 回调中新增 `ext` 字段信息。
- `clearServerHistoryMsgsWithSync` 接口新增 `isDeleteRoam` 入参（是否删除漫游消息），默认为 true。
- 优化通过 s3 上传方式上传文件的内部逻辑。

**问题修复**

- 修复 `onSessions` 回调中，出现无消息空会话的问题。
- 修复多端登录场景下，其中一端通过 `setCurrSession` 接口清除置顶会话未读数后，另一端表现异常的问题。
- 修复单向删除消息后未读数未变更的问题。
- 修复其他已知问题。

## <span id="9.8.0 - 2022-12-27">9.8.0 (2022-12-27)</span>

**优化改进**

- 系统通知更新事件 onupdatesysmsg 提供 from 和 type 字段，分别表示系统通知发送方和系统通知的状态。
- **被拉黑方** 向 **拉黑方** 发出的消息体的服务端 ID 逻辑优化。

**问题修复**

- 修复登录时报 `getNosOriginUrl failed` 错误的异常。
- 修复登录时报 `taskAfterSync syncDBDataPromise error` 的异常。
- 修复 `getCollects` 接口 `lastId`、`reverse` 入参设置无效的问题。
- 修复 `getThreadMsgs` 接口 `endTime` 入参设置无效的问题。
- 修复支付宝环境上传引起的 `beginupload` 提前终止上传代码失效的问题。
- 修复逻辑删除本地会话时，收到新消息后未读数没有在原来的基础上加 1 的问题。
- 修复逻辑删除本地会话引申出的问题，对本地会话为 undefined 的情况进行处理。
- 修复在 nodeJS 环境下引入 SDK 时异常报错的问题。
- 修复长连接使用优先级顺序存在问题。
- 修复可信时间戳协议服务器下发了但是端测没解析的问题。
- 修复连接中途就销毁后数据上报报错的问题。
- 修复通过 NOS 上传文件时，由于未设置 logger 导致文件 `Upload.onload` 回调中打印日志失败的问题。

## <span id="9.6.4 - 2022-12-7">9.6.4 (2022-12-7)</span>

**API 变更**

| <div style="width:150px">API</div> | <div style="width:120px">API 变更说明</div> |
| --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#updateLocalSession" target="_blank">`updateLocalSession`</a> | 新增入参 `needNotify`，来控制是否触发更新会话的回调。<br> 若 `needNotify` 为 `true`，触发 `onUpdateSessions` 和 `onUpdateSession` 的回调。`needNotify` 为 `false` 则不触发。默认为 `true`。 |
| <a href="https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getQuickComments" target="_blank">`getQuickComments`</a> | 新增返回参数 `scene`，来区分消息的会话类型。<br> `scene` 对应的值有 `p2p`、`team`、`superTeam`。 |
| <a href="https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html" target="_blank">`MessageInterface`</a> 模块下的消息发送相关接口 | <a href="https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.NIMBaseSendMsgOptions.html" target="_blank">`NIMBaseSendMsgOptions`</a> 新增属性 `needUpdateSession`，表示发送消息时是否刷新远端的服务器会话列表。<br>当发送消息时，设置 `needUpdateSession` 为 `true`，接收者收到的消息的 `needUpdateSession` 也为 `true`。`needUpdateSession` 为 `false`，接收者收到的消息的 `needUpdateSession` 也为 `false`。默认为 `true`。 |

**修复**

修复删除消息后的报错问题。

## <span id="9.6.3 - 2022-10-27">9.6.3 (2022-10-27)</span>

**新增特性**

9.6.3 的聊天室模块，新增根据标签（Tags）查询聊天室历史消息的功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging/docs/jgyODc1NDk?platform=web#根据标签查询历史消息" target="_blank">根据标签查询历史消息</a>。

**新增事件**

聊天室模块新增 `onTagsUpdate` 事件来监听聊天室标签的变更情况，回调包含变更后的标签信息。

**API 新增**

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
| --- | --- |
| <a href="https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/Chatroom/classes/chatroom.Chatroom.html#getHistoryMsgsByTags" target="_blank">`getHistoryMsgsByTags`</a> | 通过聊天室标签（可多个）来检索聊天室历史消息 |

## <span id="9.6.1 - 2022-9-26">9.6.1 (2022-9-26)</span>

**优化**

- 优化断连的内部逻辑。
- 统一本地（local）操作相关接口的数据来源和内部逻辑。

## <span id="9.5.0 - 2022-8-29">9.5.0 (2022-8-29)</span>

**优化**

- 优化 LBS 策略。
- 修复发送消息返回 500 导致的本地异常问题。

## <span id="9.3.2 - 2022-8-22">9.3.2 (2022-8-22)</span>

修复海外地区偶现的发送语音消息和视频消息失败的问题。

## <span id="9.3.1 - 2022-8-9">9.3.1 (2022-8-9)</span>

修复多端登录场景下，在 Web 端调用 [`deleteMsgSelfBatch`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#deleteMsgSelfBatch) 方法批量单向删除消息，在另一端未能触发回调事件通知用户的问题。

## <span id="9.3.0 - 2022-7-25">9.3.0 (2022-7-25)</span>

**新增**

初始化参数新增日志等级字段 `logLevel`（可选值为：debug、log、info、warn、error、off）。

设置对应的日志等级后，仅输出高于或等于对应等级的日志, off 则关闭所有日志，默认值 off。

**优化**

- 优化自动重连机制，实现国内外节点平滑迁移。
- 补充初始化实例的入参 `reconnectionAttempts` （重连次数）的说明。

**<font color=red>废弃</font>**

<font color=red>废弃</font> `debug` 参数，暂时保留功能，请及时调整。

## 9.2.0 (2022-05-24)

调用 [`updateSuperTeam`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#updateSuperTeam) 方法可更新 `inviteMode`、`updateCustomMode`、`updateTeamMode` 这三个权限。

## 9.1.2 (2022-05-09)

修复发现的问题，包括：
- `onSession` 会抛出不完整 session 的兼容性问题。
- 当不支持数据库，单向删除或撤回的消息恰好为最后一条消息时，`sessionSet` 中对应 session 里仍存在 `lastMsg` 的问题。
- `isTop` 属性异常。

## 9.1.1 (2022-04-26)

修复聊天室接收到的空间消息体中没有携带坐标信息的问题。

## 9.1.0 (2022-04-18)

**新增特性**

客户端反垃圾词库存储在本地，获取时本地优先。

**优化**

优化消息漫游场景，避免重连时再次拉取全量漫游消息。

**修复**

修复遗留问题，包括：
- 多 Tab 标签页操作导致会话未读数异常
- 阿里系应用在安卓 HTML5 环境中上传文件不成功
- 初始化同步完成后，会话在 ```autoMarkRead:false``` 下 ```lastMsg``` 计算错误
- 调用 ```updateMyInfo``` 方法时回调中返回的信息错误
- ```setOptions``` 方法对参数中所有的函数类型的参数加上类型判断

## 9.0.1 (2022-03-10)

**新增**

- 新增 recallMsg（撤回消息），即将替换 deleteMsg
- 新增 deleteRoamingMsgBySession（删除该会话相关的漫游消息）,即将替换掉 deleteSession

**修复**

- 修复实例销毁时已绑定的监听事件未能完全移除的问题
    - 因为机器人功能已下架所以下列 API 已删除
    - getRobots
    - getRobotList
    - parseRbotTemplate
    - sendRobotMsg

**优化**

- 压缩小程序平台包体积大小至 552 KB
- 优化实例销毁的流程，避免短时间内多次销毁可能会导致的异常

## 8.11.3 (2022-08-30)

**修复**

- 修复 收到单聊消息没有标记已读，导致下次登录还会继续下发的问题
- 优化 SDK 结构，使用 SDK 不会与当前环境全量引入的 babel-polyfill 起冲突

<!-- ## 8.11.2 (2022-02-14)

**修复**

- 修复 某会话存在撤回消息时，初始化同步到离线消息，开发者收到的会话有两条的问题 -->

## 8.11.1 (2022-01-18)

**修复**

- 修复 API getSuperTeamMembersByAccounts 回调失效的问题
- 初始化入参的回调函数支持现在传 async 方法

## 8.11.0 (2022-01-10)

**新增**

- 聊天室标签实时更新设置，见 [chatroom.updateTags](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/Chatroom.html#updateTags__anchor)
- 聊天室定向消息，见 [chatroom.sendText](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/Chatroom.html#sendText__anchor) 的 toaccount_ids 参数
- 聊天室匿名模式下支持鉴权 token，见 [chatroom.getInstance]() 的 loginAuthType 和 loginExt 参数
- 资料反垃圾，涉及以下接口
  - 更新聊天室信息 chatroom.updateChatroom 新增 antiSpamBusinessId 参数
  - 更新自己在聊天室内的信息 ChatroomFn.updateMyChatroomMemberInfo 新增 antiSpamBusinessId 参数
  - 发送文本消息 nim.sendText 新增 antiSpamBusinessId 参数
  - 更新超大群信息 nim.updateSuperTeam 新增 antiSpamBusinessId 参数
  - 创建群 nim.createTeam 新增 antiSpamBusinessId 参数
  - 更新群 nim.updateTeam 新增 antiSpamBusinessId 参数
  - 更新我的名片 nim.updateMyInfo 新增 antiSpamBusinessId 参数

## 8.10.0 (2021-12-23)

**新增**

- 支持 s3 存储。见[融合存储方案](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TgzMjg3Mzg?platformId=60179)
- 添加 isMyFriend 接口，用于本地数据库检验某账号是否是自己的好友
- 添加 isUserInBlackList 接口，用于本地数据库检验某账号是否处于自己的黑名单中。

**修复**

- 修复 IE9 的兼容性问题。

## 8.9.0 (2021-12-03)

**新增**

- 好友上限提升至 10000。同步时会得到多次回调得到全部好友数据，并新增接口分页从远端获取好友。

**优化**

- sdk 在浏览器里能更快感知到网络断线，从而断开连接，能减小聊天消息状态从 failed 突变为 success 的可能。

**修复**

- 修复超大群获取逻辑，当离开超大群后，此超大群的获取将会走远端服务器获取。

<!-- ## 8.8.4 (2021-11-26)

**新增**

- 聊天室新增空间坐标和订阅消息的距离参数，请参考 [getInstance](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/Chatroom.html#toc1__anchor)
- 聊天室发送文本消息接口新增空间坐标参数 请参考 [sendText](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/Chatroom.html#sendText__anchor)
- 新增更新坐标接口，请参考 [updateCoordinate](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/Chatroom.html#updateCoordinate__anchor) -->

<!-- ## 8.8.1 (2021-11-05)

**修复**

- 修复 8.8.0 做的同步卡顿优化引起的同步失败问题。-->

## 8.8.0 (2021-10-28)

**修复**

- 修复 deleteLocalsession 接口修复没有清除内存中的 session 的问题。

**优化**

- 优化初始化同步大量离线消息造成 UI 卡顿的场景

**新增**

- 麦序队列新增批量添加通知。
- 新增根据时间排序的全文检索消息接口，请参考 [msgFtsInServerByTiming](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/NIM.html#msgFtsInServerByTiming__anchor)

## 8.7.2 (2021-09-27)

已知问题修复。

<!--
- 修复 RN 访问 realm 数据库的一些异常，注意 realm 在 SDK 测稳定支持的版本是 3.x
 -->

## 8.7.0 (2021-08-25)

**新增**

- 聊天室队列变更新增归属账号
- 易盾反垃圾新增扩展字段支持（见 API 的 yidunAntiSpamExt 字段说明），[命中结果返回](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/IMMessage.html)(见 yidunAntiSpamRes)。

**修复**

<!--
- react-native 环境下上传文件 content-type 错误

 -->

- 断网重连后登录时 autoconnect 状态不对

## 8.6.0 (2021-07-20)

**修复**

- 多端同步批量单向删除消息时未读数异常问题
- 偶现收到 msgReceipt 后的 typeError 错误
- 会话过多时，偶现不能清空未读数问题
- 调用 getQuickComments 导致消息状态误变更

**优化**

- 优化文件上传失败的提示信息

## 8.5.1 (2021-07-01)

**新增**

- [云端消息全文检索 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#msgFtsInServer__anchor)追加发送者，消息类型参数供以筛选

**修复**

- 修复在小程序中 socketio 判断环境不准确，导致 im 无法连上的问题。

**优化**

- 日志精简，脱敏，如会话，消息等对象，日志只收集必要的 ID 等信息。

## 8.5.0 (2021-06-22)

**新增**

- [云端消息全文检索 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#msgFtsInServer__anchor)
- 支持撤回自己发送给自己的消息

**修复**

<!--
- rn sdk getLocalSessions 获取到本地会话没有过滤空会话
 -->

- SDK 实例 destroy 后，仍能收到某些数据回调
- 数据库发生错误后，下一条消息没有上报给上层

## 8.4.0 (2021-04-27)

**新增**

- 聊天室分组功能
- 自定义消息新增可本地检索字段 `text`

**修复**

- 逻辑删除本地会话，再次登录时插入本地会话，产生的会话信息不全
- 开启了自动重连，偶现断开后没有重连
- 偶现 destroy 销毁实例不成功
- 偶现已读回执乱序问题
- 收到消息的同时调用 `setCurrSession`，导致的偶现未读数异常问题

## 8.3.5 (2021-03-30)

**优化**

- 数据库中的消息对象新增 `hasRead` 字段，非必须。[发送过群已读回执](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#sendTeamMsgReceipt__anchor) 的消息，才会包含该字段 `hasRead: true`
- 数据库中的消息对象新增 `read`、`unread` 两个字段，分别代表消息的已读人数、未读人数，通过 [批量查询群消息已读未读人数](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getTeamMsgReads__anchor) API 查询过的消息，才会包含/更新 `read`、`unread` 两个字段
- [查询单个群消息的已读未读账号列表](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getTeamMsgReadAccounts__anchor) API 的查询结果会自动存本地数据库，之后断网期间向服务器查询失败时，会自动返回数据库中存储的对应数据

**修复**

- 调用服务器 API 自己给自己发消息，会重复收到两次 onMsg

## 8.3.0 (2021-03-03)

**新增**

- 支持动态 token 登录、第三方回调登录策略，请参考 [初始化参数](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#.getInstance__anchor) `authType`
- 新增[通过群 ID 及成员账号获取超大群成员信息](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getSuperTeamMembersByAccounts__anchor)
- 新增[获取超大群内被禁言的群成员列表](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getMutedSuperTeamMembers__anchor)
- `resetSessionUnread`、`resetSessionsUnread`、`resetSuperTeamSessionsUnread` 三个重置未读数的 API，增加第二个参数 done 回调，重置失败的会话 ID 会通过 done 回调上抛
- [文档转码](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#transDoc__anchor)支持的文件类型新增了 `doc`、`docx`

**修复**

- 部分撤回场景，再次登录后重复收到撤回通知
- 离开超大群后，获取到的群信息不是最新的有效数据
- 超大群新成员入群/通过入群申请后，已有成员的本地群信息未更新

**优化**

- debug 日志过滤消息的具体内容，避免消息泄漏

## 8.2.5 (2021-02-04)

- **完善 lbs 域名防劫持策略策略**：在初始化时新增配置，用户可自行定义传入备份的 lbs 域名。请参考 API 文档 `getInstance` 里的 `lbsBackupUrlsCustomer` 参数。

## 8.2.0 (2020-12-30)

**新增**

- 批量查询群组信息功能开启，请参考 API 文档 `getTeamsById`
- 群已读发送回执后，本地将会标记此条消息的 `hasSendAck` 字段为 `true`，代表它已被发送过已读回执
- 批量重置会话的未读数功能开启，请参考 API 文档 `resetSessionsUnread`
- 删除会话现已支持删除此会话的漫游消息，请参考 API 文档 `deleteLocalSession` 中新增了 `isDeleteRoaming` 参数的说明

**修复**

- 修复 **不开启数据库时 `insertLocalSession` 会抛出异常** 的问题
- 完善断线重连逻辑，如被踢导致没有继续重连的情况
- 信令 sdk 同步多端消息处理逻辑修复

## 8.1.0 (2020-11-13)

**新增**

- 新增本地日志存储及上报功能，默认开启，可以通过设置初始化参数 `dbLog` 为 `false` 关闭，也可通过 `expire` 设置日志时效
- 聊天室支持 CDN 消息功能
- 新增独立 CDN 域名功能，可统一替换文件链接域名，指定域名可通过服务器动态下发或初始化参数配置

**修复**

- 部分格式的 GIF 图片发送失败问题

## 8.0.0 (2020-09-24)

**新增**

- 新增初始化参数 `resetUnreadMode`，表示重置会话未读数时，若同步至服务器失败，是否仅重置本地会话未读数
- [批量单向删除消息](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteMsgSelfBatch__anchor)
- [删除会话服务器聊天记录](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#clearServerHistoryMsgsWithSync__anchor)，支持单聊和群聊场景，支持多端同步
- 发消息相关 API 新增 `env` 参数，用于指定服务器抄送/第三方回调会发送给哪个环境

**修复**

- 收到不计入未读数消息，重新登录后，仍被计入了未读数

<!--
- 修复 RN 环境下 `getLocalMsgs` 获取到的消息乱序问题
 -->

## 7.9.1 (2020-09-14)

**新增**

- [删除本地会话](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteLocalSession__anchor)接口支持逻辑删除模式。逻辑删除不会真的删除本地会话，而是标记会话为 **已删除** 状态，这样可以保留会话的 `unread` 和 `msgReceiptTime`，下次新建该会话时，可以保持正确的未读数和已读时间戳
- 超大群撤回消息支持多端同步

**修复**

- 离线重连后偶现未读数不准的问题

## 7.8.1 (2020-07-29)

**变更**

- [获取聊天室成员列表](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/Chatroom.html#getChatroomMembers)接口支持按进入时间排序

**修复**

- 不使用数据库场景下，会话标记已读没有多端同步

## 7.8.0 (2020-07-21)

**新增**

<!--

备注：字节跳动小程序暂不对外

- 新增对字节跳动小程序的支持，具体见小程序

 -->

- 支持自定义消息子类型。发消息时可指定消息子类型，[查询本地消息](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getLocalMsgs__anchor) 时支持按消息子类型检索
- 自定义多端互踢策略，[初始化](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#.getInstance__anchor) 参数新增 `customClientType`，表示自定义的客户端类型。不同客户端类型之间的互踢策略可在管理后台自定义
- 新增备用 lbs 功能，存储至 LocalStorage 中。可以通过 [初始化](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#.getInstance__anchor) 参数 `lbsBackup` 开启或关闭，默认开启
- 新增快速断网重连功能，加快重连速度。可通过 [初始化](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#.getInstance__anchor) 参数 `quickReconnect` 开启或关闭，默认关闭

**变更**

- 聊天室不再请求 lbs 地址
- 小程序 SDK 文件名格式变更为 `NIM_Web_XXX_miniapp_vX.X.X.js`

**修复**

- 单向删除消息后偶现没有触发更新会话

## 7.7.2 (2020-06-12)

**新增**

- 新增反作弊功能，具体见 [IM](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html) 或 [聊天室](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/Chatroom.html)发消息 API 的 `yidunAntiCheating` 字段。相关 [网易易盾文档](https://support.dun.163.com/documents/2018041901?docId=420802794453520384#%E6%AD%A5%E9%AA%A42%EF%BC%9A%E6%8E%A5%E5%85%A5%E6%96%87%E6%9C%AC%E6%A3%80%E6%B5%8Bapi,%E4%BC%A0%E5%85%A5%E5%8F%8D%E4%BD%9C%E5%BC%8Atoken%E5%AD%97%E6%AE%B5)。

## 7.7.0 (2020-05-27)

**新增**

- IM 和聊天室消息新增服务器第三方回调扩展字段 `callbackExt`
- IM 账号被服务器踢 `serverKick` 时新增自定义字段 `custom`

**修复**

- 超大群发消息没有多端同步

## 7.6.0 (2020-05-11)

**新增**

- [消息回复（thread）](/docs/TM5MzM5Njk/TUwNTU0Mzc#消息回复（thread）)
- [消息快捷评论](/docs/TM5MzM5Njk/TUwNTU0Mzc#消息快捷评论)
- [收藏功能](/docs/TM5MzM5Njk/TUwNTU0Mzc#收藏功能)
- [会话置顶功能](/docs/TM5MzM5Njk/TUwNTU0Mzc#会话置顶功能)
- [会话消息 PIN 标记](/docs/TM5MzM5Njk/TUwNTU0Mzc#会话消息 PIN 标记)
- 未接通的音视频通话支持存漫游和离线

**修复**

- 会话未读数多端同步不准的问题

**变更**

- 调整初始化回调 `onsessions` 的会话数量上限至 500

## 7.4.2 (2020-03-20)

**新增**

- 新增 `onSessionsWithMoreRoaming` 初始化回调函数，用于同步漫游消息未全部下发的会话。
- 新增 [`deleteSessionsWithMoreRoaming`](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteSessionsWithMoreRoaming__anchor)、[`getSessionsWithMoreRoaming`](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#getSessionsWithMoreRoaming__anchor)、[`updateSessionsWithMoreRoaming`](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#updateSessionsWithMoreRoaming__anchor) API

## 7.4.0 (2020-03-10)

**新增**

- 新增 [单向删除消息 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteMsgSelf__anchor)，仅删除自己看到的消息，对方无感知

**变更**

- [删除某个会话的本地消息 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteLocalMsgsBySession__anchor)支持本地标记删除
- [撤回消息 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteMsg__anchor)支持自定义推送文案和推送属性

<!--
- RN iOS 推送 API PushNotificationIOS 更改为从 [@react-native-community/push-notification-ios](https://github.com/react-native-community/react-native-push-notification-ios) 引用

 -->

**修复**

- 修复无法感知微信下的上传文件失败

<!--
- 修复无法感知微信、RN 环境下的上传文件失败
 -->

## 7.2.0 (2020-01-13)

**新增**

- 超大群新增部分 API，包括 [申请加入](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#applySuperTeam__anchor)、[添加](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#addSuperTeamManagers__anchor)/[删除管理员](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#removeSuperTeamManagers__anchor)、[群成员禁言](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#updateSuperTeamMembersMute__anchor)、[超大群禁言](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#updateSuperTeamMute__anchor)、[修改别人的群昵称](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#updateNickInSuperTeam__anchor)、[转让群](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#transferSuperTeam__anchor) 等
- 新增 [将消息存储至本地数据库](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#saveMsgsToLocal__anchor) API
- 新增 [搜索本地内容](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#searchLocal__anchor) API
- 微信小程序 SDK 上传文件支持 `uploadprogress`

**修复**

- chrome headless 不能使用数据库
- 群组消息撤回后对应的未读数没有更新
- 修复多次重连后偶现悄悄被踢 silentlyKick
- 不使用数据库时，会话未读数不能忽略通知类消息

## 7.0.3 (2019-12-04)

新增 `shouldIgnoreMsg` 初始化参数，支持开发者自定义忽略某些消息

## 7.0.0 (2019-11-13)

**新增**

- 新增服务端会话列表服务，支持更多的会话，支持获取、更新、删除
- 发送本地消息支持自定义发送方

**优化**

- 心跳逻辑优化
- 兼容本地数据库异常情况，保证仍能正常收发消息

**修复**

- 开启文件安全校验的应用，调用获取历史消息接口返回的消息顺序不正确

## 6.9.0 (2019-09-17)

**新增**

<!--
- RN SDK 支持本地存储日志及远程拉取本地日志
 -->

- [预览生成缩略图](/docs/TM5MzM5Njk/TU1OTM4NzE?#预览生成缩略图)支持将动图缩略为动图, 默认缩略为静图，初始化参数 `thumbnailToStatic = false` 时才会缩略为动图
- [撤回消息 API](https://dev.yunxin.163.com/docs/interface/即时通讯Web端/NIMSDK-Web/NIM.html#deleteMsg__anchor)支持超大群场景
- [自定义系统通知](/docs/TM5MzM5Njk/zMyMjc1NDU?platformId=60179#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%B3%BB%E7%BB%9F%E9%80%9A%E7%9F%A5)支持超大群场景

**修复**

- 偶现登录或重连后会话回调不全及缺少 msgReceiptTime 字段

## 6.7.0 (2019-08-01)

**新增**

- **API**：[指定 lastMsg 类型获取本地会话列表](/docs/TM5MzM5Njk/jc2MDQ3NTI?#指定 lastMsg 类型获取本地会话列表)

<!--

- RN 支持 OPPO 和 VIVO 推送
 -->

**修复**

- electron 环境下，断网后执行 `destroy`，再联网 SDK 仍会重连
- `notifyForNewTeamMsg` 方法不能指出具体的错误群 ID
- 缺失离线时收到的未接通的音视频通话话单

## 6.6.6 (2019-07-11)

**新增**

- [获取服务器当前时间戳](https://dev.yunxin.163.com/%E5%8D%B3%E6%97%B6%E9%80%9A%E8%AE%AFWeb%E7%AB%AF/references/NIMSDK-Web/NIM.html#getServerTime__anchor)
- **根据会话 ID 和时间区间删除本地消息**：`nim.deleteLocalMsgs`

**修复**

- 删除本地消息后会话的 `lastMsg` 为 `null`
- 修复重复收到群撤回通知

## 6.5.5 (2019-06-12)

**新增**

- [超大群功能](/docs/TM5MzM5Njk/DY2NjIzODc)
    - 拉人、踢人、更改群资料，更改自己的群属性，获取超大群、获取超大群资料、获取超大群群成员列表等
- 新增超大群 `superTeam` 类型的[消息场景](/docs/TM5MzM5Njk/jg0NTA4NjE?platformId=60179#消息场景)

## 6.5.0 (2019-05-23)

**新增**

- [连接初始化参数](/docs/TM5MzM5Njk/zE0NDY4Njc#参数解释)
  - 增加 `noCacheLinkUrl` 参数，表示不缓存链接地址，默认 `false`。
- [获取群成员的邀请者 accid](/docs/TM5MzM5Njk/DI3MjI1Nzc#获取群成员的邀请者 accid)

## 6.3.0 (2019-04-18)

**新增**

- [连接初始化参数](/docs/TM5MzM5Njk/zE0NDY4Njc#参数解释)
  - 增加 `rollbackDelMsgUnread` 参数，表示收到撤回消息是否同时撤销被撤回消息影响的未读数，默认 `false`。
- [删除好友](/docs/TM5MzM5Njk/DIyNzk1Nzc#删除好友)
  - 增加 `delAlias` 参数，表示用户删除好友时，是否需要删除备注信息，默认 `false`。
- [删除某个会话的本地消息](/docs/TM5MzM5Njk/jg5MjQ4MTM#删除某个会话的本地消息)
  - 增加 `delLastMsg` 参数，表示是否同时删除本地会话对象中的的 lastMsg，默认 `false`。
- [删除点对点云端历史记录](/docs/TM5MzM5Njk/jg5MjQ4MTM#删除点对点云端历史记录)

**变更**

- [发送文件消息](/docs/TM5MzM5Njk/jg0NTA4NjE#发送文件消息)上传文件失败时，也触发 `done` 回调。
- [预览文件](/docs/TM5MzM5Njk/jg0NTA4NjE#预览文件)、[发送文件消息](/docs/TM5MzM5Njk/jg0NTA4NjE#发送文件消息)
  - 删除 `fileInputMaxSize` 参数，增加 `maxSize` 参数，对文件进行大小限制。
  - 删除 `fileInputCommonUpload` 参数，增加 `commonUpload` 参数，表示是否使用普通上传（最大 100M 文件）。默认 `false` 为分片直传，`true` 为普通上传。

    :::note note
     默认上传方式改为了 **分片直传**，对比之前版本的 **普通上传**，会自动选择加速节点上传，文件大小限制最大约 39G，但返回的文件信息对象没有了 `md5` 值，如果依赖文件信息的 `md5` 值，则需要手动设置 `commonUpload: true` 放弃使用 **分片直传**
    :::
  - 支持 blob/dataURL 类型的分片上传。

## 6.2.0 (2019-03-14)

**新增**

- [连接初始化参数](/docs/TM5MzM5Njk/zE0NDY4Njc#参数解释)
  - 增加 `keepNosSafeUrl` 参数，表示是否保持 NOS 安全短链不变，默认 `false` 自动替换短链为源链。
- [NOS 文件短链换源链](/docs/TM5MzM5Njk/TU1OTM4NzE#NOS 文件短链换源链)
  - 将通过 [预览文件](/docs/TM5MzM5Njk/jg0NTA4NjE#预览文件)或者[发送文件消息](/docs/TM5MzM5Njk/jg0NTA4NjE#发送文件消息) 或者收到的文件消息拿到的 NOS 文件安全短链转换为源链。
- [预览文件](/docs/TM5MzM5Njk/jg0NTA4NjE#预览文件)、[发送文件消息](/docs/TM5MzM5Njk/jg0NTA4NjE#发送文件消息)
  - 增加 `fileInputMaxSize` 参数，对传入的 `fileInput` 文件进行大小限制。
  - 增加 `fileInputCommonUpload` 参数，可选择传入 `fileInput` 文件的上传方式，默认 `false` 为分片直传，`true` 为普通上传。

    :::note note
    默认上传方式改为了 **分片直传**，对比之前版本的 **普通上传**，会自动选择加速节点上传，文件大小限制最大约 39G，但返回的文件信息对象没有了 `md5` 值，如果依赖文件信息的 `md5` 值，则需要手动设置 `fileInputCommonUpload: true` 放弃使用 **分片直传**。
    :::

- [消息对象](/docs/TM5MzM5Njk/jg0NTA4NjE#消息对象)

    增加 `isInBlackList` 参数，表示发送此条消息时，发送方 `from` 是否在接收方 `to` 的黑名单列表中。

- 通知消息 `netcallBill` 类型支持云端历史、漫游，同时 `attach` 里增加主叫方 accid`from`，和其他端在发起通话时设置的自定义内容 `ext`。

## 6.1.0 (2019-01-22)

**变更**

- [拉人入群](/docs/TM5MzM5Njk/DI3MjI1Nzc#拉人入群)增加自定义扩展字段 `custom`
- [转发消息](/docs/TM5MzM5Njk/jg0NTA4NjE#转发消息)接口不改变传入的 msg 参数

## 5.9.0 (2018-11-22)

**新增**

- 通过 sessionId 获取本地会话
- 指定某个群 ID 和群内成员 Account，获取对应的群成员信息

**变更**

- 创建群时，群可以设置群人数上限 level

## 5.7.0 (2018-10-11)

**新增**

- 登录接口增加 `customTag` 字段透传，服务器推送消息回传
- 聊天室队列批量更新元素
- 重复大文件加速秒传
- 新建群、拉人入群返回 810 时返回增加 **因为被拉的成员入群数量超限导致邀请失败的 accid 列表**

**变更**

- IM 发送消息的配置选项推送文案 `pushContent` 的限制提升到 500 字

## 5.5.0 (2018-08-07)

**新增**

- IM，chatroom 初始化增加文件存储配置
- IM，chatroom 发送文件消息增加文件存储配置

## 5.3.0 (2018-06-26)

<!--
- React Native 适配
 -->

**变更**

- 微信小程序重连机制优化

## 5.1.0 (2018-05-17)

**新增**

- 销毁实例 `destroy` 及断开连接 `disconnect` 方法增加 `done` 回调
- 微信小程序机型兼容性适配，及连接性能优化

**变更**

- 微信小程序聊天室获取连接地址优化
- 不再兼容 IE8 浏览器，并对 SDK 包做了精简及优化

## 5.0.0 (2018-03-29)

**新增**

- 客户端反垃圾
- 客户端提供删除 NIM 实例缓存的接口
- 群组临时禁言
- 群组消息已读功能
- web 私有化配置
- 微信小程序支持多条 websocket
- 微信小程序白名单列表处理
- 新增文档转码功能

**变更**

- 聊天室登录带上重连标记
- 聊天室高优先级消息增加标记

## 4.8.0 (2018-02-08)

**变更**

- SDK 日志记录优化
- 易盾反垃圾配置更新

## 4.6.0 (2018-01-04)

**新增**

- 聊天室队列管理权限可配置
- 聊天室历史记录拉取可以按类型筛选
- 群管理员可以撤回其他人发的消息
- 易盾反垃圾，支持对单条消息配置对应的反垃圾业务规则

**变更**

- WebSocket 链路若因网络状态不佳，悄悄被踢，将自动重连，不再由上层做处理
- WebSocket 握手重连优化，清除实例接口

## 4.4.0 (2017-11-16)

**新增**

- 聊天室新增麦序队列元素，增加可配置选项，用户从聊天室掉线或退出的时候，需要删除这个元素

**变更**

- 取消同步群成员配置选项，强制要求开发者按需同步群成员列表

## 4.3.0 (2017-10-12)

**新增**

- 全部会话未读数清零
- 全员广播接收接口
- 展示消息图片自动转换 https 链接
- 群消息支持 **只接收管理员消息提醒** 的免打扰选项

**变更**

- 获取及同步群成员不再进行本地存储，一律取服务器数据

## 4.2.0 (2017-09-12)

**新增**

- 聊天室匿名登录
- 聊天室机器人及其发送消息接口
- 聊天室获取机器人接口

## 4.1.0 (2017-08-08)

**新增**

- 多端同步及状态同步增加 Mac 端
- 新增聊天室连麦获取连麦队列头上第一个元素的方法

**变更**

- 登录同步消息失败的重连处理优化

## 4.0.0 (2017-07-06)

**新增**

- 新增机器人消息收发接口
- 新增机器人默认 bot 类型消息的 xml 解析方法
- 新增聊天室发送消息可选不保存历史消息配置

**变更**

- 修复部分 iPhone 机型断网重连后协议解析问题
- 修复转发消息数据库记录有误的问题

## 3.8.0 (2017-06-06)

**新增**

- 新增通用同步图片预览接口，支持私有化定制方案
- 连接初始化支持选择连接协议

**变更**

- 修复忽略群通知消息配置以后，对群状态更改相关 bug
- 修复不开启数据库情况下，会话未读数不准的问题

## 3.6.0 (2017-04-27)

**新增**

- 发布订阅事件，以及多端登录状态事件的订阅

**变更**

- 修复若干开启同步会话未读数后产生的 bugs

## 3.5.0 (2017-03-15)

**新增**

- 聊天室获取历史消息记录支持双向查询

## 3.4.0 (2017-01-20)

**变更**

- 优化 SDK 内部同步操作, 加快同步速度
- 获取本地消息去掉数量限制, 由开发者自己控制

## 3.3.0 (2016-12-28)

**变更**

- 优化连接建立方式

## 3.2.0 (2016-11-30)

**新增**

- [会话初始化参数](/docs/TM5MzM5Njk/zE0NDY4Njc?platformId=60179#参数解释) syncSessionUnread, 是否同步会话的未读数

**变更**

- 获取本地历史记录, 详情参考文档

## 3.1.0 (2016-10-26)

**新增**

- [群对象](/docs/TM5MzM5Njk/DI3MjI1Nzc?platformId=60179#群对象)增加 `mute` 字段
- [获取群禁言成员列表](/docs/TM5MzM5Njk/DI3MjI1Nzc?platformId=60179#获取群禁言成员列表)
- [发送消息的配置选项](/docs/TM5MzM5Njk/jg0NTA4NjE?platformId=60179#发送消息)增加开启易盾的参数
- [自定义系统通知](/docs/TM5MzM5Njk/zMyMjc1NDU?platformId=60179#自定义系统通知)增加开启易盾的参数
- [发送聊天室消息的配置选项](/docs/TM5MzM5Njk/jgyODc1NDk?platformId=60179#发送聊天室消息)增加开启易盾的参数
- [聊天室通知消息的类型](/docs/TM5MzM5Njk/jgyODc1NDk?platformId=60179#聊天室消息类型)增加全体禁言的通知类型

## 2.8.0 (2016-08-30)

**新增**

- [消息撤回](/docs/TM5MzM5Njk/jg0NTA4NjE?platformId=60179#消息撤回)

## 2.7.0 (2016-08-11)

**变更**

- 发送消息 和 发送自定义系统通知 的时候, 如果发送方被接收方加入了黑名单, 那么将会发送失败, 返回错误码 7101

**新增**

- 获取用户名片 和 获取用户名片数组 可以传入参数 `sync=true` 来强制从服务器获取最新的数据
- [聊天室](/docs/TM5MzM5Njk/jgyODc1NDk?platformId=60179)
  - 更新聊天室信息
  - 更新自己在聊天室内的信息
- [图片操作](/docs/TM5MzM5Njk/TU1OTM4NzE?platformId=60179#图片操作)增加了一系列预览图片的操作
- 发送消息的配置选项增加了 apns 用于配置特殊推送选项, 只在群会话中使用

## 2.5.0 (2016-07-08)

**变更**

- 获取用户名片数组 限制每次最多只能获取 150 个名片

**新增**

- 转发消息
- 重发消息
- 获取包含关键词的本地历史记录
  - 新增参数 `global` 表示是否全局搜索
- 同步开关 `syncExtraTeamInfo`, 控制是否同步额外的群信息, 默认 `true` 会同步额外的群信息, 目前包括
  - 当前登录用户是否开启某个群的消息提醒 (SDK 只是存储了此信息, 具体用此信息来做什么事情完全由开发者控制)
  - 调用接口 修改自己的群属性 来关闭/开启某个群的消息提醒
  - 调用接口 是否需要群消息通知 来查询是否需要群消息通知
- 设置聊天室临时禁言

## 2.4.0 (2016-06-02)

**变更**

- 在 Safari 下禁用数据库
- 发送消息已读回执, 发送的时候请传入 `session.lastMsg`

**新增**

- 群字段增加
    - 群头像
    - 群被邀请模式
    - 群邀请模式
    - 群信息修改权限
    - 群信息自定义字段修改权限
- 修改自己的群属性 字段增加
    - 扩展字段
- 更新群成员禁言状态
    - 对应的 群通知消息 类型为 `'updateTeamMute'`

## 2.2.0 (2016-04-28)

- 获取本地系统通知 加了一个参数 `read` 来限制已读状态

## 2.1.1 (2016-04-18)

**变更**

- 后续调用接口 初始化 SDK 和 初始化聊天室 时
    - 同时也会调用接口 更新配置 和 更新聊天室配置 更新传入的配置
    - 如果连接已断开, 会自动建立连接
- 发送本地消息
    - 消息对象 增加一个字段 `isLocal` 表示是否是本地消息

## 2.1.0 (2016-03-24)

**变更**

- 使用 NIM.getInstance() 来 初始化 SDK
    - 此接口为单例模式, 对于同一个账号, 永远返回同一份实例, 即只有第一次调用会初始化一个实例, 后续调用此接口会直接返回初始化过的实例.
    - 增加 更新配置 的接口
- 使用 Chatroom.getInstance() 来 初始化聊天室
    - 此接口为单例模式, 对于同一个账号的同一个聊天室, 永远返回同一份实例, 即只有第一次调用会初始化一个实例, 后续调用此接口会直接返回初始化过的实例.
    - 增加更新聊天室配置的接口
- 聊天室回调 `onmsg` 变更为 `onmsgs`, 传入的消息对象变更为消息数组
- 去掉初始化参数 dataSource

**新增**

- 已读回执
- 聊天室支持文件等各种类型的消息

## 2.0.2 (2016-03-01)

**变更**

session 增加 `lastTextMsg` 等字段

## 2.0.1 (2016-02-19)

**变更**

- 聊天室成员类型 中的普通成员变更 "normal" -> "common"
- 设置聊天室普通成员 名字变更 markChatroomMemberLevel -> markChatroomCommonMember
- 设置聊天室普通成员 对应的 通知类型 变更
    - "addLevel" -> "addCommon"
    - "removeLevel" -> "removeCommon"
- 聊天室被关闭的时候, 聊天室成员收到的被踢通知的 `reason` 的值变更 "chatroomDismiss" -> "chatroomClosed"

## 2.0.0 (2016-01-28)

**变更**

- 发送自定义系统通知 返回拼装好的对象
- 去掉初始化参数 dataSource.getMsg 和 dataSource.getSysMsg, 由 SDK 来做消息和系统通知的过滤

**新增**

- 修改图片下载的名字
- 取消文件上传
- 将音频 url 转为 mp3
- 语音转文字

- 以下四个接口加了参数 `asc`, 默认 `false` 表示返回的消息按时间逆序排序; 传 `true` 表示按时间正序排序
    - 获取云端历史记录
    - 获取本地历史记录
    - 获取包含关键词的本地历史记录
- 群通知消息, 如果 `attach` 有 `account` 或者 `accounts` 字段, 那么 `attach` 的字段 `users` 包含这些账号对应的用户名片
- 聊天室

## 1.8.0 (2016-01-18)

**修复**

- 音频对象加了一个字段 `mp3Url`
- 修复更新好友多端同步通知
- 修复离线自定义系统通知引起的存储问题

## 1.7.2 (2015-12-30)

**修复**

- 多 Tab 页可以使用数据库了
- 消息多端同步，未读数计数问题修复

## 1.7.1 (2015-12-14)

**修复**

- IE8 下不打开控制台，直接使用 console 会报错，已修复

## 1.7.0 (2015-12-02)

**变更**

- 断线自动重连
    - SDK 加入了断线自动的逻辑, 调整了 `onerror` 和 `ondisconnect` 的使用方法
    - 请参考开发手册中的 初始化 SDK 的关于 `onwillreconnect` 和 `ondisconnect` 的描述

- 同步
    - 所有同步接口均为增量同步, 请查看开发手册中的
        - 用户关系托管 中的初始化参数描述
        - 好友关系托管 中的初始化参数描述
        - 用户名片托管 中的初始化参数描述
        - 群组 中的初始化参数描述
        - 会话 中的初始化参数描述
        - 消息 中的初始化参数描述
        - 系统通知 中的初始化参数描述
    - 去掉同步我的名片控制开关 `syncMyInfo`

- 用户关系托管
    - 同步开关 `syncBlacklistAndMutelist` 名字变更为 `syncRelations`
    - 方法 `getBlacklistAndMutelist` 名字变更为 `getRelations`
    - `onblacklist` 和 `onmutelist` 收到的内容从账号数组变为对象数组, 包含以下几个字段
        - `account`, 账号
        - `updateTime`, 更新时间
        - `reocrd`, 拼装好的对象
        - 如果只关心账号, 那么可以将此对象数组转为账号数组
        ```
        var accounts = records.map(function(record) {
            return record.account;
        });
        ```
    - 加入黑名单/从黑名单移除、加入静音列表/从静音列表移除 以及对应的多端同步 `onsyncmarkinblacklist` 和 `onsyncmarkinmutelist`, 都加了字段 `record` 包含拼装好的对象

- 用户名片托管
    - 增加回调 `onupdatemyinfo`, 用于接收更新后的我的名片
    - 增加回调 `users`, 用于接收好友的用户名片
    - 增加回调 `onupdateuser`, 用于接收用户名片更新
    - 请参考开发手册中的 用户名片托管 的关于 `onupdatemyinfo`、`users` 和 `onupdateuser` 的描述

- 群组
    - 创建群成功时传入的对象变了, 除了群对象, 额外传了创建者的信息, 请参考开发手册中的创建群
    - 拉人入群后, 所有群成员会收到一条类型为 `'addTeamMembers'` 的群通知消息。此类群通知消息的 `attach` 有一个字段 `members` 的值为被拉的群成员列表
    - 如果接受邀请, 那么该群的所有群成员会收到一条类型为 `'acceptTeamInvite'` 的群通知消息, 此类群通知消息的 `attach` 有一个字段 `members` 的值为接收入群邀请的群成员列表
    - 如果通过申请, 那么该群的所有群成员会收到一条类型为 `'passTeamApply'` 的群通知消息, 此类群通知消息的 `attach` 有一个字段 `members` 的值为被通过申请的群成员列表
    - 添加群管理员后, 所有群成员会收到一条类型为 `'addTeamManagers'` 的群通知消息。此类群通知消息的 `attach` 有一个字段 `members` 的值为被加为管理员的群成员列表
    - 移除群管理员后, 所有群成员会收到一条类型为 `'removeTeamManagers'` 的群通知消息。此类群通知消息的 `attach` 有一个字段 `members` 的值为被移除管理员的群成员列表
    - 转让群后, 所有群成员会收到一条类型为 `'transferTeam'` 的群通知消息。此类群通知消息的 `attach` 有一个字段 `members` 的值为包含新旧群主的群成员列表

- 会话
    - 完善了会话机制, 请参考开发手册中的 会话
        - 新的回调 `onupdatesession` 用于接收被更新的会话
        - 增加未读数管理机制
        - 新的方法
            - 设置当前会话
            - 重置会话未读数
    - 增加了几个新字段, 请参考开发手册中的 会话对象

- 消息
    - `onroamingmsgs` 和 `onofflinemsgs` 这两个回调为一个会话一个回调, 接收的内容从消息数组变更为一个对象, 包含以下几个字段
        - `session`, 会话
        - `scene`, 场景
        - `to`, 聊天对象
        - `msgs`, 消息数组, 按照时间正序排列
    - 消息对象的字段 `idServer` 类型变更为 `String`, 影响方法 `getHistoryMsgs` 和 `searchHistoryMsgs`
    - 消息增加了几个新字段, 请参考开发手册中的 消息对象
    - 所有发送消息的接口均返回一个拼装好的消息对象而不是消息的 `idClient`
        - 发送文本消息
        - 发送文件消息
            - 如果需要上传文件, 那么在 `beforesend` 收到要发送的消息对象而不是消息的 `idClient`
        - 发送 `Geo` 消息
        - 发送 `tip` 消息
        - 发送自定义消息
    - 发送消息的回调返回的也是一个拼装好的消息对象
    - 本地历史记录

- 系统通知
    - 完善了系统通知机制, 请参考开发手册中的 系统通知
        - 增加回调 `onupdatesysmsg` 用于接收被更新的系统通知对象
        - 增加未读数管理机制
        - 收到系统通知后需要调用标记系统通知为已读状态来将系统通知标记为已读状态
    - 增加了几个新字段, 请参考开发手册中的 系统通知对象
    - 所有拒绝、通过系统通知的接口加一个参数: 对应系统通知的 `idServer`
        - passFriendApply
        - rejectFriendApply
        - acceptTeamInvite
        - rejectTeamInvite
        - passTeamApply
        - rejectTeamApply
    - 新的方法
        - 更新本地系统通知

**新增**

- 数据源, 请查看开发手册中的 数据源

- 数据库支持, 请查看开发手册中的 数据库兼容性

- 图片操作, 请参考开发手册中的 图片操作

**优化**

- `onupdateteammember` 接收到的对象只包含被更新的字段, 可以使用 `NIM.util.merge` 来合并数据
- `onsyncfriendaction(updateFriend)` 和 `updateFriend` 接收到的对象只包含被更新的字段, 可以使用 `NIM.util.merge` 来合并数据

- 日志样式优化

## 1.5.0 (2015-09-30)

**变更**

- 无

**新增**

- 用户名片托管, 请参考开发手册中的
    - 初始化 SDK 的关于 `syncMyInfo` 和 `onmyinfo` 的描述
    - 用户名片托管
- 静音群, 请参考开发手册中的
    - 修改自己的群属性

**优化**

- 无

## 1.4.0 (2015-08-31)

**变更**

- 去掉 `onkicked` 回调，如果被踢，在收到的 `ondisconnect` 回调里会包含被踢的相关信息
- 跟群相关名字变更，包括一系列的操作及对应的群通知消息类型和系统通知类型
    - 拉人入群从 `'addMembers'` 变更为 `'addTeamMembers'`，对应的群通知消息的类型也从 `'addMembers'` 变更为 `'addTeamMembers'`。
    - 踢人出群从 `'removeMembers'` 变更为 `'removeTeamMembers'`，对应的群通知消息的类型也从 `'removeMembers'` 变更为 `'removeTeamMembers'`。
    - 接受入群邀请从 `'acceptInvite'` 变更为 `'acceptTeamInvite'`，对应的群通知消息的类型也从 `'acceptInvite'` 变更为 `'acceptTeamInvite'`。
    - 拒绝入群邀请从 `'rejectInvite'` 变更为 `'rejectTeamInvite'`，对应的系统通知类型也从 `'rejectInvite'` 变更为 `'rejectTeamInvite'`。
    - 通过入群申请从 `'passApply'` 变更为 `'passTeamApply'`，对应的群通知消息的类型也从 `'passApply'` 变更为 `'passTeamApply'`。
    - 拒绝入群申请从 `'rejectApply'` 变更为 `'rejectTeamApply'`，对应的系统通知类型也从 `'rejectApply'` 变更为 `'rejectTeamApply'`。
    - 添加群管理员从 `'addManagers'` 变更为 `'addTeamManagers'`，对应的群通知消息的类型也从 `'addManagers'` 变更为 `'addTeamManagers'`。
    - 移除群管理员从 `'removeManagers'` 变更为 `'removeTeamManagers'`，对应的群通知消息的类型也从 `'removeManagers'` 变更为 `'removeTeamManagers'`。
    - 建议直接全局查找并替换相关名字。
- 当前登录用户在其它端创建群后的回调，名字从 `oncreateteam` 变更为 `onsynccreateteam`，另外添加了一系列其他的多端同步回调，请参考下面的文档

**新增**

- 用户关系托管
    - 请参考开发手册中的
        - 初始化 SDK 的关于 `syncBlacklistAndMutelist`、`onblacklist`、`onmutelist`、`onsyncmarkinblacklist` 和 `onsyncmarkinmutelist` 的描述
        - 用户关系托管
    - 消息对象加了一个字段 `isMuted` 来标明该消息在接收方是否应该被静音
- 好友关系托管, 请参考开发手册中的
    - 初始化 SDK 的关于 `syncFriends`、`onfriends` 和 `onsyncfriendaction` 的描述
    - 好友关系托管
    - 系统通知类型 新增了与好友相关的类型
- 会话列表, 请参考开发手册中的
    - 初始化 SDK 的关于 `syncSessions` 和 `onsessions` 的描述
    - 获取会话列表
    - 删除会话
    - 批量删除会话
- 标记消息已读, 请参考开发手册中的
    - 初始化 SDK 的标记消息已读部分

**优化**

- 无

## 1.3.0 (2015-07-31)

**变更**

- 不支持断线自动重连，您可以手动重连，请参考
    - 开发手册中的初始化 SDK 的 `ondisconnect` 回调。
- 通过入群申请的参数 `options.account` 变更为 `options.from`，请参考开发手册中的
    - 通过入群申请
- 拒绝入群申请的参数 `options.account` 变更为 `options.from`，请参考开发手册中的
    - 拒绝入群申请

**新增**

- 日志功能

**优化**

- IE8/IE9，上传文件超过 100M 时的错误提示。

::: details 单击展开 8.9.104 (2022-11-08) ~ 8.9.132 (2024-09-10) 版本 NIM SDK 的更新日志。

⭐<span style="font-size:16px;"><b><span id="8.9.132 - 2024-09-10">8.9.132 (2024-09-10)</span></b></span>

修复已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.131 - 2024-09-03">8.9.131 (2024-09-03)</span></b></span>

修复空文件上传偶现问题。

⭐<span style="font-size:16px;"><b><span id="8.9.130 - 2024-08-08">8.9.130 (2024-08-08)</span></b></span>

优化连接问题。

⭐<span style="font-size:16px;"><b><span id="8.9.129 - 2024-07-30">8.9.129 (2024-07-30)</span></b></span>

内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.128 - 2024-05-24">8.9.128 (2024-05-24)</span></b></span>

优化多媒体消息文件域名配置规则。

⭐<span style="font-size:16px;"><b><span id="8.9.127 - 2024-05-21">8.9.127 (2024-05-21)</span></b></span>

- 新增 `getLoginStatus(): number` 方法，用于获取当前的登录状态。

    - **0**：未登录（包含初始状态和登录失败的状态）
    - **1**：已登录
    - **2**：登录中
    - **3**：处于重连退避间隔中（开发者无需重新调用登录接口，SDK 会自动重连）

- 其他内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.126 - 2024-04-24">8.9.126 (2024-04-24)</span></b></span>

内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.125 - 2024-04-11">8.9.125 (2024-04-11)</span></b></span>

内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.124 - 2024-02-27">8.9.124 (2024-02-27)</span></b></span>

支持初始化时配置重连的时间间隔。

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| `NIMGetInstanceOptions` | 新增入参函数 `reconnectDelayProvider?: (delay: number) => number`，用于配置和返回重连的时间间隔。 |

⭐<span style="font-size:16px;"><b><span id="8.9.123 - 2024-02-23">8.9.123 (2024-02-23)</span></b></span>

**新增特性**

- 支持根据 Thread 根消息查询本地 Thread 子消息。
- 支持根据 Thread 根消息查询本地 Thread 子消息的数量。

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`subMessages`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#subMessages) | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息。 |
| [`subMessagesCount`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#subMessagesCount) | 新增接口，用于根据 Thread 根消息查询本地 Thread 子消息的数量。 |

⭐<span style="font-size:16px;"><b><span id="8.9.122 - 2024-02-02">8.9.122 (2024-02-02)</span></b></span>

**新增特性**

支持在群免打扰状态下设置特别关注的群成员（包括高级群和超大群）。在开启群免打扰时，仍能收到特别关注的成员发送的消息提醒。

**API 变更**

方法/类/枚举 | 说明
---- | ----
`TeamInterface.addTeamMembersFollow` | 添加高级群中需要特别关注的成员列表。
`TeamInterface.removeTeamMembersFollow` | 移除高级群中需要特别关注的成员列表。
`NIMTeamMember` | 群成员属性中新增 `followAccountIds`，表示特别关注的群成员列表。
`SuperTeamInterface.addTeamMembersFollow` | 添加超大群中需要特别关注的成员列表。
`SuperTeamInterface.removeTeamMembersFollow` | 移除超大群中需要特别关注的成员列表。
`NIMSuperTeamMember` | 超大群成员属性中新增 `followAccountIds`，表示特别关注的群成员列表。

⭐<span style="font-size:16px;"><b><span id="8.9.121 - 2023-12-15">8.9.121 (2023-12-15)</span></b></span>

内部优化。

⭐<span style="font-size:16px;"><b><span id="8.9.120 - 2023-11-22">8.9.120 (2023-11-22)</span></b></span>

优化超大群系统通知逻辑。

⭐<span style="font-size:16px;"><b><span id="8.9.119 - 2023-11-06">8.9.119 (2023-11-06)</span></b></span>

**API 新增**

该版本新增以下 API，均需在开启本地数据库的前提下使用：

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`getFriendsFromDB`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#getFriendsFromDB) | 从数据库中批量获取好友信息。 |
| [`getUsersFromDB`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#getUsersFromDB) | 从数据库中批量获取用户名片。 |
| [`getTeamMembersFromDB`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamMembersFromDB) | 从数据库中批量获取群成员信息。
| [`getTeamsFromDB`](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamsFromDB) | 从数据库中批量获取群信息。

**优化**

- 优化重复消息的处理逻辑。
- 优化重连逻辑。

⭐<span style="font-size:16px;"><b><span id="8.9.118 - 2023-10-25">8.9.118 (2023-10-25)</span></b></span>

- 发送文件消息时，文件上传完成后 `uploadprogress` 回调次数优化。
- SDK 初始化同步时中断，重新连接并同步后 `onsessions` 回调次数优化。
- 修复开启数据库后，在断开连接期间收到新消息，内存中该会话未更新的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.116 - 2023-09-05">8.9.116 (2023-09-05)</span></b></span>

- 修复调用 `getLocalSessions` 接口获取的会话中包含已被删除的会话的问题。
- 修复 IM 连接失败后，未触发 `ondisconnect` 回调的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.115 - 2023-08-04">8.9.115 (2023-08-04)</span></b></span>

- 支持 safari 10 以上版本开启数据库功能。
- 优化 NOS 上传图片的内部逻辑。
- 修复撤回群消息后，实际群成员仍能看到撤回消息的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.114 - 2023-07-26">8.9.114 (2023-07-26)</span></b></span>

- 修改 `getLocalSessions` 接口查询逻辑，改为仅从内存中获取本地会话。
- 修复未读数异常问题。
- 修复自定义断网后收到的消息回包字段丢失问题。
- 修复严格模式下报错的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.113 - 2023-07-07">8.9.113 (2023-07-07)</span></b></span>

发送自定义消息的回调（`oncustomsysmsg`）中新增 `idClient` （客户端消息 ID）字段。

⭐<span style="font-size:16px;"><b><span id="8.9.112 - 2023-06-26">8.9.112 (2023-06-26)</span></b></span>

新增删除指定时间段的本地历史消息的能力，具体请参考 [删除指定时间段的历史消息](https://doc.yunxin.163.com/messaging/guide/jg5MjQ4MTM?platform=web#删除指定时间段的历史消息)。

⭐<span style="font-size:16px;"><b><span id="8.9.111 - 2023-05-25">8.9.111 (2023-05-25)</span></b></span>

修复 SDK 同步错误而导致收不到消息的问题。

⭐<span style="font-size:16px;"><b><span id="8.9.107 - 2023-02-07">8.9.107 (2023-02-07)</span></b></span>

该版本修复了如下问题：
- 修复多端登录场景下，其中一端通过 `setCurrSession` 接口清除置顶会话未读数后，另一端表现异常的问题。
- 修复 `onClearServerHistoryMsgs` 回调中没有 `ext` 字段信息的问题。
- 修复单向删除消息后未读数未变更的问题。
- 修复 `clearServerHistoryMsgsWithSync` 接口缺少 `isDeleteRoam` 入参（是否删除漫游消息，默认为 true）的问题。
- 修复 `onSessions` 回调中，出现无消息空会话的问题。
- 修复开启数据库的场景下，发送消息成功后，服务器未返回 `callback` 字段的问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.106 - 2022-12-29">8.9.106 (2022-12-29)</span></b></span>

该版本修复了如下问题：
- 修复 `getCollects` 接口 `lastId`、`reverse` 入参设置无效的问题。
- 修复支付宝环境上传引起的 `beginupload` 提前终止上传代码失效的问题。
- 修复登录时报 `getNosOriginUrl failed` 错误的异常。
- 修复 `getThreadMsgs` 接口 `endTime` 入参设置无效的问题。
- 修复连接中途就销毁后数据上报报错的问题。
- 修复 `updateSuperTeam` 接口的回调信息。
- 修复获取日志上报策略失败后未正确打印 error 的问题。
- 修复其他已知问题。

⭐<span style="font-size:16px;"><b><span id="8.9.104 - 2022-11-08">8.9.104 (2022-11-08)</span></b></span>

该版本修复了如下问题：

- 修复文件消息失败后没有保留消息的客户端 ID (`idClient`) 的问题。
- 修复发送文件消息时上传文件失败后无任何回调触发的问题。
- 修复 NOS 上传文件失败后的重试逻辑问题。
- 修复聊天室登录触发 IM 的登录上报的问题。
- 修复其他已知问题。
:::