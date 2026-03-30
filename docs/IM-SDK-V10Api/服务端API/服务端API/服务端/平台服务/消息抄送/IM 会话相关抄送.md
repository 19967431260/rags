
本文介绍 IM 会话类型消息抄送的基本格式与字段含义。

:::note note
本文假设第三方开发者的消息接收地址为 `http://yunxinservice.com.cn/receiveMsg.action`，下文的抄送地址均假设为此接口。
:::

## 会话类型消息抄送

```JSON
{
    "eventType"="1"
}
```

目前包括 P2P 聊天消息，群组聊天消息，群组操作，好友操作等。[网易云信控制台](https://app.yunxin.163.com/global/home) 上细分为三类：

- P2P 聊天消息：convType 属性为 PERSON
- 群组聊天消息：convType 属性为 TEAM/SUPER_TEAM 
- 系统通知消息：convType 属性为 CUSTOM_PERSON/CUSTOM_TEAM

### **<span id='HTTP 示例'>HTTP 示例</span>**

以下为网易云信向开发者的服务器发起 HTTP-POST 请求的示例：

```HTTP
POST  /receiveMsg.action   HTTP/1.1
Host:  yunxinservice.com.cn
Content-Type:  application/json
CurTime: 1440570500855    //当前 UTC 时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数(String)
MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx   //根据请求中的 request body 计算出来的 MD5 值。
CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01
```

```JSON
{
    "attach": "thisisattach",
    "body": "hello",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "111",
    "fromClientType": "IOS",
    "fromDeviceId": "thisisfromdeviceid",
    "fromNick": "mike",
    "msgTimestamp": "1441977355557",
    "msgType": "TEXT",
    "msgidClient": "1234567",
    "msgidServer": "3456789",
    "resendFlag": "0",
    "to": "222"
}
```

### **<span id='cURL 示例'>cURL 示例</span>**

```cURL
curl -X POST -H "Content-Type: application/json" -H "CurTime: 1440570500855" -H "MD5: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" -H "CheckSum: 001511b8435e0b28044ca50a78e8f983026c5e01" -d '
{
    "attach": "thisisattach",
    "body": "hello",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "111",
    "fromClientType": "IOS",
    "fromDeviceId": "thisisfromdeviceid",
    "fromNick": "mike",
    "msgTimestamp": "1441977355557",
    "msgType": "TEXT",
    "msgidClient": "1234567",
    "msgidServer": "3456789",
    "resendFlag": "0",
    "to": "222"
}
' 'http://yunxinservice.com.cn/receiveMsg.action'
```

## **<span id='消息体中的JSON字段说明'>消息体中的 JSON 字段说明</span>**

会话类型消息中，并不是每个字段都会一定抄送，请注意对各字段的判空处理。以下为一般情况下必有的字段：

eventType、convType、to、fromAccount、msgTimestamp、msgType、msgidClient、msgidServer

名称 | 类型 | 说明 |
--- | --- | --- |
eventType | String | 值为 1，表示是会话类型的消息 |
convType | String | 会话具体类型：<br> |\
 |  | PERSON（单聊会话内消息）、TEAM（群聊会话内消息）、SUPER_TEAM（超大群聊会话内消息）<br> |\
 |  | CUSTOM_PERSON（单聊自定义系统通知及内置好友系统通知）、CUSTOM_TEAM（群聊自定义系统通知及内置群聊系统通知），字符串类型 | |  | 
to | String | 若 convType 为 PERSON 或 CUSTOM_PERSON，则 to 为消息接收者的用户账号，字符串类型。<br> |\
 |  | 若 convType 为 TEAM 或 SUPER_TEAM 或 CUSTOM_TEAM，则 to 为 tid，即群 ID，可转为 Long 型数据 | | 
fromAccount | String | 消息发送者的用户账号，字符串类型，长度上限为 64 个字符 |
fromClientType | String | 发送客户端类型：AOS(1)、IOS(2)、PC(4)、WEB(16)、REST(32)，MAC(64)、HARMONY(65)，字符串类型 |
fromDeviceId | String | 发送设备 ID，字符串类型，长度上限为 128 个字符 |
fromNick | String | 发送方昵称，字符串类型，长度上限为 255 个字符 |
msgTimestamp | String | 消息发送时间，字符串类型 |
msgType | String | convType 为 PERSON、TEAM、SUPER_TEAM 时对应的消息类型：<br> |\
 |  | - TEXT //文本消息 |\
 |  | - PICTURE //图片消息 |\
 |  | - AUDIO //语音消息 |\
 |  | - VIDEO //视频消息 |\
 |  | - LOCATION //地理位置消息 |\
 |  | - NOTIFICATION //群通知消息，如群资料更新通知、群解散通知等。 |\
 |  | - FILE //文件消息 |\
 |  | - TIPS //提示消息 |\
 |  | - CUSTOM //自定义消息 |\
 |  | - NRTC_NETCALL // 音视频 2.0 话单消息抄送 |\
 |  | convType 为 CUSTOM_PERSON 对应的通知消息类型： |\
 |  | - FRIEND_ADD //对方 请求/已经 添加为好友 |\
 |  | - FRIEND_DELETE //被对方删除好友 |\
 |  | - CUSTOM_P2P_MSG //单聊自定义系统通知 |\
 |  | convType 为 CUSTOM_TEAM 对应的通知消息类型（请注意与 NOTIFICATION 区分）： |\
 |  | - TEAM_APPLY //申请入群 |\
 |  | - TEAM_APPLY_REJECT //拒绝入群申请 |\
 |  | - TEAM_INVITE //邀请进群 |\
 |  | - TEAM_INVITE_REJECT //拒绝邀请 |\
 |  | - CUSTOM_TEAM_MSG //群组自定义系统通知 |\
 |  | - SUPERTEAM_APPLY //超大群申请入群 |\
 |  | - SUPERTEAM_APPLY_REJECT //超大群拒绝入群申请 |\
 |  | - SUPERTEAM_INVITE //超大群邀请进群 |\
 |  | - SUPERTEAM_INVITE_REJECT //超大群拒绝进群邀请 |\
 |  | - CUSTOM_SUPERTEAM_MSG //超大群组自定义系统通知 |
body | String | 消息内容，字符串类型，长度上限为 5000 个字符。针对聊天室消息而言，无此字段。内容转由 attach 承载。 |
attach | String | 附加消息，字符串类型，长度上限为 4096 个字符。注意：音视频通话 2.0 消息抄送中，attach 字段包含通话类型、呼叫状态等通话详情。详细信息请参考 <a href="https://doc.yunxin.163.com/nertccallkit/guide/TkyODAzMDQ?platform=android#话单消息结构">话单消息结构（Android）</a> 或 <a href="https://doc.yunxin.163.com/nertccallkit/guide/zM4MjgwMTY?platform=iOS#云信话单消息结构">话单消息结构（iOS）</a>。 |
msgidClient | String | 客户端生成的消息 ID，仅在 convType 为 PERSON 或 TEAM 或 SUPER_TEAM 含此字段，字符串类型 |
msgidServer | String | 服务端生成的消息 ID，可转为 Long 型数据 |
resendFlag | String | 重发标记：0 不是重发, 1 是重发。仅在 convType 为 PERSON 或 TEAM 或 SUPER_TEAM 时含此字段，可转为 Integer 类型数据 |
customSafeFlag | String | 自定义系统通知消息是否存离线:0：不存，1：存。<br> |\
 |  | 仅在 convType 为 CUSTOM_PERSON 或 CUSTOM_TEAM 时含此字段，可转为 Integer 类型数据 | | 
customApnsText | String | 自定义系统通知消息推送文本。仅在 convType 为 CUSTOM_PERSON 或 CUSTOM_TEAM 时含此字段，字符串类型，长度上限为 500 个字符 |
tMembers | String | 当前群成员 accid 列表。仅在群成员不超过 200 人，且 convType 为 TEAM 或 CUSTOM_TEAM 时包含此字段，字符串类型<br> |\
 |  | tMembers 格式举例：<br> |\
 |  | {<br> |\
 |  | ... // 其他字段<br> |\
 |  | "tMembers":"[123, 456]" //相关的 accid 为 123 和 456<br> |\
 |  | } |
ext | String | 消息扩展字段，长度上限为 1024 个字符 |
antispam | String | 标识是否被反垃圾，仅在被反垃圾时才有此字段，可转为 Boolean 类型数据 |
yidunRes | String | 安全通反垃圾的原始处理细节，只有接入了相关功能安全通反垃圾的应用才会有这个字段。请参考以下 1.4.5.1、P2P：文本消息 和 1.4.5.2、P2P：图片消息的举例说明。<br> |\
 |  | <br> |\
 |  | 该字段中子字段释义如下：<br> |\
 |  | <br> |\
 |  | 老版本安全通反垃圾：<br> |\
 |  | yidunBusType：0：文本反垃圾业务。1、图片反垃圾业务。2、用户资料反垃圾业务。3、用户头像反垃圾业务。<br> |\
 |  | action：处理结果：检测结果，0：通过，1：嫌疑，2：不通过。（只有 yidunBusType 为 0 或 2 时，抄送时才有此字段）<br> |\
 |  | labels：具体的反垃圾判断细节：<br> |\
 |  | <a href="http://support.dun.163.com/documents/2018041901?docId=150425947576913920">文本在线检测</a><br> |\
 |  | <a href="http://support.dun.163.com/documents/2018041902?docId=150429557194936320">图片在线检测</a><br> |\
 |  | 备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br> |\
 |  | <br> |\
 |  | 新版本安全通反垃圾：<br> |\
 |  | yidunApiVersion：安全通反垃圾接口版本。2、新版本安全通反垃圾接口。<br> |\
 |  | yidunBusType：0：文本反垃圾业务。1、图片反垃圾业务。2、用户资料反垃圾业务。3、用户头像反垃圾业务。<br> |\
 |  | result：具体的反垃圾返回结果：<br> |\
 |  | <a href="https://support.dun.163.com/documents/588434200783982592?docId=589310433773625344">单次同步检测</a><br> |\
 |  | <a href="https://support.dun.163.com/documents/588434277524447232?docId=588512292354793472">同步检测</a><br> |\
 |  | 备注：考虑到安全通反垃圾相关字段后续的扩展性（一般为新增属性），请注意做好解析兼容<br> |\
 |  | <br> |\
 |  | 2021 年 9 月 28 日 19:29 前接入安全通的客户，需要升级到最新版安全通，才可使用新版本能力。升级安全通请联系商务经理。2021 年 9 月 28 日 19:29 后接入安全通的客户，将自动开通此能力。 |
blacklist | String | 标识单聊消息是否黑名单，仅在消息发送方被拉黑时才有此字段，可转为 Boolean 类型数据 |
ip | String | 消息发送方的客户端 IP 地址(仅 SDK 发送的消息才有该字段) |
port | String | 消息发送方的客户端端口号(仅 SDK 发送的消息才有该字段) |
aiParams | Object | 数字人消息相关回执。 |
 ∟direction | int | - 1：表示是一个艾特（@）数字人的消息 |\
  |  | - 2：表示是数字人响应艾特的消息 |
 ∟account | String |  数字人账号 ID（accid）。 |\
  |  | - 如果是艾特数字人的消息，则表示被艾特的数字人账号。 |\
  |  | - 如果是数字人响应艾特的消息，则表示响应的数字人账号。 |
 ∟content | JSON String | - aiAgentMsgDirection=1：表示@数字人的文本内容。 |\
  |  | - aiAgentMsgDirection=2：表示数字人回复消息。 |
 ∟messages | JSON Array String | 回溯消息列表。aiAgentMsgDirection=2 时该字段为空。 |
 ∟promptVariables | JSON String | 用于填充提示词（prompt）中的变量。如果prompt中定义了变量，则必填。例如，{ "career"："厨师"}。 |
 ∟config | JSON String | 模型相关的配置参数，不同模型配置类型不同。结构体类似为：{"maxTokens":1,"temperature":1,"prompt":"我是一个${{career}}，请回答我的问题：","topP":0.5} |

## **<span id='相关字段释义'>相关字段释义</span>**

高级群和超大群相关消息抄送中部分字段的格式定义如下：

attach 字段中 tinfo 字段的定义，为 JSONObject：

```JSON
"tinfo": [{
    "1": "群组 ID，可转为 Long 型",
    "3": "群名称",
    "4": "群类型, 1 表示高级群, 超大群未定义",
    "5": "创建者用户账号",
    "7": "群公告等各种属性",
    "8": "群有效标记, 0 表示无效, 1 表示有效",
    "9": "群有效成员个数",
    "10": "群组成员列表更新的时间戳，精确到毫秒",
    "11": "创建时间, 精确到毫秒",
    "12": "更新时间, 精确到毫秒",
    "14": "群介绍",
    "15": "群公告，为 JSONArray 的 toString，格式参考下文",
    "16": "群属性，0 表示入群不需要申请，1 表示入群需要申请",
    "18": "第三方扩展字段",
    "19": "第三方服务器扩展字段",
    "20": "群头像",
    "21": "被邀请人同意方式, 0：需要同意(默认)，1：不需要同意",
    "22": "谁可以邀请他人入群, 0：管理员(默认)，1：所有人",
    "23": "谁可以修改群资料, 0：管理员(默认)，1：所有人",
    "24": "谁可以更新群自定义属性, 0：管理员(默认)，1：所有人"
}]
```

tinfo 中"15"群公告字段的格式如下：

```JSON
"tinfo": {
    "15": [
        {
            "title": "这是群公告标题",
            "content": "这是群公告内容",
            "creator": "群公告发表者",
            "time": 1457075964
        },
        {}
    ]
}
```

attach 字段中 uinfos 字段的定义，为 JSONArray：

```JSON
"uinfos": [
    {
        "1": "用户账号",
        "3": "用户昵称",
        "4": "用户头像地址",
        "5": "个性签名",
        "6": "性别",
        "7": "邮箱",
        "8": "生日",
        "9": "手机号",
        "10": "扩展字段",
        "12": "创建时间",
        "13": "更新时间"
    },
    {}
]
```

attach 字段中 ID 字段的释义：

- 0：TEAM_INVITE，即群拉人
- 1：TEAM_KICK，即群踢人
- 2：TEAM_LEAVE，即退出群
- 3：TEAM_UPDATE，即更新群信息
- 4：TEAM_DISMISS，即群解散
- 5：TEAM_APPLY_PASS，即群申请加入成功
- 6：TEAM_OWNER_TRANSFER，即群主退群并移交群主
- 7：TEAM_ADD_MANAGER，即增加管理员
- 8：TEAM_REMOVE_MANAGER，即删除管理员
- 9：TEAM_INVITE_ACCEPT，即群接受邀请进群
- 10：TEAM_MUTE_TLIST，即禁言群成员
- 401：SUPER_TEAM_INVITE，超大群拉人
- 402：SUPER_TEAM_KICK，超大群踢人
- 403：SUPER_TEAM_LEAVE，超大群退群
- 404：SUPER_TEAM_UPDATE_TINFO，超大群修改群信息
- 405：SUPER_TEAM_DISMISS，超大群解散
- 406：SUPER_TEAM_CHANGE_OWNER，超大群移交群主
- 407：SUPER_TEAM_ADD_MANAGER，超大群添加管理员
- 408：SUPER_TEAM_REMOVE_MANAGER，超大群删除管理员
- 409：SUPER_TEAM_MUTE_TLIST，超大群禁言群成员
- 410：SUPER_TEAM_APPLY_PASS，超大群申请成功进群
- 411：SUPER_TEAM_INVITE_ACCEPT，超大群接受邀请进群

    note note
    没有给出定义的字段都是第三方无需关心的字段，可忽略。
    :::

## <span id='高级群相关示例'>高级群相关示例</span>

<!--创建群没有抄送,在创建的同时拉人进群的话，会有拉人的抄送

### <span id='创建高级群'>创建高级群</span>

:::::: div linked-codes
::: code attach 抄送示例
{
    "fromNick":"yx-tom-123test",
    "msgType":"NOTIFICATION",
    "msgidServer":"15759307314718****",
    "fromAccount":"yx",
    "fromClientType":"AOS",
    "tMembers":"[yx]",
    "eventType":"1",
    "convType":"TEAM",
    "msgidClient":"5740dc99-a45d-46ac-****-0757111d1020",
    "resendFlag":"0",
    "msgTimestamp":"1656572965158",
    "to":"2348319786",
    "attach":"{\"data\":{\"uinfos\":[{\"11\":\"84851\",\"1\":\"yx1\",\"12\":\"1431056915229\",\"2\":\"11011\",\"13\":\"1641801035679\",\"3\":\"yx1\",\"4\":\"https://nim.nosdn.127.net/xxx\",\"5\":\"签名-xw\",\"6\":\"0\",\"7\":\"e@3721.net\",\"8\":\"1984-4-7\",\"10\":\"ext\"}],\"tinfo\":{\"11\":\"1656572965051\",\"22\":\"1\",\"12\":\"1656572965051\",\"23\":\"1\",\"24\":\"1\",\"14\":\"yx-15:09:24.942\",\"16\":\"0\",\"17\":\"0\",\"1\":\"2348319786\",\"2\":\"11011\",\"3\":\"yx-2022-06-30\",\"4\":\"1\",\"5\":\"yx\",\"6\":\"3000\",\"8\":\"1\",\"9\":\"5\",\"20\":\"http://b12026.nos.netease.com/xxx\",\"10\":\"1656572965051\",\"21\":\"1\"},\"ids\":[\"yx1\",\"wmtest200\",\"wmtest201\",\"wmtest202\"]},\"id\":0}"
}
 
attach 字段释义
{
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
}
```
-->

### <span id='解散高级群'>解散高级群</span>

:::::: div linked-codes
::: code attach 抄送示例
```JSON
{
    "attach": 
        {
      "data": {
        "uinfos": [
          {
            "1": "zhangsan",
            "11": "142915",
            "12": "1438738423546",
            "13": "1446624332920",
            "2": "11011",
            "3": "zhangsan",
            "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
            "6": "0"
          }
        ]
      },
      "id": 4
    },
    "convType": "TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456810468999",
    "msgType": "NOTIFICATION",
    "msgidClient": "b697a6b2-be71-47f0-8fc0-3c7ff9b15dda",
    "msgidServer": "779872108546",
    "resendFlag": "0",
    "tMembers": "[zhangsan, lisi]",
    "to": "11621"
}
```
 
:::
::: code attach 字段解释

```JSON
{
  "data": {
    //解散群的操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 4    //解散群
}
```
:::
::: code tMembers 字段解释

```JSON
{
    "tMembers": "[lisi]" //解散高级群时的群内所有成员列表，包含群主
}
```
:::
::::::

### <span id='高级群邀请他人加群'>高级群邀请他人加群</span>

:::::: div linked-codes
::: code attach 抄送示例
```JSON
{
    "attach": {
        "tinfo": {
            "1": "11623",
            "10": "1456817802112",
            "11": "1456811497999",
            "12": "1456817802112",
            "14": "这是群介绍",
            "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
            "16": "0",
            "17": "0",
            "2": "11011",
            "21": "0",
            "22": "0",
            "23": "0",
            "24": "0",
            "3": "高级群",
            "4": "1",
            "5": "zhangsan",
            "6": "10",
            "8": "1",
            "9": "1"
        }
    },
    "body": "邀请您加入群组",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456818444874",
    "msgType": "TEAM_INVITE",
    "msgidServer": "373171",
    "tMembers": "[lisi]",
    "to": "11623"
}
```
 
:::
::: code attach 字段解释

```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
  }
}
```
:::
::: code tMembers 字段解释

```JSON
{
    "tMembers":"[zhangsan, lisi]" //被邀请入群的用户列表
}
```
:::
::::::

### <span id='高级群接受邀请入群'>高级群接受邀请入群</span>

:::::: div linked-codes
::: code attach 抄送示例
```JSON
{
	"attach": "{
        "data": {
            "id": "zhangsan",
            "tinfo": {
            "1": "11623",
            "10": "1456811521765",
            "11": "1456811497999",
            "12": "1456811521899",
            "14": "这是群介绍",
            "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
            "16": "0",
            "17": "0",
            "2": "11011",
            "21": "0",
            "22": "0",
            "23": "0",
            "24": "0",
            "3": "高级群",
            "4": "1",
            "5": "zhangsan",
            "6": "10",
            "8": "1",
            "9": "2"
            },
            "uinfos": [
            {
                "1": "lisi",
                "11": "142916",
                "12": "1438740370586",
                "13": "1438740370586",
                "2": "11011",
                "3": "lisi",
                "6": "0"
            },
            {
                "1": "zhangsan",
                "11": "142915",
                "12": "1438738423546",
                "13": "1446624332920",
                "2": "11011",
                "3": "zhangsan",
                "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                "6": "0"
            }
            ]
        },
        "id": 9
        }
    ",
	"convType": "TEAM",
	"eventType": "1",
	"fromAccount": "lisi",
	"fromClientType": "IOS",
	"msgTimestamp": "1456811521946",
	"msgType": "NOTIFICATION",
	"msgidClient": "335cf3bb-8efa-4cde-953d-9aa775f1a2b2",
	"msgidServer": "780006326273",
	"resendFlag": "0",
	"tMembers": "[zhangsan, lisi]",
	"to": "11623"
}
```
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "邀请人的账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //邀请人与被邀请人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 9    //高级群接受邀请邀请入群
}
```
:::
::: code tMembers 字段解释

```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括邀请人和被邀请人
}
```
:::
::::::

### <span id='高级群拒绝邀请入群'>高级群拒绝邀请入群</span>

抄送示例：

```JSON
{
    "body": "",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "lisi",
    "msgTimestamp": "1456819928681",
    "msgType": "TEAM_INVITE_REJECT",
    "msgidServer": "373998",
    "to": "11623"
}
```

### <span id='高级群增加管理员'>高级群增加管理员</span>

:::::: div linked-codes
::: code attach 抄送示例
```JSON
{
    "attach": {
        "data": {
            "ids": ["lisi"],
            "uinfos": [
                {
                    "1": "lisi",
                    "11": "142916",
                    "12": "1438740370586",
                    "13": "1438740370586",
                    "2": "11011",
                    "3": "lisi",
                    "6": "0"
                },
                {
                    "1": "zhangsan",
                    "11": "142915",
                    "12": "1438738423546",
                    "13": "1446624332920",
                    "2": "11011",
                    "3": "zhangsan",
                    "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                    "6": "0"
                }
            ]
        },
        "id": 7
    },
    "convType": "TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "msgTimestamp": "1456813138663",
    "msgType": "NOTIFICATION",
    "msgidClient": "3e3e2efe-4f16-4ac2-8669-a8ee17be80bc",
    "msgidServer": "780006326274",
    "resendFlag": "0",
    "tMembers": ["zhangsan", "lisi"],
    "to": "11623"
}
```
 
:::
::: code attach 字段解释

```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被设为管理员的用户账号 1",
        "被设为管理员的用户账号 2"
    ],
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 7    //高级群增加管理员
}
```

:::
::: code tMembers 字段解释

```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括操作人和被操作人
}
```
:::
::::::

### <span id='高级群删除管理员'>高级群删除管理员</span>

:::::: div linked-codes
::: code attach 抄送示例
```JSON
{
	"attach": {
		"data": {
			"ids": ["lisi"],
			"uinfos": [{
					"1": "lisi",
					"11": "142916",
					"12": "1438740370586",
					"13": "1438740370586",
					"2": "11011",
					"3": "lisi",
					"6": "0"
				},
				{
					"1": "zhangsan",
					"11": "142915",
					"12": "1438738423546",
					"13": "1446624332920",
					"2": "11011",
					"3": "zhangsan",
					"4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
					"6": "0"
				}
			]
		},
		"id": 8
	}
	",
	"convType": "TEAM",
	"eventType": "1",
	"fromAccount": "zhangsan",
	"fromClientType": "IOS",
	"msgTimestamp": "1456815660948",
	"msgType": "NOTIFICATION",
	"msgidClient": "a2b8f49a-cc06-4784-a8e4-84b59c9ac85f",
	"msgidServer": "780006326275",
	"resendFlag": "0",
	"tMembers": "[zhangsan, lisi]",
	"to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被删除管理员的用户账号 1",
        "被删除管理员的用户账号 2"
    ],
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 8    //高级群删除管理员
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括操作人和被操作人
}
```
:::
::::::

### <span id='高级群踢人出群'>高级群踢人出群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "ids": ["lisi"],
      "tinfo": {
        "1": "11623",
        "10": "1456816081224",
        "11": "1456811497999",
        "12": "1456816081359",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "高级群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "1"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        },
        {
          "1": "zhangsan",
          "11": "142915",
          "12": "1438738423546",
          "13": "1446624332920",
          "2": "11011",
          "3": "zhangsan",
          "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTZfMTQzOD***YjgtOGZlOS02MzBjZWFjYmMwZDE=",
          "6": "0"
        }
      ]
    },
    "id": 1
  },
  "convType": "TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "IOS",
  "msgTimestamp": "1456816081368",
  "msgType": "NOTIFICATION",
  "msgidClient": "f3c0437d-fd3c-4900-9b80-ef9c86c1f91f",
  "msgidServer": "780006326276",
  "resendFlag": "0",
  "tMembers": "[zhangsan, lisi]",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被踢出群的用户账号 1",
        "被踢出群的用户账号 2"
    ],
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 1    //高级群踢人出群
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括操作人和被操作人
}
```
:::
::::::

### <span id='高级群申请加入成功（无需加群验证）'>高级群申请加入成功（无需加群验证）</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "id": "lisi",
      "tinfo": {
        "1": "11631",
        "10": "1457075685304",
        "11": "1456823028193",
        "12": "1457075963090",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "高级群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "2"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        },
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 5
  },
  "convType": "TEAM",
  "eventType": "1",
  "fromAccount": "lisi",
  "fromClientType": "IOS",
  "msgTimestamp": "1457076245920",
  "msgType": "NOTIFICATION",
  "msgidClient": "39a89280-edda-47ff-8f2a-3a2a9ae03cf4",
  "msgidServer": "780543197222",
  "resendFlag": "0",
  "tMembers": "[zhangsan, lisi]",
  "to": "11631"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "申请加入成功的用户账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息，
    //此处操作人与被操作人是同一个人，uinfos 包含两条同样的信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 5    //高级群申请加入成功
}
```
:::
::: code tMembers 字段解释
```JSON
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括加入成功的用户
}
```
:::
::::::

### <span id='申请加入高级群（需要验证）'>申请加入高级群（需要验证）</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "body": "wangwu 申请加群",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "lisi",
    "msgTimestamp": "1456821259709",
    "msgType": "TEAM_APPLY",
    "msgidServer": "375024",
    "tMembers": "[zhangsan, li]",
    "to": "11623"
}
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群主和管理员账号
}
```
:::
::::::

### <span id='允许加群申请'>允许加群申请</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
  {
  "data": {
    "id": "lisi",
    "tinfo": {
      "1": "11623",
      "10": "1456821386734",
      "11": "1456811497999",
      "12": "1456821386758",
      "14": "这是群介绍",
      "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
      "16": "1",
      "17": "0",
      "2": "11011",
      "21": "0",
      "22": "0",
      "23": "0",
      "24": "0",
      "3": "高级群",
      "4": "1",
      "5": "zhangsan",
      "6": "10",
      "8": "1",
      "9": "2"
    },
    "uinfos": [
      {
        "1": "zhangsan",
        "11": "142915",
        "12": "1438738423546",
        "13": "1446624332920",
        "2": "11011",
        "3": "zhangsan",
        "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
        "6": "0"
      },
      {
        "1": "lisi",
        "11": "142916",
        "12": "1438740370586",
        "13": "1438740370586",
        "2": "11011",
        "3": "lisi",
        "6": "0"
      }
    ]
  },
  "id": 5
  },
  "convType": "TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "IOS",
  "msgTimestamp": "1456821386769",
  "msgType": "NOTIFICATION",
  "msgidClient": "dd36c8a2-30e7-476a-9608-48879f4d3146",
  "msgidServer": "780006326282",
  "resendFlag": "0",
  "tMembers": "[zhangsan, lisi]",
  "to": "11623"
}
```
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "申请加群的用户账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 5    //高级群申请加入成功
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括加入成功的用户
}
```
:::
::::::

### <span id='拒绝加群申请'>拒绝加群申请</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "tinfo": {
            "1": "11623",
            "10": "1456821961295",
            "11": "1456811497999",
            "12": "1456821961295",
            "14": "这是群介绍",
            "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
            "16": "1",
            "17": "0",
            "2": "11011",
            "21": "0",
            "22": "0",
            "23": "0",
            "24": "0",
            "3": "高级群",
            "4": "1",
            "5": "zhangsan",
            "6": "10",
            "8": "1",
            "9": "1"
        }
    },
    "body": "",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456822044104",
    "msgType": "TEAM_APPLY_REJECT",
    "msgidServer": "375093",
    "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
}
```
:::
::::::

### <span id='退出高级群'>退出高级群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "tinfo": {
        "1": "11623",
        "10": "1456817802112",
        "11": "1456811497999",
        "12": "1456817802112",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "高级群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "1"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 2
  },
  "convType": "TEAM",
  "eventType": "1",
  "fromAccount": "lisi",
  "fromClientType": "IOS",
  "fromNick": "lisi",
  "msgTimestamp": "1456817802118",
  "msgType": "NOTIFICATION",
  "msgidClient": "9ea8ad94-7b8e-4793-8302-23b554b3d5ca",
  "msgidServer": "780006326278",
  "resendFlag": "0",
  "tMembers": "[zhangsan, lisi]",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //退出群的用户信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 2    //退出高级群
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括退出群的用户
}
```
:::
::::::

### <span id='更新高级群'>更新高级群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach":{
     "data": {
        "tinfo": {
            "1": "11623",
            "14": "这是群介绍",
            "15": "[{\"title\": \"这是群公告标题\", \"content\": \"这是群公告内容\", \"creator\": \"zhangsan\", \"time\": 1457075964}]",
            "16": "1"
        },
        "uinfos": [
            {
                "1": "zhangsan",
                "11": "142915",
                "12": "1438738423546",
                "13": "1446624332920",
                "2": "11011",
                "3": "zhangsan",
                "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                "6": "0"
            }
        ]
    },
    "id": 3
    },
    "convType": "TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "msgTimestamp": "1456822570528",
    "msgType": "NOTIFICATION",
    "msgidClient": "473b64e3-5b76-4fd8-ba74-b29a8ec71f7d",
    "msgidServer": "780006326286",
    "resendFlag": "0",
    "tMembers": "[zhangsan, lisi]",
    "to": "11623"
}
```
  
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //更新群信息的操作人信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 3    //更新群信息
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括更新群的用户
}
```
:::
::::::

### <span id='移交群主'>移交群主</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach":{
    "data": {
        "id": "lisi",
        "tinfo": {
        "1": "11631",
        "10": "1456823264040",
        "11": "1456823028193",
        "12": "1456823264170",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "高级群",
        "4": "1",
        "5": "lisi",
        "6": "10",
        "8": "1",
        "9": "2"
        },
        "uinfos": [
        {
            "1": "zhangsan",
            "11": "142915",
            "12": "1438738423546",
            "13": "1446624332920",
            "2": "11011",
            "3": "zhangsan",
            "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNzBjZWFjYmMwZDE=",
            "6": "0"
        },
        {
            "1": "lisi",
            "11": "142916",
            "12": "1438740370586",
            "13": "1438740370586",
            "2": "11011",
            "3": "lisi",
            "6": "0"
        }
        ]
    },
    "id": 6
    },
  "convType": "TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "REST",
  "msgTimestamp": "1456823264181",
  "msgType": "NOTIFICATION",
  "msgidClient": "92606e37-e22f-4cd1-a13c-fc6ec7353a1b",
  "msgidServer": "780543197186",
  "resendFlag": "0",
  "tMembers": "[zhangsan, lisi]",
  "to": "11631"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    "id": "新群主的用户账号"
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //新群主和老群主的信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 6    //更新群信息
```
:::
::: code tMembers 字段解释
```JSON
{
    "tMembers":"[zhangsan, lisi]" //群内有效用户账号列表，包括新群主和老群主
}

```
:::
::::::

## **<span id='超大群相关示例'>超大群相关示例</span>**

### <span id='创建超大群'>创建超大群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
      "1": "11620",
      "10": "1456802852027",
      "11": "1456802852027",
      "12": "1456802852027",
      "16": "0",
      "17": "0",
      "2": "11011",
      "21": "0",
      "22": "0",
      "23": "0",
      "24": "0",
      "3": "超大群",
      "4": "1",
      "5": "zhangsan",
      "6": "10",
      "8": "1",
      "9": "1"
    },
    "body": "邀请您加入群组",
    "convType": "SUPER_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456802852094",
    "msgType": "NOTIFICATION",
    "msgidServer": "371929",
    "to": "11620"
}
```
:::
::: code attach 字段解释
```JSON
{
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
}
```
:::
::::::
 

### <span id='解散超大群'>解散超大群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "data": {
            "uinfos": [
                {
                    "1": "zhangsan",
                    "11": "142915",
                    "12": "1438738423546",
                    "13": "1446624332920",
                    "2": "11011",
                    "3": "zhangsan",
                    "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                    "6": "0"
                }
            ]
        },
        "id": 4
    },
    "convType": "SUPER_TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456810468999",
    "msgType": "NOTIFICATION",
    "msgidClient": "b697a6b2-be71-47f0-8fc0-3c7ff9b15dda",
    "msgidServer": "779872108546",
    "resendFlag": "0",
    "to": "11621"
}
```
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //解散群的操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 405    //超大群解散
}
```
:::
::::::
 

### <span id='超大群邀请他人加群'>超大群邀请他人加群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "tinfo": {
            "1": "11623",
            "10": "1456817802112",
            "11": "1456811497999",
            "12": "1456817802112",
            "14": "这是群介绍",
            "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
            "16": "0",
            "17": "0",
            "2": "11011",
            "21": "0",
            "22": "0",
            "23": "0",
            "24": "0",
            "3": "超大群",
            "4": "1",
            "5": "zhangsan",
            "6": "10",
            "8": "1",
            "9": "1"
        }
    },
    "body": "邀请您加入群组",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456818444874",
    "msgType": "SUPERTEAM_INVITE",
    "msgidServer": "373171",
    "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
  }
}
```
:::
::::::

### <span id='超大群接受邀请入群'>超大群接受邀请入群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "id": "zhangsan",
      "tinfo": {
        "1": "11623",
        "10": "1456811521765",
        "11": "1456811497999",
        "12": "1456811521899",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "2"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        },
        {
          "1": "zhangsan",
          "11": "142915",
          "12": "1438738423546",
          "13": "1446624332920",
          "2": "11011",
          "3": "zhangsan",
          "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNzBjZWFjYmMwZDE=",
          "6": "0"
        }
      ]
    },
    "id": 9
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "lisi",
  "fromClientType": "IOS",
  "msgTimestamp": "1456811521946",
  "msgType": "NOTIFICATION",
  "msgidClient": "335cf3bb-8efa-4cde-953d-9aa775f1a2b2",
  "msgidServer": "780006326273",
  "resendFlag": "0",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "邀请人的账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //邀请人与被邀请人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 411    //超大群接受邀请进群
}
```
:::
::::::

### <span id='超大群拒绝邀请入群'>超大群拒绝邀请入群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "body": "",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "lisi",
    "msgTimestamp": "1456819928681",
    "msgType": "SUPERTEAM_INVITE_REJECT",
    "msgidServer": "373998",
    "to": "11623"
}
```
 

### <span id='超大群增加管理员'>超大群增加管理员</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "data": {
            "ids": ["lisi"],
            "uinfos": [
                {
                    "1": "lisi",
                    "11": "142916",
                    "12": "1438740370586",
                    "13": "1438740370586",
                    "2": "11011",
                    "3": "lisi",
                    "6": "0"
                },
                {
                    "1": "zhangsan",
                    "11": "142915",
                    "12": "1438738423546",
                    "13": "1446624332920",
                    "2": "11011",
                    "3": "zhangsan",
                    "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                    "6": "0"
                }
            ]
        },
        "id": 7
    },
    "convType": "SUPER_TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "msgTimestamp": "1456813138663",
    "msgType": "NOTIFICATION",
    "msgidClient": "3e3e2efe-4f16-4ac2-8669-a8ee17be80bc",
    "msgidServer": "780006326274",
    "resendFlag": "0",
    "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被设为管理员的用户账号 1",
        "被设为管理员的用户账号 2"
    ],
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 407    //超大群添加管理员
}
```
:::
::::::

### <span id='超大群删除管理员'>超大群删除管理员</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "data": {
            "ids": ["lisi"],
            "uinfos": [
                {
                    "1": "lisi",
                    "11": "142916",
                    "12": "1438740370586",
                    "13": "1438740370586",
                    "2": "11011",
                    "3": "lisi",
                    "6": "0"
                },
                {
                    "1": "zhangsan",
                    "11": "142915",
                    "12": "1438738423546",
                    "13": "1446624332920",
                    "2": "11011",
                    "3": "zhangsan",
                    "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                    "6": "0"
                }
            ]
        },
        "id": 8
    },
    "convType": "SUPER_TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "msgTimestamp": "1456815660948",
    "msgType": "NOTIFICATION",
    "msgidClient": "a2b8f49a-cc06-4784-a8e4-84b59c9ac85f",
    "msgidServer": "780006326275",
    "resendFlag": "0",
    "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被删除管理员的用户账号 1",
        "被删除管理员的用户账号 2"
    ],
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 408    //超大群删除管理员
}
```
:::
::::::

### <span id='超大群踢人出群'>超大群踢人出群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "ids": ["lisi"],
      "tinfo": {
        "1": "11623",
        "10": "1456816081224",
        "11": "1456811497999",
        "12": "1456816081359",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "1"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        },
        {
          "1": "zhangsan",
          "11": "142915",
          "12": "1438738423546",
          "13": "1446624332920",
          "2": "11011",
          "3": "zhangsan",
          "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNzBjZWFjYmMwZDE=",
          "6": "0"
        }
      ]
    },
    "id": 1
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "IOS",
  "msgTimestamp": "1456816081368",
  "msgType": "NOTIFICATION",
  "msgidClient": "f3c0437d-fd3c-4900-9b80-ef9c86c1f91f",
  "msgidServer": "780006326276",
  "resendFlag": "0",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "ids":[
        "被踢出群的用户账号 1",
        "被踢出群的用户账号 2"
    ],
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 402    //超大群踢人
}
```
:::
::::::

### <span id='超大群申请加入成功（无需加群验证）'>超大群申请加入成功（无需加群验证）</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "id": "lisi",
      "tinfo": {
        "1": "11631",
        "10": "1457075685304",
        "11": "1456823028193",
        "12": "1457075963090",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "2"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        },
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 5
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "lisi",
  "fromClientType": "IOS",
  "msgTimestamp": "1457076245920",
  "msgType": "NOTIFICATION",
  "msgidClient": "39a89280-edda-47ff-8f2a-3a2a9ae03cf4",
  "msgidServer": "780543197222",
  "resendFlag": "0",
  "to": "11631"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "申请加入成功的用户账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息，
    //此处操作人与被操作人是同一个人，uinfos 包含两条同样的信息
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 410    //超大群申请成功进群
}
```
:::
::::::

### <span id='申请加入超大群（需要验证）'>申请加入超大群（需要验证）</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "body": "wangwu 申请加群",
    "convType": "CUSTOM_TEAM",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "lisi",
    "msgTimestamp": "1456821259709",
    "msgType": "SUPERTEAM_APPLY",
    "msgidServer": "375024",
    "to": "11623"
}
```
:::
::::::

### <span id='允许加超大群申请'>允许加超大群申请</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "id": "lisi",
      "tinfo": {
        "1": "11623",
        "10": "1456821386734",
        "11": "1456811497999",
        "12": "1456821386758",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "1",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "2"
      },
      "uinfos": [
        {
          "1": "zhangsan",
          "11": "142915",
          "12": "1438738423546",
          "13": "1446624332920",
          "2": "11011",
          "3": "zhangsan",
          "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNzBjZWFjYmMwZDE=",
          "6": "0"
        },
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 5
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "IOS",
  "msgTimestamp": "1456821386769",
  "msgType": "NOTIFICATION",
  "msgidClient": "dd36c8a2-30e7-476a-9608-48879f4d3146",
  "msgidServer": "780006326282",
  "resendFlag": "0",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //邀请人
    "id": "申请加群的用户账号" ,
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //操作人与被操作人的用户信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 410    //超大群申请成功进群
}
```
:::
::::::

### <span id='拒绝加超大群申请'>拒绝加超大群申请</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "tinfo": {
      "1": "11623",
      "10": "1456821961295",
      "11": "1456811497999",
      "12": "1456821961295",
      "14": "这是群介绍",
      "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
      "16": "1",
      "17": "0",
      "2": "11011",
      "21": "0",
      "22": "0",
      "23": "0",
      "24": "0",
      "3": "超大群",
      "4": "1",
      "5": "zhangsan",
      "6": "10",
      "8": "1",
      "9": "1"
    }
  },
  "body": "",
  "convType": "CUSTOM_TEAM",
  "customSafeFlag": "0",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "msgTimestamp": "1456822044104",
  "msgType": "SUPERTEAM_APPLY_REJECT",
  "msgidServer": "375093",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    }
}
```
:::
::::::

### <span id='退出超大群'>退出超大群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "tinfo": {
        "1": "11623",
        "10": "1456817802112",
        "11": "1456811497999",
        "12": "1456817802112",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "zhangsan",
        "6": "10",
        "8": "1",
        "9": "1"
      },
      "uinfos": [
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 2
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "lisi",
  "fromClientType": "IOS",
  "fromNick": "lisi",
  "msgTimestamp": "1456817802118",
  "msgType": "NOTIFICATION",
  "msgidClient": "9ea8ad94-7b8e-4793-8302-23b554b3d5ca",
  "msgidServer": "780006326278",
  "resendFlag": "0",
  "to": "11623"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //退出群的用户信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 403    //超大群退群
}
```
:::
::::::

### <span id='更新超大群'>更新超大群</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "data": {
            "tinfo": {
                "1": "11623",
                "14": "这是群介绍",
                "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
                "16": "1"
            },
            "uinfos": [
                {
                    "1": "zhangsan",
                    "11": "142915",
                    "12": "1438738423546",
                    "13": "1446624332920",
                    "2": "11011",
                    "3": "zhangsan",
                    "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xN***ZlOS02MzBjZWFjYmMwZDE=",
                    "6": "0"
                }
            ]
        },
        "id": 3
    },
    "convType": "SUPER_TEAM",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "msgTimestamp": "1456822570528",
    "msgType": "NOTIFICATION",
    "msgidClient": "473b64e3-5b76-4fd8-ba74-b29a8ec71f7d",
    "msgidServer": "780006326286",
    "resendFlag": "0",
    "to": "11623"
}
```
  
:::
::: code attach 字段解释
```JSON
{
  "data": {
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //更新群信息的操作人信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 404    //超大群修改群信息
}
```
:::
::::::

### <span id='移交超大群群主'>移交超大群群主</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "data": {
      "id": "lisi",
      "tinfo": {
        "1": "11631",
        "10": "1456823264040",
        "11": "1456823028193",
        "12": "1456823264170",
        "14": "这是群介绍",
        "15": "[{\"title\":\"这是群公告标题\",\"content\":\"这是群公告内容\",\"creator\":\"zhangsan\",\"time\":1457075964}]",
        "16": "0",
        "17": "0",
        "2": "11011",
        "21": "0",
        "22": "0",
        "23": "0",
        "24": "0",
        "3": "超大群",
        "4": "1",
        "5": "lisi",
        "6": "10",
        "8": "1",
        "9": "2"
      },
      "uinfos": [
        {
          "1": "zhangsan",
          "11": "142915",
          "12": "1438738423546",
          "13": "1446624332920",
          "2": "11011",
          "3": "zhangsan",
          "4": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNzBjZWFjYmMwZDE=",
          "6": "0"
        },
        {
          "1": "lisi",
          "11": "142916",
          "12": "1438740370586",
          "13": "1438740370586",
          "2": "11011",
          "3": "lisi",
          "6": "0"
        }
      ]
    },
    "id": 6
  },
  "convType": "SUPER_TEAM",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "REST",
  "msgTimestamp": "1456823264181",
  "msgType": "NOTIFICATION",
  "msgidClient": "92606e37-e22f-4cd1-a13c-fc6ec7353a1b",
  "msgidServer": "780543197186",
  "resendFlag": "0",
  "to": "11631"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "data": {
    "id": "新群主的用户账号"
    //群信息
    //具体参考 tinfo 字段的定义
    "tinfo": {
 
    },
    //新群主和老群主的信息，
    //具体参考 uinfos 字段的定义
    "uinfos": [
        {},
        {}
    ]
  },
  "id": 406    //超大群移交群主
}
```
:::
::::::

## **<span id='好友相关示例'>好友相关示例</span>**

### <span id='加好友'>加好友</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": "{\"vt\":1}",
    "body": "",
    "convType": "CUSTOM_PERSON",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456827801260",
    "msgType": "FRIEND_ADD",
    "msgidServer": "375387",
    "to": "lisi"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "vt": 1   //vt 即 verify type，加好友验证类型。1：直接加好友，无需验证。2：请求加好友，需要验证。3：同意加好友申请。4：拒绝加好友申请
}
```
:::
::::::

### <span id='删除好友'>删除好友</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "convType": "CUSTOM_PERSON",
    "customSafeFlag": "0",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "msgTimestamp": "1456827724200",
    "msgType": "FRIEND_DELETE",
    "msgidServer": "375386",
    "to": "lisi"
}
```
:::
::::::

## **<span id='单聊消息相关示例'>单聊消息相关示例</span>**

### <span id='文本消息'>文本消息</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": "",
    "body": "文字消息",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromDeviceId": "B0BFF2EB-E2E1-4063-9E73-92FB926BF388",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456888017105",
    "msgType": "TEXT",
    "msgidClient": "f33f0716-6027-47de-a582-37a8dc2d217c",
    "msgidServer": "8364607",
    "resendFlag": "0",
    "to": "lisi",
    "yidunRes": "{\"yidunBusType\":0,\"action\":0,\"labels\":[]}"
}
```
:::
::::::

### <span id='图片消息'>图片消息</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
  "attach": {
    "md5": "d0323f8d447abf3df7256bd66f9d5b62",
    "h": 500,
    "ext": "jpg",
    "size": 9093,
    "w": 500,
    "name": "图片发送于 2016-03-02 11:09",
    "url": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5MTVfMTQ1NTY4==/yMWE1ODBjYjA1MWE="
  },
  "body": "",
  "convType": "PERSON",
  "eventType": "1",
  "fromAccount": "zhangsan",
  "fromClientType": "IOS",
  "fromDeviceId": "B0BFF2EB-E2E1-4063-9E73-92FB926BF388",
  "fromNick": "zhangsan",
  "msgTimestamp": "1456888195062",
  "msgType": "PICTURE",
  "msgidClient": "472f2f50-2b00-4d7b-8b8d-d8870daa0dbd",
  "msgidServer": "8364613",
  "resendFlag": "0",
  "to": "lisi",
  "yidunRes": {
    "yidunBusType": 1,
    "labels": [
      {
        "level": 0,
        "rate": 0.0,
        "label": 100
      },
      {
        "level": 0,
        "rate": 0.0,
        "label": 200
      },
      {
        "level": 0,
        "rate": 0.0,
        "label": 110
      },
      {
        "level": 0,
        "rate": 0.0,
        "label": 400
      },
      {
        "level": 0,
        "rate": 0.0,
        "label": 300
      },
      {
        "level": 0,
        "rate": 0.0,
        "label": 210
      }
    ]
  }
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "md5":"xxxxxxxx",      //图片的 md5 值
  "h":500,               //图片的高
  "w":500,               //图片的宽
  "size":9093,           //图片的大小
  "name":"xxxxxxxx",     //图片的名称
  "url":"xxxxxxxx",      //图片的 url
  "ext":"jpg"            //图片格式
}
```
:::
::::::

### <span id='音频消息'>音频消息</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "size": 14181,
        "ext": "aac",
        "dur": 3900,
        "url": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltYV8xNDI5M***TkzMzAzOGZiZjc=",
        "md5": "4c5cc81dd00817b548b5eef42eac4d11"
    },
    "body": "发来了一段语音",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromDeviceId": "B0BFF2EB-E2E1-4063-9E73-92FB926BF388",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456888940830",
    "msgType": "AUDIO",
    "msgidClient": "b0b703ea-3e10-453e-8650-e3a2802130bd",
    "msgidServer": "8364635",
    "resendFlag": "0",
    "to": "lisi"
}
```
 
:::
::: code attach 字段解释
```JSON
{
  "size":14181,          //音频的大小
  "ext":"aac",           //音频的格式
  "dur":3900,            //音频的时长
  "url":"xxxxxxxx",      //音频的 url
  "md5":"xxxxxxxx"       //音频的 md5 值
}
```
:::
::::::

### <span id='视频消息'>视频消息</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": {
        "url": "http://b12026.nos.netease.com/MTAxMTAxMA==/bmltY***TQxNGEtYWE5ZC04ZDhmYjQyMTE2OTQ=",
        "md5": "c2f2e15af1c9e341187f81e5f8453399",
        "ext": "mp4",
        "h": 480,
        "size": 114347,
        "w": 360,
        "name": "视频发送于 2016-03-02 11:16",
        "dur": 1456
    },
    "body": "",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromDeviceId": "B0BFF2EB-E2E1-4063-9E73-92FB926BF388",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456888595916",
    "msgType": "VIDEO",
    "msgidClient": "57a33622-cd80-4c65-b8d3-15f3c2bb128f",
    "msgidServer": "8364616",
    "resendFlag": "0",
    "to": "lisi"
}
``` 
:::
::: code attach 字段解释
```JSON
{
  "url":"xxxxxxxx",      //视频的 url
  "md5":"xxxxxxxx",      //视频的 md5 值
  "ext":"mp4",           //视频的格式
  "h":"480",             //视频的高
  "w":"360",             //视频的宽
  "size":14181,          //视频的大小
  "name":"xxxxxxxx",     //视频的名称
  "dur":1456             //视频的时长
}
```
:::
::::::

### <span id='地理位置消息'>地理位置消息</span>

:::::: div linked-codes
::: code attach 抄送示例

```JSON
{
    "attach": "{\"title\":\"中国 浙江省 杭州市 网商路 599 号\",\"lng\":120.1908686708565, \"lat\":30.18704515647036}",
    "body": "",
    "convType": "PERSON",
    "eventType": "1",
    "fromAccount": "zhangsan",
    "fromClientType": "IOS",
    "fromDeviceId": "B0BFF2EB-E2E1-4063-9E73-92FB926BF388",
    "fromNick": "zhangsan",
    "msgTimestamp": "1456888595916",
    "msgType": "LOCATION",
    "msgidClient": "57a33622-cd80-4c65-b8d3-15f3c2bb128f",
    "msgidServer": "8364616",
    "resendFlag": "0",
    "to": "lisi"
}
```

:::
::: code attach 字段解释

```JSON
{
  "title":"中国 浙江省 杭州市 网商路 599 号",    //地理位置 title
  "lng":120.1908686708565,        // 经度
  "lat":30.18704515647036                  // 纬度
}
```
:::
::::::