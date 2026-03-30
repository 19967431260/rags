本文介绍 NERoom SDK 的 Restful API 列表。  



## 账号管理
|API|方法|请求URL|
|--|--|--|
|<a href="https://doc.yunxin.163.com/neroom/docs/TY1NzM5MjQ?platform=server" target="_blank">创建账号</a>|PUT|https://roomkit.yunxinapi.com/apps/{appKey}/v1/users/{userUuid}|
|<a href="https://doc.yunxin.163.com/docs/zU3Mjk0MTk/TE0MTY4ODE?platformId=121098" target="_blank">刷新 Token</a>|POST|https://roomkit.yunxinapi.com/apps/v1/refreshToken|
|<a href="https://doc.yunxin.163.com/neroom/docs/zUwNjAxMzg?platform=server" target="_blank">更新昵称和头像</a>|PUT|https://roomkit.yunxinapi.com/apps/{appKey}/v1/users/{userUuid}/update|

## 房间管理
|API|方法|请求URL|
|--|--|--|
|<a href="https://doc.yunxin.163.com/neroom/docs/TM0MTUyNjc?platform=server" target="_blank">创建房间</a>|PUT|https://roomkit.yunxinapi.com/apps/v2/room|
|<a href="https://doc.yunxin.163.com/neroom/docs/jYzNjE5MTE?platform=server" target="_blank">关闭房间</a>|DELETE|https://roomkit.yunxinapi.com/apps/v2/room?roomArchiveId={roomArchiveId}|
|<a href="https://doc.yunxin.163.com/neroom/docs/jc1NjY4MjM?platform=server" target="_blank">查询房间信息</a>|GET|https://roomkit.yunxinapi.com/apps/v2/room?roomArchiveId={roomArchiveId}|



## 房间成员管理
|API|方法|请求URL|
|--|--|--|
|<a href="https://doc.yunxin.163.com/neroom/docs/TExNjQ4MzQ?platform=server" target="_blank">查询在线人员列表</a>|GET|https://roomkit.yunxinapi.com/apps/v2/online-user-list?roomArchiveId={roomArchiveId}&pageNumber={pageNumber}&pageSize={pageSize}|
|<a href="https://doc.yunxin.163.com/neroom/docs/jY5NzAyODQ?platform=server" target="_blank">移出房间成员</a>|DELETE|https://roomkit.yunxinapi.com/apps/v2/room-user?roomArchiveId={roomArchiveId}&userUuid={userUuid}|

## 即时消息
|API|方法|请求URL|
|--|--|--|
|<a href="https://doc.yunxin.163.com/neroom/docs/jQ2MDI1Nzc?platform=server" target="_blank">发送聊天室自定义消息</a>|POST|https://roomkit.yunxinapi.com/apps/v2/sendChatRoomCustomMessage|


## 数据统计
|API|方法|请求URL|
|--|--|--|
|<a href="https://doc.yunxin.163.com/neroom/docs/TI1NzEyMzM?platform=server" target="_blank">查询房间录制记录</a>|GET|https://roomkit.yunxinapi.com/apps/v2/room-media?roomArchiveId={roomArchiveId}|
|<a href="https://doc.yunxin.163.com/neroom/docs/zMzMDQwODU?platform=server" target="_blank">查询房间直播流名称</a>|GET|https://roomkit.yunxinapi.com/apps/v2/live-stream-name?roomArchiveId={roomArchiveId}|