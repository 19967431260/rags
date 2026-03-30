## <span id="直播服务API">直播服务API</span>
  
### <span id="流状态查询">流状态查询</span>

##### 接口说明
按直播流名查询状态，状态包括直播中和空闲
##### 请求方式

POST /app/live/stream/status HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数   | 类型  | 必选  | 说明   |
| :--- | :----- | :---------- | :--- |
| streamName | String | 是 | 流名称    |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/live/stream/status

##### 返回参数

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| streamStatus | Int | 流状态（0：空闲；1：直播中） |


##### 返回状态码

| 状态码 | 说明             |
| ------ | ---------------- |
| 2102   | 直播流记录不存在 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2102,
    "msg":"直播流记录不存在",
    "requestId": "xxx"
}
```

### <span id="流禁用">流禁用</span>

##### 接口说明
按直播流名请求禁播。每个应用上限10000条。
##### 请求方式

POST /app/live/stream/forbid HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数   | 类型  | 必选  | 说明   |
| :--- | :----- | :---------- | :--- |
| streamName | String | 是 | 流名称 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/live/stream/forbid

##### 返回参数

##### 返回状态码

| 状态码 | 说明           |
| ---- | -------------- |
| 2104 | 直播流禁用失败 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2104,
    "msg":"直播流禁用失败",
    "requestId": "xxx"
}
```
### <span id="4.3 流恢复">4.3 流恢复</span>

##### 接口说明
恢复禁播的流

##### 请求方式
POST /app/live/stream/resume HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数   | 类型  | 必选  | 说明   |
| :--- | :----- | :---------- | :--- |
| streamName | String | 是 | 流名称 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/live/stream/resume

##### 返回参数

##### 返回状态码

| 状态码 | 说明           |
| ---- | -------------- |
| 2105 | 直播流恢复失败 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2105,
    "msg":"直播流恢复失败",
    "requestId": "xxx"
}
```
### <span id="流禁用列表查询">流禁用列表查询</span>

##### 接口说明
查询被禁用的直播流列表

频控：60秒内最多100次请求，无惩罚时间

##### 请求方式
POST /app/live/stream/blackList HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数     | 类型    | 必选 | 说明                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| marker   | String  | 否   | 流名，字典序的起始标记，只列出该标记，不填默认从头开始       |
| pageSize | Integer | 否   | 限定每页返回的数量，返回的结果小于或等于该值，范围[1,500]，默认100 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"marker": "streamxxxxxxxxx","pageSize":10}' https://vcloud.163.com/app/live/stream/blackList

##### 返回参数

| 参数           | 类型          | 说明                                                      |
| -------------- | ------------- | --------------------------------------------------------- |
| isTruncated    | Boolean       | 是否截断，true表示后面还有数据，false表示所有数据均已返回 |
| nextMarker     | String        | 下一次查询的起点标记，仅当isTruncated=true时返回          |
| totalSize      | Integer       | 所有被禁用的流总数                                        |
| streamNameList | List\<String> | 流列表，按字典升序排列                                    |

##### 返回状态码

| 状态码 | 说明           |
| ---- | -------------- |
| 2401 | 参数marker非法 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2401,
    "msg":"参数marker非法",
    "requestId": "xxx"
}
```
### <span id="推流状态通知">推流状态通知</span>

#### <span id="设置">设置</span>

##### 接口说明
开启推流状态通知，配置接收通知的URL地址，修改时也通过该接口进行变更。

##### 请求方式

POST /app/live/notify/set HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数   | 类型  | 必选  | 说明   |
| :--- | :----- | :---------- | :--- |
| notifyURL | String | 是 | 直播推流状态通知接收URL地址 |
| signKey | String | 否 | 通知请求签名密钥，默认vcloud |

> signKey是回调通知的加密秘钥，用该秘钥对通知内容生成MD5签名，用于接口的校验，如不设置，则默认为"vcloud"

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"notifyUrl": "http://example.com"}' https://vcloud.163.com/app/live/notify/set

##### 返回参数

##### 返回状态码

| 状态码 | 说明                       |
| ---- | -------------------------- |
| 655  | 请求参数中回调地址无法访问 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":655,
    "msg":"请求参数中回调地址无法访问",
    "requestId": "xxx"
}
```
**流状态通知回调示例**

```json
{
	"status":"1",
	"streamName":"stream_name_test",
	"time":"1575969859000",
	"type":"stream_status"
}
```

> 计算MD5签名时须考虑body所有字段，请以实际收到的body字段为准，以下仅为body字段示例。

| 参数       | 类型   | 说明                                          |
| ---------- | ------ | --------------------------------------------- |
| status     | String | 流状态，0表示空闲，1表示直播中                |
| streamName | String | 流名                                          |
| time       | String | 流状态变化时间戳，毫秒                        |
| type       | String | 通知类型，流状态通知回调默认为"stream_status" |

#### <span id="查询">查询</span>

##### 接口说明
查询推流状态通知配置。

##### 请求方式

POST /app/live/notify/get HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" https://vcloud.163.com/app/live/notify/get

##### 返回参数

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| notifyURL | String | 直播推流状态通知接收URL地址 |
| signKey | String | 通知请求签名密钥，默认vcloud |

##### 返回状态码

| 状态码 | 说明           |
| ---- | -------------- |
| 2103 | 回调配置不存在 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2103,
    "msg":"回调配置不存在",
    "requestId": "xxx"
}
```
#### <span id="4.5.3 删除">4.5.3 删除</span>

##### 接口说明
删除推流状态通知配置，关闭推流状态通知。

##### 请求方式

POST /app/live/notify/delete HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" https://vcloud.163.com/app/live/notify/delete

##### 返回参数

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2101,
    "msg":"请先开通直播服务2.0",
    "requestId": "xxx"
}
```
### <span id="流配置操作历史查询">流配置操作历史查询</span>

##### 接口说明
查询直播流上的管理操作记录，保留最近30天的数据

频控：60秒内最多100次请求，无惩罚时间

##### 请求方式

POST /app/live/stream/actionList HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数       | 类型    | 必选 | 说明                                                         |
| ---------- | ------- | ---- | ------------------------------------------------------------ |
| streamName | String  | 是   | 流名称                                                       |
| beginTime  | Long    | 是   | 查询开始时间(s)                                              |
| endTime    | Long    | 是   | 查询结束时间(s)，endTime和beginTime之间的间隔不能超过30天    |
| curPage    | Integer | 否   | 分页索引，不填默认是1                                        |
| pageSize   | Integer | 否   | 限定每页返回的数量，返回的结果小于或等于该值，范围[1, 500]，默认100 |
| sort       | String  | 否   | 按操作时间排序，asc表示按时间升序，desc表示按时间降序，默认为asc |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx", "beginTime":1580900653, "endTime:1580900953}' https://vcloud.163.com/app/live/stream/actionList

##### 返回参数

| 参数         | 类型    | 说明                                           |
| ------------ | ------- | ---------------------------------------------- |
| actionList   |         | 查询结果列表                                   |
| - action     | String  | 管理操作<br>"forbid"表示禁用，"resume"表示恢复 |
| - clientIp   | String  | 操作IP                                         |
| - time       | Long    | 操作时间(s)                                    |
| curPage      | Integer | 当前页数                                       |
| pageSize     | Integer | 每页大小                                       |
| totalPageNum | Integer | 总页数                                         |
| totalSize    | Integer | 总记录数                                       |

##### 返回状态码

| 状态码 | 说明             |
| ---- | ---------------- |
| 2102 | 直播流记录不存在 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2102,
    "msg":"直播流记录不存在",
    "requestId": "xxx"
}
```
### <span id="直播中流列表查询">直播中流列表查询</span>

##### 接口说明

分页查询正在直播中的流列表

频控：60秒内最多100次请求，无惩罚时间

##### 请求方式

POST /app/live/stream/onlineList HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数     | 类型    | 必须 | 说明                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| marker   | String  | 否   | 流名，字典序的起始标记，只列出该标记之后的部分，不填默认从头开始 |
| pageSize | Integer | 否   | 限定每页返回的数量，返回的结果小于或等于该值，范围[1, 500]，默认100 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"marker": "streamxxxxxxxxx"}' https://vcloud.163.com/app/live/stream/onlineList

##### 返回参数

| 参数           | 类型          | 说明                                                      |
| -------------- | ------------- | --------------------------------------------------------- |
| isTruncated    | Boolean       | 是否截断，true表示后面还有数据，false表示所有数据均已返回 |
| nextMarker     | String        | 下一次查询的起点标记，仅当isTruncated=true时返回          |
| totalSize      | Integer       | 所有正在直播中的流总数                                    |
| streamNameList | List\<String> | 流列表，按字典升序排列                                    |

##### 返回状态码

| 状态码 | 说明           |
| ---- | -------------- |
| 2401 | 参数marker非法 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2401,
    "msg":"参数marker非法",
    "requestId": "xxx"
}
```
### <span id="直播中流观看人数查询">直播中流观看人数查询</span>

##### 接口说明

查询直播中的流观看人数，数据延迟1分钟左右

频控：5分钟内最多30次请求，无惩罚时间

##### 请求方式

POST /app/live/stream/stat/onlineUserNum HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数           | 类型   | 必选 | 说明     |
| -------------- | ------ | ---- | -------- |
| streamName     | String | 是   | 流名称   |
| pullDomainName | String | 是   | 拉流域名 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx", "pullDomainName":"pull.domain.name"}' https://vcloud.163.com/app/live/stream/stat/onlineUserNum

##### 返回参数

| 参数     | 类型    | 说明       |
| :------- | :------ | :--------- |
| totalNum | Integer | 在线总人数 |

> 注意：如用户开启了录制，则接口返回的在线人数会略微大于实际在线观看人数

##### 返回状态码

| 状态码 | 说明                     |
| ---- | ------------------------ |
| 2102 | 直播流记录不存在         |
| 2106 | 统计数据查询失败         |
| 2402 | 域名不存在或与用户不匹配 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2102,
    "msg":"直播流记录不存在",
    "requestId": "xxx"
}
```
### <span id="历史直播的流观看人数查询">历史直播的流观看人数查询</span>

##### 接口说明

查询历史直播的流观看人数（最多可查询最近15天的数据）

频控：5分钟内最多30次请求，无惩罚时间

##### 请求方式

POST /app/live/stream/stat/historyUserNum HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数           | 类型    | 必选 | 说明                                                       |
| -------------- | ------- | ---- | ---------------------------------------------------------- |
| streamName     | String  | 是   | 流名称                                                     |
| pullDomainName | String  | 是   | 拉流域名                                                   |
| beginTime      | Long    | 否   | 查询开始时间(s)                                            |
| endTime        | Long    | 否   | 查询结束时间(s)，endTime和beginTime之间的间隔不能超过2小时 |
| gap            | Integer | 否   | 打点间隔(s)，可选10、60，默认60                            |
| time           | Long    | 否   | 查询时刻(s)                                                |

> 填写beginTime和endTime代表查询历史上某一时间段内的直播观看人数，返回数据的打点间隔由gap指定
>
> 填写time代表查询历史上某一时刻的直播观看人数
>
> 两种查询模式只能选择其一，两种都填优先以time为准

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx", "pullDomainName":"pull.domain.name", "beginTime":1580900653, "endTime:1580900953}' https://vcloud.163.com/app/live/stream/stat/historyUserNum

##### 返回参数

| 参数     | 类型    | 说明                         |
| -------- | ------- | ---------------------------- |
| totalNum | Integer | 在线总人数，仅在传time时返回 |
| details  | List    | 详细信息列表                 |
| - time   | String  | 时间戳，形如20191208144500   |
| - num    | Integer | 在线人数                     |

##### 返回状态码

| 状态码 | 说明                     |
| ---- | ------------------------ |
| 2102 | 直播流记录不存在         |
| 2106 | 统计数据查询失败         |
| 2402 | 域名不存在或与用户不匹配 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2102,
    "msg":"直播流记录不存在",
    "requestId": "xxx"
}
```
### <span id="直播中流信息查询">直播中流信息查询</span>

##### 接口说明

查询直播中推流的详细统计信息

频控：5分钟内最多100次请求，无惩罚时间

##### 请求方式

POST /app/live/stream/stat/onlineDetail HTTP/1.1
Content-Type: application/json;charset=utf-8

##### 请求参数

| 参数       | 类型   | 必选 | 说明   |
| ---------- | ------ | ---- | ------ |
| streamName | String | 是   | 流名称 |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/live/stream/stat/onlineDetail

##### 返回参数

| 参数         | 类型   | 说明                                 |
| ------------ | ------ | ------------------------------------ |
| detail       | Map    | 详细信息                             |
| - bitRate    | Float  | 主播当前码率 单位：bps               |
| - startTime  | String | 主播开始推流时间，形如20191208144500 |
| - frameRate  | Float  | 主播当前编码帧率                     |
| - resolution | String | 分辨率                               |

##### 返回状态码

| code | 说明             |
| ---- | ---------------- |
| 2102 | 直播流记录不存在 |
| 2106 | 统计数据查询失败 |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx"
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":2102,
    "msg":"直播流记录不存在",
    "requestId": "xxx"
}
```
### <span id="直播截图（后续补充）">直播截图（后续补充）</span>