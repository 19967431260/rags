本文介绍如何通过 WebSocket 协议接入网易云信对话式 AI 服务，实现设备与云端服务的实时通信。通过 WebSocket 接入，您可以快速为智能硬件设备添加语音交互能力，无需深度集成嵌入式 SDK。

## 前提条件

在开始 WebSocket 接入之前，请确保您已经完成了 [准备工作](https://doc.yunxin.163.com/ai-hardware/guide/zIzNTI4MDQ?platform=client)，包括创建应用、获取 App Key 以及配置智能体。

<style>
table th:first-of-type {width: 35%;}
</style>

## 技术原理

WebSocket 是一种全双工通信协议，基于 TCP 连接实现客户端与服务器之间的实时双向数据传输。与传统 HTTP 请求-响应模式不同，WebSocket 连接一旦建立，客户端和服务器都可以主动发送数据，适合对话式 AI 的交互场景。相比较 [嵌入式 SDK 接入方式](https://doc.yunxin.163.com/nertc/server-apis/jUyMDgyNTQ?platform=client)，WebSocket 接入具备以下特性，更适合轻量级语音交互设备、快速原型开发等核心 AI 对话功能场景。

- **持久连接**：避免频繁的连接建立和断开开销。
- **低延迟传输**：消息推送延迟通常在毫秒级别。
- **帧分离传输**：支持 Text Frame 文本帧（控制信令和事件消息）和 Binary Frame 二进制帧（音频流）同时传输，控制帧支持连接管理（Close、Ping、Pong 等）。
- **协议轻量化**：相比 HTTP 具有更小的协议开销。

## 接入方式

<a id="address"></a>

### 请求地址

WebSocket 接入的请求地址格式如下：

```
wss://mps.yunxinvcloud.com/?device_id={device_id}
```

其中 `device_id` 为在 [网易云信智能体管理平台](https://doc.yunxin.163.com/ai-hardware/guide/TU3MjE3NjE?platform=client) 中绑定的设备标识符，用于唯一标识您的硬件设备。

### 请求头

以 Python 为例，WebSocket 接入的请求头格式如下：

```Python
# 构建请求头
websocket_headers = {
    "yunxin-license": "license",
    "app-key": "your-netease-yunxin-appkey",
    "token": "your--netease-yunxin-token"
}
```

### 设备授权

设备授权通过为设备绑定授权码（`license`）实现：

<!-- 
根据是否 [接入网易云信嵌入式 SDK](https://doc.yunxin.163.com/ai-hardware/guide/jUyMDgyNTQ?platform=client) 的集成需求，针对设备 ID 与 License 绑定方案，您可以选择以下两种方案之一：

### 不接入嵌入式 SDK

该方案适用于只需要 WebSocket 接入能力、不需要使用嵌入式 SDK 完整功能的场景： -->

<img alt="未接入 SDK 方案" src="https://yx-web-nosdn.netease.im/common/c93e02202a666804ac2655b208734e97/image.png" style="width:65%;border: 1px solid #BFBFBF;border-radius:0px;">

**授权步骤**：

1. 客户业务服务器生成全局唯一的 `device_id`。
2. 在 [网易云信智能体管理平台](https://doc.yunxin.163.com/ai-hardware/guide/TU3MjE3NjE?platform=client) 中绑定 `device_id` 与 `agent-id`、`user-id` 的映射关系。
3. 在网易云信智能体管理平台中激活设备，并 [获取对应的授权码（`license`）](https://doc.yunxin.163.com/nertc/server-apis/zU3NDcxMTc?platform=server)。
4. 设备端接入：
    - 在接入 WebSocket [请求地址](#address) 时，在 URI 中传入 `device_id`。
    - 在请求头中传入 `yunxin-license`（客户业务服务器返回的 `license`）。

### 身份鉴权

为保证通信安全，WebSocket 连接需要根据应用密钥鉴权（`app-key`）和设备身份认证（`token`）：

<img alt="认证流程" src="https://yx-web-nosdn.netease.im/common/e668c42fe26a3be6636886c1a509f942/image.png" style="width:65%;border: 1px solid #BFBFBF;border-radius:0px;">

**认证流程**：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 申请 `appkey`，获取鉴权密钥 `appsecret`。
2. 客户业务服务器安全存储 `appsecret`，参考下文示例生成 [动态 Token](#generateToken)。
3. 客户设备端从业务服务器获取动态 Token。
4. 在 WebSocket 连接的请求头中指定 `app-key` 和 `token` 进行动态身份验证。

## 协议规范

本章节介绍 WebSocket 连接的通信协议规范，包括会话初始化、音频流传输、交互控制等。

### 会话初始化

WebSocket 连接的会话初始化遵循以下规范：

:::::: div linked-codes
::: code 客户端 → 服务端

**发送开始信令**

```JSON
{
  "action": "start",
  "data": {
    "input_audio": {
      "format": "pcm",
      "sample_rate": 24000,
      "channels": 1,
      "encoding": "raw"
    },
    "output_audio": {
      "format": "pcm",
      "sample_rate": 24000,
      "channels": 1,
      "encoding": "raw"
    }
  }
}
```

**`data` 参数说明**：

| 参数名 | 参数说明 
| ---- | ---- |
| `format` | 音频格式，当前支持 PCM。 |
| `sample_rate` | 采样率，支持常见采样率（8kHz - 48kHz）。 |
| `channels` | 声道数，当前支持单声道。 |
| `encoding` | 编码方式，取值支持 `raw`，`raw` 表示原始 PCM 数据<!-- ，`base64` 表示 Base64 编码 -->。 |

请根据实际支持的采样率范围选择合适的表述方式。

:::
::: code 服务端 → 客户端

**认证成功响应**

```JSON
{
  "action": "server_ready",
  "data": {
    "code": 0,
    "msg": "OK",
    "connection_id": "c70cde776a074170bb5d270cfd8691f"
  }
}
```

**`data` 参数说明**：

| 参数名 | 参数说明 
| ---- | ---- |
| `code` | 状态码，0 表示成功，非 0 表示错误。 |
| `msg` | 状态描述信息。 |
| `connection_id` | 连接唯一标识符。 |

:::
::::::

### 音频流传输

WebSocket 连接的音频流传输遵循以下规范：

:::::: div linked-codes
::: code 客户端 → 服务端

**上传音频流**

客户端通过二进制帧持续发送音频数据，格式须符合开始信令中 `input_audio` 的规范。

:::
::: code 服务端 → 客户端

**下载音频流**

服务端通过二进制帧发送合成的音频数据，格式符合开始信令中 `output_audio` 的规范。

:::
::::::

### 交互控制

WebSocket 连接的交互控制遵循以下规范：

:::::: div linked-codes
::: code 客户端 → 服务端

**手动打断**

```JSON
{
  "action": "manual_interrupt",
  "data": {
    "id": "c70cde77"
  }
}
```

**手动提交对话内容**

```JSON
{
  "action": "manual_message",
  "data": {
    "id": "c70cde77",
    "role": "user",
    "text": "图中描绘的是什么景象?",
    "img_url": "https://yunxin.com/nos/test.jpeg",
    "img_fragment": 10,
    "img_fragment_seq": 1,
    "interrupt_mode": 1
  }
}
```

**`data` 参数说明**：

| 参数名 | 参数说明 
| ---- | ---- |
| `id` | 会话 ID。 |
| `role` | 角色类型。 |
    `user` | 用户消息，系统将生成语音回复，支持文本和图片输入。 |
    `assistant` | 助手消息，系统将进行文本转语音并加入对话上下文。 |
| `img_url` | 图片 URL 格式<!-- 使用限制 可参考 <https://help.aliyun.com/zh/model-studio/vision?spm=a2c4g.11186623.help-menu-2400256.d_0_2_0.5a0b453aCzGL7m#da33480805fjh> -->。 |\
| |  - **网络图片**：`https://yunxin.com/nos/test.jpeg` |\
| |  - **本地图片**：`data:image/{format};base64,{base64_image}`，例如 `data:image/jpeg;base64,{base64_image}` |
| `img_fragment` | 用于处理大型本地图片的分片传输，图片分片总数，默认为 1。 |
| `img_fragment_seq` | 用于处理大型本地图片的分片传输，当前分片序号，从 1 开始，默认为 1。 |
| `interrupt_mode` | 消息处理优先级。 |\
| |  - `1` | 高优先级，立即打断当前交互进行处理。 |\
| |  - `2` | 中优先级，等待当前交互结束后处理。 |\
| |  - `3` | 低优先级，如正在交互则直接丢弃。 |

:::
::::::

### Function Call

WebSocket 连接的 Function Call 遵循以下规范：

:::::: div linked-codes
::: code 客户端 → 服务端

**设备状态同步**

```JSON
{
  "action": "iot_status",
  "data": {
    "iot_status": [
      {
        "name": "SetVolume",
        "status": {
          "volume": 50
        }
      }
    ]
  }
}
```

**工具执行结果**

```JSON
{
  "action": "tool_outputs",
  "data": {
    "tool_outputs": [
      {
        "tool_call_id": "call_123",
        "tool_call_name": "SetVolume",
        "output": {
          "volume": 50
        }
      }
    ]
  }
}
```

:::
::: code 服务端 → 客户端

**意图识别结果**

```JSON
{
  "action": "tool_calls",
  "data": {
    "request": "声音设置为 80%",
    "tool_calls": [
      {
        "id": "call_123",
        "type": "function",
        "function": {
          "name": "SetVolume",
          "arguments": "{\"volume\": 80}"
        }
      }
    ]
  }
}
```

:::
::::::

**工具配置**

在 [网易云信智能体管理平台](https://doc.yunxin.163.com/ai-hardware/guide/TU3MjE3NjE?platform=client) 配置 tools 时，建议添加 `response_success` 参数用于操作反馈：

```JSON
{
  "parameters": {
    "type": "object",
    "properties": {
      "response_success": {
        "description": "操作成功时的友好回复，关于该设备的操作结果，设备名称尽量使用 description 中的名称",
        "type": "string"
      }
    },
    "required": ["response_success"]
  }
}
```

## 事件通知

WebSocket 连接的服务端事件通知遵循以下规范：

### **语音转文本结果**

```JSON
{
  "action": "asr_text",
  "data": {
    "type": 0,
    "content": "Have a good day"
  }
}
```

### **大模型回复结果**

```JSON
{
  "action": "llm_text",
  "data": {
    "type": 0, // 结果类型，0 表示最终结果，1 表示中间结果
    "content": "Have a good day"
  }
}
```

### **文本转语音状态**

```JSON
// TTS 开始
{
  "action": "tts_start",
  "data": {}
}

// TTS 结束
{
  "action": "tts_stop",
  "data": {}
}
```

### **错误响应**

```JSON
{
  "action": "error",
  "data": {
    "code": 400,
    "msg": "param error"
  }
}
```

<a id="generateToken"></a>

## 生成 Token

您可以参考下文示例生成 Token，用于 WebSocket 连接 Token 验证：

### 算法实现

以下示例代码中，使用 Java 语言实现 Token 生成算法。

```Java
public class TokenGenerator {
    private String appSecret;

    public String getToken(int ttlSec) throws Exception {
        long curTimeMs = System.currentTimeMillis();
        return getTokenWithCurrentTime(ttlSec, curTimeMs);
    }

    public String getTokenWithCurrentTime(int ttlSec, long curTimeMs) throws Exception {
        DynamicToken tokenModel = new DynamicToken();

        // 生成 signature：将 curTime、ttl、appsecret 拼接后进行 SHA1 编码
        tokenModel.signature = sha1(String.format("%d%d%s", curTimeMs, ttlSec, appSecret));
        tokenModel.curTime = curTimeMs; // 当前时间戳（毫秒）
        tokenModel.ttl = ttlSec;         // Token 有效期（秒）

        ObjectMapper objectMapper = new ObjectMapper();
        String signature = objectMapper.writeValueAsString(tokenModel);

        // 对 JSON 字符串进行 Base64 编码
        return Base64.getEncoder().encodeToString(signature.getBytes(StandardCharsets.UTF_8));
    }

    private String sha1(String input) throws NoSuchAlgorithmException {
        MessageDigest mDigest = MessageDigest.getInstance("SHA-1");
        byte[] result = mDigest.digest(input.getBytes(StandardCharsets.UTF_8));
        StringBuilder sb = new StringBuilder();
        for (byte b : result) {
            sb.append(String.format("%02x", b));
        }
        return sb.toString();
    }

    public static class DynamicToken {
        public String signature;
        public long curTime;
        public int ttl;
    }
}
```

### 验证 Token

网易云信服务器接收到 Token 后将进行以下验证：

1. **时效性验证**：当前时间不得超过 `curTime + ttl`。
2. **签名验证**：使用 Token 中的 `curTime`、`ttl` 以及服务器存储的 `appsecret` 重新计算签名，与 Token 中的签名进行比对。

任一验证失败都将导致鉴权失败。

## 下一步

- 了解如何在设备端优化音频处理以提高识别准确率。
- 探索如何结合 Function Call 机制实现设备控制功能。