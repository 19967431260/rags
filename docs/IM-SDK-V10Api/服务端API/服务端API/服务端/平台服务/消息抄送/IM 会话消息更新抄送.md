网易云信服务端可以通过抄送功能将会话消息更新（单聊和群聊）的数据实时同步至您预设的服务器，满足您的应用对于会话更新数据的本地存储和相关业务处理的需求。

当消息更新时会触发该抄送，如编辑原消息等操作。

会话更新涉及的抄送类型（eventType）包括单聊消息更新抄送（89）、高级群聊消息更新抄送（90）以及超大群聊消息抄送（91），更多消息抄送类型请参见 [消息抄送类型](https://doc.yunxin.163.com/messaging/server-apis/jQ4ODE0NTY?platform=server#抄送消息类型)。

::: note note 
本文示例均假设您预设的服务器地址为`http://yunxinservice.com.cn/receiveMsg.action`。
:::

## 前提条件

本抄送功能需要单独开通后才能使用。如需开通，可通过云信控台自助开通（**应用管理**->**应用配置**->**消息抄送**->**抄送类型**->**IM 即时通讯**->**更新消息**），具体请参考 [开通和配置消息抄送](https://doc.yunxin.163.com/messaging/docs/jY5MDk1NTQ?platform=server)。

## 抄送数据 JSON 字段说明

以下字段信息，可抄送至您指定的服务器。

| 参数 | 类型 | 说明
| ---- | ---- | ----
| `eventType` | Integer | <li>值为 `89`，表示是单聊消息更新抄送。<li>值为 `90`，表示是高级群消息更新抄送。<li>值为 `91`，表示是超大群消息更新抄送。 |
| `from` | String | 消息发送者账号。 |
| `to` | String | 消息接收者账号 ID，或群组 ID。 |
| `msgId` | Long | 消息服务器 ID。 |
| `clientId` | String | 消息客户端 ID。 |
| `fromClientType` | String | 消息发送者客户端类型。 |
| `modifyAccountId` | String | 消息更新者账号 ID。|
| `modifyTime` | Long | 消息更新时间。 |
| `text` | String | 消息更新内容。 |
| `extension` | String | 消息更新的扩展字段。 |
| `subType` | Integer | 消息更新的消息子类型。 |
| `attachment` | String | 更新的消息附件。 |

## 请求示例（cURL）
                           
```cURL
curl -X POST \
  http://yunxinservice.com.cn/receiveMsg.action \
  -H 'appkey: 1589**19453d6542' \
  -H 'cache-control: no-cache' \
  -H 'checksum: 6f08c5ee2dd**d5f1411e657a1' \
  -H 'content-type: application/json' \
  -H 'curtime: 1541583920979' \
  -H 'md5: e89c284a5a**3108920f81' \
  -d '{"from": "t3","to": "t2","msgId": 1223,"clientId": "dddd","eventType": "89","modifyAccountId": "t3","modifyTime": 1608877682237,"text": "dfsfsffs"}'
```

## 请求示例（HTTP）

```HTTP
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
AppKey: 158983***453d6542
CurTime: 1541**20979
MD5: e89c28**08920f81
CheckSum: 6f08c5ee**e5d5f1411e657a1
Content-Type: application/json
Cache-Control: no-cache

{"from": "t3","to": "t2","msgId": 1223,"clientId": "dddd","eventType": "89","modifyAccountId": "t3","modifyTime": 1608877682237,"text": "dfsfsffs"} 
```