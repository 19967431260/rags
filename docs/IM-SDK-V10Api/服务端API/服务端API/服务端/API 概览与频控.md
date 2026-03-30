本文罗列了网易云信即时通讯（NIM）的 10.x.x 系列 API 列表，以及各 API 的使用限制（频控）。10.x.x 系列大部分 API 都对应并兼容 [3.1.0 ~ 9.x.x](https://doc.yunxin.163.com/messaging/server-apis/zk4Mzg0MjE?platform=server) 系列 API（统称 V9 系列 API），对应关系也在下列表格中说明。

## 频控说明

<style>
table th:first-of-type {
    width: 20%;
}
</style>

超过网易云信 IM API 调用限制会返回 416 错误码，并触发一段时间的调用屏蔽。服务端 API 频控分两类：

**单次类 API 频控**：
- 用户&关系：用户账号、名片、好友关系、静音、黑名单等
- 会话：会话、会话分组、未读数等，存储模式区分云端会话和本地会话
- 消息：发送消息、查询消息、系统通知等（例外情况：**批量发送单聊消息** 和 **批量发送自定义系统通知** 至 [批量发送消息](#批量发送消息) 分类调整。**发送广播消息** 和 **发送聊天室全服广播** 至 [广播消息](#广播消息) 分类调整，删除和查询广播消息 API 仍在 [消息](#消息功能) 分类中调整。）
- 群组：创建群、获取群列表、管理群成员等
- 聊天室：聊天室地址、信息、用户管理、队列等
- 圈组：创建服务器、获取频道列表、管理身份组等
- 其他：文本翻译等

**批量类 API 频控**：
- 批量发送消息：批量发送单聊消息、批量发送自定义系统通知
- 发送广播消息：发送广播消息、发送聊天室全服广播

<a id="throttling"></a>

## 频控限制

IM 各套餐包下不同 **频控类别** 的 API 频控限制情况不同，具体限值需要参考对应的套餐包。各套餐详情请参考 [计费概述](https://doc.yunxin.163.com/messaging2/concept/DczNjI1ODM?platform=client)。

10.x.x 系列 API 频控均遵从以下调用频率限制：

:::::: div custom-tabs
::: tab 单次类 API 频控
| 套餐版本 | 单个 API 的频控默认值 | 可配置最高值 | 增值费用(国内) | 增值费用(海外) |
| :--- | :---- | :---- | :---- | :---- |
| **2024 标准版** | 100/s | 不可调整 | - | - |
| **2024 高级版** | 100/s | 5000/s | 每超 100 功能费+400 元/月 | 每超 100 功能费+600 元/月 |
| **2024 旗舰版** | 500/s | 10000/s | 每超 100 功能费+300 元/月 | 每超 100 功能费+500 元/月 |
| **2024 专属版** | 5000/s | 50000/s | 每超 100 功能费+500 元/月 | 每超 100 功能费+800 元/月 |
:::
::: tab 批量类 API 频控(批量发送消息)

| 套餐版本 | 单个 API 的频控默认值 | 可配置最高值 | 增值费用(国内) | 增值费用(海外) |
| :--- | :---- | :---- | :---- | :---- |
| **2024 标准版** | 120/min | 不可调整 | - | - |
| **2024 高级版** | 120/min | 2000/min | 每超 100 功能费+1000 元/月 | 每超 10 功能费+1000 元/月 |
| **2024 旗舰版** | 200/min | 5000/min | 每超 100 功能费+800 元/月 | 每超 10 功能费+800 元/月 |
| **2024 专属版** | 2000/min | 10000/min | 每超 100 功能费+300 元/月 | 每超 10 功能费+300 元/月 |

:::
::: tab 批量类 API 频控(广播消息)

| 套餐版本 | 单个 API 的频控默认值 | 可配置最高值 | 增值费用(国内) | 增值费用(海外) |
| :--- | :---- | :---- | :---- | :---- |
| **2024 标准版** | 不支持 | 不支持 | - | - |
| **2024 高级版** | 10/min | 1000/min | 每超 10 功能费+800 元/月 | 每超 10 功能费+1000 元/月 |
| **2024 旗舰版** | 50/min | 2000/min | 每超 10 功能费+500 元/月 | 每超 10 功能费+800 元/月 |
| **2024 专属版** | 1000/min | 5000/min | 每超 10 功能费+200 元/月 | 每超 10 功能费+300 元/月 |
:::
::::::

若根据业务需要调整部分 API 的频控，可在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，参考下文 [自行调整](#modify) API 频控，或通过官网首页右侧的联系方式联系网易云信商务经理进行调整。

## 用户&关系

包含用户账号、用户名片、好友关系、用户在线状态事件订阅、静音以及黑名单等用户管理相关的单次类 API。

API 调用频控限制，请参考上文 [频控限制](#throttling)。

### IM 账号管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [注册 IM 账号](https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server) | `POST https://open.yunxinapi.com/im/v2/accounts` | [注册 IM 账号](https://doc.yunxin.163.com/messaging/server-apis/DQ3Nzk1MTY?platform=server)
| [更新账号属性](https://doc.yunxin.163.com/messaging2/server-apis/TgwNTIyODk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/accounts/{account_id}` | [账号功能模块禁言](https://doc.yunxin.163.com/messaging/server-apis/DU5NDM5MjQ?platform=server)
| [刷新 Token](https://doc.yunxin.163.com/messaging2/server-apis/DUwODIwMTg?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/accounts/{account_id}/actions/refresh_token` | [刷新 Token](https://doc.yunxin.163.com/messaging/server-apis/DUxNDQ3NjA?platform=server)
| [封禁账号](https://doc.yunxin.163.com/messaging2/server-apis/TIxMzI4MjE?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/accounts/{account_id}/actions/disable` | [ 封禁账号](https://doc.yunxin.163.com/messaging/server-apis/TUzOTA4NTY?platform=server)
| [更新移动端推送配置](https://doc.yunxin.163.com/messaging2/server-apis/zU3OTk0MTg?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/accounts/{account_id}/actions/push_config` | [设置移动端是否需要推送(桌面端在线时)](https://doc.yunxin.163.com/messaging/server-apis/TcwMDU1MjQ?platform=server)
| [ 查询账号属性](https://doc.yunxin.163.com/messaging2/server-apis/Dc5NzYxMTA?platform=server) | `GET https://open.yunxinapi.com/im/v2/accounts/{account_id}` | -
| [批量查询账号信息](https://doc.yunxin.163.com/messaging2/server-apis/zQ2NjMyMTI?platform=server) | `GET https://open.yunxinapi.com/im/v2/accounts` | -
| [强制账号下线](https://doc.yunxin.163.com/messaging2/server-apis/TkwNjgzNTk?platform=server) | `POST https://open.yunxinapi.com/im/v2/accounts/{account_id}/actions/kick` | -

### 用户名片管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [更新用户名片](https://doc.yunxin.163.com/messaging2/server-apis/TA0NzYzNjk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/users/{account_id}` | [更新用户名片](https://doc.yunxin.163.com/messaging/server-apis/zI0NzYyMDQ?platform=server#更新用户名片)
| [查询用户名片](https://doc.yunxin.163.com/messaging2/server-apis/TIzNjEzNjc?platform=server) | `GET https://open.yunxinapi.com/im/v2/users/{account_id}` | -
| [批量查询用户名片](https://doc.yunxin.163.com/messaging2/server-apis/jI2NzY1ODI?platform=server) | `GET https://open.yunxinapi.com/im/v2/users` | [获取用户名片](https://doc.yunxin.163.com/messaging/server-apis/zI0NzYyMDQ?platform=server#获取用户名片)
| [批量查询用户在线状态](https://doc.yunxin.163.com/messaging2/server-apis/jU3NDkwNzY?platform=server) | `POST https://open.yunxinapi.com/im/v2/users/actions/onlineStatus` | [批量查询账号在线状态](https://doc.yunxin.163.com/messaging/server-apis/zYwNzA5ODk?platform=server)

### 好友管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [添加好友](https://doc.yunxin.163.com/messaging2/server-apis/TU5NDMzMjM?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/friends` | [添加好友](https://doc.yunxin.163.com/messaging/server-apis/DQ0MTY1NzI?platform=server#添加好友)
| [删除好友](https://doc.yunxin.163.com/messaging2/server-apis/Tk5NzI2ODQ?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/friends/{account_id}` | [删除好友关系](https://doc.yunxin.163.com/messaging/server-apis/DQ0MTY1NzI?platform=server#删除好友关系)
| [更新好友信息](https://doc.yunxin.163.com/messaging2/server-apis/TcxMjIxMTg?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/friends/{account_id}` | [更新好友相关信息](https://doc.yunxin.163.com/messaging/server-apis/DQ0MTY1NzI?platform=server#更新好友相关信息)
| [同意/拒绝添加好友](https://doc.yunxin.163.com/messaging2/server-apis/zAwMzgwNTU?platform=server) | `POST https://{endpoint}/im/v2.1/friends/actions/handle_friend_addition` | -
| [查询好友信息](https://doc.yunxin.163.com/messaging2/server-apis/DYwOTk2NjQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/friends/{account_id}` | [获取好友关系](https://doc.yunxin.163.com/messaging/server-apis/DQ0MTY1NzI?platform=server#获取好友关系)
| [分页查询好友信息](https://doc.yunxin.163.com/messaging2/server-apis/DUyNzA2OTc?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/friends` | [获取好友列表](https://doc.yunxin.163.com/messaging/server-apis/DQ0MTY1NzI?platform=server#获取好友列表)

### 静音管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [设置静音](https://doc.yunxin.163.com/messaging2/server-apis/DEzNTg0Nzg?platform=server) | `POST https://open.yunxinapi.com/im/v2/mute_contacts` | [设置黑名单/静音](https://doc.yunxin.163.com/messaging/server-apis/jEzNDQ4ODc?platform=server#设置黑名单静音)
| [解除静音](https://doc.yunxin.163.com/messaging2/server-apis/jk1MTE5Nzc?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/mute_contacts/{account_id}` | ^^
| [分页查询静音列表](https://doc.yunxin.163.com/messaging2/server-apis/Tg4MDk4NzA?platform=server) | `GET https://open.yunxinapi.com/im/v2/mute_contacts` | [查看指定用户的黑名单和静音列表](https://doc.yunxin.163.com/messaging/server-apis/jEzNDQ4ODc?platform=server#查看指定用户的黑名单和静音列表)

### 黑名单管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [列入黑名单](https://doc.yunxin.163.com/messaging2/server-apis/Dk0MTM1MTE?platform=server) | `POST https://open.yunxinapi.com/im/v2/block_contacts` | [设置黑名单/静音](https://doc.yunxin.163.com/messaging/server-apis/jEzNDQ4ODc?platform=server#设置黑名单静音)
| [移出黑名单](https://doc.yunxin.163.com/messaging2/server-apis/DE0MzMwNTI?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/block_contacts/{account_id}` | ^^
| [分页查询黑名单列表](https://doc.yunxin.163.com/messaging2/server-apis/TM0MjkzNTI?platform=server) | `GET https://open.yunxinapi.com/im/v2/block_contacts` | [查看指定用户的黑名单和静音列表](https://doc.yunxin.163.com/messaging/server-apis/jEzNDQ4ODc?platform=server#查看指定用户的黑名单和静音列表)

### 用户在线状态事件订阅

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [订阅用户在线状态事件](https://doc.yunxin.163.com/messaging2/server-apis/zI4NjY1NzA?platform=server) | `POST https://open.yunxinapi.com/im/v2/subscription/{account_id}` | [订阅在线状态事件](https://doc.yunxin.163.com/messaging/server-apis/jc5NDQwODk?platform=server#订阅在线状态事件)
| [取消用户在线状态事件的订阅](https://doc.yunxin.163.com/messaging2/server-apis/zUwMTY3Mzg?platform=server) | `POST https://open.yunxinapi.com/im/v2/subscription/{account_id}` | <li> [取消在线状态事件订阅](https://doc.yunxin.163.com/messaging/server-apis/jc5NDQwODk?platform=server#取消在线状态事件订阅) <li>[取消全部在线状态事件订阅](https://doc.yunxin.163.com/messaging/server-apis/jc5NDQwODk?platform=server#取消全部在线状态事件订阅)
[查询订阅的用户在线状态事件](https://doc.yunxin.163.com/messaging2/server-apis/jU4MjMwMTE?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/subscription/{account_id}` | [查询在线状态事件订阅关系](https://doc.yunxin.163.com/messaging/server-apis/jc5NDQwODk?platform=server#查询在线状态事件订阅关系)

## 消息功能

API 调用频控限制，请参考上文 [频控限制](#throttling)。

### 消息管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [发送消息](https://doc.yunxin.163.com/messaging2/server-apis/TEzMDQwODc?platform=server) | `POST https://open.yunxinapi.com/im/v2/conversations/{conversation_id}/messages` | [发送消息](https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server)
| [批量发送单聊消息](https://doc.yunxin.163.com/messaging2/server-apis/zgzOTE1MTI?platform=server) | `POST https://open.yunxinapi.com/im/v2/conversations/messages` | [批量发送单聊消息](https://doc.yunxin.163.com/messaging/server-apis/zI5OTk5MjA?platform=server)
| [更新消息](https://doc.yunxin.163.com/messaging2/server-apis/DA2ODM5NTU?platform=server) | `POST https://open.yunxinapi.com/im/v2/messages/actions/modify` | -
| [撤回/删除消息](https://doc.yunxin.163.com/messaging2/server-apis/jAwNTEzODQ?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/conversations/{conversation_id}/messages/{message_server_id}` | <li> [消息撤回](https://doc.yunxin.163.com/messaging/server-apis/zE1NjUyNDg?platform=server) <li>[删除单条消息](https://doc.yunxin.163.com/messaging/server-apis/Dg5OTcwMDk?platform=server)
| [删除会话中的漫游和历史消息](https://doc.yunxin.163.com/messaging2/server-apis/Tc1MTIyMDg?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/conversations/{conversation_id}/messages` | [删除漫游消息](https://doc.yunxin.163.com/messaging/server-apis/DY3MTM3MjQ?platform=server)
| [发送单聊已读回执](https://doc.yunxin.163.com/messaging2/server-apis/TQ0MzA4MTc?platform=server) | `POST https://open.yunxinapi.com/im/v2/messages/actions/p2p_read_receipt` | [发送单聊已读回执](https://doc.yunxin.163.com/messaging/server-apis/zcwMDk2Mzk?platform=server)
| [发送高级群已读回执](https://doc.yunxin.163.com/messaging2/server-apis/DIwMTU2ODA?platform=server) | `POST https://open.yunxinapi.com/im/v2/messages/actions/team_read_receipt` | [发送群聊消息回执](https://doc.yunxin.163.com/messaging/server-apis/DU4MjM3NTA?platform=server)
| [查询群消息已读未读详情](https://doc.yunxin.163.com/messaging2/server-apis/DIzNDY0ODk?platform=server) | `GET https://open.yunxinapi.com/im/v2/messages/actions/team_read_receipt` | [获取群消息已读未读详情](https://doc.yunxin.163.com/messaging/server-apis/zU0NDEzNzA?platform=server)
| [查询单条消息](https://doc.yunxin.163.com/messaging2/server-apis/DEzNTMwNTY?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/messages/{message_server_id}` | [单聊云端历史消息查询](https://doc.yunxin.163.com/messaging/server-apis/DE0MTk0OTY?platform=server#单聊云端历史消息查询)
| [搜索历史消息](https://doc.yunxin.163.com/messaging2/server-apis/zQ1MzM5NjM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/messages/actions/search_messages` | -
| [分页查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jcwNDA0Nzg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/messages` | <li> [单聊云端历史消息查询](https://doc.yunxin.163.com/messaging/server-apis/DE0MTk0OTY?platform=server#单聊云端历史消息查询)<li>[群聊云端历史消息查询](https://doc.yunxin.163.com/messaging/server-apis/DE0MTk0OTY?platform=server#群聊云端历史消息查询) <li>[超大群云端历史消息查询](https://doc.yunxin.163.com/messaging/server-apis/DY5MDA3NTU?platform=server)
| [发送聊天室消息](https://doc.yunxin.163.com/messaging2/server-apis/TAwMzc0NzE?platform=server) | `POST https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/messages` | [发送聊天室消息](https://doc.yunxin.163.com/messaging/server-apis/jY2MDg1MTk?platform=server)
| [批量发送聊天室消息](https://doc.yunxin.163.com/messaging2/server-apis/TA1NTM3NzM?platform=server) | `POST https://open.yunxinapi.com/im/v2/chatrooms/messages` | [批量发送聊天室消息](https://doc.yunxin.163.com/messaging/server-apis/jU3NzYzMTk?platform=server)
| [撤回/删除聊天室历史消息](https://doc.yunxin.163.com/messaging2/server-apis/Tk5MTE3MDY?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/messages/{message_client_id}` | <li> [撤回聊天室消息](https://doc.yunxin.163.com/messaging/server-apis/jM2MTE5NzE?platform=server) <li>[删除聊天室云端历史消息](https://doc.yunxin.163.com/messaging/server-apis/DE0MTk0OTY?platform=server#删除聊天室云端历史消息)
| [分页查询聊天室历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jQxNDU2MTM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/chatrooms/{room_id}/messages` | [聊天室云端历史消息查询](https://doc.yunxin.163.com/messaging/server-apis/DE0MTk0OTY?platform=server#聊天室云端历史消息查询)
| [根据消息 ID 查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jczMzMzMjg?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}/batch_messages` | -
| [查询 Thread 消息](https://doc.yunxin.163.com/messaging2/server-apis/zE0MzA0NzM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/messages/actions/thread_messages` | -
| [添加快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/zg1ODU4ODc?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/messages/actions/quick_comment` | -
| [删除快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/jU4MjMwMTE?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/messages/actions/quick_comment` | -
| [查询快捷评论](https://doc.yunxin.163.com/messaging2/server-apis/DYwMTA5MTI?platform=server) | `POST https://open.yunxinapi.com/im/v2/messages/actions/quick_comment` | -

### 广播消息管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [发送广播消息](https://doc.yunxin.163.com/messaging2/server-apis/zMzMzUxODQ?platform=server) | `POST https://open.yunxinapi.com/im/v2/broadcast_notification` | [发送广播消息](https://doc.yunxin.163.com/messaging/server-apis/Dg1NDYxNTM?platform=server#发送广播消息)
| [删除广播消息](https://doc.yunxin.163.com/messaging2/server-apis/jcwMzM0MDY?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/broadcast_notification/{broadcast_id}` | [删除单条广播消息](https://doc.yunxin.163.com/messaging/server-apis/Dg1NDYxNTM?platform=server#删除单条广播消息)
| [查询广播消息](https://doc.yunxin.163.com/messaging2/server-apis/DA0Njc5MzE?platform=server) | `GET https://open.yunxinapi.com/im/v2/broadcast_notification/{broadcast_id}` | [查询单条广播消息](https://doc.yunxin.163.com/messaging/server-apis/TcxNjU5Mzg?platform=server#查询单条广播消息)
| [分页查询广播消息](https://doc.yunxin.163.com/messaging2/server-apis/zgxNTU3Mjc?platform=server) | `GET https://open.yunxinapi.com/im/v2/broadcast_notification` | [批量查询广播消息](https://doc.yunxin.163.com/messaging/server-apis/TcxNjU5Mzg?platform=server#批量查询广播消息)
| [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging2/server-apis/DQyMDY2MzQ?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/broadcast_notification/actions/chatroom` | [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging/server-apis/zc1MTY2NDQ?platform=server)

### 系统通知管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [发送自定义系统通知](https://doc.yunxin.163.com/messaging2/server-apis/jUyNDUyNTU?platform=server) | `POST https://open.yunxinapi.com/im/v2/custom_notification` | [发送自定义系统通知](https://doc.yunxin.163.com/messaging/server-apis/jYxMjQ1NTk?platform=server)
| [批量发送自定义系统通知](https://doc.yunxin.163.com/messaging2/server-apis/Tc0ODg0OTA?platform=server) | `POST https://open.yunxinapi.com/im/v2/custom_notification/batch` | [批量发送自定义系统通知](https://doc.yunxin.163.com/messaging/server-apis/Dk2MjQwODA?platform=server)

## 会话功能

API 调用频控限制，请参考上文 [频控限制](#throttling)。

### 会话未读数管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [获取会话总未读数](https://doc.yunxin.163.com/messaging2/server-apis/DIzMDIyNjI?platform=server) | `GET https://open.yunxinapi.com/im/v2/conversation_overviews/{account_id}` | -
| [清空指定会话未读数](https://doc.yunxin.163.com/messaging2/server-apis/Dk1OTM4MjY?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/conversations/{conversation_id}/actions/clear_conversation_unread` | -

### 会话分组

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [创建会话分组](https://doc.yunxin.163.com/messaging2/server-apis/jExMDkyMjA?platform=server) | `POST https://open.yunxinapi.com/im/v2/conversation_groups` | -
| [更新会话分组](https://doc.yunxin.163.com/messaging2/server-apis/TIzODU0NzQ?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/conversation_groups/{group_id}` | -
| [删除会话分组](https://doc.yunxin.163.com/messaging2/server-apis/jkxNDAwMjY?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/conversation_groups/{group_id}` | -
| [查询会话分组](https://doc.yunxin.163.com/messaging2/server-apis/TE4Nzk5OTY?platform=server) | `GET https://open.yunxinapi.com/im/v2/conversation_groups/{group_id}` | -
| [批量查询会话分组](https://doc.yunxin.163.com/messaging2/server-apis/DA1ODI1NTk?platform=server) | `GET https://open.yunxinapi.com/im/v2/conversation_groups/actions/group_ids` | -
| [查询所有会话分组](https://doc.yunxin.163.com/messaging2/server-apis/zY2NzY0ODc?platform=server) | `GET https://open.yunxinapi.com/im/v2/conversation_groups` | -
| [分页查询指定账号的指定会话分组的会话列表](https://doc.yunxin.163.com/messaging2/server-apis/jM0MjQ2MzQ?platform=server) | `GET https://open.yunxinapi.com/im/v2/conversation_groups/{group_id}/conversations` | -

### 会话管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [创建会话](https://doc.yunxin.163.com/messaging2/server-apis/DgwMjAzMjM?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/conversations` | -
| [更新会话](https://doc.yunxin.163.com/messaging2/server-apis/zMwOTAzMTI?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/conversations/{conversation_id}` | -
| [删除会话](https://doc.yunxin.163.com/messaging2/server-apis/TcyMjk1NDk?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/conversations/{conversation_id}` | -
| [批量删除会话](https://doc.yunxin.163.com/messaging2/server-apis/Dk2ODgyNTk?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/conversations/actions/conversation_ids` | -
| [查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/jUyOTA0NjM?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/{conversation_id}` | -
| [批量查询会话信息](https://doc.yunxin.163.com/messaging2/server-apis/DAwNDQ0NTU?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations/actions/conversation_ids` | -
| [分页查询用户的所有会话列表](https://doc.yunxin.163.com/messaging2/server-apis/DI2NDczOTg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/conversations` | -
| [设置会话置顶](https://doc.yunxin.163.com/messaging2/server-apis/jEzMTE5NTI?platform=server) | `POST https://open.yunxinapi.com/im/v2/conversations/{conversation_id}/actions/stick_top_conversation` | -

## AI 功能

包含 AI 相关的单次类 API。

API 调用频控限制，请参考上文 [频控限制](#throttling)。

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [AI 助聊](https://doc.yunxin.163.com/messaging2/server-apis/jk4Mzg4OTA?platform=server) | `POST https://open.yunxinapi.com/ai/chat_assistant/v1/chat_assist` | -

## 群组功能

API 调用频控限制，请参考上文 [频控限制](#throttling)。

### 群组管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [创建群组](https://doc.yunxin.163.com/messaging2/server-apis/DIwODUwMTE?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/teams` | <li> [创建高级群](https://doc.yunxin.163.com/messaging/server-apis/Dk4MDY3MzQ?platform=server) <li>[创建超大群](https://doc.yunxin.163.com/messaging/server-apis/jk1ODEwNDY?platform=server)
| [更新群组信息](https://doc.yunxin.163.com/messaging2/server-apis/jE2MTc1Mjk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/teams/{team_id}` | <li> [修改群组信息](https://doc.yunxin.163.com/messaging/server-apis/TkyNTkzMzY?platform=server)<li> [修改超大群信息](https://doc.yunxin.163.com/messaging/server-apis/zE3OTkyNjI?platform=server) <li>[修改超大群人数级别](https://doc.yunxin.163.com/messaging/server-apis/zA4MDEyNzk?platform=server) <li>[禁言群组](https://doc.yunxin.163.com/messaging/server-apis/zc0MTQyNzA?platform=server) <li>[禁言超大群](https://doc.yunxin.163.com/messaging/server-apis/jA3MjQ0ODI?platform=server)
| [转让群组](https://doc.yunxin.163.com/messaging2/server-apis/zI5NTYzNTg?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/teams/{team_id}/actions/transfer_owner` | <li> [转让群组](https://doc.yunxin.163.com/messaging/server-apis/jM0MjQzODA?platform=server) <li>[转让超大群](https://doc.yunxin.163.com/messaging/server-apis/Dg1NjMxMzM?platform=server)
| [添加管理员](https://doc.yunxin.163.com/messaging2/server-apis/DY0MTgxNzE?platform=server) | `POST https://open.yunxinapi.com/im/v2/teams/{team_id}/actions/add_manager` | <li> [添加管理员](https://doc.yunxin.163.com/messaging/server-apis/TAyMDk0MjM?platform=server) <li>[添加超大群管理员](https://doc.yunxin.163.com/messaging/server-apis/Dg1NTY5MTc?platform=server)
| [移除管理员](https://doc.yunxin.163.com/messaging2/server-apis/TAxNTIzNjU?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/teams/{team_id}/actions/remove_manager` | <li> [移除管理员](https://doc.yunxin.163.com/messaging/server-apis/TQyMDE3MzY?platform=server) <li>[移除超大群管理员](https://doc.yunxin.163.com/messaging/server-apis/DU4NDA2OTE?platform=server)
| [解散群组](https://doc.yunxin.163.com/messaging2/server-apis/zk0NDkwOTc?platform=server) | `DELETE https://open.yunxinapi.com/im/v2.1/teams/{team_id}` | <li> [解散群组](https://doc.yunxin.163.com/messaging/server-apis/TYzNDc3OTk?platform=server) <li>[解散超大群](https://doc.yunxin.163.com/messaging/server-apis/DIzMjIxNTg?platform=server)
| [查询群组信息](https://doc.yunxin.163.com/messaging2/server-apis/DI1Nzc3MDY?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams/{team_id}` | <li> [获取群组详细信息](https://doc.yunxin.163.com/messaging/server-apis/TMzNDMyNTI?platform=server) <li>[获取超大群信息](https://doc.yunxin.163.com/messaging/server-apis/DEwMDk2Mjg?platform=server)
| [批量查询群组信息列表](https://doc.yunxin.163.com/messaging2/server-apis/DAyODY4ODE?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams` | [批量获取群组信息与成员列表](https://doc.yunxin.163.com/messaging/server-apis/zcxNzE5OTM?platform=server)
| [查询高级群在线成员列表](https://doc.yunxin.163.com/messaging2/server-apis/jAyMTkyOTA?platform=server) | `GET https://open.yunxinapi.com/im/v2/teams/{team_id}/actions/list_online_members` | [获取群组的在线成员列表](https://doc.yunxin.163.com/messaging/server-apis/TA1MjcwMDE?platform=server)
| [批量查询高级群在线成员数](https://doc.yunxin.163.com/messaging2/server-apis/DQzMjczMDg?platform=server) | `GET https://open.yunxinapi.com/im/v2/teams/actions/online_members_count` | [批量获取群组的在线成员数量](https://doc.yunxin.163.com/messaging/server-apis/zU4NDM1NTY?platform=server)
| [分页查询群成员列表](https://doc.yunxin.163.com/messaging2/server-apis/zIxNTk1Mzc?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/teams/{team_id}/actions/list_members` | <li> [批量获取群组信息与成员列表](https://doc.yunxin.163.com/messaging/server-apis/zcxNzE5OTM?platform=server)<li> [获取群组禁言列表](https://doc.yunxin.163.com/messaging/server-apis/jIxODU5Nzg?platform=server) <li>[获取超大群禁言成员信息](https://doc.yunxin.163.com/messaging/server-apis/TM2NTQzMjc?platform=server) <li>[获取超大群成员信息](https://doc.yunxin.163.com/messaging/server-apis/TI4NTM3Mjg?platform=server)

### 群成员管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [拉人入群](https://doc.yunxin.163.com/messaging2/server-apis/jc0MjY4NzA?platform=server) | `POST https://open.yunxinapi.com/im/v2/team_members` | <li>[拉人入群](https://doc.yunxin.163.com/messaging/server-apis/DA2MzQ0MzA?platform=server) <li>[拉人入超大群](https://doc.yunxin.163.com/messaging/server-apis/Tk5MDQwOTY?platform=server)
| [踢人出群](https://doc.yunxin.163.com/messaging2/server-apis/TkzNTM5NTI?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/team_members/actions/kick_member` | <li> [踢人出群](https://doc.yunxin.163.com/messaging/server-apis/TY4MDA5ODE?platform=server) <li>[踢人出超大群](https://doc.yunxin.163.com/messaging/server-apis/zQ2MDYxMjI?platform=server)
| [主动退群](https://doc.yunxin.163.com/messaging2/server-apis/DI0MTg0ODg?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/team_members/actions/leave` | <li> [主动退群](https://doc.yunxin.163.com/messaging/server-apis/zM4NTM3MDQ?platform=server) <li>[主动退出超大群](https://doc.yunxin.163.com/messaging/server-apis/DIxNTMxOTA?platform=server)
| [更新群成员信息](https://doc.yunxin.163.com/messaging2/server-apis/TQ4MzM2NTk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/team_members/{account_id}` | <li> [禁言指定群成员](https://doc.yunxin.163.com/messaging/server-apis/DU0MzE3MjE?platform=server)<li> [修改群昵称](https://doc.yunxin.163.com/messaging/server-apis/TM0MjM1NTQ?platform=server)<li>[设置群消息提醒开关](https://doc.yunxin.163.com/messaging/server-apis/zk5Mjk4MjQ?platform=server) <li>[修改超大群成员信息](https://doc.yunxin.163.com/messaging/server-apis/TgzNTY2MjE?platform=server) <li>[修改超大群昵称](https://doc.yunxin.163.com/messaging/server-apis/TA0Nzc5OTg?platform=server)
| [批量禁言群成员](https://doc.yunxin.163.com/messaging2/server-apis/DkyNjI4ODk?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/team_members/actions/batch_mute` | [禁言指定超大群成员](https://doc.yunxin.163.com/messaging/server-apis/jEzNDM5ODk?platform=server)
| [分页查询指定账号已加入的群组信息](https://doc.yunxin.163.com/messaging2/server-apis/TkwODkwNTQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/team_members/{account_id}/actions/joined_teams` | <li> [获取用户已加入的群组信息](https://doc.yunxin.163.com/messaging/server-apis/zQ1NjEyMjA?platform=server)<li>[获取已加入的超大群信息](https://doc.yunxin.163.com/messaging/server-apis/TA5MzkzNDE?platform=server) <li>[获取用户已加入的群组的所有群成员信息](https://doc.yunxin.163.com/messaging/server-apis/Tk3MzM2MDY?platform=server)

## 聊天室

### 频控限制

API 调用频控限制，请参考上文 [频控限制](#throttling)。

### 聊天室管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [创建聊天室](https://doc.yunxin.163.com/messaging2/server-apis/DU5NjcwNTk?platform=server) | `POST https://open.yunxinapi.com/im/v2/chatrooms` | [创建聊天室](https://doc.yunxin.163.com/messaging/server-apis/jA0MzQxOTI?platform=server)
| [获取聊天室地址](https://doc.yunxin.163.com/messaging2/server-apis/DU5MDQ1MDQ?platform=server) | `GET https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/address` | [获取聊天室地址](https://doc.yunxin.163.com/messaging/server-apis/TMxODkzNjE?platform=server)
| [更新聊天室信息](https://doc.yunxin.163.com/messaging2/server-apis/jM0ODUxOTc?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/chatrooms/{room_id}` | [更新聊天室信息](https://doc.yunxin.163.com/messaging/server-apis/jI3MDg2MjU?platform=server)
| [开放/关闭聊天室](https://doc.yunxin.163.com/messaging2/server-apis/DkwNzE5MjA?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/update_status` | [开放/关闭聊天室](https://doc.yunxin.163.com/messaging/server-apis/TI5ODE4NTg?platform=server)
| [聊天室禁言](https://doc.yunxin.163.com/messaging2/server-apis/zIyODkxMTY?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/chat_banned` | [将聊天室整体禁言](https://doc.yunxin.163.com/messaging/server-apis/TQyNTAwODY?platform=server#将聊天室整体禁言)
| [开启/关闭进出聊天室事件通知](https://doc.yunxin.163.com/messaging2/server-apis/DEyMDExMTU?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/in_out_notification` | [开启/关闭进出聊天室事件通知](https://doc.yunxin.163.com/messaging/server-apis/Dc2MDQ5ODY?platform=server)
| [查询聊天室信息](https://doc.yunxin.163.com/messaging2/server-apis/TIzODMxODA?platform=server) | `GET https://open.yunxinapi.com/im/v2/chatrooms/{room_id}` | [查询聊天室信息](https://doc.yunxin.163.com/messaging/server-apis/DMyNzgyNDE?platform=server)
| [查询开放状态的聊天室](https://doc.yunxin.163.com/messaging2/server-apis/zMxMzQzNzg?platform=server) | `GET https://open.yunxinapi.com/im/v2/chatrooms/actions/opend_chatrooms` | [查询开放状态的聊天室](https://doc.yunxin.163.com/messaging/server-apis/DU0NTUyNjY?platform=server)
| [分页查询聊天室在线成员列表](https://doc.yunxin.163.com/messaging2/server-apis/jY2NDI2NDk?platform=server) | `GET https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/list_online_members` | [获取聊天室成员列表](https://doc.yunxin.163.com/messaging/server-apis/zAzMjUxMzc?platform=server)
| [查询聊天室固定成员列表](https://doc.yunxin.163.com/messaging2/server-apis/zUyNDg1NzM?platform=server) | `GET https://open.yunxinapi.com/im/v2/chatrooms/{room_id}/actions/list_members` | ^^

### 聊天室成员管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [设置聊天室成员角色](https://doc.yunxin.163.com/messaging2/server-apis/Dk0ODQ1NDU?platform=server) | `POST https://open.yunxinapi.com/im/v2/room_members/{account_id}` | [管理聊天室用户角色](https://doc.yunxin.163.com/messaging/server-apis/DY1NTQwMDU?platform=server)
| [更新聊天室成员信息](https://doc.yunxin.163.com/messaging2/server-apis/jc0MDA0NTc?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/{account_id}` | ^^
| [禁言聊天室成员](https://doc.yunxin.163.com/messaging2/server-apis/zkwMjA0NTI?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/{account_id}/actions/chat_banned` | [设置角色](https://doc.yunxin.163.com/messaging/server-apis/DY1NTQwMDU?platform=server#设置角色)
| [临时禁言聊天室成员](https://doc.yunxin.163.com/messaging2/server-apis/DU0NzQxNTY?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/{account_id}/actions/temp_chat_banned` | [设置临时禁言状态](https://doc.yunxin.163.com/messaging/server-apis/TQyNTAwODY?platform=server#设置临时禁言状态)
| [拉黑聊天室成员](https://doc.yunxin.163.com/messaging2/server-apis/DEwMTg2MzI?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/{account_id}/actions/blocked` | [设置角色](https://doc.yunxin.163.com/messaging/server-apis/DY1NTQwMDU?platform=server#设置角色)
| [查询聊天室禁言列表](https://doc.yunxin.163.com/messaging2/server-apis/DE1NTg2NzQ?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/{room_id}/actions/chat_banned` | [获取聊天室成员列表](https://doc.yunxin.163.com/messaging/server-apis/zAzMjUxMzc?platform=server)
| [查询聊天室黑名单列表](https://doc.yunxin.163.com/messaging2/server-apis/zY2MTI1MTI?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/{room_id}/actions/blocked` | ^^
| [批量查询聊天室固定成员信息](https://doc.yunxin.163.com/messaging2/server-apis/Tg2Mzk0Nzk?platform=server) | `GET https://open.yunxinapi.com/im/v2/room_members/{room_id}/actions/batch` | ^^
| [聊天室标签禁言](https://doc.yunxin.163.com/messaging2/server-apis/jMwNjc3NjY?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/actions/chat_banned_tagged_members` | [标签禁言](https://doc.yunxin.163.com/messaging/server-apis/TA0NjA1MzY?platform=server#标签禁言)
| [聊天室踢人](https://doc.yunxin.163.com/messaging2/server-apis/DE1ODkwMDA?platform=server) | `PATCH https://open.yunxinapi.com/im/v2.1/room_members/{account_id}/actions/kicked` | [聊天室踢人](https://doc.yunxin.163.com/messaging/server-apis/DYyODU4MjQ?platform=server) 
| [修改聊天室在线成员标签](https://doc.yunxin.163.com/messaging2/server-apis/Dg0MjIyMjU?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_members/{account_id}/actions/tags` | [修改聊天室用户标签](https://doc.yunxin.163.com/messaging/server-apis/TA0NjA1MzY?platform=server#修改聊天室用户标签)
| [查询标签下的在线成员数](https://doc.yunxin.163.com/messaging2/server-apis/DIxOTA0ODE?platform=server) | `GET https://open.yunxinapi.com/im/v2/room_members/{room_id}/actions/tagged_members_count` | [查询标签下的在线用户数](https://doc.yunxin.163.com/messaging/server-apis/TA0NjA1MzY?platform=server#查询标签下的在线用户数)
| [分页查询标签下的在线成员列表](https://doc.yunxin.163.com/messaging2/server-apis/zI3NjI3OTE?platform=server) | `GET https://open.yunxinapi.com/im/v2/room_members/{room_id}/actions/list_tag_members` | [根据标签查询在线成员列表](https://doc.yunxin.163.com/messaging/server-apis/TA0NjA1MzY?platform=server#根据标签查询在线成员列表)
| [添加聊天室虚构用户](https://doc.yunxin.163.com/messaging2/server-apis/TA3OTM3ODU?platform=server) | `POST https://open.yunxinapi.com/im/v2/room_members/actions/virtual_members` | [添加聊天室机器人](https://doc.yunxin.163.com/messaging/server-apis/TYyNjY4MTg?platform=server#添加聊天室机器人)
| [删除聊天室虚构用户](https://doc.yunxin.163.com/messaging2/server-apis/TMxNDg1NTI?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/room_members/actions/virtual_members` | [删除聊天室机器人](https://doc.yunxin.163.com/messaging/server-apis/TYyNjY4MTg?platform=server#删除机器人)
| [清空聊天室虚构用户](https://doc.yunxin.163.com/messaging2/server-apis/TU0NjkxMzg?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/room_members/actions/clear_virtual_members` | [清空聊天室机器人](https://doc.yunxin.163.com/messaging/server-apis/TYyNjY4MTg?platform=server#清空机器人)
| [查询聊天室虚构用户](https://doc.yunxin.163.com/messaging2/server-apis/TI1OTg2NDg?platform=server) | `GET https://open.yunxinapi.com/im/v2.1/room_members/actions/virtual_members` | -

### 聊天室队列管理

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [初始化聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/TQ2NTA1Mzk?platform=server) | `POST https://open.yunxinapi.com/im/v2/room_queues/{room_id}` | [初始化聊天室队列](https://doc.yunxin.163.com/messaging/server-apis/TU0Mzg1MzA?platform=server#初始化队列)
| [更新聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/TY1NDI5NjI?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_queues/{room_id}` | <li> [添加或更新元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#添加或更新元素)<li>[批量添加队列元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#批量添加队列元素) <li>[批量更新队列元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#批量更新队列元素)
| [删除聊天室队列](https://doc.yunxin.163.com/messaging2/server-apis/DAzNjQ0NTQ?platform=server) | `DELETE https://open.yunxinapi.com/im/v2/room_queues/{room_id}` | [删除清理队列](https://doc.yunxin.163.com/messaging/server-apis/TU0Mzg1MzA?platform=server#删除清理队列)
| [查询聊天室队列元素](https://doc.yunxin.163.com/messaging2/server-apis/DY4NzAwMjE?platform=server) | `POST https://open.yunxinapi.com/im/v2/room_queues/{room_id}/actions/query` | <li> [获取指定的队列元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#获取指定的队列元素) <li>[排序列出队列中所有元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#排序列出队列中所有元素)
| [从聊天室队列中取出元素](https://doc.yunxin.163.com/messaging2/server-apis/DUwNzI2NjY?platform=server) | `PATCH https://open.yunxinapi.com/im/v2/room_queues/{room_id}/actions/poll` | [从队列中取出元素](https://doc.yunxin.163.com/messaging/server-apis/TE0MDE4NjQ?platform=server#从队列中取出元素)

## 工具

包含文本翻译、语音转文字等其他相关的单次类 API。

API 调用频控限制，请参考上文 [频控限制](#throttling)。

| API | 请求 URL | 对应并兼容的 V9 API |
| :---- | :---- | :---- | :---- |
| [文本翻译](https://doc.yunxin.163.com/messaging2/server-apis/DYxNjA4NjY?platform=server) | `POST https://open.yunxinapi.com/im/v2/translations` | [文本翻译](https://doc.yunxin.163.com/messaging/server-apis/DY2OTgxNzc?platform=server)
| [语音转文字](https://doc.yunxin.163.com/messaging2/server-apis/jIyMjY5MDc?platform=server) | `POST https://open.yunxinapi.com/im/v2/tools/asr` | -

## 圈组

- API 调用频控限制，请参考上文 [频控限制](#throttling)。
- 圈组相关 API 请参考 [圈组 API 概览](https://doc.yunxin.163.com/messaging/server-apis/Dg2NDQ2NTU?platform=server)。

## 批量发送消息

API 调用频控限制，请参考上文 [频控限制](#throttling)。

| V10 版本 API | 请求 URL | V9 版本 API |
| :---- | :---- | :---- |
| [批量发送单聊消息](https://doc.yunxin.163.com/messaging2/server-apis/zgzOTE1MTI?platform=server) | `POST https://open.yunxinapi.com/im/v2/conversations/messages` | [批量发送单聊消息](https://doc.yunxin.163.com/messaging/server-apis/zI5OTk5MjA?platform=server)
| [批量发送自定义系统通知](https://doc.yunxin.163.com/messaging2/server-apis/Tc0ODg0OTA?platform=server) | `POST https://open.yunxinapi.com/im/v2/custom_notification/batch` | [批量发送自定义系统通知](https://doc.yunxin.163.com/messaging/server-apis/Dk2MjQwODA?platform=server)

## 广播消息

API 调用频控限制，请参考上文 [频控限制](#throttling)。

| V10 版本 API | 请求 URL | V9 版本 API |
| :---- | :---- | :---- |
| [发送广播消息](https://doc.yunxin.163.com/messaging2/server-apis/zMzMzUxODQ?platform=server) | `POST https://open.yunxinapi.com/im/v2/broadcast_notification` | [发送广播消息](https://doc.yunxin.163.com/messaging/server-apis/Dg1NDYxNTM?platform=server#发送广播消息)
| [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging2/server-apis/DQyMDY2MzQ?platform=server) | `POST https://open.yunxinapi.com/im/v2.1/broadcast_notification/actions/chatroom` | [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging/server-apis/zc1MTY2NDQ?platform=server)

<a id="modify"></a>

## 调整频控

对于部分 API 支持在 [网易云信控制台](https://app.yunxin.163.com/global/home) 自行调整，其他 API 频控的变更需要联系网易云信商务经理处理。自行调整的步骤如下：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 中选择应用，然后单击 **IM 即时通讯** 下的 **功能配置** 按钮进入功能配置页。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b4c08cb9c2fa97f2bcc99523ffae697a/image.png" style="width:30%;border: 1px solid #BFBFBF;">

2. 顶部选择 **服务端频控** 页签，开启需要调整的 API 频控。

    <img alt="开启频控.png" src="https://yx-web-nosdn.netease.im/common/3835d67762341134153c295cbc0559f2/开启频控.png" style="width:30%;border: 1px solid #BFBFBF;">

3. 开启后，可单击 **编辑**，输入频控值。

    后续会根据新设置的频控进行计费。