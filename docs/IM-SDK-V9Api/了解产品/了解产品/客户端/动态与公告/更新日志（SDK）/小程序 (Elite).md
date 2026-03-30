本文介绍网易云信即时通讯 IM SDK（简称 NIM SDK）稳定版适配小程序 v0.x.x 及以下版本的更新日志。有关开发版 v10.x.x，请参考《IM 即时通讯 V10》[Web/uni-app/小程序更新日志](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)。

## **近期重要更新**

- 从 v0.13.0 起，新增服务端会话服务功能模块。
- 从 v0.9.2 起，新增动态查询历史消息接口，网易云信提供智能选择云端、本地历史消息。

----
## <span id="0.19.0 - 2024-08-16">0.19.0 (2024-08-16)</span>

分片上传新增备用域名。

## <span id="0.18.0 - 2024-07-18">0.18.0 (2024-07-18)</span>

- 上传支持多个备份域名。
- SDK 默认上传地址将由 `wanproxy-web.127.net` 替换为 `wannos-web.127.net`。
- 其他内部优化。

:::note note
- 由于小程序上传地址变更，您需要新增小程序上传域名白名单配置，白名单配置中需要增加关于上传文件（uploadFile）的域名：
    - `https://fileup.chatnos.com`
    - `https://oss.chatnos.com`
- 原来使用的上传域名（`https://nos.netease.com`）也可以继续保留。
:::

## <span id="0.17.0 - 2023-12-26">0.17.0 (2023-12-26)</span>

优化未读数处理逻辑。

## <span id="0.16.0 - 2023-12-01">0.16.0 (2023-12-01)</span>

**API 新增**

API | 说明
---- | ----
[`getServerTime`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_MiscServiceInterface.MiscServiceInterface.html#getServerTime) | 获取服务器时间戳（毫秒）。用于校准消息时间信息。

**优化**

- 优化信令回调数据
- 优化群未读计数
- 优化小程序低版本兼容性
- 优化断网恢复后，会话未读计数逻辑

## <span id="0.15.0 - 2023-07-07">0.15.0 (2023-07-07)</span>

**新增特性**

- 圈组订阅机制支持自动订阅。开启自动订阅后，当用户登录到圈组服务器，无需手动订阅服务器或频道，进入服务器或频道时即可收到消息、事件和系统通知，退出时则自动取消订阅。具体请参考 [圈组订阅机制](https://doc.yunxin.163.com/messaging-enhanced/guide/jc0Mzg1NDA?platform=web)。

- 新增 `updateUserInfo` 回调事件。当收到其他用户发来的消息时，如果该用户资料中有更新，或之前从未同步过该用户资料，SDK 会触发该回调并返回该用户的最新资料。

**优化**

支持在用户资料、群组、聊天室、圈组功能中设置用户昵称为空。

**修复**

本次版本修复以下问题：

- 当批量将会话消息未读数清零(标记已读)时，会话数量过大导致报错。
- 发送视频/音频/图片/文件消息时，url 地址未解码导致返回消息体中的 url 无法正常打开。
- 置顶会话获取不完整。

**API 变更**

API | 说明
---- | ----
`QChatOtherOptions.qchatChannelConfig.autoSubscribe` | 新增圈组自动订阅开启/关闭参数。
`updateUserInfo` | 新增其他用户资料更新回调事件。

## <span id="0.14.0 - 2023-05-30">0.14.0 (2023-05-30)</span>

**优化**

使 S3 文件上传过程中触发相关回调，并统一以下回调的回参表现。
- `onUploadProgress`：上传进度回调
- `onUploadStart`：上传开始回调
- `onUploadDone`：上传完成的回调

**修复**

- 修复撤回已读消息以及删除未读消息后，未读数显示异常的问题。
- 修复当发送未传 `pushInfo` 的消息时，转发该消息会失败的问题。
- 修复调用 `disconnect` 接口后报错的问题。
- 修复微信小程序断网重连报错的问题。
- 修复微信小程序实际重连次数与初始化设置的 `reconnectionAttempts` 次数不一致的问题。

**API 变更**

调用获取圈组快捷评论接口（`getQuickComments`）返回的数据中新增快捷评论的创建时间，即 `QChatQuickCommentDetail` 中新增评论创建时间字段（`createTime`）。

## <span id="0.13.0 - 2023-04-11">0.13.0 (2023-04-11)</span>

**新增特性**

- 新增服务端会话服务功能模块，与本地最近会话不同，其提供了新的会话列表获取服务，需要从云端拉取，不支持同步到本地最近会话列表，具体请参考 [服务端会话服务](https://doc.yunxin.163.com/messaging-enhanced/guide/DYzMjcxODk?platform=web)。
- 新增获取内存中的所有会话的能力，具体请参考 [最近会话](https://doc.yunxin.163.com/messaging-enhanced/guide/TgxNjczNzk?platform=web#获取本地会话)。
- 新增 [myTeamMembers](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#myTeamMembers) 和 [mySuperTeamMembers](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#mySuperTeamMembers) 事件，在初始化可获取个人在所有群组（高级群和超大群）中的成员信息。
- 新增 [msgReceipts](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.IMEventInterface.html#msgReceipts) 事件，查看某消息是否已读。

**API 新增**

| <div style="width:50px">API</div> | API 说明 |
| --- | --- |
| [getAllSessions](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_SessionServiceInterface.SessionServiceInterface.html#getAllSessions) | 获取内存中的所有会话
| [queryCloudSessionList](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_CloudSessionServiceInterface.CloudSessionServiceInterface.html#queryCloudSessionList) | 查询服务端会话列表
| [queryCloudSession](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_CloudSessionServiceInterface.CloudSessionServiceInterface.html#queryCloudSession) | 查询指定服务端会话的详细信息
| [updateCloudSession](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_CloudSessionServiceInterface.CloudSessionServiceInterface.html#updateCloudSession) | 更新服务端会话的扩展信息
| [deleteCloudSessionList](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_CloudSessionServiceInterface.CloudSessionServiceInterface.html#deleteCloudSessionList) | 删除服务端会话列表

**优化**

优化内部拉黑后的消息重发逻辑。

**问题修复**

- 修复 uni-app 重复监听套接字（socket）事件的问题。
- 修复调用 `destroy` 后，可能销毁失败的问题。
- 修复小程序环境问题。
- 修复其他已知问题。

## <span id="0.12.1 - 2023-02-16">0.12.1 (2023-02-16)</span>

**新增特性**

新增信令（signaling）模块。具体接口请参考 [`SignalingServiceInterface`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/SignalingServiceInterface.SignalingServiceInterface-1.html)。

**问题修复**

修复支付宝小程序的长连接的若干问题。

## <span id="0.12.0 - 2023-02-10">0.12.0 (2023-02-10)</span>

**API 变更**

| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`NIMEModuleParamCloudStorageConfig`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/modules/CloudStorageServiceInterface.html#NIMEModuleParamCloudStorageConfig) | 新增 `isNeedToGetUploadPolicyFromServer` 参数，此参数用来控制是否通过服务器获取上传策略，默认为 true。<note type=notice>只有当 `isNeedToGetUploadPolicyFromServer` 为 false 时，`otherOptions` 的 [`ServerConfig`](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/modules/NIMInterface.html#ServerConfig) 的 CDN 配置才生效。</note>

**问题修复**

修复已知问题。

## <span id="0.11.0 - 2022-12-27">0.11.0 (2022-12-27)</span>

**优化改进**

**被拉黑方** 向 **拉黑方** 发出的消息体的服务端 ID 逻辑优化。

**问题修复**

- 修复当会话数量超过 10 个时，调用 `resetAllSessionsUnreadCount` 方法异常报错的问题。

- 修复其他已知问题。

## <span id="0.9.2 - 2022-10-27">0.9.2 (2022-10-27)</span>

**新增特性**

v0.9.3 的聊天室模块，新增根据标签（Tags）查询聊天室历史消息的功能，具体请参考 <a href="https://doc.yunxin.163.com/messaging-enhanced/guide/DkwNDM5MTU?platform=web#根据标签查询历史消息" target="_blank">根据标签查询历史消息</a>。

**新增事件**

聊天室模块新增 <a href="https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/ChatroomInterface.ChatroomEventInterface.html#tagsUpdate" target="_blank">`tagsUpdate`</a> 事件，回调包含变更后的标签信息。

**API 新增**

| <div style="width:150px">API</div> | <div style="width:120px">API 说明</div> |
| --- | --- |
| <a href="https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/ChatroomMsgServiceInterface.ChatroomMsgServiceInterface-1.html#getHistoryMsgsByTags" target="_blank">`getHistoryMsgsByTags`</a> | 通过聊天室标签（可多个）来检索聊天室历史消息 |

## <span id="0.9.0 - 2022-8-29">0.8.5 (2022-8-29)</span>

- IM 会话中撤回消息后重置未读数更新: 若会话的未读数已经为 0，不需要触发协议，也不更新会话。
- 修正更新会话 `lastmsg` 的条件，补充处理一种情况：本地发送消息时，本地时间故意调的比远端服务器的大，导致收到消息回包后无法触发 `session.lastMsg` 的 `status` 从 sending 到 sent 状态的更新。
- 调用 `resetSessionUnreadCount` 时 本地的时间比服务器的小上几秒钟，导致本地时间不可信，所以修复为使用 `lastMsg.time` 或者 `session.updateTime`。
- 修复发送文件消息时磁盘删除对应选中资源后没有回调。
- 修复其他已知问题。

## <span id="0.7.1 - 2022-7-25">0.7.1 (2022-7-29)</span>

**新增特性**

新增最近会话置顶功能。

**新增 API**
| <div style="width:150px">API</div> | API 说明 |
| --- | --- |
| [`addStickTopSession`](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/interfaces/src_SessionServiceInterface.SessionServiceInterface.html#addStickTopSession) | 添加云端置顶的会话 |
| [`deleteStickTopSession`](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/interfaces/src_SessionServiceInterface.SessionServiceInterface.html#deleteStickTopSession) | 取消云端置顶的会话 |
| [`updateStickTopSession`](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/interfaces/src_SessionServiceInterface.SessionServiceInterface.html#updateStickTopSession) | 更新云端置顶的会话 |

## <span id="0.6.4 - 2022-7-20">0.6.4 (2022-7-20)</span>

[NIM Web SDK](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/NIM/index.html)，[聊天室 Web SDK](https://doc.yunxin.163.com/messaging-enhanced/references/web/typedoc/Latest/zh/Chatroom/index.html) 新增了 `setOptions` 方法，您可以调用此方法更新初始化传入的参数，在初始化完成后使用。

## <span id="0.6.1 - 2022-6-2">0.6.1 (2022-6-2)</span>

优化 ESM 模块的 tree-shaking。

## 0.5.1 (2022-04-22)

修复 `npm install` 失败的问题。该问题由 `package.json` 里的 `denpencies` 存在无法安装的依赖而导致。

## 0.5.0 (2022-04-22)

::: note notice
如您安装了 0.5.0 版本的 SDK，强烈建议您将其升级至 0.5.1 版本。0.5.1 版本修复了 0.5.0 版本中存在的 `npm install` 失败的问题。
:::

- 新增聊天室队列服务。聊天室队列指聊天室（房间）中由多个元素（key-value 键值对）构成的队列，主要应用于直播连麦场景。功能详情请参考 [聊天室队列服务](https://doc.yunxin.163.com/messaging-enhanced/guide/jEzNDIyNjY?platform=web)。
- SDK 增加对微信小程序和支付宝小程序设配。

## 0.4.2

- **优化** : 优化了 TS 定义。
- **修复** : 修复了 nim 发送消息的 needPushNick 参数设置为 true，不能真的让移动端收到推送里的昵称的问题。

连接相关的优化或修复有：

- **优化** : 缩短了 NIM SDK 对于 lbs 请求的超时时间的默认值，降至 10 s。
- **优化** : 优化了 nim，chatroom 三个 SDK 的重连表现。SDK 目前针对初始化的连接失败都会断开并且抛出异常，重连阶段尝试连接失败，只会记录日志而不会向上抛出异常。

## 0.4.0

- **功能优化** : 优化建立连接的一些表现，如允许传入多个 lbsUrls，遍历找到一个可用值。

## 0.3.2

- fix: 修复调用 resetAllSessionsUnreadCount api 无响应的问题。

## 0.3.1-beta1

- 增加对微信小程序、支付宝小程序等环境的适配。

<!-- * feature: 增加对微信小程序，支付宝小程序，百度小程序，今日头条小程序等环境的适配 -->
- 变更 crypto-js 库的引入方式。

## 0.3.0

- feature: 追加 deleteSelfMsgs 单向删除接口。
- feature: 推送插件以及适配代码，推送功能的使用参考 [uni-app 离线推送](https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp)。
- chore: uni-app 平台适配优化，能够支持编译去支付宝小程序，微信小程序
- chore: 优化撤回消息逻辑，使撤回消息后 session 的 unread 数等参数能得到正确的更新。
- chore: 聊天室追加鉴权方式
- fix: 修复登出协议的一些问题

## 0.2.0

- feature: 追加 superTeam 超级群逻辑。
- fix: 修复同步阶段错误的把 syncRelations 当作是同步回包的缺陷。
- fix: 修复同步包超时问题。
- fix: 修复被拉黑的情况下消息漫游下来的状态显示成功。
- chore: 优化，追加 esm/index 供开发者上层使用 esm 打包的模块，便于做 tree shaking 节省体积。
- chore: 使用 lodash 替代内部一些函数，打包体积增大 30kb。

## 0.1.1

- 初始化参数支持传入 lbsUrls 和 linkUrl 来指定默认的连接地址。
- 修复 NIM 建立连接没有区别出自动重连的情况。

## 0.1.0

初版上线，支持好友，用户，群，消息，会话，透传协议，系统消息，聊天室能力。