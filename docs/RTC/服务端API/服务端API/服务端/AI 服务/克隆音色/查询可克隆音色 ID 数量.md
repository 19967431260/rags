<!--keywords: RTC 音视频通话,TTS 语音合成,音色克隆,声音克隆,语音技术-->

查询可克隆音色 ID 数量，获取当前可用于声音克隆的音色 ID 列表及对应的可克隆次数。若返回为空，表示无克隆音色 ID 可用，需要先行申请。

::: note notice
- 音色 ID 数量有限，建议及时查询可用数量。
- 每个音色 ID 有克隆次数限制，请合理规划使用。
:::

## 请求信息

<style>
table th:first-of-type {
    width: 20%;
}
</style>

### 请求 URI

```
GET https://rtc-ai.yunxinapi.com/v1/api/tts/voice-id-apply
```

### 请求头参数

请求 Header 的参数说明请参考 [请求结构](https://doc.yunxin.163.com/nertc/server-apis/TYyNjA3MzQ?platform=server#%E8%AF%B7%E6%B1%82%E5%A4%B4header)。

## 响应信息

### 响应参数

| 参数名称 | 类型 | 说明 | 是否必返回 |
| :--- | :--- | :--- | :--- |
| code | Number | 状态码，200 表示成功 | 是 |
| count | Number | 可用的音色 ID 数量统计 | 是 |

### 响应体示例

```JSON
{
    "code": 200,
    "count": 2
}
```

<!-- ### 错误码

本文仅列举部分业务接口错误码，完整列表请参考 [错误码](https://doc.yunxin.163.com/nertc/server-apis/TQ3Njc1Nzg?platform=server)。

| 错误码 | 错误信息 | 说明 | 处理建议 |
| :--- | :--- | :--- | :--- |
| 400 | Bad Request | 请求参数错误 | 检查请求参数格式和内容 |
| 401 | Unauthorized | 认证失败 | 检查 AppKey 和签名是否正确 |
| 403 | Forbidden | 权限不足 | 确认账号是否开通 TTS 服务 |
| 500 | Internal Server Error | 服务器内部错误 | 稍后重试或欢迎 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师 | -->
