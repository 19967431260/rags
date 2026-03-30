网易云信 NERoom 房间组件（下文简称 NERoom） 以房间为基础，提供网易云信全系列能力，包括即时消息、音视频通话、直播、互动白板等。提供易接入、强扩展、高效部署和覆盖多场景的服务。通过组件与 UI kit，助力企业快速搭建业务场景，例如多人语聊房、秀场直播、电商直播、在线教育、企业培训、活动直播等多种场景。

## 概述

NERoom 基于网易云信在 IM 即时消息、音视频通话等领域多年的客户积累与业务沉淀，为您提供高效、低成本的能力接入。

NERoom 提供典型业务场景的模板，让房间灵活可变形。场景模板包括多人语聊房、秀场直播、电商直播、在线教育、企业培训、活动直播等。

NERoom 提供即时消息、音视频通话、互动白板、麦位管理、角色管理等模块，您可根据模块按需选择业务能力，实现积木式的功能组装。通过可视化界面配置，快速开通相关能力，降低集成难度、提升接入效率。

NERoom 还开放各类标准接口和扩展能力，您可基于标准接口对接第三方厂商或自有业务系统，扩展自有业务所需功能，真正实现业务的全面发展。

## API 列表

本文介绍 NERoom SDK 的 Restful API 列表。

## 账号管理

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [创建账号](https://doc.yunxin.163.com/neroom/server-apis/DAwOTUxMzE?platform=server) | POST | `https://{endpoint}/neroom/v3/users` |
| [更新账号和 Token](https://doc.yunxin.163.com/neroom/server-apis/jQ3MTcxMjY?platform=server) | PATCH | `https://{endpoint}/neroom/v3/users/:user_uuid` |
| [获取账号信息](https://doc.yunxin.163.com/neroom/server-apis/DU2MzY4MjI?platform=server) | GET | `https://{endpoint}/neroom/v3/users/:user_uuid` |
| [批量获取账户信息](https://doc.yunxin.163.com/neroom/server-apis/TA0NzM1ODg?platform=server) | GET | `https://{endpoint}/neroom/v3/users?user_uuids=:user_uuids` |
| [创建 RTC 账号](https://doc.yunxin.163.com/neroom/server-apis/DQ1NDY2MjY?platform=server) | POST | `POST https://{endpoint}/neroom/v4/rtc_uid` |

## 房间管理

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [创建房间](https://doc.yunxin.163.com/neroom/server-apis/jQ3MDk5ODc?platform=server) | POST | `https://{endpoint}/neroom/v3/rooms` |
| [更新房间](https://doc.yunxin.163.com/neroom/server-apis/TM3MDg5NTE?platform=server) | POST | `https://{endpoint}/neroom/v4/rooms/{room_archive_id}`|
| [关闭房间](https://doc.yunxin.163.com/neroom/server-apis/zU5NDM1NDk?platform=server) | DELETE | `https://{endpoint}/neroom/v3/rooms/:room_archive_id` |
| [房间禁言](https://doc.yunxin.163.com/neroom/server-apis/DM2NzAzMzI?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/mute` |
| [房间解禁](https://doc.yunxin.163.com/neroom/server-apis/DQzODE2MDU?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/cancel_mute` |
| [获取禁言房间列表](https://doc.yunxin.163.com/neroom/server-apis/DMwMzA4ODQ?platform=server) | GET | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/mute_list` |
| [添加黑名单](https://doc.yunxin.163.com/neroom/server-apis/DU5NTI0NDQ?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/{room_archive_id}/add_blacklist` |
| [移除黑名单](https://doc.yunxin.163.com/neroom/server-apis/TY4Nzk0NTc?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/remove_blacklist` |
| [获取黑名单](https://doc.yunxin.163.com/neroom/server-apis/jU2NDc2MjM?platform=server) | GET | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/blacklist` |
| [开启/停止录制](https://doc.yunxin.163.com/neroom/server-apis/TU1MTg4NzE?platform=server) | POST | `https://{endpoint}/scene/apps/{appKey}/v2/rooms/{roomUuid}/record/state/{recordState}` |
| [获取房间录制列表](https://doc.yunxin.163.com/neroom/server-apis/TcyNjE4OTA?platform=server) | GET | `https://{endpoint}/scene/apps/{appKey}/v2/rooms/record/list` |

## 房间成员管理

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [查询在线人员列表](https://doc.yunxin.163.com/neroom/server-apis/jQ1OTgyNDk?platform=server) | GET | `https://{endpoint}/v3/rooms/:room_archive_id/online_user_list?page_number=:page_number&page_size=:page_size` |
| [变更成员角色](https://doc.yunxin.163.com/neroom/server-apis/DU1NDY0MDE?platform=server) | PATCH | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/users/:user_uuid/role` |
| [移出房间成员](https://doc.yunxin.163.com/neroom/server-apis/TIxNjQ5NTA?platform=server) | DELETE | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/users/:user_uuid` |
| [更新成员](https://doc.yunxin.163.com/neroom/server-apis/DE3MjEzMTg?platform=server) | PUT | `https://{endpoint}/neroom/v4/rooms/{room_archiveId}/members/{user_uuid}`
| [成员禁言](https://doc.yunxin.163.com/neroom/server-apis/DA0MjI3ODc?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/users/:user_uuid/mute` |
| [成员解禁](https://doc.yunxin.163.com/neroom/server-apis/DEwNzY1Mzg?platform=server) | PATCH | `https://{endpoint}/neroom/v1/rooms/:room_archive_id/users/:user_uuid/cancel_mute` |

## 即时消息

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [发送聊天室消息](https://doc.yunxin.163.com/neroom/server-apis/DY1MTI2ODY?platform=server) | POST | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/messages` |
| [发送全服广播消息](https://doc.yunxin.163.com/neroom/server-apis/TQzOTM4MDY?platform=server) | POST | `https://{endpoint}/neroom/v1/broadcast` |
| [发送自定义房间信令](https://doc.yunxin.163.com/neroom/server-apis/TY1NzA1MzE?platform=server) | POST | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/custom_messages` |
| [聊天室消息撤回](https://doc.yunxin.163.com/neroom/server-apis/jM2MDY0MDE?platform=server) | POST | `https://{endpoint}/scene/apps/{appKey}/v2/rooms/{roomUuid}/chatrooms/{chatroomId}/recall` |
| [聊天室消息查询](https://doc.yunxin.163.com/neroom/server-apis/Tk0NjY1MTg?platform=server) | GET | `https://{endpoint}/scene/apps/{appKey}/v2/rooms/chatroom/msg/export` |

## 麦位

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [获取麦位信息](https://doc.yunxin.163.com/neroom/server-apis/Tc4ODA1MTc?platform=server) | GET | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/seats/slot_list` |
| [切换麦位模式](https://doc.yunxin.163.com/neroom/server-apis/DY4OTgwNDg?platform=server) | POST | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/seat_mode`
| [用户下麦](https://doc.yunxin.163.com/neroom/server-apis/Tk3OTE2NzU?platform=server) | POST | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/seats/kick_user/:user_uuid` |

## 数据统计

| API | 方法 | 请求 URL |
| --- | --- | --- |
| [查询房间录制记录](https://doc.yunxin.163.com/neroom/server-apis/DA1MjA3NjI?platform=server) | GET | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/media_info` |
| [查询房间直播流名称](https://doc.yunxin.163.com/neroom/server-apis/DcwMTYyNDE?platform=server) | GET | `https://{endpoint}/neroom/v3/rooms/:room_archive_id/live_stream_name` |

## 消息抄送

[NERoom 消息抄送事件](https://doc.yunxin.163.com/neroom/server-apis/zg1Mjg1MDM?platform=server)

<style>
table th:first-of-type {
    width: 25%;
}
table th:nth-of-type(2) {
    width: 20%;
}
table th:nth-of-type(3) {
    width: 55%;
}
</style>