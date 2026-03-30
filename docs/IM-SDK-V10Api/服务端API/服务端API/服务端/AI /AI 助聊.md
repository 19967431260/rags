AI 助聊接口提供智能聊天辅助功能，帮助用户根据聊天场景和风格要求生成合适的回复建议，让用户可以快速选择合适的回复内容，提升社交互动体验。

## 调用频率

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging2/server-apis/DUzNjAzMTc?platform=server)。

## 请求信息

### 请求 URL

```
POST https://{endpoint}/ai/chat_assistant/v1/chat_assist
```

:::note note
请求 URL 中的 `{endpoint}` 代表服务地址域名，您可以根据用户服务区域选择中国大陆和海外服务地址，并支持搭建高可用主备域名机制。详情请参考 [调用方式](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#%E6%9C%8D%E5%8A%A1%E5%9C%B0%E5%9D%80) 服务地址章节。
:::

### 请求头参数

请求 Header 的参数说明请参考 [请求 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#请求-header)。

### 请求体参数

参数名称 | 类型 | 是否必选 | 说明 | <div style="width:185px">示例</div>
---- | ---- | ---- | ---- | ----
`sender_id` | String | 是 | 发送者账号 ID。 | yx1 |
`sender_tag_list` | Array of strings | 否 | 发送者标签，最大长度限制为 2000 字符。 | ["热情", "开朗", "喜欢足球"] |
`receiver_id` | String | 是 | 接收者账号 ID。 | yx2 |
`receiver_tag_list` | Array of strings | 否 | 接收者标签，最大长度限制为 2000 字符。 | ["漂亮", "性感"] |
`receiver_last_message` | String | 否 | 接收者发送的最后一句话，作为回复的主要依据，最大长度限制为 256 字符。 | 我今天的衣服漂亮吗？ |
`style_list` | Array of strings | 是 | 对话风格，指定回复的内容风格。<br>可选的风格：warm（温暖）、hot（热情）、smart（机智）、stochastic（随机）。最多默认可指定 3 种风格。<br>风格后续会持续补充。<note type=note><li>若选择 stochastic 风格，则建议传入 `sender_tag_list` 和 `receiver_tag_list` 字段，AI 模型会根据双方的标签人设信息生成比较贴近真人的对话内容。<li>选择 stochastic 风格后，每次对话可直接返回 5 条消息（回复中可能会包含其他风格）；选择 warm、hot、smart 风格，每次对话仅直接返回 1 条消息。因此请勿将 stochastic 风格与其他风格进行混用，若需要额外配置（定制风格或者指定风格单次返回的消息数量），请联系云信技术支持。 | [ "hot", "warm"] |
`history` | Array of objects | 否 | 聊天历史记录，用于提供对话上下文，最大长度为 1500 字符。<br>只支持 **文本** 内容，建议倒序填入最近的双方回复的文本消息（对方回复的最后一条除外）。 | [{<div style="padding-left: 20px;">"sender_id": "yx2",</div><div style="padding-left: 20px;">"text": "我买了一件衣服"</div>},<br>{<div style="padding-left: 20px;">"sender_id": "yx1",</div><div style="padding-left: 20px;">"text": "好看吗？"</div>},<br>{<div style="padding-left: 20px;">"sender_id": "yx2",</div><div style="padding-left: 20px;">"text": "我穿上给你看一下"</div>}] |
 `sender_id` | String | 是 | 历史消息的发送者账号 ID。 | yx1 |
 `text` | String | 是 | 历史消息的文本内容。 | 好看吗？ |

### 请求体示例

```JSON
{
    "style_list": [ "hot", "warm"],
    "sender_tag_list": ["热情", "开朗", "喜欢足球"],
    "receiver_tag_list": ["漂亮", "性感"],
    "receiver_last_message": "我今天的衣服漂亮吗？",
    "history": [
        {
            "sender_id": "yx2",
            "text": "我买了一件衣服"
        },{
            "sender_id": "yx1",
            "text": "好看吗？"
        },{
            "sender_id": "yx2",
            "text": "我穿上给你看一下"
        }
    ],
    "sender_id": "yx1",
    "receiver_id": "yx2"
}
```

## 响应信息

### 响应头参数

响应 Header 的参数说明请参考 [响应 Header](https://doc.yunxin.163.com/messaging2/server-apis/zcwODA3MTU?platform=server#响应-header)。

### 响应体参数

参数名称 | 类型 | 说明 | 是否必返回 |
---- | ---- | ---- | ----
`code` | Integer | 状态码，200 表示请求成功。 | 是
`msg` | String | 提示信息。请求失败时返回错误信息，请求成功时返回 "success"。 | 是
`data` | Object | 返回的 JSON 数据对象，请求失败则返回空对象。 | 是
 `items` | Array of objects | AI 助聊生成的回复列表，包含不同风格的回复建议。 | 是
  `style` | String | 回复消息的风格。 | 是
  `style_name` | String | 风格名称。 | 是
  `answer` | String | 回复的内容。 | 是

### 响应体示例

```JSON
{
    "code": 200,
    "msg": "success",
    "data": {
        "items": [
            {
                "style": "hot",
                "style_name": "升温热聊",
                "answer": "哇哦，必须漂亮啊，穿啥都好看！"
            },
            {
                "style": "warm",
                "style_name": "贴心暖男",
                "answer": "哇，超级漂亮，很适合你！"
            }
        ]
    }
}
```

## 错误码

本文仅列举部分业务接口错误码，完整列表请参考客户端 API [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client)。 <!-- IM V10 -->

| 错误码 | 错误码描述 | 错误信息示例
| ---- | ---- | ----
| 200 | 请求成功 | success
| 414 | 参数错误 | parameter error
| 102404 | 用户不存在 | account not exist
| 500 | 服务器内部错误 | internal server error