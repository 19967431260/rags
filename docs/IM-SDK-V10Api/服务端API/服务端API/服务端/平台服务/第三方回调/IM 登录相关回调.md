

## <span id='登录回调'>登录回调</span> 

   
### HTTP示例

``` http
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
AppKey: 1589838**d219453d6542
CurTime: 1541583920979
MD5: e89c284a5ad9a76b3176e23108920f81
CheckSum: 6f08c5ee2dd16a5fc34a12005e5d5f1411e657a1
Content-Type: application/json
Cache-Control: no-cache

{"eventType":36,"fromAccount":"wm1","fromClientIp":"36.18.111.225","fromClientPort":"39632","fromClientType":"AOS","fromDeviceId":"ef6b789c-3079-463b-a52b-4924ae539e01","msgFromAccid":"wm1","msgId":184409700039655569,"msgidClient":"b897b26234d246858031291f12bc498d","opeType":8,"time":1590482455336,"timestamp":"1590482457381","toAccount":"2747918666"}

```

### cURL示例

``` curl
curl -X POST \
  http://yunxinservice.com.cn/receiveMsg.action \
  -H 'appkey: 158983**d219453d6542' \
  -H 'cache-control: no-cache' \
  -H 'checksum: 6f08c5ee2dd16a5fc34a12005e5d5f1411e657a1' \
  -H 'content-type: application/json' \
  -H 'curtime: 1541583920979' \
  -H 'md5: e89c284a5ad9a76b3176e23108920f81' \
  -d '{"eventType":36,"fromAccount":"wm1","fromClientIp":"36.18.111.225","fromClientPort":"39632","fromClientType":"AOS","fromDeviceId":"ef6b789c-3079-463b-a52b-4924ae539e01","msgFromAccid":"wm1","msgId":184409700039655569,"msgidClient":"b897b26234d246858031291f12bc498d","opeType":8,"time":1590482455336,"timestamp":"1590482457381","toAccount":"2747918666"}'
```

### 消息体中的JSON字段说明

:::note notice
回调消息中并不是每个字段都会一定抄送，请注意对各字段的判空处理。
:::

<table><thead><tr><th style="width:160px">名称</th><th style="width:100px">类型</th><th style="width:80px">必须</th><th>说明</th></tr></thead>
<tr><td> eventType </td><td>Integer</td><td>是</td><td>值为36，表示是登录回调</td></tr>
<tr><td> fromAccount </td><td>String</td><td>是</td><td>操作者账号</td></tr>
<tr><td> fromDeviceId </td><td>String</td><td>是</td><td>操作者设备id</td></tr>
<tr><td> fromClientType </td><td>String</td><td>是</td><td>操作者客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)</td></tr>
<tr><td> fromClientIp </td><td>String</td><td>否</td><td>操作者的客户端IP地址<note type=notice>ipv4 地址或 ipv6 地址</note></td></tr>
<tr><td> fromClientPort </td><td>String</td><td>否</td><td>操作者的客户端端口号</td></tr>
<tr><td> token </td><td>String</td><td>是</td><td>登录token</td></tr>
<tr><td> authType </td><td>Integer</td><td>是</td><td>登录鉴权方式，0表示经典模式，1表示动态token模式，2表示基于第三方回调的校验模式（该模式下云信对token不会做校验）</td></tr>
<tr><td> loginExt </td><td>String</td><td>是</td><td>登录扩展字段。</td></tr>
<tr><td> customTag </td><td>String</td><td>是</td><td>登录自定义tag</td></tr>
<tr><td> customClientType </td><td>String</td><td>是</td><td>自定义端类型</td></tr>
<tr><td> autoLogin </td><td>Boolean</td><td>否</td><td>本次登录是否是自动登录</td></tr>
<tr><td> timestamp </td><td>String</td><td>是</td><td>操作时间，字符串类型</td></tr>

</table> 