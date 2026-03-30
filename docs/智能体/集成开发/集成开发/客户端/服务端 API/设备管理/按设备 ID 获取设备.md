<!--keywords: RTC, 设备管理, 按设备 ID 获取设备, 设备查询, 音视频通话-->

按设备 ID 获取设备信息。

## 功能说明

根据设备 ID 获取指定设备的详细信息，包括设备归属用户、关联代理等信息。

<style>
table th:first-of-type {
    width: 20%;
}
</style>

## 请求信息

### 请求 URI

```
GET https://rtc-agent.yunxinapi.com/v1/device/getDevice
```

### 请求头参数

请求 Header 的参数说明请参考 [请求结构](https://doc.yunxin.163.com/ai-hardware/server-apis/DYwNTk5MzM?platform=server#Header)。

### 请求查询参数

| 参数名称 | 类型 | 是否必选 | 示例 | 说明 |
| :---- | :--- | :---- | :--- | :--- |
| deviceId | String | 是 | device1 | 设备 ID |

## 响应信息

### 响应参数

| 参数名称 | 类型 | 说明 | 是否必返回 |
| :---- | :--- | :--- | :--- |
| code | Integer | 状态码，200 表示请求成功 | 是 |
| message | String | 提示信息。请求失败时返回错误信息，请求成功时返回 "success"。 | 是 |
| requestId | String | 请求的唯一标识 ID | 是 |
| data | Object | 响应数据 | 是 |
    deviceId | String | 设备 ID | 是 |
    userId | String | 用户 ID | 是 |
    agentId | String | Agent ID | 是 |
    agentName | String | Agent 名称 | 是 |
    createdAt | Long | 创建时间戳，单位毫秒 | 是 |
    updatedAt | Long | 更新时间戳，单位毫秒 | 是 |
    customProperties | Array | 设备的自定义属性，用于在 MCP 调用中传递设备信息 | 否 |
      key | String | 自定义属性的名称 | 否 |
      value | String | 自定义属性的值 | 否 |
| success | Boolean | 操作是否成功 | 是 |

### 响应体示例

```JSON
{
    "code": 200,
    "message": "操作成功",
    "requestId": "ai56f35572d3174c45b2ce383297e1847a",
    "data": {
        "deviceId": "device1",
        "userId": "user1",
        "agentId": "99b6176cf",
        "agentName": "设备名称",
        "createdAt": 1751107896000,
        "updatedAt": 1751107896000,
        "customProperties": [
            {
            "key": "deviceType",
            "value": "smartSpeaker"
            }]
    },
    "success": true
}
```

<!-- ### 错误码

本文仅列举部分业务接口错误码，完整列表请参考 [错误码](https://doc.yunxin.163.com/ai-hardware/server-apis/DY5MDEzOTQ?platform=server)。

| 错误码 | 错误信息 | 说明 | 处理建议 |
| :---- | :---- | :--- | :---- |
| 40001 | 参数错误 | 请求参数不合法 | 检查请求参数格式和内容 |
| 40004 | 设备不存在 | 指定的设备 ID 不存在 | 确认设备 ID 是否正确 |
| 50001 | 系统内部错误 | 服务器内部异常 | 稍后重试或欢迎 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师 | -->