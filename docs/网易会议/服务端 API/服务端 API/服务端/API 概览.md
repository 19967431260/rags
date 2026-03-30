网易会议提供全套开放、简单、安全的视频会议服务，帮助您实现卓越的音视频性能、丰富的会议协作能力、坚实的会议安全保障，为您打造企业专属的会议能力，提升办公协作效率，满足大、中、小会议全场景需求。您可以使用服务端 API 实现远程音视频会议、在线协作、会管会控、会议录制、指定邀请、布局管理等会议功能。

## 使用说明

网易会议提供客户端和服务端 RESTful API 供您调用，服务端 API 使用 HTTPS 网络请求协议，允许 POST 方法。API 参考主要介绍接口的请求语法、相关参数含义以及请求和返回示例。如果要进行快速二次开发，建议您使用客户端 SDK 开发包。

部分功能可通过客户端和服务端 API 两种方式实现，请根据您的实际需求和场景选择合适的调用方式。

<style>
table th:first-of-type {
    width: 20%;
}
table th:nth-of-type(2) {
    width: 10%;
}
table th:nth-of-type(3) {
    width: 70%;
}
</style>

## <span id="会议账号管理">会议账号管理</span>

| API | 方法 | 请求 URL |
| ---- | ---- | ---- |
| [创建会议账号](https://doc.yunxin.163.com/meeting/server-apis/jU0MDAzNTg?platform=server) | POST | <code>https://meeting.yunxinroom.com/scene/meeting/api/v2/add-user</code> |
| [批量查询会议账号](https://doc.yunxin.163.com/meeting/server-apis/jI1MTgwNTE?platform=server) | GET | <code>https://meeting.yunxinroom.com/scene/meeting/api/v2/batch-get-user?userUuids=user_uuid_sample1,user_uuid_sample2</code> |
| [更新会议账号](https://doc.yunxin.163.com/meeting/server-apis/zIxNjcwMDg?platform=server) | POST | <code>https://meeting.yunxinroom.com/scene/meeting/api/v2/update-user</code> |
| [封禁会议账号](https://doc.yunxin.163.com/meeting/server-apis/zU5OTQ2OTQ?platform=server) | POST | `https://meeting.yunxinroom.com/scene/meeting/api/v2/ban-user` |
| [解禁会议账号](https://doc.yunxin.163.com/meeting/server-apis/jkzMjgxOTA?platform=server) | POST | `https://meeting.yunxinroom.com/scene/meeting/api/v2/unban-user` |
| [注销会议账号](https://doc.yunxin.163.com/meeting/server-apis/jU4NDUwNjc?platform=server) | POST | `https://meeting.yunxinroom.com/scene/meeting/v2/delete-user` |
| [重置用户令牌](https://doc.yunxin.163.com/meeting/server-apis/zc3MTAyODU?platform=server) | POST | `https://meeting.yunxinroom.com/scene/meeting/api/v2/refresh-user-token` |

## <span id="会议管理">会议管理</span>

| API | 方法 | 请求 URL |
| ---- | ---- | ---- |
| <a href="https://doc.yunxin.163.com/meeting/server-apis/TUwMzc3NzY">创建会议</a> | PUT | <code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/create/{type}</code> |
| <a href="https://doc.yunxin.163.com/meeting/server-apis/TU4NjQxODU">查询会议信息</a> | GET | <code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/info/{meetingId}</code> |
| <a href="https://doc.yunxin.163.com/meeting/server-apis/jY3ODE3NDg">修改会议信息</a> | POST | <code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/edit/{meetingId}</code> |
| [取消会议](https://doc.yunxin.163.com/meeting/server-apis/DAzNzc5MDg?platform=server) | DELETE | <code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/cancel/{meetingId}</code>
| [修改会议销毁时间](https://doc.yunxin.163.com/meeting/server-apis/DgyNjU0OTI?platform=server) | PUT | <code> https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/meeting/{meetingId}/destroyTime/{destroyTime} </code>
| <a href="https://doc.yunxin.163.com/meeting/server-apis/Dk3MDU5NTc">结束会议</a> | DELETE | <li><code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/close/meetingId/{meetingId}/recycle/{recycle}</code><li><code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/close/meetingNum/{meetingNum}/recycle/{recycle}</code><li><code>https://roomkit.yunxinapi.com/scene/meeting/api/{appId}/v1/close/meetingShortNum/{meetingShortNum}/recycle/{recycle}</code> |

## 巡检者角色管理

| API | 方法 | 请求 URL |
| ---- | ---- | ---- |
| <a href="https://doc.yunxin.163.com/meeting/server-apis/jM2NDU1NTI">增加巡检者</a> | PUT | <code>https://roomkit.yunxinapi.com/apps/v2/room/bind/observer</code> |
| <a href="https://doc.yunxin.163.com/meeting/server-apis/DcwNDM3NjA">解绑巡检者角色</a> | POST | <code>https://roomkit.yunxinapi.com/apps/v2/room/unbind/observer</code> |

## 会议直播管理

| API | 方法 | 请求 URL |
| ---- | ---- | ---- |
| [开始直播](https://doc.yunxin.163.com/meeting/server-apis/Tg1OTgxNjc?platform=server) | POST | <code>https://{endpoint}/apps/v2/live-start</code> |
| [修改直播](https://doc.yunxin.163.com/meeting/server-apis/jU3NDMyODk?platform=server) | POST | <code> https://{endpoint}/apps/v2/live-update</code> |
| [查询直播信息](https://doc.yunxin.163.com/meeting/server-apis/DY5MTgwMTg?platform=server) | GET | <code> https://{endpoint}/apps/v2/live-info/?roomArchiveId={roomArchiveId}</code> |
| [结束直播](https://doc.yunxin.163.com/meeting/server-apis/zI2NDkwMjc?platform=server) | POST | <code>https://{endpoint}/apps/v2/live-end</code>

## 会议录播管理

| API | 方法 | 请求 URL |
| ---- | ---- | ---- |
| [获取转写文件](https://doc.yunxin.163.com/meeting/server-apis/zY3NDkyMjI?platform=server) | GET | <code>https://roomkit.yunxinapi.com/scene/meeting/api/v1/transcript-file?meetingId={meetingId}&ttl={ttl}</code> |