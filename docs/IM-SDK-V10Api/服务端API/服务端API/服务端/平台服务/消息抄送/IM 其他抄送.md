除消息抄送和会话抄送以外，网易云信即时通讯 IM 还提供涉及 IM 其他功能模块的抄送服务，如登录登出相关事件抄送、群聊相关抄送、聊天室相关抄送等。您可以通过这些抄送功能，将相应的数据同步至您指定的本地服务器。

::: note note
本文示例均假设您指定的接收抄送的服务器地址为 `http://yunxinservice.com.cn/receiveMsg.action`。
:::

## <span id='登录事件消息抄送'>登录事件消息抄送</span>

```
"eventType" = "2"
```

::: note notice
- 需要在 [网易云信控制台](https://app.yunxin.163.com/global/home) 单独开通。
- 如果使用消息抄送功能来实现在线状态，需要注意登录登出消息抄送并不一定成对出现，可能出现乱序或丢失，因此，需要解析登录登出消息抄送的时间戳字段 `timestamp` 并将其维护为在线状态时间戳，如果新到达的登录登出消息抄送时间戳小于已保存的在线状态时间戳，则需要忽略新到达的登录登出抄送。
:::

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
Content-Type: application/json
CurTime: 1440570500855 // 当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx // 根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
   "clientType": "AOS",
   "code": "200",
   "clientIp": "60.2*.**.202",
   "customTag": "登录自定义字段",
   "accid": "t3",
   "sdkVersion": "152",
   "eventType": "2",
   "deviceId": "c25f82d0-5f2e-492f-b5cc-3f4a585c25a2",
   "timestamp": "1608877682237"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "accid": "t3",
   "clientIp": "60.2*.**.202",
   "clientType": "AOS",
   "code": "200",
   "eventType": "2",
   "sdkVersion": "152",
   "timestamp": "1608877682237"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 2，表示是登录事件的消息
accid | String | 发生登录事件的用户账号，字符串类型
clientIp | String | 登录时的 IP 地址<note type=notice>ipv4 地址或 ipv6 地址
clientType | String | 客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
code | String | 登录事件的返回码，可转为 Integer 类型数据
sdkVersion | String | 当前 SDK 的版本信息，字符串类型
sdkHumanVersion | String | 当前 SDK 的可读版本信息，字符串类型
timestamp | String | 登录事件发生时的时间戳，可转为 Long 型数据

## <span id='登出事件消息抄送'>登出事件消息抄送</span>

```
"eventType"="3"
```

:::note note
- 当终端用户主动登出、被踢出、断网离线、应用被清理后，网易云信将会发起登出事件抄送。需要在 [网易云信控制台](https://app.yunxin.163.com/global/home) 单独开通。
- 如果使用消息抄送功能来实现在线状态，需要注意登录登出消息抄送并不一定成对出现，可能出现乱序或丢失，因此，需要解析登录登出消息抄送的时间戳字段 `timestamp` 并将其维护为在线状态时间戳，如果新到达的登录登出消息抄送时间戳小于已保存的在线状态时间戳，则需要忽略新到达的登录登出抄送。
:::

### <span id='HTTP 示例'>HTTP 示例</span>

```http
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
Content-Type: application/json
CurTime: 1440570500855 //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
   "clientType": "iOS",
   "code": 200,
   "accid": "tes",
   "sdkVersion": "155",
   "eventType": "3",
   "timestamp": 1608872658452
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "accid": "tes",
   "clientType": "IOS",
   "code": "200",
   "eventType": "3",
   "sdkVersion": "155",
   "timestamp": "1608872658452"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
登出事件消息中，`clientIp` 字段并不一定保证抄送。登录事件消息中的该字段是一定保证抄送的。
:::

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 3，表示是登出事件的消息
accid | String | 发生登出事件的用户账号，字符串类型
clientIp | String | 登出时的 IP 地址<note type=notice>ipv4 地址或 ipv6 地址
clientType | String | 客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
code | String | 登出事件的返回码，可转为 Integer 类型数据
sdkVersion | String | 当前 SDK 的版本信息，字符串类型
sdkHumanVersion | String | 当前 SDK 的可读版本信息，字符串类型
timestamp | String | 登出事件发生时的时间戳，可转为 Long 型数据
logOutReason | Integer| 登出原因：<li>1：用户注销<li>2：用户断开连接<li>3：用户被自己其它端踢下线<li>4：根据互踢策略被踢下线

## <span id='聊天室消息抄送'>聊天室消息抄送</span>

```
"eventType" = "4"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
Content-Type: application/json
CurTime: 1440570500855 //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
   "attach": "{\"type\": 1, \"data\": {\"value\": 3}}",
   "eventType": "4",
   "ext": "{\"type\": -2}",
   "fromAccount": "zqpret1101",
   "fromAvator": "",
   "fromClientType": "WEB",
   "fromExt": "",
   "fromNick": "zhangsan",
   "msgTimestamp": "1456123424339",
   "msgType": "CUSTOM",
   "msgidClient": "e4d9065fdb5fde927b16d87b7e861d46",
   "resendFlag": "0",
   "roleInfoTimetag": "1456123382533",
   "roomId": "2016"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "attach":"{\"type\":1,\"data\":{\"value\":3}}",
   "eventType":"4",
   "ext":"{\"type\":-2}",
   "fromAccount":"zhangsan",
   "fromAvator":"",
   "fromClientType":"WEB",
   "fromExt":"",
   "fromNick":"zhangsan",
   "msgTimestamp":"1456123424339",
   "msgType":"CUSTOM",
   "msgidClient":"e4d9065fdb5fde927b16d87b7e861d46",
   "resendFlag":"0",
   "roleInfoTimetag":"1456123382533",
   "roomId":"2016"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
聊天室类型消息中，并不是每个字段都会一定抄送，请注意对各字段的判空处理。一般情况下必有的字段为 eventType、attach、fromAccount、msgTimestamp、msgType、msgidClient、roomId。
:::

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 4，表示是聊天室消息
attach | String | 消息内容，若 msgType 为 CUSTOM 自定义消息，该字段为 JSON 格式。否则该字段为普通字符串类型
ext | String | 第三方扩展字段, 格式不限，长度限制 4096，字符串类型
fromAccount | String | 消息发送者的账号，字符串类型
fromAvator | String | 发送者的头像，字符串类型
fromClientType | String | 客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
fromExt | String | 发送者身份的扩展字段，您可以自定义，字符串类型
fromNick | String | 发送方昵称，字符串类型
msgTimestamp | String | 消息发送的时间戳
msgType | String | 消息类型：<br>TEXT、<br>PICTURE、<br>AUDIO、<br>VIDEO、<br>LOCATION、<br>FILE、//文件消息 <br>NETCALL_AUDIO、//网络电话音频聊天 <br>NETCALL_VEDIO、//网络电话视频聊天 <br>DATATUNNEL_NEW、//新的数据通道请求通知 <br>TIPS、//提示类型消息 <br>CUSTOM //自定义消息<br>
msgidClient | String | 客户端生成的消息 ID
resendFlag | String | 重发标记：0 不是重发, 1 是重发
roleInfoTimetag | String | 消息发送者用户名片的最后更新时间，可转为 Long 型数据
roomId | String | 消息所属的聊天室 ID，可转为 Long 型数据
antispam | String | 标识是否被反垃圾，仅在被反垃圾时才有此字段，可转为 Boolean 类型数据
yidunRes | String | 安全通反垃圾的原始处理细节，只有接入了相关功能安全通反垃圾的应用才会有这个字段。请参考以下 4.4.1、聊天室：发送文本消息 和 4.4.2、聊天室：发送图片消息的举例说明。<br>该字段中子字段释义如下：<br>老版本安全通反垃圾：<br>yidunBusType：0：文本反垃圾业务。1、图片反垃圾业务。2、用户资料反垃圾业务。3、用户头像反垃圾业务。<br>action：处理结果：检测结果，0：通过，1：嫌疑，2：不通过。（只有 yidunBusType 为 0 或 2 时，抄送时才有此字段）<br>labels：具体的反垃圾判断细节：<br>文本类反垃圾参考 <br><a href="http://support.dun.163.com/documents/2018041901?docId=150425947576913920">labels 字段的释义</a><br>图片类反垃圾参考 <br><a href="http://support.dun.163.com/documents/2018041902?docId=150429557194936320">labels 字段的释义</a><br>备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br><br>新版本安全通反垃圾：<br>yidunApiVersion：安全通反垃圾接口版本。2、新版本安全通反垃圾接口。<br>yidunBusType：0：文本反垃圾业务。1、图片反垃圾业务。2、用户资料反垃圾业务。3、用户头像反垃圾业务。<br>result：具体的反垃圾返回结果：<br>文本类反垃圾参考 <br><a href="http://support.dun.163.com/documents/2018041901?docId=589310433773625344">labels 字段的释义</a><br>图片类反垃圾参考 <br><a href="http://support.dun.163.com/documents/2018041901?docId=588512292354793472">labels 字段的释义</a><br>备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br><br>
2021 年 9 月 28 日 19:29 前接入安全通的客户，需要升级到最新版安全通，才可使用新版本能力。升级安全通请联系商务经理。2021 年 9 月 28 日 19:29 后接入安全通的客户，将自动开通此能力。

### <span id='消息抄送详细示例'>消息抄送详细示例</span>

#### **<span id='文本消息'>文本消息抄送示例</span>**

```json
{
   "attach": "聊天室文本消息",
   "eventType": "4",
   "ext": "",
   "fromAccount": "zhangsan",
   "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
   "fromClientType": "REST",
   "fromNick": "zhangsan",
   "msgTimestamp": "1456986458240",
   "msgType": "TEXT",
   "msgidClient": "wangwue-12345-9876543210123",
   "resendFlag": "0",
   "roleInfoTimetag": "0",
   "roomId": "64",
   "yidunRes": "{\"yidunBusType\":0,\"action\":0,\"labels\":[]}"
}
```

`attach` 字段说明：参考 P2P 消息中的文本消息中 attach 字段释义。

#### **<span id='图片消息'>图片消息抄送示例</span>**

```json
{
   "attach": "{\"md5\": \"d0323f8d447abf3df7256bd66f9d5b62\", \"h\": 500, \"ext\": \"jpg\", \"size\": 9093, \"w\": 500, \"name\": \"图片发送于 2016-03-02 18:29\", \"url\": \"http:\\/\\/b12026.nos.netease.com\\/MTAxMTAxMA==\\/bmltYV8xNDI5MTVfMTQ1NTY4NzIxMDkyNl84NzBmZjY5Ni0yOGI5LTRiZDgtYjQ4Yy02ZmVjYWI0NjcxM2Y=\"}",
   "eventType": "4",
   "ext": "",
   "fromAccount": "zhangsan",
   "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
   "fromClientType": "REST",
   "fromNick": "zhangsan"
   "msgTimestamp": "1456974764820",
   "msgType": "PICTURE",
   "msgidClient": "abcde-12345-987654",
   "resendFlag": "0",
   "roleInfoTimetag": "0",
   "roomId": "113",
   "yidunRes": "{\"yidunBusType\":1,\"labels\":[{\"level\":0,\"rate\":0.0,\"label\":100},{\"level\":0,\"rate\":0.0,\"label\":200},{\"level\":0,\"rate\":0.0,\"label\":110},{\"level\":0,\"rate\":0.0,\"label\":400},{\"level\":0,\"rate\":0.0,\"label\":300},{\"level\":0,\"rate\":0.0,\"label\":210}]}"
}
```  

`attach` 字段说明：参考 P2P 消息中的图片消息中 attach 字段释义。


#### **<span id='音频消息'>音频消息抄送示例</span>**

```json
{
   "attach": "{\"size\": 13738, \"ext\": \"aac\", \"dur\": 3808, \"url\": \"http:\\/\\/b12026.nos.netease.com\\/MTAxMTAxMA==\\/bmltYV8xNDI5MTVfMTQ1NTY4NzIxMDkyNl9lOWExMmNmMy1lZDhkLTQ2Y2UtYWRiYS1mOTA4ODhjZTliNTM=\", \"md5\": \"35411b36f22077309daec3b970b46e89\"}",
   "eventType": "4",
   "ext": "",
   "fromAccount": "zhangsan",
   "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
   "fromClientType": "REST",
   "fromNick": "zhangsan",
   "msgTimestamp": "1456983964169",
   "msgType": "AUDIO",
   "msgidClient": "abcde-12345-98765432",
   "resendFlag": "0",
   "roleInfoTimetag": "0",
   "roomId": "113"
}
```

`attach` 字段说明：参考 P2P 消息中的音频消息中 attach 字段释义。

#### **<span id='视频消息'>视频消息抄送示例</span>**

```json
{
   "attach": "{\"dur\":1473,\"ext\":\"mp4\",\"h\":480,\"md5\":\"6ba2b50225469d46263ba70736c37cd3\",\"size\":150495,\"url\":\"http:\\/\\/b12026.nos.netease.com\\/MTAxMTAxMA==\\/bmltYV8xNDI5MTVfMTQ1NTY2MjI5MzcxMV9kMjA3NjMwYy1lZjkzLTQ1OWYtYjJhZi0yMzVjOGJhYmI2MzA=\",\"w\":360}",
   "eventType": "4",
   "ext": "",
   "fromAccount": "zhangsan",
   "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
   "fromClientType": "REST",
   "fromNick": "zhangsan",
   "msgTimestamp": "1456985454300",
   "msgType": "VIDEO",
   "msgidClient": "abcde-12345-9876543210",
   "resendFlag": "0",
   "roleInfoTimetag": "0",
   "roomId": "64"
}
```

`attach` 字段说明：参考 P2P 消息中的视频消息中 attach 字段释义

#### **<span id='地理位置消息'>地理位置消息抄送示例</span>**

```json
{
    "attach": "{\"lat\":30.18704515647036,\"lng\":120.1908686708565,\"title\":\"中国 浙江省 杭州市 网商路 599 号\"}",
    "eventType": "4",
    "ext": "",
    "fromAccount": "zhangsan",
    "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
    "fromClientType": "REST",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456986934675",
    "msgType": "LOCATION",
    "msgidClient": "abcde-12345-98765432101234567",
    "resendFlag": "0",
    "roleInfoTimetag": "0",
    "roomId": "64"
}
```

`attach` 字段说明：参考 P2P 消息中的地理位置消息中 attach 字段释义。

 
#### **<span id='文件消息'>文件消息抄送示例</span>**

```json
{
    "attach": {
        "ext": "ttf",
        "md5": "79d62a35fa3d34c367b20c66afc2a500",
        "name": "BlizzardReg.ttf",
        "size": "91680",
        "url": "http://nimtest.nos.netease.com/08c9859d-183f-4daa-9904-d6cacb51c95b"
    },
    "eventType": "4",
    "ext": "",
    "fromAccount": "zhangsan",
    "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
    "fromClientType": "REST",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456987025760",
    "msgType": "FILE",
    "msgidClient": "abcde-12345-987654321012345678",
    "resendFlag": "0",
    "roleInfoTimetag": "0",
    "roomId": "64"
}
```

`attach` 字段说明：参考 P2P 消息中的发送文件消息中 attach 字段释义。


#### **<span id='自定义消息'>自定义消息抄送示例</span>**

```json
{
    "attach": "{\"myKey1\":\"myValue1\",\"myKey2\":10}",
    "eventType": "4",
    "ext": "",
    "fromAccount": "zhangsan",
    "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
    "fromClientType": "REST",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456987119256",
    "msgType": "CUSTOM",
    "msgidClient": "abcde-12345-9876543210123456789",
    "resendFlag": "0",
    "roleInfoTimetag": "0",
    "roomId": "64"
}
```

`attach` 字段说明：由第三方自己定义并解析相应的 Key-Value 值。
 
SDK 中定义的几类自定义消息释义：

- 剪刀石头布（type = 1）：

```JSON
{
    "attach": "{\"type\": 1, \"data\": {\"value\": 3}}",
    "eventType": "4",
    "ext": "{\"type\": -2}",
    "fromAccount": "zhangsan",
    "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
    "fromClientType": "IOS",
    "fromExt": "",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456987221992",
    "msgType": "CUSTOM",
    "msgidClient": "aba76741-f5c4-40ce-9f84-4b76c89d9b71",
    "resendFlag": "0",
    "roleInfoTimetag": "1456987212647",
    "roomId": "64"
}
```

`attach` 字段说明：

```json
{
    "type": 1,                                   // type=1 表示是剪刀石头布
    "data": {
        "value": 3                                // 1：石头。2：剪刀。3：布
    }
}
```
 
- 贴图表情（type = 3）：

```json
{
    "attach": "{\"type\":3,\"data\":{\"catalog\":\"xxy\",\"chartlet\":\"xxy001\"}}",
    "eventType": "4",
    "ext": "",
    "fromAccount": "zhangsan",
    "fromAvator": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzODg2NDI4ODE0Ml81NjM3ZTIxMC1iMjE5LTRhYjgtOGZlOS02MzBjZWFjYmMwZDE=",
    "fromClientType": "REST",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456987840942",
    "msgType": "CUSTOM",
    "msgidClient": "abcde-12345-987654321012345678901",
    "resendFlag": "0",
    "roleInfoTimetag": "0",
    "roomId": "64"
}
```
     
`attach` 字段说明：

```JSON
{
    "type": 3,                                          // type=3 表示是贴图表情
    "data": {
        "catalog": "xxy",                               // 贴图所在文件夹的名称
        "chartlet": "xxy002"                            // 贴图文件的名称
    }
}
```

## <span id='单聊消息撤回抄送'>单聊消息撤回抄送</span>

```
"eventType"="7"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "clientId": "9e549196-1bb4-4143-a428-d13eaa0cd732",
    "deleteTime": "1487308054709",
    "eventType": "7",
    "from": "zhangsan",
    "fromClientType": "IOS",
    "msgId": "11555996",
    "selfMsg": "撤回了一条消息",
    "sendTime": "1487308046652",
    "to": "lisi"
}
```  

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "clientId": "9e549196-1bb4-4143-a428-d13eaa0cd732",
   "deleteTime": "1487308054709",
   "eventType": "7",
   "from": "zhangsan",
   "fromClientType": "IOS",
   "msgId": "11555996",
   "selfMsg": "撤回了一条消息",
   "sendTime": "1487308046652",
   "to": "lisi"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明：'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 7，表示是一个单聊消息撤回抄送事件
clientId | String | 客户端 ID，字符串类型
deleteTime | String | 消息撤回时间，13 位时间戳
from | String | 用户账号，消息发送者，字符串类型
fromClientType | String | 消息撤回时的客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
msgId | String | 撤回的消息的服务端 ID，可转为 Long 值
selfMsg | String | 撤回消息的附言，字符串类型
sendTime | String | 消息发送的时间，13 位时间戳
to | String | 用户账号，消息接收者，字符串类型
attach | String | 消息撤回自定义扩展字段，字符串类型

## <span id='群聊消息撤回抄送'>群聊消息撤回抄送</span>

```
"eventType"="8"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "clientId": "3651689e-53a0-4a1c-beba-7e3703203ef6",
    "deleteTime": "1487309158801",
    "eventType": "8",
    "from": "zhangsan",
    "fromClientType": "IOS",
    "msgId": "927914262574",
    "selfMsg": "撤回了一条消息",
    "sendTime": "1487309155228",
    "to": "13827"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "clientId": "3651689e-53a0-4a1c-beba-7e3703203ef6",
   "deleteTime": "1487309158801",
   "eventType": "8",
   "from": "zhangsan",
   "fromClientType": "IOS",
   "msgId": "927914262574",
   "selfMsg": "撤回了一条消息",
   "sendTime": "1487309155228",
   "to": "13827"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 8，表示是一个群聊消息撤回抄送事件
clientId | String | 客户端 ID，字符串类型
deleteTime | String | 消息撤回时间，13 位时间戳
from | String | 用户账号，消息发送者，字符串类型
fromClientType | String | 消息撤回时的客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
msgId | String | 撤回的消息的服务端 ID，可转为 Long 值
selfMsg | String | 撤回消息的附言，字符串类型
sendTime | String | 消息发送的时间，13 位时间戳
to | String | 群 ID，可转为 Long 值
attach | String | 消息撤回自定义扩展字段，字符串类型


## <span id='超大群聊消息撤回抄送'>超大群聊消息撤回抄送</span>

```
"eventType"="25"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "clientId": "3651689e-53a0-4a1c-beba-7e3703203ef6",
    "deleteTime": "1487309158801",
    "eventType": "25",
    "from": "zhangsan",
    "fromClientType": "IOS",
    "msgId": "927914262574",
    "selfMsg": "撤回了一条消息",
    "sendTime": "1487309155228",
    "to": "13827"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "clientId": "3651689e-53a0-4a1c-beba-7e3703203ef6",
   "deleteTime": "1487309158801",
   "eventType": "8",
   "from": "zhangsan",
   "fromClientType": "IOS",
   "msgId": "927914262574",
   "selfMsg": "撤回了一条消息",
   "sendTime": "1487309155228",
   "to": "13827"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 25，表示是一个超大群聊消息撤回抄送事件
clientId | String | 客户端 ID，字符串类型
deleteTime | String | 消息撤回时间，13 位时间戳
from | String | 用户账号，消息发送者，字符串类型
fromClientType | String | 消息撤回时的客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
msgId | String | 撤回的消息的服务端 ID，可转为 Long 值
selfMsg | String | 撤回消息的附言，字符串类型
sendTime | String | 消息发送的时间，13 位时间戳
to | String | 群 ID，可转为 Long 值

## <span id='聊天室成员进出聊天室事件抄送'>聊天室成员进出聊天室事件抄送</span>

```
"eventType"="9"
```

:::note note
- 本抄送包含 **创建者或管理员进出聊天室事件抄送** 和 **全员进出聊天室抄送**。您可以自行在 [网易云信控制台](https://app.yunxin.163.com/global/home) 开通这两种抄送。
- 如果需要开通全员进出聊天室抄送，需要先开通创建者或管理员进出聊天室事件抄送功能。
:::

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST /receiveMsg.action HTTP/1.1
Host: yunxinservice.com.cn
Content-Type: application/json
CurTime: 1440570500855 // 当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx // 根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "roomId": "1001",
    "event": "IN",
    "accid": "test",
    "clientIp": "192.1**.*.100",
    "clientType": "PC",
    "code": "200",
    "eventType": "9",
    "sdkVersion": "18",
    "timestamp": "1452504942126"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "roomId": "1001",
   "event": "IN",
   "accid": "test",
   "clientIp": "192.1**.*.100",
   "clientType": "PC",
   "code": "200",
   "eventType": "9",
   "sdkVersion": "18",
   "timestamp": "1452504942126"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
聊天室进出抄送消息中，并不是每个字段都会一定抄送，请注意对各字段的判空处理。一般情况下必有的字段为 eventType、roomId、event、accid、code。
:::

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 9，表示聊天室成员（包括创建者、管理员以及普通成员）进出聊天室事件抄送。
roomId | String | 聊天室 ID。
event | String | 进入或退出。<li>IN：进入聊天室。<li>OUT：主动退出聊天室，或掉线。<li>KICK：被踢出聊天室。<note type=notice>不包括成员被拉黑导致踢出聊天室的情况，即该情况没有抄送。
accid | String | 用户账号，字符串类型。
clientIp | String | 客户端的 IP 地址，OUT 时不保证能提供此字段。<note type=notice>ipv4 地址或 ipv6 地址。
clientType | String | 客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型。
code | String | 返回码，可转为 Integer 类型数据。
sdkVersion | String | 当前 SDK 的版本信息，字符串类型。
timestamp | String | 事件发生时的时间戳，可转为 Long 型数据。
roleType | String | 成员角色。<li>0：普通用户<li>1：创建者<li>2：管理员<li>3：临时用户(游客)<li>4：匿名用户<li>-1：受限用户(禁言、黑名单)
anonymous | String | 是否匿名登录，true 表示是匿名登录，可转化为 Boolean 类型。
tags | String | 针对聊天室标签功能：用户登录聊天室时设置的 tags 信息。
notifyTargetTags | String | 针对聊天室标签功能：用户登录聊天室时设置的 notifyTargetTags 信息。
logOutReason | String | 聊天室离线原因抄送。<li>OFFLINE：成员离线<li>KICK：成员被强制移除<li>LOGIN_KICK：被自己其它端强制下线<li>EXIT：成员主动退出<br>要获取该字段，需要您在 <a href="https://app.yunxin.163.com/global/home">网易云信控制台</a> 开启 <b>聊天室离线原因抄送配置。
ext | String | 扩展字段。


## <span id='专线电话通话结束回调抄送'>专线电话通话结束回调抄送</span>

```
"eventType"="10"
```

:::note note
- 新版专线电话抄送由 `"type":"CALL"` 标识，请以实际收到的内容为准。
- 需要单独开通，如有需要，请联系相关网易云信商务经理。
:::

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```
 
双人专线电话示例：

```json
{
    "callback": "{\"callee\":\"15967161***\",\"caller\":\"18605815***\",\"createtime\":1484118614911,\"durationSec\":0,\"initAccount\":\"abcd\",\"legs\":[{\"endTime\":\"2017-01-11 15:10:30\",\"endpoint\":\"18605815***\",\"hangCause\":\"NO_USER_RESPONSE\"},{\"endTime\":\"2017-01-11 15:10:30\",\"endpoint\":\"15967161***\",\"hangCause\":\"NO_USER_RESPONSE\"}],\"session\":\"7c4b7673-4f70-4164-82a0-decb84d77914\",\"starttime\":\"2017-01-11 15:10:30\",\"status\":\"SUCCESS\"}",
    "eventType": "10"
}
```

专线会议示例：

```json
{
    "callback": "{\"createtime\":1484103244***,\"durationSec\":0,\"initAccount\":\"call817\",\"members\":\"[\\\"18605811***\\\",\\\"18158125***\\\",\\\"15967169***\\\"]\",\"session\":\"4ea1e712-cfd5-4891-b66a-4aa71fe65383\",\"starttime\":\"2017-01-11 10:52:38\",\"status\":\"SUCCESS\"}",
    "eventType": "10"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
//双人专线电话示例
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
    "callback": "{\"callee\":\"15967161234\",\"caller\":\"18605815***\",\"createtime\":1484118614911,\"durationSec\":0,\"initAccount\":\"abcd\",\"legs\":[{\"endTime\":\"2017-01-11 15:10:30\",\"endpoint\":\"18605815***\",\"hangCause\":\"NO_USER_RESPONSE\"},{\"endTime\":\"2017-01-11 15:10:30\",\"endpoint\":\"15967161***\",\"hangCause\":\"NO_USER_RESPONSE\"}],\"session\":\"7c4b7673-4f70-4164-82a0-decb84d77914\",\"starttime\":\"2017-01-11 15:10:30\",\"status\":\"SUCCESS\"}",
    "eventType": "10"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

```cURL
// 专线会议示例
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
    "callback": "{\"createtime\":1484103244335,\"durationSec\":0,\"initAccount\":\"call817\",\"members\":\"[\\\"18605811***\\\",\\\"18158125678\\\",\\\"15967169***\\\"]\",\"session\":\"4ea1e712-cfd5-4891-b66a-4aa71fe65383\",\"starttime\":\"2017-01-11 10:52:38\",\"status\":\"SUCCESS\"}",
    "eventType": "10"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 值为 10，特别注意这里是 10，表示是一个专线电话通话结束回调事件
callback | String | 话单回调的具体内容，为 String 类型，可转为 JSONObject

## <span id='短信回执抄送'>短信回执抄送</span>

```
"eventType"="11"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "eventType": "11",
    "objects": [
        {
            "mobile": "12345678945",
            "sendid": "1490",
            "result": "DELIVRD",
            "sendTime": "2017-06-02 14:40:45",
            "reportTime": "2017-06-06 10:40:30",
            "spliced": "1",
            "templateId": 1234
        },
        {
            "mobile": "12345678945",
            "sendid": "1491",
            "result": "DELIVRD",
            "sendTime": "2017-06-02 14:41:00",
            "reportTime": "2017-06-02 10:41:20",
            "spliced": "2",
            "templateId": 1234
        }
    ]
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '{
   "eventType": "11",
   "objects": [
      {
         "mobile": "12345678945",
         "sendid": "1490",
         "result": "DELIVRD",
         "sendTime": "2017-06-02 14:40:45",
         "reportTime": "2017-06-06 10:40:30",
         "spliced": "1",
         "templateId": 1234
      },
      {
         "mobile": "12345678945",
         "sendid": "1491",
         "result": "DELIVRD",
         "sendTime": "2017-06-02 14:41:00",
         "reportTime": "2017-06-02 10:41:20",
         "spliced": "2",
         "templateId": 1234
      }
   ]
}' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型 
objects | Array of objects | 短信回执详情
 mobile | String | 手机号码
 sendid | String | 短信发送接口返回的 sendid
 result | String | 运营商返回的短信发送状态码
 sendTime | String | 短信发送时间，调用 [sms-api](https://doc.yunxin.163.com/sms/server-apis/jg2NDEyMzI?platform=server) 接口发送短信的时间
 reportTime | String | 运营商返回的短信送达时间
 spliced | String | 短信计费条数
 templateId | Long | 短信对应的模版 ID

## <span id='短信上行抄送'>短信上行抄送</span>

```
"eventType"="12"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```
```json
{
    "eventType": "12",
    "objects": "[{ \"mobile\": \"18605818212\", \"content\": \"TD\", \"replytime\": \"2017-09-20 10:40:30\"},{ \"mobile\": \"18605818213\", \"content\": \"TD\", \"replytime\": \"2017-09-20 10:40:30\" }]"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "eventType": "12",
   "objects": "[{ \"mobile\": \"18605818***\", \"content\": \"TD\", \"replytime\": \"2017-09-20 10:40:30\"},{ \"mobile\": \"18605818***\", \"content\": \"TD\", \"replytime\": \"2017-09-20 10:40:30\" }]"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明 
--- | --- | --- 
eventType | String | 抄送事件类型
objects | Array of objects | 短信上行详情
 mobile | String | 手机号码
 content | String | 上行短信内容
 replytime | String | 短信回复时间

## <span id='聊天室队列操作事件抄送'>聊天室队列操作事件抄送</span>

```
"eventType"="14"
```

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
//==== "qEvent":"1" ====
{"fromWebApi":"true",
"eventType":"14",
"roomid":"32",
"qEvent":"1",
"operator":"zyy"}

//==== "qEvent":"2" ====
{"transient":"false",
"elements":"{\"2\":\"1512702269.556135-2\"}",
"fromWebApi":"false",
"belongTo":"zyy",
"eventType":"14",
"roomid":"101",
"qEvent":"2",
"operator":"zyy"}

//==== "qEvent":"3" ====
{"transient":"false",
"elements":"{\"2\":\"2\"}",
"fromWebApi":"true",
"belongTo":"zyy",
"eventType":"14",
"roomid":"48",
"qEvent":"3",
"operator":"zyy"}

//==== "qEvent":"4" ====
{"keys":"[\"2\"]",
"fromWebApi":"false",
"eventType":"14",
"roomid":"57",
"qEvent":"4",
"operator":"zyy"}

//==== "qEvent":"5" ====
{"elements":"{\"1\":\"1512702269.686414-1\"}",
"fromWebApi":"false",
"eventType":"14",
"roomid":"101",
"qEvent":"5",
"operator":"zyy"}

//==== "qEvent":"6" ====
{"elements":"{\"1\":\"1512702269.686414-1\"}",
"fromWebApi":"false",
"eventType":"14",
"roomid":"101",
"qEvent":"6",
"operator":"zyy"}

//==== "qEvent":"7" ====
{"fromWebApi":"false",
"eventType":"14",
"roomid":"101",
"qEvent":"7",
"operator":"zyy"}

//==== "qEvent":"8" ====
{"fromWebApi":"false",
"eventType":"14",
"roomid":"101",
"qEvent":"8",
"operator":"zyy"}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{  
  "fromWebApi": "true",
  "eventType": "14",
  "roomid": "32",
  "qEvent": "1",
  "operator": "zyy"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
qEvent | String | 具体的操作，可转为 int，具体枚举如下：<br>1：表示 INIT 操作, 队列初始化 <br>2：表示 ADD 操作，队列新增 key-value <br>3：表示 UPDATE 操作，队列更新已有 key 对应的 value <br>4：表示 DELETE 操作，队列删除元素<br>5：表示 POLL 操作，取出（指定/头）元素<br>6：表示 PEAK 操作，查看头上的第一个元素，但是不删除<br>7：表示 LIST 操作，排序列出所有元素<br>8：表示 DROP 操作，队列清空<br>9：表示批量 UPDATE 操作，队列更新已有 key 对应的 value
fromWebApi | String | 是不是由网易云信服务端 api 发起的操作，可转为 Boolean 类型
roomid | String | 聊天室 ID，可转为 Long 值
operator | String | 该操作的发起者 accid
belongTo | String | 该元素归属用户的 accid
elements | String | 元素的 key 和对应 value
keys | String | 元素的 keys，不包含 value
transient | String | 这个新元素的提交者 operator 的所有聊天室连接在从该聊天室掉线或者离开该聊天室的时候，提交的元素是否需要删除。可转为 Boolean 值<br>true：需要删除。false：不需要删除
operationTime | Long | 具体操作的时间戳

## <span id='易盾异步反垃圾抄送'>易盾异步反垃圾抄送</span>

```
"eventType"="20"
```

::: note note 
需要单独开通，如有需要，请在 [网易云信控制台](https://app.yunxin.163.com/global/home) 开通
:::

- 示例-语音消息事件抄送：

   15.1. HTTP 示例

   15.2. cURL 示例

   15.3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
   "objects": "[{\"audioUrl\":\"http://nim-nosdn.netease.im/MTAxMTAwMA==/bmltd18wXzE1NTg2NDYxMjAxNDNfYWEwOTQ3YTAtNTg1Ny00ZTVmLTlmMTgtZThmMWUzYmY3NTQ0\",\"serverMsgId\":\"171450683457798182\",\"antispam\":true,\"clientMsgId\":\"90ad7356-b591-4fa4-8edb-c042d9caa3ea\",\"yidunRes\":{\"asrResult\":0.0,\"action\":1.0,\"asrStatus\":3.0,\"taskId\":\"342f252af8014bb7a2005794050f06af\",\"labels\":[{\"level\":1.0,\"details\":{\"hitType\":30.0,\"hint\":[{\"value\":\"命中反垃圾的文字\",\"segments\":[{\"startTime\":0.0,\"endTime\":2.0}]}]},\"label\":600.0}]},\"from\":\"pre00001\",\"to\":\"2554814271\",\"type\":\"TEAM_MSG_AUDIO\"}]",
   "eventType": "20"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "objects":"[{\"audioUrl\":\"http://nim-nosdn.netease.im/MTAxMTAwMA==/bmltd18wXzE1NTg2NDYxMjAxNDNfYWEwOTQ3YTAtNTg1Ny00ZTVmLTlmMTgtZThmMWUzYmY3NTQ0\",\"serverMsgId\":\"171450683457798182\",\"antispam\":true,\"clientMsgId\":\"90ad7356-b591-4fa4-8edb-c042d9caa3ea\",\"yidunRes\":{\"asrResult\":0.0,\"action\":1.0,\"asrStatus\":3.0,\"taskId\":\"342f252af8014bb7a2005794050f06af\",\"labels\":[{\"level\":1.0,\"details\":{\"hitType\":30.0,\"hint\":[{\"value\":\"命中反垃圾的文字\",\"segments\":[{\"startTime\":0.0,\"endTime\":2.0}]}]},\"label\":600.0}]},\"from\":\"pre00001\",\"to\":\"2554814271\",\"type\":\"TEAM_MSG_AUDIO\"}]",
   "eventType":"20"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
易盾异步反垃圾抄送结果中部分字段可能为空，请注意对各字段的判空处理。一般情况下必有的字段为 eventType、antispam、type、yidunRes。
:::

名称 | 类型 | 说明
--- | --- | --- 
eventType | String | 抄送事件类型
objects | Array of objects | 易盾发垃圾详情
 audioUrl | String | 音频、视频文件下载地址
 serverMsgId | String | 服务器消息 ID
 antispam | String | 是否命中反垃圾<br/>true：命中(目前仅抄送命中的情况)<br>false：没有命中
 clientMsgId | String | 客户端消息 ID
 yidunRes | Object | 安全通反垃圾结果，详细请参考安全通文档：<br>老版本安全通反垃圾：<li><a href="https://support.dun.163.com/documents/2018082201?docId=410644689942007808">音频类反垃圾的 callbackData 字段的释义</a><li><a href="https://support.dun.163.com/documents/2018041903?docId=150440859531399168">视频类反垃圾的 callbackData 字段的释义</a><br>备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br>新版本安全通反垃圾：<li><a href="https://support.dun.163.com/documents/588434426518708224?docId=589589116186927104">音频类反垃圾的 callbackData 字段的释义</a><li><a href="https://support.dun.163.com/documents/588434393394810880?docId=589590110273245184">视频类反垃圾的 callbackData 字段的释义</a><li><a href="https://support.dun.163.com/documents/588434277524447232?docId=589231544060317696">图片类反垃圾的 callbackData 字段的释义</a><br>备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br>2021 年 9 月 28 日 19:29 前接入安全通的客户，需要升级到最新版安全通，才可使用新版本能力。升级安全通请联系商务经理。2021 年 9 月 28 日 19:29 后接入安全通的客户，将自动开通此能力。
 yidunApiVersion | String | 安全通反垃圾接口版本。2、新版本安全通反垃圾接口。只有对接新版本安全通反垃圾才有
 type | String | 易盾异步反垃圾类型：<li>P2P_MSG_AUDIO:点对点语音消息，对应 to 为接收方账号<li>TEAM_MSG_AUDIO：群聊语音消息，对应 to 为群 ID<li>SUPERTEAM_MSG_AUDIO：超大群语音消息，对应 to 为群 ID<li>CHATROOM_MSG_AUDIO：聊天室语音消息，对应 to 为聊天室 ID<li>QCHAT_MSG_AUDIO：圈组语音消息<li>P2P_MSG_VIDEO:点对点视频消息，对应 to 为接收方账号<li>TEAM_MSG_VIDEO：群聊视频消息，对应 to 为群 ID<br>SUPERTEAM_MSG_VIDEO：超大群视频消息，对应 to 为群 ID<li>CHATROOM_MSG_VIDEO：聊天室视频消息，对应 to 为聊天室 ID<li>QCHAT_MSG_VIDEO：圈组视频消息<li>P2P_MSG_PICTURE：点对点图片消息，对应 to 为接收方账号<li>TEAM_MSG_PICTURE：群聊图片消息，对应 to 为群 ID<li>SUPERTEAM_MSG_PICTURE：超大群图片消息，对应 to 为超大群 ID<li>CHATROOM_MSG_PICTURE：聊天室图片消息，对应 to 为聊天室 ID<li>QChat_MSG_PICTURE：圈组图片消息
 from | String | 消息发送人的账号
 to | String | 消息接收方，详细参考 type 字段

## <span id='点对点消息已读回执抄送'>点对点消息已读回执抄送</span>

```
"eventType"="30"
```

- 示例-点对点消息已读回执事件抄送：

   16.1. HTTP 示例

   16.2. cURL 示例

   16.3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "objects": "[{\"toAccount\":\"test100\",\"clientType\":\"AOS\",\"fromAccount\":\"test101\",\"msgidClient\":\"076a5519-59c0-42c9-916d-9652ab390310\",\"timestamp\":1578551421737}]",
    "eventType": "30"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "objects":"[{\"toAccount\":\"test100\",\"clientType\":\"AOS\",\"fromAccount\":\"test101\",\"msgidClient\":\"076a5519-59c0-42c9-916d-9652ab390310\",\"timestamp\":1578551421737}]",
   "eventType":"30"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
请注意对各字段的判空处理。一般情况下必有的字段为 eventType、fromAccount、toAccount、clientType、timestamp。
:::

名称 | 类型 | 说明 
--- | --- | --- 
eventType | String | 抄送事件类型
objects | Array of objects | 已读回执信息
 fromAccount | String | 标记消息已读的账号
 toAccount | String | 接收消息已读通知的账号(即点对点消息发送方账号)
 clientType | String | 客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型
 msgidClient | String | 客户端消息 ID
 timestamp | String | 消息已读事件时间戳

## <span id='独立信令抄送'>独立信令抄送</span>

```
"eventType"="31"
```

- 示例-独立信令抄送：

   17.1. HTTP 示例

   17.2. cURL 示例

   17.3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "type": "CREATE_ROOM",
    "channelId": "xxxx",
    "channelName": "abc",
    "createTime": "1234",
    "creator": "aaa",
    "ext": "aaa",
    "eventType": "31"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "type":"CREATE_ROOM",
   "channelId":"xxxx",
   "channelName":"abc",
   "createTime":"1234",
   "creator":"aaa",
   "ext":"aaa",
   "eventType":"31"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

:::note note
请注意对各字段的判空处理，一般来说，只有 eventType、type、channalId 字段是必填的。
:::

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型，31 表示独立信令抄送
type | String | 独立信令抄送类型，包括：CREATE_ROOM、CLOSE_ROOM、LEAVE_ROOM、JOIN_ROOM、INVITE、CANCEL_INVITE、ACCEPT、REJECT、CTRL
channelId | String | 房间的 channelId
channelName | String | 房间的 channelName
createTime | String | 房间创建时间
creator | String | 房间创建者
ext | String | 扩展字段
from | String | 操作者
to | String | 被操作者
timestamp | String | 操作时间
attachExt | String | 通知扩展字段
isSave | String | 是否存离线，true/false
uid | String | uid，加入房间时会返回
requestId | String | 请求 ID，邀请/取消邀请/接受/拒绝时包含该字段
needPush | String | 是否需要第三方推送，true/false，邀请时包含该字段
pushTitle | String | 第三方推送标题，邀请时包含该字段
pushContent | String | 第三方推送内容，邀请时包含该字段
pushPayload | String | 第三方推送扩展字段，邀请时包含该字段
needBadge | String | 第三方推送是否需要计入未读计数，true/false，邀请时包含该字段

## <span id='上传任务抄送'>上传任务抄送</span>

```
"eventType"="36"
```

- 示例-上传任务抄送：

   18.1. HTTP 示例

   18.2. cURL 示例

   18.3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "type": "1",
    "uploadInfo": {
        "uploadMsg": "attach",
        "sdkLogUrl": "https://nim-nosdn.netease.im/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
    },
    "eventType": "36"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "type": "1",
   "uploadInfo": {
      "uploadMsg": "attach",
      "sdkLogUrl": "https://nim-nosdn.netease.im/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
   },
   "eventType": "36"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型，36 表示上传任务抄送
type | String | 上传任务类型：1：上传 SDK 日志
uploadInfo | String | 上传的具体信息

## <span id='长连接心跳抄送'>长连接心跳抄送</span>

```
"eventType"="42"
```

- 示例-长连接心跳抄送：

   21.1. HTTP 示例

   21.2. cURL 示例

   21.3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "clientType": "PC",
    "consid": "e824d8aa-8b07-4684-89c8-574fc73fd140",
    "clientIp": "183.13*.***.138",
    "customTag": "PC",
    "clientPort": "44772",
    "accid": "qdf666",
    "eventType": "42",
    "deviceId": "71054493e01cb62968f4914a20078409ab3719357756e05da99e5563299550a9",
    "timestamp": "1614687765251"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "clientType": "PC",
   "consid": "e824d8aa-8b07-4684-89c8-574fc73fd140",
   "clientIp": "183.13*.***.138",
   "customTag": "PC",
   "clientPort": "44772",
   "accid": "qdf666",
   "eventType": "42",
   "deviceId": "71054493e01cb62968f4914a20078409ab3719357756e05da99e5563299550a9",
   "timestamp": "1614687765251"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型，42 表示长连接心跳抄送
accid | String | 网易云信账号 ID（accid）
consid | String | 长连接的连接号
clientIp | String | 客户端 IP<note type=notice>ipv4 地址或 ipv6 地址
clientPort | String | 客户端端口
clientType | String | 客户端类型，AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)
deviceId | String | 设备 ID
timestamp | String | 时间戳

## <span id='登录失败抄送'>登录失败抄送</span>

```
"eventType"="84"
```

- 示例- 登录失败抄送：

   1. HTTP 示例

   2. cURL 示例

   3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "code": "302",
    "appLogin": "true",
    "customTag": "customTag-test",
    "sdkType": "1",
    "eventType": "84",
    "deviceId": "8bd9cba1-f607-4760-90de-f2a2d3ec5562",
    "sdkHumanVersion": "8.1.0",
    "fail": "login.token.error",
    "clientType": "AOS",
    "consid": "51530a27-76d6-452a-a456-75bed01adba0",
    "clientIp": "115.236.119.139",
    "accid": "yx",
    "sdkVersion": "150",
    "event": "1",
    "timestamp": "1653899015393"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```shell
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
   "code":"302",
   "appLogin":"true",
   "customTag":"customTag-test",
   "sdkType":"1",
   "eventType":"84",
   "deviceId":"8bd9cba1-f607-4760-90de-f2a2d3ec5562",
   "sdkHumanVersion":"8.1.0",
   "fail":"login.token.error",
   "clientType":"AOS",
   "consid":"51530a27-76d6-452a-a456-75bed01adba0",
   "clientIp":"115.236.119.139",
   "accid":"yx",
   "sdkVersion":"150",
   "event":"1",
   "timestamp":"1653899015393"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型，84 表示登录失败抄送
event | String | 抄送事件，0：聊天室登录失败，1：IM 登录失败
chatRoomId | String | 聊天室 ID，当 event 为 0 时一定存在
accid | String | 网易云信账号 ID（accid）
clientType | String | 客户端类型，AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)
appLogin | String | 登录方式，true：客户端发起的密码登录，false：SDK 发起的自动登录
customTag | String | 自定义消息
sdkVersion | String | 当前客户端 SDK 的版本
consid | String | 连接 ID
clientIp | String | 客户端 IP <note type=notice>ipv4 地址或 ipv6 地址
deviceId | String | 设备 ID
sdkHumanVersion | String | 当前客户端 SDK 的可读版本
sdkType | String | 客户端 SDK 类型
code | String | 错误码：<br>302：账号密码错误<br>403：禁止操作<br>404：聊天室不存在<br>414：参数不合法<br>422：账号被禁止<br>500：未知错误<br>13001：聊天室连接状态异常<br>13002：聊天室状态错误<br>13003：聊天室黑名单<br>13005：聊天室发垃圾
fail | String | 失败原因：<br>param.error：参数不合法<br>special.app.forbidden：app 禁止访问该集群<br>account.not.exists: 账号不存在<br>account.block：账号被锁定<br>unknown.authType：鉴权类型错误<br>authType.forbidden：应用不支持的鉴权类型<br>login.token.error: 登录 token 校验失败<br>login.ext.over.max.length: loginExt 超过最大长度<br>bundleId.check.error: bundleId 校验失败<br>res.eunknown: 未知异常<br>chatroom.accid.not.match：求进入聊天室的账号和登录验证的账号不是同一个账号<br>chatroom.imconnection.stats.err：聊天室连接状态异常<br>chatroom.not.exists：聊天室不存在<br>chatroom.room.stats.err：聊天室状态错误<br>chatroom.in.blacklist：禁止进入该聊天室<br>chatroom.antispam：被反垃圾

## <span id='第三方回调失败抄送'>第三方回调失败抄送</span>

```
"eventType"="83"
```

- 示例- 第三方回调失败抄送：

   1. HTTP 示例

   2. cURL 示例

   3. 消息体中的 JSON 字段说明

### <span id='HTTP 示例'>HTTP 示例</span>

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx //根据请求中的 request body 计算出来的 MD5 值
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```json
{
    "reason": "1",
    "timestamp": "1653899015393",
    "callbackBody": "{\"attach\":\"attach\"}",
    "eventType": "83"
}
```

### <span id='cURL 示例'>cURL 示例</span>

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
    "reason": "1",
    "timestamp": "1653899015393",
    "callbackBody": "{\"attach\":\"attach\"}",
    "eventType": "83"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

### <span id='消息体中的 JSON 字段说明'>消息体中的 JSON 字段说明</span>

名称 | 类型 | 说明
--- | --- | ---
eventType | String | 抄送事件类型，83 表示第三方回调失败抄送 
reason | String | 回调失败的原因：<li>1：请求超时<li>2：回包格式不合法<li>3：熔断降级
callbackBody | String | 回调内容 
timestamp | String | 发送回调失败的时间 