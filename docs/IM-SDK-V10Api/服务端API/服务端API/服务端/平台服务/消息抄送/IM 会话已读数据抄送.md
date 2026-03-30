
网易云信服务端可以通过抄送功能将会话（单聊和群聊）的已读数据实时同步至您预设的服务器，满足您的应用对于会话已读/未读数据的本地存储和相关业务处理的需求。

当客户端清理会话未读数时（标记为已读）会触发该抄送，如清空未读数等操作。

会话事件消息抄送对应的抄送类型（eventType）为 85，更多消息抄送类型请参见[消息抄送类型](https://doc.yunxin.163.com/messaging/docs/jQ4ODE0NTY?platform=server#%E6%8A%84%E9%80%81%E6%B6%88%E6%81%AF%E7%B1%BB%E5%9E%8B)。


::: note note 
本文示例均假设您预设的服务器地址为`http://yunxinservice.com.cn/receiveMsg.action`。
:::

## 前提条件

本抄送功能需要单独开通后才能使用。如需开通，可通过云信控台自助开通（**应用管理**->**应用配置**->**消息抄送**->**抄送类型**->**会话已读回执**），具体请参考[开通和配置消息抄送](https://doc.yunxin.163.com/messaging/docs/jY5MDk1NTQ?platform=server)。


## 抄送数据 JSON 字段说明

会话中的以下字段信息，可抄送至您指定的服务器。

参数 | 类型 | 说明
---- | -------------- | ---------
eventType|String|值为 85，表示是会话已读数据抄送事件
msgType | String |消息类型， 0：单聊会话的消息，1：群聊会话的消息
ackMsgTime |  Long  | 会话最后一条消息的已读时间戳。如果会话最后一条消息已读，则默认会话所有消息都已读
accid | String  | 发送已读动作的云信 accid
ackAccid | String | 已读会话对应的云信 accid，msgType 为 0 时可用
ackTeamId | String  | 已读会话对应的云信群组 id，msgType 为 1 时可用

## 请求示例（curl）

### **单聊会话已读**
```
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '{"ackAccid":"84851","msgType":"0","accid":"yx","eventType":"85","ackMsgTime":"1658283011566"}' 'http://yunxinservice.com.cn/receiveMsg.action'
```
### **群聊会话已读**

```
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '{"ackTeamId":"2348369454","msgType":"1","accid":"yx1","eventType":"85","ackMsgTime":"1658283965194"}' 'http://yunxinservice.com.cn/receiveMsg.action'
```

## 请求示例（HTTP）

### **单聊会话已读**
```
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前UTC时间戳，从1970年1月1日0点0 分0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx   //根据请求中的request body计算出来的MD5值。
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01

{"ackAccid":"84851","msgType":"0","accid":"yx","eventType":"85","ackMsgTime":"1658283011566"}
```
### **群聊会话已读**

```
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前UTC时间戳，从1970年1月1日0点0 分0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx   //根据请求中的request body计算出来的MD5值。
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01

{"ackTeamId":"2348369454","msgType":"1","accid":"yx1","eventType":"85","ackMsgTime":"1658283965194"}
```




  







