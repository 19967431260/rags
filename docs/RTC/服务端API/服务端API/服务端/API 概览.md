网易云信提供 RESTful 形式的服务端 API，通过发送 HTTPS 请求就可以获取 （GET），更新（PUT）, 创建 （POST），删除 （DELETE） 房间管理、房间踢人等相关数据或执行相关操作。

<style>
table th:first-of-type {
    width: 15%;
}
table th:nth-of-type(2) {
    width: 10%;
}
table th:nth-of-type(3) {
    width: 40%;
}
</style>

## <span id="房间管理">房间管理</span>

<table>
<tr>
<th><b>API</b></th>
<th><b>方法</b></th>
<th><b>请求 URI</b></th>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/jg3NjcyNTE">创建房间</a></td>
<td>POST</td>
<td><code>https://rtc.yunxinapi.com/v2/api/room</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TI5MTIwNDc">查看房间信息</a></td>
<td>GET</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/jUzODcwODE">查看房间内成员信息</a></td>
<td>GET</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/members</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/members?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TA5MTExNjg">移除成员</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/kicklist/{cid}/members/{uid}</code><li><code>https://rtc.yunxinapi.com/v3/api/kicklist/members?cname={cname}&uid={uid}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/zAzNjE5NTM">查看被移除成员列表</a></td>
<td>GET</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/kicklist/{cid}</code><li><code>https://rtc.yunxinapi.com/v3/api/kicklist?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TA2NTYzMTQ">撤销移除</a></td>
<td>DELETE</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/kicklist/{cid}/members/{uid}</code><li><code>https://rtc.yunxinapi.com/v3/api/kicklist/members?cname={cname}&uid={uid}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TQ5MDE3NDM?platform=server">查询房间媒体流状态</a></td>
<td>GET </td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/streams</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/streams?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TM3MzM4MzM">设置房间成员封禁状态</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/right/change</code><li><code>https://rtc.yunxinapi.com/v3/api/right/change?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/DM2NzQyMTc">删除房间</a></td>
<td>DELETE</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms?cname={cname}</code></td>
</tr>
</table>

## AI 服务

| API | 方法 | 请求 URI |
| ---- | ---- | ---- |
| [创建 RTC AI 任务](https://doc.yunxin.163.com/nertc/server-apis/jQzOTE2NTc?platform=server) | POST | - `https://rtc-ai.yunxinapi.com/v1/api/task/create` |\
|  |  | - `https://rtc-ai.yunxinapi.com/ai/task/create` |
| [结束 RTC AI 任务](https://doc.yunxin.163.com/nertc/server-apis/TM5NTMwNzY?platform=server)  | POST | - `https://rtc-ai.yunxinapi.com/v1/api/task/close` |\
|  |  | - `https://rtc-ai.yunxinapi.com/ai/task/close` |
| [开启同声传译](https://doc.yunxin.163.com/nertc/server-apis/TYzMTUzMTc?platform=server)  | POST | - `https://rtc-ai.yunxinapi.com/v1/api/si/start` |\
|  |  | - `https://rtc-ai.yunxinapi.com/ai/si/start` |
| [关闭同声传译](https://doc.yunxin.163.com/nertc/server-apis/DQzODU5MTY?platform=server)  | POST | - `https://rtc-ai.yunxinapi.com/v1/api/si/stop` |\
|  |  | - `https://rtc-ai.yunxinapi.com/ai/si/stop` |
| [智能摘要](https://doc.yunxin.163.com/nertc/server-apis/jA1MjA2NDY?platform=server)  | POST | `https://rtc-ai.yunxinapi.com/v1/api/task/create` |
| [申请克隆音色](https://doc.yunxin.163.com/nertc/server-apis/DI1MDYyMjk?platform=server) | POST | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice-id-apply`|
| [查询可克隆音色 ID 数量](https://doc.yunxin.163.com/nertc/server-apis/jY5ODUzNTQ?platform=server) | GET | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice-id-apply`|
| [克隆音色](https://doc.yunxin.163.com/nertc/server-apis/jU4ODk4OTE?platform=server) | POST | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice-clone`|
| [重新克隆音色](https://doc.yunxin.163.com/nertc/server-apis/TMxNDc4NTE?platform=server) | POST | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice-reclone`|
| [查询已克隆音色](https://doc.yunxin.163.com/nertc/server-apis/TAxMzM2ODc?platform=server) | GET | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice`|
| [删除克隆音色](https://doc.yunxin.163.com/nertc/server-apis/DQxOTcyOTk?platform=server) | DELETE | `https://rtc-ai.yunxinapi.com/v1/api/tts/voice`|

## 安全通

| API | 方法 | 请求 URI |
| ---- | ---- | ---- |
| [创建安全通审核任务](https://doc.yunxin.163.com/nertc/server-apis/DA3OTIwNzg) | POST | `https://rtc.yunxinapi.com/livewallsolution/submit` |
| [查询审核视频截图](https://doc.yunxin.163.com/nertc/server-apis/jQzMjU5MDg) | POST | `https://rtc.yunxinapi.com/livewallsolution/query/image` |
| [查询审核音频断句](https://doc.yunxin.163.com/nertc/server-apis/DI3NjEwNjA) | POST | `https://rtc.yunxinapi.com/livewallsolution/query/audio/task` |
| [停止安全通审核任务](https://doc.yunxin.163.com/nertc/server-apis/Dg5NzQ1MjM) | POST | `https://rtc.yunxinapi.com/livewallsolution/feedback` |

## 云端播放

<table>
<tr>
<th><b>API</b></th>
<th><b>方法</b></th>
<th><b>请求 URI</b></th>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/DgwMTQ2NzA">创建云端播放任务</a></td>
<td>POST</td>
<td><code>https://rtc.yunxinapi.com/v2/api/task/create</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/jAzNjQ1Mzg">更新云端播放任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/task/update</code><li><code>https://rtc.yunxinapi.com/v3/api/task/update?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/DE0NDgzODA">查询云端播放任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/task/list</code><li><code>https://rtc.yunxinapi.com/v3/api/task/list?cname={cname}</code></td>
</tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TM1ODMyMTA">暂停云端播放任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/task/pause</code><li><code>https://rtc.yunxinapi.com/v3/api/task/pause?cname={cname}</code></td>
</tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/DQ2ODI0NjQ">恢复云端播放任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/task/resume</code><li><code>https://rtc.yunxinapi.com/v3/api/task/resume?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/jE4MzIwNzQ">销毁云端播放任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/task/close</code><li><code>https://rtc.yunxinapi.com/v3/api/task/close?cname={cname}</code></td>
</tr>
</table>

## 云端录制

| API | 方法 | 请求 URI |
| ---- | ---- | ---- |
| [云端录制（旧版）](https://doc.yunxin.163.com/nertc/server-apis/jA5NTIzOTY) | POST | - `https://rtc.yunxinapi.com/v2/api/record/{cid}` |\
| | | - `https://rtc.yunxinapi.com/v3/api/record?cname={cname}` |
| [创建录制任务](https://doc.yunxin.163.com/nertc/server-apis/TEyOTk2OTY) | POST | - `https://rtc.yunxinapi.com/v2/api/cloudrecord/submit` |\
| | | - `https://rtc.yunxinapi.com/v3/api/cloudrecord/submit?cname={cname}` |
| [更新录制布局](https://doc.yunxin.163.com/nertc/server-apis/jg1MDk1MjY?platform=server) | POST | - `https://rtc.yunxinapi.com/v2/api/cloudrecord/update` |\
| | | - `https://rtc.yunxinapi.com/v3/api/cloudrecord/update?cname={cname}` |
| [更新订阅列表](https://doc.yunxin.163.com/nertc/server-apis/DYwODU5NTQ) | POST | - `https://rtc.yunxinapi.com/v2/api/cloudrecord/updateSubs` |\
| | | - `https://rtc.yunxinapi.com/v3/api/cloudrecord/updateSubs?cname={cname}` |
| [查询录制任务信息 ](https://doc.yunxin.163.com/nertc/server-apis/TU4ODczNDk) | POST | - `https://rtc.yunxinapi.com/v2/api/cloudrecord/tasks` |\
| | | - `https://rtc.yunxinapi.com/v3/api/cloudrecord/tasks?cname={cname}` |
| [查询云端录制文件信息](https://doc.yunxin.163.com/nertc/server-apis/jYwNzI3MDk) | POST | `https://api.yunxinapi.com/nimserver/history/queryMediaFileByChannelId.action` |
| [停止录制任务](https://doc.yunxin.163.com/nertc/server-apis/zIwNDM4NDg) | POST | - `https://rtc.yunxinapi.com/v2/api/cloudrecord/stop` |\
| | | - `https://rtc.yunxinapi.com/v3/api/cloudrecord/stop?cname={cname}` |


## 旁路推流

<table>
<tr>
<th><b>API</b></th>
<th><b>方法</b></th>
<th><b>请求 URI</b></th>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/DM0MTg2NTM">创建旁路推流任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/task</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/task?cname={cname} </code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/jE5OTE5NDA">查询指定旁路推流任务</a></td>
<td>GET</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/task/{taskId}</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/task?cname={cname}&taskId={taskId}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TQ0MjA3NjA">查询所有旁路推流任务</a></td>
<td>GET</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/tasks</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/tasks?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/zQ0MDkzNDI">更新旁路推流任务</a></td>
<td>POST</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/update/task</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/update/task?cname={cname}</code></td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/nertc/server-apis/TE4MjU4NjY">停止旁路推流任务</a></td>
<td>DELETE</td>
<td><ul><li><code>https://rtc.yunxinapi.com/v2/api/rooms/{cid}/task</code><li><code>https://rtc.yunxinapi.com/v3/api/rooms/task?cname={cname}</code></td>
</tr>
</table>