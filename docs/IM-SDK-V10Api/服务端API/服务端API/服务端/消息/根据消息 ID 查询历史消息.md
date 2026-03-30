::: note important
该接口已废弃，如需根据消息 ID 查询历史消息请参考新的 [根据消息 ID 查询历史消息](https://doc.yunxin.163.com/messaging2/server-apis/jczMzMzMjg?platform=server) API。
:::

该接口可以根据消息 ID 批量查询历史消息（包括单聊消息，高级群消息和超大群消息）。

## 调用频率

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging2/server-apis/DUzNjAzMTc?platform=server)。

## 请求信息

### 请求 URL

```
POST https://{endpoint}/im/v2/conversations/{conversation_id}/batch_messages
```

:::note note
请求 URL 中的 `{endpoint}` 代表服务地址域名，您可以根据用户服务区域选择中国大陆和海外服务地址，并支持搭建高可用主备域名机制。详情请参考 [调用方式](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#%E6%9C%8D%E5%8A%A1%E5%9C%B0%E5%9D%80) 服务地址章节。
:::

<style>
table th:first-of-type {
    width: 25%;
}
</style>

### 请求头参数

请求 Header 的参数说明请参考 [请求 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#请求-header)。

### 路径参数

参数名称 | 类型 | 是否必选 | 说明 | 示例
--- | --- | --- | --- | ---
`conversation_id` | String | 是 | 会话 ID。会话 ID 需要用户自行拼装，拼装规则：<br> `owner_id|conversation_type|other_id` 或 `owner_id|conversation_type|team_id` <br><ul><li>owner_id：操作者账号 ID</li><li>conversation_type：会话类型，1：单聊会话；2：高级群会话；3：超大群会话</li><li>other_id：对方账号 ID（单聊对话）</li><li>team_id：群组 ID（群组会话）</li>|单聊会话：`Accid1|1|Accid2`<br>高级群会话：`Accid1|2|tid`<br>超大群会话：`Accid1|3|tid` |

### 请求体参数

参数名称 | 类型 | 是否必选 | 说明 |
--- | --- | --- | ---
`messages` | Array of objects | 是 | 需要查询的消息对象。
 `message_server_id` | Long | 是 | 消息的服务器 ID。
 `create_time` | Long | 是 | 消息的发送时间（毫秒）。

## 响应信息

### 响应头参数

响应 Header 的参数说明请参考 [响应 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#响应-header)。

### 响应体参数

参数名称 | 类型 | 说明 | 是否必返回 |
--- | --- | --- | ---
`code` | Integer | 状态码，200 表示请求成功。 | 是
`msg` | String | 提示信息。请求失败时返回错误信息，请求成功时返回 "success"。 | 是
`data` | Object | 返回的 JSON 数据对象，请求失败则返回空对象。 | 是
 `failed_list` | Array of objects | 查询失败的消息列表。 | 否
  `message_server_id` | Long | 服务端消息 ID。 | 是
  `create_time` | Long | 消息发送时间戳。 | 是
  `error_code` | Long | 错误码。 | 是
  `error_msg` | String | 错误信息。 | 是
 `success_list` |　Array of objects　| 查询到的消息列表。 | 否
  `message_server_id` | Long | 服务端消息 ID。 | 是
  `conversation_type` | Integer | 会话类型。1：单聊；2：高级群；3：超大群。 | 是
  `sender_id` | String | 消息发送方账号 ID。 | 是
  `message_type` | Integer | 消息类型。0：文本；1：图片；2：语音；3：视频；4：地址位置；5：通知；6：文件；10：提示；11：机器人；100：自定义。 | 是
  `create_time` | Long | 消息发送时间戳。 | 是
  `message_client_id` | String | 客户端消息 ID。 | 是
  `sender_client_type` | Integer | 消息发送端类型。1：Android；2：iOS；4：PC；16：Web；32：REST；64：MAC。 | 否
  `text` | String | 文本消息内容或多媒体消息的描述文本（该描述信息可用于云端历史消息关键词检索）。 | 否
  `attachment` | Object | 多媒体消息的属性或自定义消息内容。 | 否
  `extension` | String | 消息发送时传入的第三方扩展字段。 | 否
  `team_id` | Long | 群组 ID。`team_id` 与 `receiver_id` 只会返回一个。 | 否
  `receiver_id` | String | 消息的接收者 ID。 | 否
  `sub_type` | Integer | 自定义消息子类型，大于 0。message_type = 100 时该字段才有效。 | 否
  `modify_account_id` | String | 消息更新者的用户账号 ID。<br>只有消息被更新才会返回该字段。 | 否
  `modify_time` | Long | 消息的更新时间。<br>只有消息被更新才会返回该字段。 | 否
  `thread_config` | Object | Thread 消息配置项。 | 否
   `thread_root` | Object | Thread 根消息对象。 | 否
    `sender_id` | String | 根消息的发送者。 | 否
    `receiver_id` | String | 根消息的接收者。 | 否
    `create_time` | Long | 根消息的发送时间。 | 否
    `message_server_id` | String | 根消息的服务器消息 ID。 | 否
    `message_client_id` | String | 根消息的客户端消息 ID。 | 否
   `thread_reply` | Object | 被回复的消息对象。 | 否
    `sender_id` | String | 被回复消息的发送者。 | 否
    `receiver_id` | String | 被回复消息的接收者。 | 否
    `create_time` | Long | 被回复消息的发送时间。 | 否
    `message_server_id` | String | 被回复消息的服务器消息 ID。 | 否
    `message_client_id ` | String | 被回复消息的客户端消息 ID。 | 否

### 响应体示例

```JSON
{
    "code": 200,
    "msg": "success",
    "data": {
        "success_list": [{
            "text": "{\"msg\":\"30l7mgx1elkf9xi9g7wqc0ry4av43gawqgkecl4f9p46us6kzi\"}",
            "message_server_id": 167595237,
            "message_client_id": "80227c89-3374-4258-97bd-424db19d5360",
            "sender_id": "wmtest2",
            "create_time": 1695362207119,
            "message_type": 0,
            "sender_client_type": "32"
        }],
        "failed_list": [
            {
                "message_server_id": 123,
                "create_time": 123,
                "error_code": 107404,
                "error_msg": "message not exist"
            }
        ]
    }
}
```

## 错误码

本文仅列举部分业务接口错误码，完整列表请参考客户端 API [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client)。 <!-- IM V10 -->

| 错误码 | 错误码描述 | 错误信息示例
| --- | --- | ---
| 200 | 请求成功 | success
| 414 | 参数错误 | parameter error
| 102404 | 用户不存在 | account not exist
| 108404 | 群不存在 | team not exist
| 500 | 服务器内部错误 | internal server error 