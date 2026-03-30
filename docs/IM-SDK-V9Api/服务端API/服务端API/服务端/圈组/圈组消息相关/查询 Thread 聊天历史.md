云信服务端提供 API， 支持传入某个 Thread 的根消息的信息来查询该 Thread 的消息列表，即该 Thread 的聊天历史。Thread 指以一条消息作为根消息的消息回复树状结构（更多介绍参见[会话消息回复（Thread）](https://doc.yunxin.163.com/messaging/docs/jg2MDk5NjA?platform=android)）。

## URL
```
POST  http://api.yunxinapi.com/nimserver/qchat/queryThreadTalkHistory.action  HTTP/1.1
Content-Type: application/x-www-form-urlencoded;charset=utf-8
```


## 请求参数

- POST 请求中 Headers 的设置请参考[API调用方式](/docs/TM5MzM5Njk/jk3MzY2MTI)。

- POST 请求中 Body 的设置如下：
<table>
    <thead><tr> <th style="width:180px">参数</th><th style="width:100px">类型</th><th style="width:80px">是否必填</th><th>说明</th></tr></thead>
        <tr> <td>accid</td><td>String</td><td>否</td><td>操作者的 IM 账号（accid），代表以谁的名义查询</td></tr>
     <tr> <td>serverId</td><td>String</td><td>是</td><td>服务器唯一标识</td></tr>
        <tr> <td>channelId</td><td>String</td><td>是</td><td>频道唯一标识</td></tr>
        <tr> <td>excludeMsgId</td><td>String</td><td>否</td><td>排除的消息 ID，分页时请填写上一页最后一条消息的消息 ID，用于定位锚点<br>
        主要是为了处理分页时，边界上多条消息的发送时间戳相同的情况</td></tr>
      <tr> <td>fromTime</td><td>String</td><td>否</td><td>查询开始时间，默认 0</td></tr>
        <tr> <td>limit</td><td>String</td><td>否</td><td>查询条数上限，默认 100，最大 100</td></tr>
        <tr> <td>msgIdServer</td><td>String</td><td>是</td><td>云信服务器生成的 Thread 聊天的根消息 ID</td></tr>
        <tr> <td>msgTime</td><td>String</td><td>是</td><td>Thread 聊天的根消息的发送时间</td></tr>
        <tr> <td>reverse</td><td>String</td><td>否</td><td>是否逆序，默认false，表示从现在往过去查</td></tr>
            <tr> <td>toTime</td><td>String</td><td>否</td><td>查询结束时间，默认当前时间</td></tr>

</table>

## 返回参数




<div style="width:180px">参数</div> | 说明
---- | ----------------
code  |     状态码
threadMsg  |  根消息信息，具体包含字段的说明请参见[云端历史消息的 data 的字段说明](https://doc.yunxin.163.com/messaging/docs/zE5NjI2NDM?platform=server#返回参数)
total | 总回复数
timestamp | 最后一条回复的时间戳
msgs   | 该 Thread 的根消息以外的消息列表，具体包含的字段见下表





<div style="width:180px">msgs 的字段</div> | <div style="width:100px">类型</div>| 说明
---- | -------------- | ---------
fromAccount | String | 回复消息的发送方账号
fromNick | String | 回复消息的发送方昵称
fromClientType| String  | 回复消息的发送方所使用设备的类型，如 AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65) 等
time |  Long |  回复消息的发送时间
updateTime |Long |  回复消息的更新时间
status    | int | 	回复消息的消息状态，0 表示消息默认状态，1 表示撤回，2 表示删除，大于等于 10000 表示自定义状态
body |String | 回复消息的消息内容
attach  |String|   回复消息的附件
ext   |  String  | 回复消息的扩展字段
type   |  int  | 回复消息的类型，具体参见[发送消息](https://doc.yunxin.163.com/messaging/docs/zI5ODE5MzY?platform=server)中 type 的说明
msgIdServer  |Long   | 回复消息的服务端消息 ID 
msgIdClient |  Long | 回复消息的客户端消息 ID 
replyMsgIdClient |  Long  |  被回复消息的客户端消息 ID
replyMsgIdServer | Long   | 被回复消息的服务端消息 ID
replyMsgTime | Long  | 被回复消息的发送时间
replyMsgFromAccount| String | 被回复消息的账号
threadMsgIdClient  | Long | 根消息的客户端消息 ID
threadMsgIdServer | Long  | 根消息的服务端消息 ID 
threadMsgTime  | Long   | 根消息的发送时间
threadMsgFromAccount | String | 根消息的发送方账号



## 示例

### cURL 请求示例
```
curl -X POST -H "AppKey: go9dnk**1kglw0803mgq3" -H "Nonce: 4tggger**23t" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Content-Type: application/x-www-form-urlencoded" -d 'serverId=1513535&channelId=123&msgFromAccount=aaa&msgIdServer=121&msgTime=121&msgIdClient=sasasa' 'http://api.yunxinapi.com/nimserver/qchat/queryThreadTalkHistory.action'
```
### 返回示例
HTTP 响应：JSON
```
"Content-Type": "application/json; charset=utf-8"
{
    "code": 200,
    "threadMsg":
    {
        "fromAccount": "zhangsan",
        "fromNick": "张三",
        "fromClientType": "IOS",
        "time": 1650284147467,
        "updateTime": 1650284147467,
        "status": 1,
        "body": "哈哈哈",
        "attach": "abc",
        "ext": "ext123",
        "type": 0,
        "msgIdServer": 123,
        "msgIdClient": "qwerty1"
    },
    "total": 123,
    "timestamp": 12121,
    "msgs":
    [
        {
            "fromAccount": "lisi",
            "fromNick": "李四",
            "fromClientType": "IOS",
            "time": 1650284147500,
            "updateTime": 1650284147500,
            "status": 1,
            "body": "abc",
            "attach": "sasa",
            "ext": "sasa",
            "type": 0,
            "msgIdServer": 124,
            "msgIdClient": "qwerty2",
            "replyMsgIdClient": "qwerty1",
            "replyMsgIdServer": 123,
            "replyMsgTime": 1650284147467,
            "replyMsgFromAccount": "zhangsan",
            "threadMsgIdClient": "qwerty1",
            "threadMsgIdServer": 123,
            "threadMsgTime": 1650284147467,
            "threadMsgFromAccount": "zhangsan"
        },
        {
            "fromAccount": "wangwu",
            "fromNick": "王五",
            "fromClientType": "IOS",
            "time": 1650284147766,
            "updateTime": 1650284147766,
            "status": 1,
            "body": "abc",
            "attach": "sasa",
            "ext": "sasa",
            "type": 0,
            "msgIdServer": 125,
            "msgIdClient": "qwerty3",
            "replyMsgIdClient": "qwerty2",
            "replyMsgIdServer": 124,
            "replyMsgTime": 1650284147500,
            "replyMsgFromAccount": "lisi",
            "threadMsgIdClient": "qwerty1",
            "threadMsgIdServer": 123,
            "threadMsgTime": 1650284147467,
            "threadMsgFromAccount": "zhangsan"
        }
    ]
}
```
## 状态码

该接口在 HTTPS Body 中返回请求的状态码，以下仅列出与接口业务相关的状态码。完整状态码及说明请参见[状态码](https://doc.yunxin.163.com/messaging/docs/TM5NTk2Mzc?platform=server)。



|状态码 | 说明 | 处理建议|
|---- | -------------- | ---------|
| 200 | 请求成功  | - |
| 403 | 非法操作或没有权限 |   <ul><li>检查是否已开通圈组功能</li><li>检查是否已经开通圈组的会话消息回复（Thread）功能</li></ul>  |
| 404  |对象不存在 | <ul><li>检查传入的账号、消息 ID、服务器 ID、频道 ID 等信息是否存在</li><li>检查是否存在必传参数为空的问题</li></ul>|
| 414 | 参数错误 | 根据提示信息，检查传入参数的格式和限制条件|
| 416 |调用频率超限 | 降低调用频率 |
| 431 | HTTP 重复请求| -  |


