本文介绍了网易云信音视频通话 2.0 AI 服务的抄送事件。

<style>
table th:first-of-type {
    width: 17%;
}
table th:nth-of-type(2) {
    width: 17%;
}
table th:nth-of-type(3) {
    width: 15%;
}
table th:nth-of-type(4) {
    width: 30%;
}
</style>

## <span id="事件类型">事件类型</span>

| event_type | 事件含义 |
| --- | --- |
| 700 | [AI 对话消息](#700) |

## <span id="700">700 AI 对话消息</span>

**字段说明**

| 字段 | 类型 | 示例 | 说明 |
| --- | --- | --- | --- |
| eventType | Number | 700 | 事件类型。 |
| data | Object | - | 抄送消息体。 |
   subType | String | ai_message | 消息子类型。 |
   chatId | String | 3 | 聊天 ID。 |
   messages | Array | - | 消息数组。 |
     senderId | String | 3974027 | 发送者 ID。 |
     role | String | user | 角色类型。 |
     content | String | 你好 | 消息内容。 |
   sessionId | String | 000079b4f8cc5902e18891f74e14d7b5 | 会话 ID。 |
   timestamp | Number | 1753683530935 | 时间戳。 |
   deviceId | String | device_13579 | 设备 ID。 | 

**JSON 示例**

```JSON
{
    "data":
    {
        "subType": "ai_message",
        "chatId": "3",
        "messages":
        [
            {
                "senderId": "3974027",
                "role": "user",
                "content": "你好"
            },
            {
                "senderId": "956e2d3d73024d9d854446a053363813",
                "role": "agent",
                "content": "你好啊，有什么可以帮你"
            }
        ],
        "sessionId": "000079b4f8cc5902e18891f74e14d7b5",
        "deviceId": "device_13579",
        "timestamp": 1753683530935
    },
    "eventType": 700
}
```