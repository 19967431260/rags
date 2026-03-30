本文介绍如何修改NERoom 账号的昵称、头像和token。



::: note notice
请先 <a href="https://doc.yunxin.163.com/neroom/docs/DAwOTUxMzE?platform=server" target="_blank">创建 NERoom 账号</a>，再调用本接口。
:::


  

## 请求
### URI

```
PATCH https://{endpoint}/neroom/v3/users/:user_uuid
```
- {endpoint} 为 NERoom 接入地址的域名，默认为 `roomkit.yunxinapi.com`。如果您的应用主要服务于海外用户，请将域名设置为海外数据中心域名（`roomkit-sg.yunxinapi.com`）。
- Content-Type：application/json
### Header

请求 Header 的设置请参见 <a href="https://doc.yunxin.163.com/neroom/docs/TMyMDg2Mzg?platform=server" target="_blank">请求结构</a>。


### 路径参数

| 参数名称    | 类型   | 是否必选 | 示例 | 描述                                                 |
|-------------|--------|----------|------|--------------|
|   user_uuid      | String   | 是  |  user01 |用户账号|

### 请求体参数



| 参数名称    | 类型   | 是否必选 | 示例 | 描述 |
|-------------|--------|----------|------|--------------|
|user_name|String     | 可选   |  用户01  | 用户昵称。最大长度64个字符。不传或者传空字符串时不会修改。 |
|icon|String| 可选     | https://tupian.jpg | 用户头像的图片 URL。URL 地址的最大长度为 1000 个字符。不传或者传空字符串时不会修改。 |
|im_token|String     | 可选     | 0ZNLD4***2N251D1 | IM 的 Token。最大长度64个字符，不传或者传空字符串时不会修改。|
|user_token|String| 可选   | qwer**** | 用户的Token。最大长度64个字符，不传或者传空字符串时不会修改。 |

### 请求示例
```
PATCH https://roomkit.yunxinapi.com/neroom/v3/users/user01
```

```json
{
    "user_token":"0ZNLD4***2N251D1",
    "user_name":"我是昵称1",
    "im_token":"0ZNLD4***2N251D1",
    "icon":"https://tupian.jpg"
}
```

## 响应
### 响应参数
| 参数名称    | 类型   |  示例 | 描述 |
|-------------|--------|-------|--------------|
|code|int|0|状态码，0表示成功，具体请参见错误码。|
|msg|String|Operation succeeded.|业务结果描述|
|ts|Long|1648021056815|NERoom 服务器处理该请求的完成时间。<br>该时间为 Unix 时间戳，即从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数。|
|request_id|String|7c4b***e3a4d995|请求的唯一标识。|
|cost|String|48ms|处理该请求所消耗的时间。|
|data| | | 无|




### 响应体示例

```json
{
    "code": 0,
    "msg": "Operation succeeded.",
    "ts": 1657079917019,
    "cost": "146ms",
    "request_id": "prod_8e04a8ed7879***b6a30557279a1b",
    "data": null
}
```

### 错误码


错误码 | 错误信息 | 说明 | 处理建议
---- | -------------- | ---------|---------|
0 | Success | 请求成功| 无需处理
400|Invalid parameter.|参数错误	|检查接口传参|