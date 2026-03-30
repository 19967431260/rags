<!--keywords: RTC,音视频通话,声纹,声纹识别,声纹添加,URL 音频,声纹向量,语音识别-->

从外部 URL 添加声纹信息，支持通过音频 URL 创建用户声纹数据，自动提取音频特征生成声纹向量。

::: note notice
- 目前只支持 wav 格式的音频文件。
- 建议使用 3-15 秒的音频，文件最大为 1MB。
- 音频质量会影响声纹识别准确率。
:::

## 请求信息

<style>
table th:first-of-type {
    width: 20%;
}
</style>

### 请求 URI

```
POST https://rtc-agent.yunxinapi.com/v1/voice_prints/add_from_url
```

### 请求头参数

请求 Header 的参数说明请参考 [请求结构](https://doc.yunxin.163.com/ai-hardware/server-apis/DYwNTk5MzM?platform=server#Header)。

### 请求体参数

 参数名称 | 类型 | 是否必选 | 示例 | 说明 |
 :--- | :--- | :--- | :--- | :--- |
 userId | String | 是 | user01 | 用户唯一标识 |
 name | String | 是 | jack | 声纹名称，用于标识该声纹 |
 url | String | 是 | https://example.com/example.wav | 音频文件 URL，仅支持 wav 格式，建议 3-15 秒，最大 1MB |
 subAccountUid | String | 否 | subAccountUid | 子用户 ID，在操作子用户时候必填。最大长度 32 字节，只允许字母、数字以及 "_@.-" |

### 请求体示例

```JSON
{
    "userId": "user01",
    "name": "jack",
    "description": "this is jack",
    "url": "https://example.com/example.wav"
}
```

## 响应信息

### 响应参数

 参数名称 | 类型 | 说明 | 是否必返回 |
 :--- | :--- | :--- | :--- |
 code | Integer | 状态码，200 表示请求成功 | 是 |
 message | String | 提示信息，请求成功时返回 "success"，失败时返回错误信息 | 是 |
 data | Object | 返回的数据对象，请求失败则返回空对象 | 是 |
   userId | String | 用户唯一标识 | 是 |
   name | String | 声纹名称 | 是 |
   description | String | 声纹描述信息 | 是 |
   embedding | Array | 声纹特征向量数组 | 是 |
   voicePrintId | String | 声纹唯一标识，用于后续声纹识别 | 是 |

### 响应体示例

```JSON
{
    "code": 200,
    "message": "success",
    "data": {
        "userId": "user01",
        "name": "jack",
        "description": "this is jack",
        "embedding": [0.0067223333333, -0.23333344433, 0.15678901234],
        "voicePrintId": "99IOEqmdsa"
    }
}
```
<!--

### 错误码

本文仅列举部分业务接口错误码，完整列表请参考 [错误码](https://doc.yunxin.163.com/ai-hardware/server-apis/DY5MDEzOTQ?platform=server)。

 错误码 | 错误信息 | 说明 | 处理建议 |
 :--- | :--- | :--- | :--- |
 400 | Invalid audio format | 音频格式不支持 | 请使用 wav 格式的音频文件 |
 400 | Audio file too large | 音频文件过大 | 请确保音频文件小于 1MB |
 400 | Audio duration invalid | 音频时长不符合要求 | 请使用 3-15 秒的音频文件 |
 404 | Audio URL not accessible | 无法访问音频 URL | 请检查 URL 是否有效且可访问 |
 500 | Voice print extraction failed | 声纹提取失败 | 请检查音频质量或重试 | -->