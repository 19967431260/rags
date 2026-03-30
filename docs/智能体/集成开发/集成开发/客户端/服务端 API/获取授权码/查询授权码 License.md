调用该接口通过授权码名称（LicenseKey）查询智能设备对应的授权码（License），包括 License 内容、过期时间等详细信息。

## 请求信息

<style>
table th:first-of-type {
    width: 22%;
}
</style>

### 请求 URI

```
POST https://nrtc-plugins.yunxinapi.com/v2/license/query
```

- `nrtc-plugins.yunxinapi.com` 是网易云信 RTC 智能体服务的 API 域名。
- **Content-Type**：application/json; charset=utf-8

### 请求头参数

请求 Header 的参数说明请参考 [请求结构](https://doc.yunxin.163.com/ai-hardware/server-apis/DYwNTk5MzM?platform=server#Header)。

### 请求体参数

| 参数名称 | 类型 | 是否必选 | 示例 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| licenseKey | String | 是 | netease_yunxin_1234 | 授权码的名称，全局唯一，用于标识需要查询的 License。 |

### 请求体示例

```JSON
{
    "licenseKey": "netease_yunxin_1234"
}
```

## 响应信息

### 响应参数

| 参数名称 | 类型 | 说明 | 是否必返回 |
| ---- | ---- | ---- | ---- |
| code | Integer | 状态码，200 表示成功。 | 是 |
| message | String | 状态描述信息。 | 是 |
| requestId | String | 请求的唯一标识。 | 是 |
| data | Object | 响应数据。 | 是 |
    license | String | base64 编码后的 License 信息。 | 否 |
    licenseKey | String | License 名称。 | 否 |
    expireDate | Long | License 到期时间的 UTC+8 unix 时间戳，单位秒。 | 否 |
    expireDateFormat | String | License 到期时间，RFC3339 格式。 | 否 |
    ttl | Long | License 剩余有效时间，单位秒。 | 否 |

### 响应示例

```JSON
{
    "code": 200,
    "message": "success",
    "requestId": "nrtcplugins60be1938877143868db1aee6a2eaa4ab",
    "data": {
        "license": "eyJhbGdvcml0aG0iOiJkZWZhdWx0IiwiY3*****LVFNaZTBBPT0iLCJ2ZXJzaW9uIjoiMS4wIn0=",
        "licenseKey": "netease_yunxin_1234",
        "expireDate": 1785984225,
        "expireDateFormat": "2026-08-06T10:43:45+08:00",
        "ttl": 31535994
    }
}
```

## 错误码

本文仅列举部分业务接口错误码，完整列表请参考 [错误码](https://doc.yunxin.163.com/ai-hardware/server-apis/DY5MDEzOTQ?platform=server)。 <!-- IM V10 -->

| 错误码 | 说明 | 处理建议 |
| ---- | ---- | ---- |
| 200 | 查询成功 | - |
| 4000 | License 不存在 | 请检查设备 ID 是否正确，或申请新的 License。 |
| 4002 | License 已过期 | 请重新激活有效的 License。 |