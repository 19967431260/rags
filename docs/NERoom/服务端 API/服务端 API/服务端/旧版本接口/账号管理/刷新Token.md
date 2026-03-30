通过该接口刷新 Token。

使用场景：为了更好的保障账号的安全，您可以定期刷新 Token。当 Token 不慎泄漏时，您需要调用该接口立即刷新 Token。
## 接口请求地址

- 请求方法：POST
- URL：https://roomkit.yunxinapi.com/apps/v1/refreshToken
- Content-Type：application/json


## 请求参数

- POST 请求中 Header 的设置请参考调用方式中的请求结构描述。
- POST 请求中 Body 的设置如下：

| 参数名称    | 类型   | 是否必选 | 示例 | 描述 |
|-------------|--------|----------|------|--------------|
|userUuid|String| 必选     | user01 |    用户账号，必须保证唯一性。<br>由小写英文、数字、下划线(_)、@、英文句号（.）和短横线（-）组成，最大32个字符。|
|deviceId|String     | 可选     |  7fc26ed***e6b724765  | 终端设备ID，用户自定义。<br> 由英文、数字、下划线（_）和短横线（-）组成，最大长度64个字符。           |
     

## 返回结果
| 参数名称    | 类型   |  示例 | 描述 |
|-------------|--------|-------|--------------|
|code|int|0|状态码，0表示成功，具体请参见错误码。|
|msg|String|Success|业务结果描述，**Success**表示成功。|
|ts|Long|1648021056815|NERoom 服务器处理该请求的完成时间。<br>该时间为 Unix 时间戳，即从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。|
|requestId|String|7c4b6d9c3e9d42*****cc6e3a4d995|请求的唯一标识。|
|cost|String|48ms|处理该请求所消耗的时间。|
|data|Object| - |token的结果。|  
| data.accessToken | String |  0ZNLD4***251D1 |  获取Token的参数返回结果。            |


## 示例
### 请求示例

```java
{
	"userUuid":"test1",
	"deviceId":"7fc26ed***e6b724765"
}
```

### 返回示例

```java
{
    "code": 0,
    "msg": "Success",
    "ts": 1648038869677,
    "cost": "16ms",
    "requestId": "7c23f617319***515551b8296eed1",
    "data": {
        "accessToken": "0ZNLD4***2N251D1"
    }
}
```


