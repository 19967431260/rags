## <span id="录制服务API">录制服务API</span>  

### <span id="录制配置">录制配置</span>

#### <span id="录制配置设置">录制配置设置</span>

#####  接口说明

按流名配置录制信息

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/config/set HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

|参数 | 类型 | 说明 | 必须|
|:------|:------|:------|:------|
|streamName | String | 流名称 | 是 |
| duration | Int | 录制切片时长, 取值范围[5,120], 单位分钟, 默认120 | 否|
| format | Int | 录制切片文件容器格式, 0:mp4,1:flv,2:mp3，默认1| 否|
| filenamePrefix | Int | 录制切片文件名前缀,录制文件名前缀，默认为流名称） | 否|
| autoRecord | Int | 是否开启自动录制，0：否；1：是，默认为：1，设置为0后，可以通过主动录制接口控制录制 |否 |

**注意：**

* 在推流过程中调用此接口，相关参数变化会在下次推流中生效
* streamName和filenamePrefix，只支持中文、字母和数字等3字节及以下编码长度的utf-8，编码字符长度不超过128字节，字符长度指的是字符编码单元的数量。下面的录制相关接口，streamName描述同此。
* format值意义如下：0-mp4, 1-flv, 2-mp3, 在mp3录制场景下, 即使推流有视频流, 录制也只会包含音频流
* 录制切片在点播系统中的名称为{filePrefix}\_{sliceStartTime}\_{sliceEndTime}, 如：20190808演唱会直播_20190808-200106_20190808-220105

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx","duration": 300,"format": 0, "filenamePrefix":"20190808演唱会直播"}' https://vcloud.163.com/app/record/stream/config/set

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | Int | 状态码 
 requestId | String | 请求id
 msg | String | 错误信息, 非200状态码下返回

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
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败   
 501     | 内部错误             
 607     | 用户信息不存在           
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空       
 631     | 请求参数错误      
 723     | 使用直播录制功能需开通云点播服务

#### <span id="录制配置查询">录制配置查询</span>

##### 接口说明

按流名获取录制相关配置。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/config/get HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

|参数 | 类型 | 说明 | 必须|
|:------|:------|:------|:------|
| streamName   | String | 流名称| 是  |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/record/stream/config/get

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| streamName | String | 流名称 |
| format | Int | 录制文件格式，0:mp4,1:flv,2:mp3 |
| duration | Int | 录制切片时长，分钟，取值范文5~120，默认120 |
| filenamePrefix | String |录制切片文件名前缀,录制文件名前缀，默认为流名称）|
| autoRecord | Int | 是否开启自动录制，0：否；1：是，默认为：1|

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
    "ret":{
        "streamName": "xxx",
        "duration": 120,
        "format": 0,
        "filePrefixPrefix": "20190808演唱会直播",
        "autoRecord": 0
    }
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误        
 723     | 使用直播录制功能需开通云点播服务
 2200 | 直播流录制配置不存在

#### <span id="录制配置删除">录制配置删除</span>

##### 接口说明

按流名删除录制相关配置。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/config/delete HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

|参数 | 类型 | 说明 | 必须|
|:------|:------|:------|:------|
| streamName   | String | 流名称| 是  |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/record/stream/config/delete

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 msg | String | 错误信息, 非200状态码下返回

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
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误        
 723     | 使用直播录制功能需开通云点播服务

### <span id="查询录制状态">查询录制状态</span>

#### <span id="接口说明">接口说明</span>

按流名获取录制状态。

#### <span id="请求说明">请求说明</span>

    POST https://vcloud.163.com/app/record/stream/status HTTP/1.1
    Content-Type: application/json;charset=utf-8

#### <span id="参数说明">参数说明</span>

|参数 | 类型 | 说明 | 必须|
|:------|:------|:------|:------|
| streamName   | String | 流名称| 是  |

#### <span id="curl请求示例">curl请求示例</span>

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamxxxxxxxxx"}' https://vcloud.163.com/app/record/stream/status

#### <span id="返回说明">返回说明</span>

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| recordStatus | Int | 流状态（0：空闲；1：录制中） |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
    "ret":{
        "recordStatus": 0
    }
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

#### <span id="响应状态码">响应状态码</span>

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误        
 723     | 使用直播录制功能需开通云点播服务
 2200     | 直播流录制配置不存在

### <span id="录制回调">录制回调</span>

##### 回调请求说明

**录制回调请求头**

| 字段名 | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| sign   | 对回调body内容按指定格式转换后进行MD5加密生成的签名，sign字段为http请求头内容。签名规则：将body所有字段按key进行字典排序(升序)组成待签名字符串content，对字符串content+signKey进行MD5签名，如：beginTime=1483406830579&streamName=123456&endTime=1483406857109&nId=nId1000&orig_video_key=6355099987a648bfbec0c53.mp4&vid=1000&video_name=092710_20170103signKey,对其进行MD5签名 |

**录制文件回调示例**

```
{"vid":"7563","orig_video_key":"8bfe052367414ef1bf8baa5b118111_1480499359291_1480499570111_2541778-00002.flv","video_name":"创建频道1_20161130-174919_20161130-175250","nId":"nId1144","beginTime":"1480499359291","endTime":"1480499570111","streamName":"1234XXX","type":"record_stream_file"}
```

>  计算MD5签名时须考虑body所有字段，请以实际收到的body字段为准，body字段可能会有新增，以下仅为body字段示例。

| 参数                  | 类型   | 说明                                                         |
| --------------------- | ------ | ------------------------------------------------------------ |
| video_name            | String | 录制后文件名，格式为filename_YYYYMMDD-HHmmssYYYYMMDD-HHmmss, 文件名录制起始时间（年月日时分秒) -录制结束时间（年月日时分秒) |
| orig_video_key        | String | 录制文件在点播桶中的存储路径                                 |
| vid                   | String | 录制文件ID                                                   |
| streamName            | String | 流名                                                         |
| beginTime             | String | 录制文件起始时间戳(毫秒)                                     |
| endTime               | String | 录制文件结束时间戳(毫秒)                                     |
| customizedCallbackTag | String | 自定义回调标签                                               |
| recordFileFlag        | String | 录制文件标签，为1表示直播流有分辨率变化                      |
| type                  | String | 通知类型，录制文件通知回调默认为"record_stream_file"         |
| nId                   | String | 消息ID，同一条消息nId全局唯一，网络超时或接收方返回非200状态码时根据业务规则进行重发，接收方接到多条通知情况下可用于进行消息去重 |
| origUrl               | String | 录制文件地址（不带防盗链）                                        |

**流状态通知回调示例**

```
{"status":"1","streamName":"1234XXX","time":"1480499359291","nId":"nId1145","type":"record_stream_status"}
```

>  计算MD5签名时须考虑body所有字段，请以实际收到的body字段为准，body字段可能会有新增，以下仅为body字段示例。

| 参数       | 类型   | 说明                                                         |
| ---------- | ------ | ------------------------------------------------------------ |
| status     | String | 流录制状态，0表示空闲，1表示录制中                           |
| streamName | String | 流名                                                         |
| time       | String | 流状态变化时间戳，毫秒                                       |
| type       | String | 通知类型，录制状态通知回调默认为"record_stream_status"       |
| nId        | String | 消息ID，同一条消息nId全局唯一，网络超时或接收方返回非200状态码时根据业务规则进行重发，接收方接到多条通知情况下可用于进行消息去重 |

#### <span id=""></span>

#### <span id="录制回调设置">录制回调设置</span>

##### 接口说明

配置接收录制通知的URL地址，修改时也通过该接口进行变更。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/notify/set HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

|参数 | 类型 | 说明 | 必须|
|:------|:------|:------|:------|
| notifyURL | String | 是 | 直播录制回调URL地址 |
| signKey | String | 否 | 通知请求签名密钥，默认vcloud |
| notifyExtParams | List<String> | 否 | 直播回调扩展参数，当前仅可选择origUrl（录制文件地址） |

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"notifyURL": "http://xx","notifyExtParams": ["origUrl"]}' https://vcloud.163.com/app/record/stream/notify/set

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

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
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误
 655  | 请求参数中回调地址无法访问
 723     | 使用直播录制功能需开通云点播服务

#### <span id="查询回调配置">查询回调配置</span>

##### 接口说明

查询录制通知配置。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/notify/get HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

无

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" https://vcloud.163.com/app/record/stream/notify/get

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| notifyURL | String | 直播推流状态通知接收URL地址 |
| signKey | String | 通知请求签名密钥，默认vcloud |

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
    "ret":{
        "notifyURL": "http://xxx",
        "signKey": "vcloud"
    }
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误        
 723     | 使用直播录制功能需开通云点播服务
 2103 | 回调配置不存在

#### <span id="回调配置删除">回调配置删除</span>

##### 接口说明

删除录制通知配置。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/notify/delete HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

无

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" https://vcloud.163.com/app/record/stream/notify/delete

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 msg | String | 错误信息, 非200状态码下返回

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "msg":"使用直播录制功能需开通云点播服务",
    "requestId": "xxx"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功   
 409     | 认证失败
 501     | 内部错误             
 607     | 用户信息不存在        
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空          
 631     | 请求参数错误        
 723     | 使用直播录制功能需开通云点播服务

### <span id="主动录制">主动录制</span>

#### <span id="主动发起直播录制">主动发起直播录制</span>

##### 接口说明

该接口用于主动发起直播录制。

返回结果状态码为200，表明录制任务成功发起。非200状态码，请根据错误码按需进行重试等相应操作。

录制任务成功发起后，如果推流中止而导致拉不到流，超时后任务会自动停止，同时发送流的录制状态通知。重新推流直播后，需要用户自己重新请求发起。

主动录制提供了实时控制录制时间的能力，不建议用户将该接口与自动录制同时间混合使用。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/start HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 是

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamNamexxxxxxxxx"}' https://vcloud.163.com/app/record/stream/start

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| streamName | String | 流名|
| devMsg | String | 系统任务信息，部分情况下返回，仅供参考|

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
    "ret":{
        "streamName": "xxx"
    }
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "requestId": "xxx",
    "msg":"使用直播录制功能需开通云点播服务"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功  
 409     | 认证失败       
 501     | 内部错误             
 607     | 用户信息不存在         
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空        
 618     | 查询数据信息不存在        
 631     | 请求参数错误
 723     | 使用直播录制功能需开通云点播服务
 2200     | 直播流录制配置不存在
 2210     | 直播流创建录制失败  

#### <span id="主动停止直播录制">主动停止直播录制</span>

##### 接口说明

该接口用于结束直播录制。

在录制任务运行后，如果系统未收到该接口请求，那么在推流行为结束后拉流超时，任务会自动停止，如果注册了状态回调，系统会发送一个状态通知。重新推流直播后，需要用户自己重新请求发起直播录制。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/stop HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 是

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamNamexxxxxxxxx"}' https://vcloud.163.com/app/record/stream/stop

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | Int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| streamName | String | 流名|

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{        
    "code":200,
    "requestId": "xxx",
    "ret":{
        "streamName": "xxx"
    }
}
    
//错误返回示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":723,
    "requestId": "xxx",
    "msg":"使用直播录制功能需开通云点播服务"
}
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败     
 501     | 内部错误             
 607     | 用户信息不存在          
 613     | CheckSum为空       
 614     | AppKey为空         
 615     | CurTime为空
 631     | 请求参数错误         
 723     | 使用直播录制功能需开通云点播服务
 2211     | 直播流录制停止失败

### <span id="录制重置">录制重置</span>

#### <span id="接口说明">接口说明</span>

该接口用于对直播流正在进行的录制任务进行重置，此时会进行切片，并以最新录制配置发起新的录制任务。

录制重置适用于自动录制和主动录制。

#### <span id="请求说明">请求说明</span>

    POST https://vcloud.163.com/app/record/stream/reset HTTP/1.1
    Content-Type: application/json;charset=utf-8

#### <span id="参数说明">参数说明</span>

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 是

#### <span id="curl请求示例">curl请求示例</span>

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName": "streamNamexxxxxxxxx"}' https://vcloud.163.com/app/record/stream/reset

#### <span id="返回说明">返回说明</span>

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| streamName | String | 流名|

```
    //成功结果示例
    "Content-Type": "application/json; charset=utf-8"
    {        
        "code":200,
        "requestId": "xxx",
        "ret":{
            "streamName": "xxx"
        }
    }
    
    //错误返回示例
    "Content-Type": "application/json; charset=utf-8"
    {
        "code":723,
        "requestId": "xxx",
        "msg":"使用直播录制功能需开通云点播服务"
    }
```

#### <span id="响应状态码">响应状态码</span>

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败     
 501     | 内部错误             
 607     | 用户信息不存在
 613     | CheckSum为空
 614     | AppKey为空         
 615     | CurTime为空     
 631     | 请求参数错误 
 723     | 使用直播录制功能需开通云点播服务
 2200     | 直播流录制配置不存在
 2212     | 直播流录制重置失败

### <span id="录制文件列表查询">录制文件列表查询</span>

#### <span id="接口说明">接口说明</span>

通过开始和结束的时间点，获取某直播流录制文件列表。(时间跨度不能超过1周)

#### <span id="请求说明">请求说明</span>

```
    POST https://vcloud.163.com/app/record/stream/files HTTP/1.1
    Content-Type: application/json;charset=utf-8
```

#### <span id="参数说明">参数说明</span>

 参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名 | 是
 beginTime | Long | 查询的起始时间戳，单位秒| 是
 endTime | Long | 查询的结束时间戳，单位秒 | 是
 curPage | Int | 分页索引，不填默认是1|否
 pageSize | Int | 限定每页返回的数量，返回的结果小于或等于该值，范围[1, 100]，默认100|否
 sort | String | 按录制文件开始时间排序，asc表示升序，desc表示降序，默认为asc | 否

#### <span id="curl请求示例">curl请求示例</span>

```
    curl -X POST -H "Content-Type: application/json" -H "AppKey: 027338bf05cc4a65b5d98bc9d6af80b3" -H "Nonce: 12345" -H "CurTime: 1469427735815" -H "CheckSum: 86d9602149544997a86769a8d6088cabb12b212b" -d '{"streamName":"123456", "beginTime":1476115200, "endTime":1476201600}' https://vcloud.163.com/app/record/stream/files
```

#### <span id="返回说明">返回说明</span>

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
|curPage | Int | 分页大小|
|pageSize | Int |每页大小|
|totalPageNum | Int | 总页数|
|totalSize | Int | 总记录数|
| fileList | JsonArray | 录制文件列表|
| name | String | 录制后文件名，格式为filenamePrefix_YYYYMMDD-HHmmss_YYYYMMDD-HHmmss, 文件名\_录制起始时间（年月日时分秒) -录制结束时间（年月日时分秒)|
| objectName | String | 录制文件在点播桶中的存储对象名|
| vid | Long | 录制文件ID|

```
//成功结果示例
"Content-Type": "application/json; charset=utf-8"
{
    "code":200,
    "requestId": "xxx",
    "ret":{
        "curPage":1,
        "pageSize":100,
        "totalPageNum":2,
        "totalSize":104,
        "fileList":[
            {
                "name":"new_20160628-113352_20160628-133351",
                "objectName":"123456_1467092031353_1312-00001.flv",
                "vid":42
            },
            {
                "name":"new_20160628-093349_20160628-113352",
                "objectName":"123456_1467084832593_1312-00000.flv",
                "vid":41
            },
            ...
        ]
    }
}
```

#### <span id="响应状态码">响应状态码</span>

 状态码 | 含义
:------|:------
 200 | 操作成功
 409 | 用户登录认证失败
 501 | 内部错误
 613 | CheckSum为空
 614 | AppKey为空
 615 | CurTime为空
 618 | 频道信息不存在
 631 | 请求参数错误
 723  | 使用直播录制功能需开通云点播服务

### <span id="录制文件存活时间">录制文件存活时间</span>

#### <span id="录制文件存活配置设置">录制文件存活配置设置</span>

##### 接口说明

用户可设置录制文件的存活时间，过期后文件将被自动删除。配置只对新生成的录制文件生效。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/expire/set HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 否
 lifespan | Long | 录制文件存活时间（单位：秒），范围：[1天-1年]| 是

**注意：**

* 如果streamName为NULL，则是用户级别的存活时间；如果streamName不为NULL，则是流级别的存活时间
* 如果同时设置了用户级别和流级别的存活时间，如：设置用户级别存活时间为172800（2天），流名为"streamxxx"的录制文件存活时间为86400（1天），那么流名为"streamxxx"下产生的录制文件的存活时间为1天，除了"streamxxx"之外的所有流产生的录制文件的存活时间为2天
* 配置只对新生成的录制文件生效

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"lifespan": 86400}' https://vcloud.163.com/app/record/stream/expire/set

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 msg | String | 错误信息, 非200状态码下返回

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
        "code":723,
        "requestId": "xxx",
        "msg":"使用直播录制功能需开通云点播服务"
    }
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败     
 501     | 内部错误             
 607     | 用户信息不存在
 613     | CheckSum为空
 614     | AppKey为空         
 615     | CurTime为空 
 631     | 请求参数错误 
 723     | 使用直播录制功能需开通云点播服务

#### <span id="录制文件存活配置查询">录制文件存活配置查询</span>

##### 接口说明

用户查询之前设置的录制文件的存活时间，包括用户级别和流级别。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/expire/get HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 否

**注意：**

* 如果streamName不为NULL，且已设置其存活配置，则返回结果会包含流级别
* 如果已设置用户级存活配置，则返回结果会包含用户级别
* 如果无streamName和用户级别的存活配置，那么返回空

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName":"123456"}' https://vcloud.163.com/app/record/stream/expire/get

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 ret | JSON | 返回信息, 200状态码下返回
 msg | String | 错误信息, 非200状态码下返回

 其中，ret格式如下：

| 参数   | 类型     | 说明          |
| :--- | :----- | :---------- |
| userLifespan | Long | 用户级别的存活时间（单位：秒），范围：[1天-1年]|
| streamLifespan | String | 流级别的存活时间（单位：秒），范围：[1天-1年]|

```
    //成功结果示例,未配置存活时间
    "Content-Type": "application/json; charset=utf-8"
    {        
        "code":200,
        "requestId": "xxx",
        "ret":{
         }
    }
    //成功结果示例
    "Content-Type": "application/json; charset=utf-8"
    {        
        "code":200,
        "requestId": "xxx",
         "ret":{
             "userLifespan": 86400,
             "streamLifespan": 86400
         }
    }
    
    //错误返回示例
    "Content-Type": "application/json; charset=utf-8"
    {
        "code":723,
        "requestId": "xxx",
        "msg":"使用直播录制功能需开通云点播服务"
    }
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败     
 501     | 内部错误             
 607     | 用户信息不存在
 613     | CheckSum为空
 614     | AppKey为空         
 615     | CurTime为空
 631     | 请求参数错误 
 723     | 使用直播录制功能需开通云点播服务

#### <span id="录制文件存活配置取消">录制文件存活配置取消</span>

##### 接口说明

用户取消录制文件的存活时间。取消后，录制文件不再有存活时间的概念，除非主动删除否则文件将永久保存。同时，对于已经入库且等待失效删除的文件，将不会被删除。

##### 请求说明

    POST https://vcloud.163.com/app/record/stream/expire/cancel HTTP/1.1
    Content-Type: application/json;charset=utf-8

##### 参数说明

参数 | 类型 | 说明 | 必须
:------|:------|:------|:------
 streamName | String | 流名| 否

**注意：**

* 取消用户级别和流级别的存活时间是互不影响的。如果同时设置了用户级别和流级别的存活时间：取消某流级别的存活时间后，该流下新生成录制文件的存活时间遵循用户级别的设置；取消用户级别的存活时间后，对于有设置存活配置的流，其下后续新生成录制文件的存活时间仍遵循该流的设置。

##### curl请求示例

    curl -X POST -H "Content-Type: application/json" -H "AppKey: 29781bbc4db54742a3ebcxxxxxxxxxxx" -H "Nonce: 12345" -H "CurTime: 1469171950571" -H "CheckSum: 4ba6ca70c685eb900917e423eadaxxxxxxxxxxxxx" -d '{"streamName":"123456"}' https://vcloud.163.com/app/record/stream/expire/cancel

##### 返回说明

http 响应：json

 参数 | 类型 | 说明
:------|:------|:------
 code | int | 状态码 
 requestId | String | 请求id
 msg | String | 错误信息, 非200状态码下返回

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
        "code":723,
        "requestId": "xxx",
        "msg":"使用直播录制功能需开通云点播服务"
    }
```

##### 响应状态码

 状态码 | 含义
:------|:------
 200     | 操作成功
 409     | 认证失败     
 501     | 内部错误             
 607     | 用户信息不存在
 613     | CheckSum为空
 614     | AppKey为空         
 615     | CurTime为空
 631     | 请求参数错误 
 723     | 使用直播录制功能需开通云点播服务