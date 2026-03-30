本文主要罗列了网易云信 IM 开放的服务端 API 列表，以及各个接口的使用限制（频控）。

## 频控说明

- 单个应用内的用户在一定时间内调用网易云信 IM 接口的次数超出限制，网易云信服务端会返回 416 错误码，并且会有一定的惩罚时间，即超出限制后在一定时间内再调用该接口会被屏蔽，各接口的频控限制以及超出限制后的屏蔽时间请查看以下表格。

- 若根据业务需要调整部分接口的频控，可在 [网易云信控制台](https://app.yunxin.163.com/global/home) [自行调整](#调整接口频控)，或通过官网首页右侧的联系方式联系网易云信商务经理进行调整。

## IM 接口频控

### IM 账号管理

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ---- |
| [注册 IM 账号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server) | https://api.yunxinapi.com/nimserver/user/create.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [刷新指定 Token](https://doc.yunxin.163.com/messaging/docs/DUxNDQ3NjA?platform=server) | https://api.yunxinapi.com/nimserver/user/update.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [刷新不指定 Token](https://doc.yunxin.163.com/messaging/docs/DUxNDQ3NjA?platform=server#不指定token) | https://api.yunxinapi.com/nimserver/user/refreshToken.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 封禁账号](https://doc.yunxin.163.com/messaging/docs/TUzOTA4NTY?platform=server#封禁账号) | https://api.yunxinapi.com/nimserver/user/block.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 解禁账号](https://doc.yunxin.163.com/messaging/docs/TUzOTA4NTY?platform=server#解禁账号) | https://api.yunxinapi.com/nimserver/user/unblock.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 账号全局禁言](https://doc.yunxin.163.com/messaging/docs/zY0MzIxNDE?platform=server) | https://api.yunxinapi.com/nimserver/user/mute.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [账号功能模块禁言](https://doc.yunxin.163.com/messaging/docs/DU5NDM5MjQ?platform=server) | https://api.yunxinapi.com/nimserver/user/muteModule.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 设置移动端是否需要推送（桌面端在线时）](https://doc.yunxin.163.com/messaging/docs/TcwMDU1MjQ?platform=server) | https://api.yunxinapi.com/nimserver/user/setDonnop.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 消息功能

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ---- |
| [ 发送消息](https://doc.yunxin.163.com/messaging/docs/DQ2NTg4ODE?platform=server) | https://api.yunxinapi.com/nimserver/msg/sendMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量发送单聊消息](https://doc.yunxin.163.com/messaging/docs/zI5OTk5MjA?platform=server) | https://api.yunxinapi.com/nimserver/msg/sendBatchMsg.action | 单个应用默认最高调用频率：<font color=red>120 次/分</font>，如超限，将被屏蔽 1 分钟。
| [ 发送单聊已读回执](https://doc.yunxin.163.com/messaging/docs/zcwMDk2Mzk?platform=server) | https://api.yunxinapi.com/nimserver/msg/markReadMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送群聊已读回执](https://doc.yunxin.163.com/messaging/docs/DU4MjM3NTA?platform=server) | https://api.yunxinapi.com/nimserver/msg/markReadTeamMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 双向撤回消息](https://doc.yunxin.163.com/messaging/docs/zE1NjUyNDg?platform=server) | https://api.yunxinapi.com/nimserver/msg/recall.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 单向撤回消息](https://doc.yunxin.163.com/messaging/docs/zE1NjUyNDg?platform=server#单向撤回) | https://api.yunxinapi.com/nimserver/msg/delMsgOneWay.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送广播消息](https://doc.yunxin.163.com/messaging/docs/Dg1NDYxNTM?platform=server) | https://api.yunxinapi.com/nimserver/msg/broadcastMsg.action | 单个应用默认最高调用频率：<font color=red>10 次/分</font>，如超限，将被屏蔽 1 分钟。
| [ 删除单条广播消息](https://doc.yunxin.163.com/messaging/docs/Dg1NDYxNTM?platform=server#删除单条广播消息) | https://api.yunxinapi.com/nimserver/history/delBroadcastMsgById.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 上传文件（非分片）](https://doc.yunxin.163.com/messaging/docs/zQyNDM0NzE?platform=server) | https://api.yunxinapi.com/nimserver/msg/upload.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 分片上传文件](https://doc.yunxin.163.com/messaging/docs/zQyNDM0NzE?platform=server#分片上传) | https://api.yunxinapi.com/nimserver/msg/fileUpload.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [清理已上传文件](https://doc.yunxin.163.com/messaging/docs/zQyNDM0NzE?platform=server#清理已上传文件) | https://api.yunxinapi.com/nimserver/job/nos/del.action | 单个应用默认最高调用频率：<font color=red>5 次/天</font>，如超限，将被屏蔽 1 天。
| [ 删除单条消息](https://doc.yunxin.163.com/messaging/docs/Dg5OTcwMDk?platform=server) | https://api.yunxinapi.com/nimserver/msg/delMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 删除漫游消息](https://doc.yunxin.163.com/messaging/docs/DY3MTM3MjQ?platform=server) | https://api.yunxinapi.com/nimserver/msg/delRoamSession.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 历史消息与记录

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ----
| [ 单聊云端历史消息查询](https://doc.yunxin.163.com/messaging/docs/DE0MTk0OTY?platform=server#单聊云端历史消息查询) | https://api.yunxinapi.com/nimserver/history/querySessionMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 群聊云端历史消息查询](https://doc.yunxin.163.com/messaging/docs/DE0MTk0OTY?platform=server#群聊云端历史消息查询) | https://api.yunxinapi.com/nimserver/history/queryTeamMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 聊天室云端历史消息查询](https://doc.yunxin.163.com/messaging/docs/DE0MTk0OTY?platform=server#聊天室云端历史消息查询) | https://api.yunxinapi.com/nimserver/history/queryChatroomMsg.action | 单个应用默认最高调用频率：<font color=red>1200 次/分</font>，如超限，将被屏蔽 1 分钟。
| [ 删除聊天室云端历史消息](https://doc.yunxin.163.com/messaging/docs/DE0MTk0OTY?platform=server#删除聊天室云端历史消息) | https://api.yunxinapi.com/nimserver/chatroom/deleteHistoryMessage.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 服务端会话列表查询](https://doc.yunxin.163.com/messaging/docs/DE0MTk0OTY?platform=server#服务端会话列表查询) | https://api.yunxinapi.com/nimserver/history/querySessionList.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 查询单条广播消息](https://doc.yunxin.163.com/messaging/docs/TcxNjU5Mzg?platform=server) | https://api.yunxinapi.com/nimserver/history/queryBroadcastMsgById.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量查询广播消息](https://doc.yunxin.163.com/messaging/docs/TcxNjU5Mzg?platform=server#批量查询广播消息) | https://api.yunxinapi.com/nimserver/history/queryBroadcastMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ IM 登录/登出记录查询](https://doc.yunxin.163.com/messaging/docs/jE0ODgwMDM?platform=server) | https://api.yunxinapi.com/nimserver/history/queryUserEvents.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 自定义系统通知

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ----
| [ 发送自定义系统通知](https://doc.yunxin.163.com/messaging/docs/jYxMjQ1NTk?platform=server) | https://api.yunxinapi.com/nimserver/msg/sendAttachMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量发送自定义系统通知](https://doc.yunxin.163.com/messaging/docs/Dk2MjQwODA?platform=server) | https://api.yunxinapi.com/nimserver/msg/sendBatchAttachMsg.action | 单个应用默认最高调用频率：<font color=red>120 次/分</font>，如超限，将被屏蔽 1 分钟。

### 用户和好友关系

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ----
| [ 获取用户名片](https://doc.yunxin.163.com/messaging/docs/zI0NzYyMDQ?platform=server) | https://api.yunxinapi.com/nimserver/user/getUinfos.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 更新用户名片](https://doc.yunxin.163.com/messaging/docs/zI0NzYyMDQ?platform=server#更新用户名片) | https://api.yunxinapi.com/nimserver/user/updateUinfo.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 添加好友](https://doc.yunxin.163.com/messaging/docs/DQ0MTY1NzI?platform=server) | https://api.yunxinapi.com/nimserver/friend/add.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 更新好友相关信息](https://doc.yunxin.163.com/messaging/docs/DQ0MTY1NzI?platform=server#更新好友相关信息) | https://api.yunxinapi.com/nimserver/friend/update.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 删除好友关系](https://doc.yunxin.163.com/messaging/docs/DQ0MTY1NzI?platform=server#删除好友关系) | https://api.yunxinapi.com/nimserver/friend/delete.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 获取好友列表](https://doc.yunxin.163.com/messaging/docs/DQ0MTY1NzI?platform=server#获取好友列表) | https://api.yunxinapi.com/nimserver/friend/get.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 获取好友关系](https://doc.yunxin.163.com/messaging/docs/DQ0MTY1NzI?platform=server#获取好友关系) | https://api.yunxinapi.com/nimserver/friend/getByAccid.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 设置黑名单/静音](https://doc.yunxin.163.com/messaging/docs/jEzNDQ4ODc?platform=server) | https://api.yunxinapi.com/nimserver/user/setSpecialRelation.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 获取指定用户的黑名单和静音列表](https://doc.yunxin.163.com/messaging/docs/jEzNDQ4ODc?platform=server#查看指定用户的黑名单和静音列表) | https://api.yunxinapi.com/nimserver/user/listBlackAndMuteList.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 高级群

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ----
| [ 创建高级群](https://doc.yunxin.163.com/messaging/docs/Dk4MDY3MzQ?platform=server) | https://api.yunxinapi.com/nimserver/team/create.action | 单个应用中默认 1 秒内所有的高级群操作 API 合计最多可调用 100 次，如超限，将被屏蔽 10 秒。<note type=notice>除发送群消息 API 外，其他所有高级群 API 都属于高级群操作 API。</note>
| [ 拉人入群](https://doc.yunxin.163.com/messaging/docs/DA2MzQ0MzA?platform=server) | https://api.yunxinapi.com/nimserver/team/add.action | ^^
| [ 添加管理员](https://doc.yunxin.163.com/messaging/docs/TAyMDk0MjM?platform=server) | https://api.yunxinapi.com/nimserver/team/addManager.action | ^^
| [ 移除管理员](https://doc.yunxin.163.com/messaging/docs/TQyMDE3MzY?platform=server) | https://api.yunxinapi.com/nimserver/team/removeManager.action | ^^
| [ 转让群主 ](https://doc.yunxin.163.com/messaging/docs/jM0MjQzODA?platform=server) | https://api.yunxinapi.com/nimserver/team/changeOwner.action | ^^
| [ 禁言群主](https://doc.yunxin.163.com/messaging/docs/zc0MTQyNzA?platform=server) | https://api.yunxinapi.com/nimserver/team/muteTlistAll.action | ^^
| [ 禁言指定群成员](https://doc.yunxin.163.com/messaging/docs/DU0MzE3MjE?platform=server) | https://api.yunxinapi.com/nimserver/team/muteTlist.action | ^^
| [ 踢人出群](https://doc.yunxin.163.com/messaging/docs/TY4MDA5ODE?platform=server) | https://api.yunxinapi.com/nimserver/team/kick.action | ^^
| [ 主动退群](https://doc.yunxin.163.com/messaging/docs/zM4NTM3MDQ?platform=server) | https://api.yunxinapi.com/nimserver/team/leave.action | ^^
| [ 修改群组信息](https://doc.yunxin.163.com/messaging/docs/TkyNTkzMzY?platform=server) | https://api.yunxinapi.com/nimserver/team/update.action | ^^
| [ 修改群昵称](https://doc.yunxin.163.com/messaging/docs/TM0MjM1NTQ?platform=server) | https://api.yunxinapi.com/nimserver/team/updateTeamNick.action | ^^
| [ 设置群消息提醒开关](https://doc.yunxin.163.com/messaging/docs/zk5Mjk4MjQ?platform=server) | https://api.yunxinapi.com/nimserver/team/muteTeam.action | ^^
| [ 解散群组](https://doc.yunxin.163.com/messaging/docs/TYzNDc3OTk?platform=server) | https://api.yunxinapi.com/nimserver/team/remove.action | ^^
| [ 获取群组详细信息](https://doc.yunxin.163.com/messaging/docs/TMzNDMyNTI?platform=server) | https://api.yunxinapi.com/nimserver/team/queryDetail.action | ^^
| [ 获取群组禁言列表](https://doc.yunxin.163.com/messaging/docs/jIxODU5Nzg?platform=server) | https://api.yunxinapi.com/nimserver/team/listTeamMute.action | ^^
| [ 获取群消息已读未读详情](https://doc.yunxin.163.com/messaging/docs/zU0NDEzNzA?platform=server) | https://api.yunxinapi.com/nimserver/team/getMarkReadInfo.action | ^^
| [ 获取用户已加入的群组信息](https://doc.yunxin.163.com/messaging/docs/zQ1NjEyMjA?platform=server) | https://api.yunxinapi.com/nimserver/team/joinTeams.action | ^^
| [ 获取用户已加入的群组的所有群成员信息](https://doc.yunxin.163.com/messaging/docs/Tk3MzM2MDY?platform=server) | https://api.yunxinapi.com/nimserver/team/listMemberInfo.action | ^^
| [ 获取群组的在线成员列表](https://doc.yunxin.163.com/messaging/docs/TA1MjcwMDE?platform=server) | https://api.yunxinapi.com/nimserver/team/listOnlineUsers.action | ^^
| [ 批量获取群组信息与成员列表](https://doc.yunxin.163.com/messaging/docs/zcxNzE5OTM?platform=server) | https://api.yunxinapi.com/nimserver/team/query.action | ^^
| [ 批量获取群组的在线成员数量](https://doc.yunxin.163.com/messaging/docs/zU4NDM1NTY?platform=server) | https://api.yunxinapi.com/nimserver/team/listOnlineUserCount.action | ^^
| [发送群消息](https://doc.yunxin.163.com/messaging/docs/jgzMjIzNzc?platform=server) | https://api.yunxinapi.com/nimserver/msg/sendMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 超大群

| API | 请求 URL | 默认频控值
| ---- | ---- | ----
| [ 创建超大群](https://doc.yunxin.163.com/messaging/docs/jk1ODEwNDY?platform=server) | https://api.yunxinapi.com/nimserver/superteam/create.action | 单个应用中默认 1 秒内所有的超大群操作 API 合计最多可调用 100 次，如超限，将被屏蔽 10 秒。<note type=notice>除 **超大群消息相关 API** 外，其他所有超大群 API 都属于超大群操作 API。<br> **超大群消息相关 API** 包括：发送超大群消息，发送超大群自定义系统通知，撤回超大群消息，根据用户 ID/消息 ID 查询超大群历史消息。</note>
| [ 拉人入群 ](https://doc.yunxin.163.com/messaging/docs/Tk5MDQwOTY?platform=server) | https://api.yunxinapi.com/nimserver/superteam/invite.action | ^^
| [添加管理员](https://doc.yunxin.163.com/messaging/docs/Dg1NTY5MTc?platform=server) | https://api.yunxinapi.com/nimserver/superteam/addManager.action | ^^
| [移除管理员](https://doc.yunxin.163.com/messaging/docs/DU4NDA2OTE?platform=server) | https://api.yunxinapi.com/nimserver/superteam/removeManager.action | ^^
| [转让群主](https://doc.yunxin.163.com/messaging/docs/Dg1NjMxMzM?platform=server) | https://api.yunxinapi.com/nimserver/superteam/changeOwner.action | ^^
| [ 禁言超大群 ](https://doc.yunxin.163.com/messaging/docs/jA3MjQ0ODI?platform=server) | https://api.yunxinapi.com/nimserver/superteam/mute.action | ^^
| [ 禁言指定超大群成员 ](https://doc.yunxin.163.com/messaging/docs/jEzNDM5ODk?platform=server) | https://api.yunxinapi.com/nimserver/superteam/muteTlist.action | ^^
| [ 踢人出群](https://doc.yunxin.163.com/messaging/docs/zQ2MDYxMjI?platform=server) | https://api.yunxinapi.com/nimserver/superteam/kick.action | ^^
| [ 主动退群](https://doc.yunxin.163.com/messaging/docs/DIxNTMxOTA?platform=server) | https://api.yunxinapi.com/nimserver/superteam/leave.action | ^^
| [ 修改超大群昵称](https://doc.yunxin.163.com/messaging/docs/TA0Nzc5OTg?platform=server) | https://api.yunxinapi.com/nimserver/superteam/updateTeamNick.action | ^^
| [ 修改超大群信息 ](https://doc.yunxin.163.com/messaging/docs/zE3OTkyNjI?platform=server) | https://api.yunxinapi.com/nimserver/superteam/updateTinfo.action | ^^
| [ 修改超大群成员信息 ](https://doc.yunxin.163.com/messaging/docs/TgzNTY2MjE?platform=server) | https://api.yunxinapi.com/nimserver/superteam/updateTlist.action | ^^
| [ 解散超大群](https://doc.yunxin.163.com/messaging/docs/DIzMjIxNTg?platform=server) | https://api.yunxinapi.com/nimserver/superteam/dismiss.action | ^^
| [ 修改超大群人数级别 ](https://doc.yunxin.163.com/messaging/docs/zA4MDEyNzk?platform=server) | https://api.yunxinapi.com/nimserver/superteam/changeLevel.action | ^^
| [ 获取超大群信息 ](https://doc.yunxin.163.com/messaging/docs/DEwMDk2Mjg?platform=server) | https://api.yunxinapi.com/nimserver/superteam/getTinfos.action | ^^
| [ 获取超大群成员信息 ](https://doc.yunxin.163.com/messaging/docs/TI4NTM3Mjg?platform=server) | https://api.yunxinapi.com/nimserver/superteam/getTlists.action | ^^
| [ 获取超大群禁言成员信息 ](https://doc.yunxin.163.com/messaging/docs/TM2NTQzMjc?platform=server) | https://api.yunxinapi.com/nimserver/superteam/getMuteTlists.action | ^^
| [ 获取已加入的超大群信息 ](https://doc.yunxin.163.com/messaging/docs/TA5MzkzNDE?platform=server) | https://api.yunxinapi.com/nimserver/superteam/joinTeams.action | ^^
| [ 根据用户 ID 查询超大群历史消息 ](https://doc.yunxin.163.com/messaging/docs/DY5MDA3NTU?platform=server#根据用户-id-查询超大群历史消息) | https://api.yunxinapi.com/nimserver/superteam/queryHistoryMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 根据消息 ID 查询超大群历史消息 ](https://doc.yunxin.163.com/messaging/docs/DY5MDA3NTU?platform=server#根据消息-id-查询超大群历史消息) | https://api.yunxinapi.com/nimserver/superteam/queryHistoryMsgByIds.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送超大群消息](https://doc.yunxin.163.com/messaging/docs/zY0ODk0NjU?platform=server) | https://api.yunxinapi.com/nimserver/superteam/sendMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送超大群自定义系统通知](https://doc.yunxin.163.com/messaging/docs/TQyNzI0NzY?platform=server) | https://api.yunxinapi.com/nimserver/superteam/sendAttachMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 撤回超大群消息](https://doc.yunxin.163.com/messaging/docs/DE3NDM4NTc?platform=server) | https://api.yunxinapi.com/nimserver/superteam/recallMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 聊天室

| API | 请求 URL | 默认频控值
| ---- | ---- | ----
| [ 创建聊天室 ](https://doc.yunxin.163.com/messaging/docs/jA0MzQxOTI?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/create.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 获取聊天室地址](https://doc.yunxin.163.com/messaging/docs/TMxODkzNjE?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/requestAddr.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 更新聊天室信息](https://doc.yunxin.163.com/messaging/docs/jI3MDg2MjU?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/update.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 查询聊天室信息](https://doc.yunxin.163.com/messaging/docs/DMyNzgyNDE?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/get.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [批量查询聊天室信息](https://doc.yunxin.163.com/messaging/docs/DMyNzgyNDE?platform=server#批量查询聊天室信息) | https://api.yunxinapi.com/nimserver/chatroom/getBatch.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 开放/关闭聊天室](https://doc.yunxin.163.com/messaging/docs/TI5ODE4NTg?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/toggleCloseStat.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 查询开放状态的聊天室](https://doc.yunxin.163.com/messaging/docs/DU0NTUyNjY?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/queryUserRoomIds.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 设置聊天室定时关闭](https://doc.yunxin.163.com/messaging/docs/jgzNzA0Nzk?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/updateDelayClosePolicy.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 开启/关闭进出聊天室时间通知](https://doc.yunxin.163.com/messaging/docs/Dc2MDQ5ODY?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/updateInOutNotification.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [聊天室踢人](https://doc.yunxin.163.com/messaging/docs/DYyODU4MjQ?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/kickMember.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 设置聊天室角色](https://doc.yunxin.163.com/messaging/docs/DY1NTQwMDU?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/setMemberRole.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 变更聊天室角色](https://doc.yunxin.163.com/messaging/docs/DY1NTQwMDU?platform=server#变更角色) | https://api.yunxinapi.com/nimserver/chatroom/updateMyRoomRole.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 分页获取聊天室成员列表](https://doc.yunxin.163.com/messaging/docs/zAzMjUxMzc?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/membersByPage.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 根据角色获取聊天室成员列表](https://doc.yunxin.163.com/messaging/docs/zAzMjUxMzc?platform=server#根据角色获取) | https://api.yunxinapi.com/nimserver/chatroom/queryMembersByRole.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量获取聊天室成员信息](https://doc.yunxin.163.com/messaging/docs/zAzMjUxMzc?platform=server#批量获取成员信息) | https://api.yunxinapi.com/nimserver/chatroom/queryMembers.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送聊天室消息](https://doc.yunxin.163.com/messaging/docs/jY2MDg1MTk?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/sendMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量发送聊天室消息](https://doc.yunxin.163.com/messaging/docs/jU3NzYzMTk?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/batchSendMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 撤回聊天室消息](https://doc.yunxin.163.com/messaging/docs/jM2MTE5NzE?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/recall.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送聊天室定向消息](https://doc.yunxin.163.com/messaging/docs/DkzNTA5NTI?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/sendMsgToSomeone.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量发送聊天室定向消息](https://doc.yunxin.163.com/messaging/docs/zczMTk5NDU?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/batchSendMsgToSomeone.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging/docs/zc1MTY2NDQ?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/broadcast.action | 单个应用默认最高调用频率：<font color=red>10 次/分</font>，如超限，将被屏蔽 1 分钟。
| [ 添加聊天室机器人](https://doc.yunxin.163.com/messaging/docs/TYyNjY4MTg?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/addRobot.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 删除聊天室机器人](https://doc.yunxin.163.com/messaging/docs/TYyNjY4MTg?platform=server#删除机器人) | https://api.yunxinapi.com/nimserver/chatroom/removeRobot.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 清空聊天室机器人](https://doc.yunxin.163.com/messaging/docs/TYyNjY4MTg?platform=server#清空机器人) | https://api.yunxinapi.com/nimserver/chatroom/cleanRobot.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 设置临时禁言状态](https://doc.yunxin.163.com/messaging/docs/TQyNTAwODY?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/temporaryMute.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 聊天室整体禁言](https://doc.yunxin.163.com/messaging/docs/TQyNTAwODY?platform=server#将聊天室整体禁言) | https://api.yunxinapi.com/nimserver/chatroom/muteRoom.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 标签禁言](https://doc.yunxin.163.com/messaging/docs/TA0NjA1MzY?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/tagTemporaryMute.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 查询标签下的在线用户数 ](https://doc.yunxin.163.com/messaging/docs/TA0NjA1MzY?platform=server#查询标签下的在线用户数) | https://api.yunxinapi.com/nimserver/chatroom/tagMembersCount.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 根据标签查询在线成员列表 ](https://doc.yunxin.163.com/messaging/docs/TA0NjA1MzY?platform=server#根据标签查询在线成员列表) | https://api.yunxinapi.com/nimserver/chatroom/tagMembersQuery.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 根据标签查询历史消息](https://doc.yunxin.163.com/messaging/docs/TA0NjA1MzY?platform=server#根据标签查询历史消息) | https://api.yunxinapi.com/nimserver/chatroom/queryTagHistoryMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 修改聊天室用户标签](https://doc.yunxin.163.com/messaging/docs/TA0NjA1MzY?platform=server#修改聊天室用户标签) | https://api.yunxinapi.com/nimserver/chatroom/updateChatRoomRoleTag.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 初始化队列](https://doc.yunxin.163.com/messaging/docs/TU0Mzg1MzA?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/queueInit.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 删除清理队列 ](https://doc.yunxin.163.com/messaging/docs/TU0Mzg1MzA?platform=server#删除清理队列) | https://api.yunxinapi.com/nimserver/chatroom/queueDrop.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 添加或更新元素 ](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server) | https://api.yunxinapi.com/nimserver/chatroom/queueOffer.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量添加队列元素 ](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server#批量添加队列元素) | https://api.yunxinapi.com/nimserver/chatroom/queueBatchOffer.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 批量更新队列元素 ](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server#批量更新队列元素) | https://api.yunxinapi.com/nimserver/chatroom/queueBatchUpdateElements.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 排序列出队列中所有元素](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server#排序列出队列中所有元素) | https://api.yunxinapi.com/nimserver/chatroom/queueList.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 从队列中取出元素](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server#从队列中取出元素) | https://api.yunxinapi.com/nimserver/chatroom/queuePoll.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 获取指定的队列元素 ](https://doc.yunxin.163.com/messaging/docs/TE0MDE4NjQ?platform=server#获取指定的队列元素) | https://api.yunxinapi.com/nimserver/chatroom/queueMultiGet.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 在线状态订阅

| API | 请求 URL | 默认频控值
| ---- | ---- | ----
| [ 订阅在线状态事件](https://doc.yunxin.163.com/messaging/docs/jc5NDQwODk?platform=server) | https://api.yunxinapi.com/nimserver/event/subscribe/add.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 查询在线状态事件订阅关系](https://doc.yunxin.163.com/messaging/docs/jc5NDQwODk?platform=server#查询在线状态事件订阅关系) | https://api.yunxinapi.com/nimserver/event/subscribe/query.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 取消在线状态事件订阅](https://doc.yunxin.163.com/messaging/docs/jc5NDQwODk?platform=server#取消在线状态事件订阅) | https://api.yunxinapi.com/nimserver/event/subscribe/delete.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [ 取消全部在线状态事件订阅](https://doc.yunxin.163.com/messaging/docs/jc5NDQwODk?platform=server#取消全部在线状态事件订阅) | https://api.yunxinapi.com/nimserver/event/subscribe/batchdel.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 其他

| API | 请求 URL | 默认频控值
| ---- | ---- | ----
| [ 文本翻译](https://doc.yunxin.163.com/messaging/docs/DY2OTgxNzc?platform=server) | https://api.yunxinapi.com/nimserver/translator/textMsg.action | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。

### 圈组

圈组相关 API 请参考 [圈组 API 概览](https://doc.yunxin.163.com/messaging/docs/Dg2NDQ2NTU?platform=server)。

## 调整接口频控

对于部分接口支持在 [网易云信控制台](https://app.yunxin.163.com/global/home) 自行调整，其他接口频控的变更需要联系网易云信商务经理处理。

支持在 [网易云信控制台](https://app.yunxin.163.com/global/home) 自行调整的接口：

| API | 请求 URL | 默认频控值 |
| ---- | ---- | ---- |
| [发送普通消息](https://doc.yunxin.163.com/messaging/docs/DQ2NTg4ODE?platform=server) | `https://api.yunxinapi.com/nimserver/msg/sendMsg.action` | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [批量发送普通消息](https://doc.yunxin.163.com/messaging/docs/zI5OTk5MjA?platform=server) | `https://api.yunxinapi.com/nimserver/msg/sendBatchMsg.action` | 单个应用默认最高调用频率：<font color=red>120 次/分</font>，如超限，将被屏蔽 1 分钟。
| [发送自定义系统通知](https://doc.yunxin.163.com/messaging/docs/jYxMjQ1NTk?platform=server) | `https://api.yunxinapi.com/nimserver/msg/sendAttachMsg.action` | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [批量发送自定义系统通知](https://doc.yunxin.163.com/messaging/docs/Dk2MjQwODA?platform=server) | `https://api.yunxinapi.com/nimserver/msg/sendBatchAttachMsg.action` | 单个应用默认最高调用频率：<font color=red>120 次/分</font>，如超限，将被屏蔽 1 分钟。
| [发送广播消息](https://doc.yunxin.163.com/messaging/docs/Dg1NDYxNTM?platform=server) | `https://api.yunxinapi.com/nimserver/msg/broadcastMsg.action` | 单个应用默认最高调用频率：<font color=red>10 次/分</font>，如超限，将被屏蔽 1 分钟。
| [发送聊天室消息](https://doc.yunxin.163.com/messaging/docs/jY2MDg1MTk?platform=server) | `https://api.yunxinapi.com/nimserver/chatroom/sendMsg.action` | 单个应用默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。
| [发送聊天室全服广播消息](https://doc.yunxin.163.com/messaging/docs/zc1MTY2NDQ?platform=server) | `https://api.yunxinapi.com/nimserver/chatroom/broadcast.action` | 单个应用默认最高调用频率：<font color=red>10 次/分</font>，如超限，将被屏蔽 1 分钟。
| [群组管理操作](#高级群) | 除发送群消息 API 外，其他所有高级群 API 都属于高级群操作 API。 | 单个应用中默认 1 秒内所有的高级群操作 API 合计最多可调用 100 次，如超限，将被屏蔽 10 秒。 |

**网易云信控制台配置频控**

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 中选择应用，然后单击 **IM 即时通讯** 下的 **功能配置** 按钮进入功能配置页。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b4c08cb9c2fa97f2bcc99523ffae697a/image.png" style="width:50%">

2. 顶部选择 **服务端频控** 页签，开启需要调整的接口频控。

    <img alt="开启频控.png" src="https://yx-web-nosdn.netease.im/common/3835d67762341134153c295cbc0559f2/开启频控.png" style="width:50%;border: 0px solid #BFBFBF;">

3. 开启后，可单击 **编辑**，输入频控值。

    后续会根据新设置的频控进行计费。

<style>
table th:first-of-type {
    width: 20%;
}
table th:nth-of-type(2) {
    width: 45%;
}
table th:nth-of-type(3) {
    width: 35%;
}
</style>