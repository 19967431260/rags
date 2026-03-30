该接口可以根据 Thread 根消息分页查询 Thread 消息列表（包括单聊消息，高级群消息和超大群消息）。

Thread 消息的定义可参考 [消息扩展](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client#实现消息回复)。

## 调用频率

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging2/server-apis/DUzNjAzMTc?platform=server)。

## 请求信息

### 请求 URL

```
GET https://{endpoint}/im/v2.1/messages/actions/thread_messages
```

:::note note
请求 URL 中的 `{endpoint}` 代表服务地址域名，您可以根据用户服务区域选择中国大陆和海外服务地址，并支持搭建高可用主备域名机制。详情请参考 [调用方式](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#服务地址) 服务地址章节。
:::

<style>
table th:first-of-type {
    width: 20%;
}
</style>

### 请求头参数

请求 Header 的参数说明请参考 [请求 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#请求头)。

### 查询参数

参数名称 | 类型 | 是否必选 | 描述
--- | --- | --- | --- | ---
`begin_time` | Long | 是 | 查询开始时间（毫秒）。
`end_time` | Long | 是 | 查询截止时间（毫秒）。
`page_token` | String | 否 | 分页标识符，如果为空，则从第一页开始查询。
`limit` | Integer | 是 | 每页返回的消息数上限，最大为 100。小于等于 0，或者大于 100，会报 414 错误。
`descending` | Boolean | 否 | 是否按时间正序，true：按时间正序。false：按时间倒序。
`conversation_type` | Integer | 是 | Thread 根消息的会话类型。1：单聊。2：高级群。3：超大群。
`sender_id` | String | 是 | Thread 根消息的发送者。
`receiver_id` | String | 是 | Thread 根消息的接收者。
`message_server_id` | Long | 是 | Thread 根消息的服务器 ID。
`message_client_id` | String | 是 | Thread 根消息的客户端 ID。
`create_time` | Long | 是 | Thread 根消息的发送时间（毫秒）。

## 响应信息

### 响应头参数

响应 Header 的参数说明请参考 [响应 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#响应头)。

### 响应体参数

参数名称 | 类型 | 说明 | 是否必返回 |
--- | --- | --- | ---
`code` | Integer | 状态码，200 表示请求成功。 | 是
`msg` | String | 提示信息。请求失败时返回错误信息，请求成功时返回 "success"。 | 是
`data` | Object | 返回的 JSON 数据对象，请求失败则返回空对象。 | 是
 `has_more` | Boolean | 是否还有更多数据。 | 是
 `next_token` | String | 分页标识符。 | 否
 `thread_root` | Object | Thread 根消息对象。 | 是
  `message_server_id` | Long | 服务端消息 ID。 | 是
  `sender_id` | String | 消息发送方账号 ID。 | 是
  `message_type` | Integer | 消息类型。0：文本。1：图片。2：语音。3：视频。4：地址位置。6：文件。10：提示。12：音视频话单。100：自定义。 | 是
  `create_time` | Long | 消息发送时间戳。 | 是
  `message_client_id` | String | 客户端消息 ID。 | 是
  `sender_client_type` | Integer | 消息发送端类型。1：AOS；2：iOS；4：PC；16：Web；32：REST；64：MAC；65：HARMONY。 | 是
  `text` | String | 文本消息内容或多媒体消息的描述文本（该描述信息可用于云端历史消息关键词检索）。 | 否
  `attachment` | Object | 多媒体消息的属性或自定义消息内容。 | 否
  `extension` | String | 消息发送时传入的第三方扩展字段。 | 否
  `team_id` | Long | 群组 ID。`team_id` 与 `receiver_id` 只会返回一个。 | 否
  `receiver_id` | String | 消息的接收者 ID。 | 否
  `receiver_account_ids` | Array of strings | 定向消息接收者账号 ID 列表。 | 否
  `inclusive` | Boolean | 定向消息接收者列表是为可读列表。true（默认）：可读；false：不可读。 | 否
  `new_member_visible` | Boolean | 新进群成员是否可查看该消息。true：可查看；false：不可查看。 | 否
  `sub_type` | Integer | 消息子类型。用于对消息进行二级分类，取值范围为大于 0 的正整数。推荐自定义消息类型使用此字段区分不同业务场景，其他消息类型可根据实际需求选择性使用。 | 否
  `modify_account_id` | String | 消息更新者的用户账号 ID。<br>只有消息被更新才会返回该字段。 | 否
  `modify_time` | Long | 消息的更新时间。<br>只有消息被更新才会返回该字段。 | 否
  `conversation_type` | Integer | 会话类型。1：单聊。2：高级群。3：超大群。 | 是
  `thread_config` | Object | Thread 消息配置项。 | 否
   `thread_root` | Object | Thread 根消息对象。 | 否
    `sender_id` | String | 根消息的发送者。 | 否
    `receiver_id` | String | 根消息的接收者。 | 否
    `create_time` | Long | 根消息的发送时间。 | 否
    `message_server_id` | Long | 根消息的服务器消息 ID。 | 否
    `message_client_id` | String | 根消息的客户端消息 ID。 | 否
   `thread_reply` | Object | 被回复的消息对象。 | 否
    `sender_id` | String | 被回复消息的发送者。 | 否
    `receiver_id` | String | 被回复消息的接收者。 | 否
    `create_time` | Long | 被回复消息的发送时间。 | 否
    `message_server_id` | Long | 被回复消息的服务器消息 ID。 | 否
    `message_client_id` | String | 被回复消息的客户端消息 ID。 | 否
 `total` | Long | Thread 下的消息总数。 | 是
 `timestamp` | Long | 查询时间戳。 | 是
 `messages` | Array of objects | 消息列表。 | 是
  `message_server_id` | Long | 服务端消息 ID。 | 是
  `sender_id` | String | 消息发送方账号 ID。 | 是
  `message_type` | Integer | 消息类型。0：文本；1：图片；2：语音；3：视频；4：地址位置；6：文件；10：提示；12：音视频话单；100：自定义。 | 是
  `create_time` | Long | 消息发送时间戳。 | 是
  `message_client_id` | String | 客户端消息 ID。 | 是
  `sender_client_type` | Integer | 消息发送端类型。1：AOS；2：iOS；4：PC；16：Web；32：REST；64：MAC；65：HARMONY。 | 是
  `text` | String | 文本消息内容或多媒体消息的描述文本（该描述信息可用于云端历史消息关键词检索）。 | 否
  `attachment` | Object | 多媒体消息的属性或自定义消息内容。 | 否
  `extension` | String | 消息发送时传入的第三方扩展字段。 | 否
  `team_id` | Long | 群组 ID。`team_id` 与 `receiver_id` 只会返回一个。 | 否
  `receiver_id` | String | 消息的接收者 ID。 | 否
  `receiver_account_ids` | Array of strings | 定向消息接收者账号 ID 列表。 | 否
  `inclusive` | Boolean | 定向消息接收者列表是为可读列表。true（默认）：可读；false：不可读。 | 否
  `new_member_visible` | Boolean | 新进群成员是否可查看该消息。true：可查看；false：不可查看。 | 否
  `sub_type` | Integer | 消息子类型。用于对消息进行二级分类，取值范围为大于 0 的正整数。推荐自定义消息类型使用此字段区分不同业务场景，其他消息类型可根据实际需求选择性使用。 | 否
  `conversation_type` | Integer | 会话类型。 | 否
  `modify_account_id` | String | 消息更新者的用户账号 ID。<br>只有消息被更新才会返回该字段。 | 否
  `modify_time` | Long | 消息的更新时间。<br>只有消息被更新才会返回该字段。 | 否
  `thread_config` | Object | Thread 消息配置项。 | 否
   `thread_root` | Object | Thread 根消息对象。 | 否
    `sender_id` | String | 根消息的发送者。 | 否
    `receiver_id` | String | 根消息的接收者。 | 否
    `create_time` | Long | 根消息的发送时间。 | 否
    `message_server_id` | Long | 根消息的服务器消息 ID。 | 否
    `message_client_id` | String | 根消息的客户端消息 ID。 | 否
   `thread_reply` | Object | 被回复的消息对象。 | 否
    `sender_id` | String | 被回复消息的发送者。 | 否
    `receiver_id` | String | 被回复消息的接收者。 | 否
    `create_time` | Long | 被回复消息的发送时间。 | 否
    `message_server_id` | Long | 被回复消息的服务器消息 ID。 | 否
    `message_client_id` | String | 被回复消息的客户端消息 ID。 | 否

### 响应体示例

```JSON
{
  "code": 200,
  "msg": "success",
  "data": {
    "total": 2,
    "messages": [
      {
        "text": "2025-07-31T16:50:03.534文本消息测试-单聊-检索检索8s4",
        "message_server_id": 158844553334358019,
        "sender_id": "yytest36",
        "message_client_id": "9eb34***83c92c53",
        "conversation_type": 2,
        "team_id": 2366968294,
        "create_time": 1753951804178,
        "message_type": 0,
        "thread_config": {
          "thread_root": {
            "sender_id": "yytest36",
            "receiver_id": "2366968294",
            "create_time": 1753951803793,
            "message_server_id": 158844553334358018,
            "message_client_id": "632938***96b183"
          },
          "thread_reply": {
            "sender_id": "yytest36",
            "receiver_id": "2366968294",
            "create_time": 1753951803793,
            "message_server_id": 158844553334358018,
            "message_client_id": "632938**596b183"
          }
        },
        "sender_client_type": 32
      },
      {
        "text": "{\"msg\":\"2025-07-31T16:50:03.534文本消息测试-单聊-检索检索8s4\"}",
        "extension": "ext",
        "message_server_id": 158844553334358020,
        "sender_id": "yytest36",
        "message_client_id": "7cdb4036-0***e03639c7",
        "conversation_type": 2,
        "team_id": 2366968294,
        "create_time": 1753951805248,
        "message_type": 0,
        "sub_type": 1,
        "receiver_account_ids": [
          "yytest69"
        ],
        "inclusive": true,
        "new_member_visible": false,
        "modify_account_id": "yytest36",
        "modify_time": 1753951811315,
        "thread_config": {
          "thread_root": {
            "sender_id": "yytest36",
            "receiver_id": "2366968294",
            "create_time": 1753951803793,
            "message_server_id": 158844553334358018,
            "message_client_id": "63293886***2596b183"
          },
          "thread_reply": {
            "sender_id": "yytest36",
            "receiver_id": "2366968294",
            "create_time": 1753951803793,
            "message_server_id": 158844553334358018,
            "message_client_id": "63293886***6b183"
          }
        },
        "sender_client_type": 32
      }
    ],
    "has_more": false,
    "timestamp": 1753951805248,
    "thread_root": {
      "text": "{\"msg\":\"2025-07-31T16:50:03.534文本消息测试-单聊-检索检索8s4\"}",
      "extension": "ext",
      "message_server_id": 158844553334358018,
      "sender_id": "yytest36",
      "message_client_id": "6329388***02596b183",
      "conversation_type": 2,
      "team_id": 2366968294,
      "create_time": 1753951803793,
      "message_type": 0,
      "sub_type": 1,
      "receiver_account_ids": [
        "yytest69"
      ],
      "inclusive": true,
      "new_member_visible": false,
      "modify_account_id": "yytest36",
      "modify_time": 1753951803914,
      "sender_client_type": 32
    }
  }
}
```

## 错误码

本文仅列举部分业务接口错误码，完整列表请参考客户端 API [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client)。

| 错误码 | 错误码描述 | 错误信息示例
| --- | --- | ---
| 200 | 请求成功 | success
| 414 | 参数错误 | parameter error
| 102404 | 用户不存在 | account not exist
| 108404 | 群不存在 | team not exist
| 500 | 服务器内部错误 | internal server error 