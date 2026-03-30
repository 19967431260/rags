调用该接口激活智能设备授权码（License）。License 是使用网易云信音视频通话 2.0 智能硬件 RTC 功能的必要凭证。

## 请求信息

<style>
table th:first-of-type {
    width: 22%;
}
</style>

### 请求 URI

```
POST https://nrtc-plugins.yunxinapi.com/v2/license/activate
```

- `nrtc-plugins.yunxinapi.com` 是网易云信 RTC 智能体服务的 API 域名。
- **Content-Type**：application/json; charset=utf-8

### 请求头参数

请求 Header 的参数说明请参考 [请求结构](https://doc.yunxin.163.com/ai-hardware/server-apis/DYwNTk5MzM?platform=server#Header)。

### 请求体参数

| 参数名称 | 类型 | 是否必选 | 示例 | 说明 |
| ---- | --- | ---- | --- | --- |
| licenseKey | String | 是 | netease_yunxin_1234 | 授权码名称，全局唯一，只能为数字、英文字母、下划线（`_`）组成，最高支持 256 个字符。用于设备激活和绑定智能体平台鉴权的 License。 |

### 请求体示例

```JSON
{
  "licenseKey": "netease_yunxin_1234"
}
```

## 响应信息

### 响应参数

| 参数名称 | 类型 | 说明 | 是否必返回 |
| ---- | --- | --- | ---- |
| code | Integer | 响应码，200 表示成功。 | 是 |
| message | String | 响应信息。 | 是 |
| requestId | String | 请求唯一标识。 | 是 |
| data | Object | 响应数据。 | 是 |
    license | String | 将 License 原始信息 Base64 编码后的结果。 | 否 |
    licenseKey | String | License 名称。 | 否 |
    expireDate | Long | License 到期时间，UTC+8 的 Unix 时间戳，单位秒。 | 否 |
    expireDateFormat | String | License 到期时间，格式为 RFC3339，单位为秒。 | 否 |
    ttl | Long | 有效期剩余时间，单位秒。 | 否 |

### 响应示例

```JSON
{
  "code": 200,
  "message": "success",
  "requestId": "ai56f35572d3174c45b2ce383297e1847a",
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
| 4007 | License 已激活 | 请重新激活有效的 License。 |
| 4008 | License 未授权 | 请重新激活有效的 License。 |