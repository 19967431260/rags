
云信服务端提供 API，支持批量查询某个频道下的多个 Thread 的根消息的 meta 信息（如总回复数和最后回复时间）。Thread 指以一条消息作为根消息的消息回复树状结构（更多介绍参见[会话消息回复（Thread）](https://doc.yunxin.163.com/messaging/docs/jg2MDk5NjA?platform=android)）。




## URL
```
POST  http://api.yunxinapi.com/nimserver/qchat/batchQueryThreadTalkMeta.action  HTTP/1.1
Content-Type: application/x-www-form-urlencoded;charset=utf-8

```


## 请求参数


- POST 请求中 Headers 的设置请参考[API调用方式](/docs/TM5MzM5Njk/jk3MzY2MTI)。

- POST 请求中 Body 的设置如下：

<table>
    <thead><tr> <th style="width:180px">参数</th><th style="width:100px">类型</th><th style="width:80px">是否必填</th><th>说明</th></tr></thead>
    <tr> <td>serverId</td><td>String</td><td>是</td><td>服务器 ID，服务器的唯一标识</td></tr>
      <tr> <td>channelId</td><td>String</td><td>是</td><td>频道 ID，频道唯一标识</td></tr>
        <tr> <td>accid</td><td>String</td><td>否</td><td>操作者的 IM 账号（accid），代表以谁的名义查询</td></tr>
        <tr> <td>queryMsgs</td><td>String</td><td>否</td><td><p>可以转成 JSON array，一次最多查询 100 条，每一个 JSON 报文包括 2 个字段：</p>

<ul><li>msgIdServer：云信服务端生成的消息 ID，即服务端消息 ID</li>
<li>msgTime：消息发送时间</li></ul>

<p>例子：[{"msgIdServer":12121,"msgTime":121},{"msgIdServer":122121,"msgTime":1221}]</p></td></tr>
</table>

## 返回参数

<div style="width:180px">参数</div>  |说明
---- | ---------------
code  | 状态码
data  | 查询到的 meta 信息，具体字段见下表



<div style="width:180px">data 的字段</div> | 说明
---- | -------------- | ---------
msgIdServer |  根消息的服务端消息 ID 
msgTime  | 根消息的发送时间
total   |   回复总数
timestamp | 最后一条回复的时间


## 示例

### cURL 请求示例


```
curl -X POST -H "AppKey: go9dnk49bkd9jd9vmel1kg******mgq3" -H "Nonce: 4tgggergigwow323t23t" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf3e6f7316fcc55583f86" -H "Content-Type: application/x-www-form-urlencoded" -d 'serverId=1513535&channelId=123&queryMsgs=[{"msgIdServer":12121,"msgTime":121},{"msgIdServer":122121,"msgTime":1221}]' 'http://api.yunxinapi.com/nimserver/qchat/batchQueryThreadTalkMeta.action'
```


### 返回示例
HTTP 响应：JSON
```
"Content-Type": "application/json; charset=utf-8"
{
    "code":200,
    "data": 
    [
       {
         "msgIdServer":"125",
         "msgTime":"1650284147766",
         "total":6
         "timestamp":"1650284149000"
       },
       {
          "msgIdServer":"125",
         "msgTime":"1650284147866",
         "total":3
         "timestamp":"1650284149999",
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
