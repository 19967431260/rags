网易云信即时通讯 SDK（NetEase IM SDK，以下简称 NIM SDK）提供 AI 数字人。数字人既可以是虚拟的 AI 对话伙伴、高效的协同工作助手、也可定制贴合业务所需更高安全性的本地大模型。

本文介绍 AI 数字人相关的 API。更多详情，请参考《集成开发》 [AI 数字人](https://doc.yunxin.163.com/messaging2/guide/zQ1MDEwNzA?platform=client)。

## API 概览

### AI 数字人监听

API | 说明 | 起始版本
---- | ---- | ----
[listen](#listen) | 注册 AI 数字人相关监听器 | v10.3.0 |
[cancel](#cancel) | 取消注册 AI 数字人相关监听器 | v10.3.0 |

### AI 数字人操作

API | 说明 | 起始版本
---- | ---- | ----
[getAIUserList](#getAIUserList) | 根据用户账号 ID 列表获取 AI 数字| v10.3.0
[proxyAIModelCall](#proxyAIModelCall ) | AI 数字人向 LLM 发起查询请求 | v10.3.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendMessage) | AI 数字人发送消息 | v10.3.0
[stopAIModelStreamCall](#stopAIModelStreamCall) | 停止 AI 流式输出请求。 | v10.8.0

## 接口类

`AiService` 类提供 AI 数字人相关接口，包括查询数字人、LLM 模型请求、添加 AI 数字人监听、移除 AI 数字人监听。

## <span id="listen">listen</span>

**接口描述**

注册添加 AI 数字人相关监听。

注册成功后，当聊天会话中添加了 AI 数字人后，SDK 会返回对应的回调。

::: note note
- 建议在初始化后调用该接口。
- 全局只需注册一次。
- 该方法为同步。
:::

**参数说明**

```dart
Stream<NIMAIModelCallResult> get onProxyAIModelCall =>
    _platform.onProxyAIModelCall;
Stream<NIMAIModelStreamCallResult> get onProxyAIModelStreamCall;
    _platform.onProxyAIModelStreamCall;
```

**回调事件**

- `onProxyAIModelCall`：AI 透传接口的响应的回调。
- `onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调。

**示例代码**

```dart
subsriptions.add(NimCore.instance.aiService.onProxyAIModelCall.listen((e) {
      // do something
    }));
subsriptions.add(NimCore.instance.aiService.onProxyAIModelStreamCall.listen((e) {
      // do something
    }));
```

## <span id="cancel">cancel</span>

**接口描述**

取消注册 AI 数字人相关监听。

**示例代码**

```dart
subsriptions.forEach((subsription) {
      subsription.cancel();
    });
```

## <span id="getAIUserList">getAIUserList</span>

**接口描述**

批量查询 AI 数字人列表。返回全量的开发者账号下的相关的数字人用户。

**参数说明**

```dart
Future<NIMResult<List<NIMAIUser>>> getAIUserList() =>
    _platform.getAIUserList();
```

**示例代码**

```dart
await NimCore.instance.aiService.getAIUserList();
```

**返回值**

NIMResult\<List\<NIMAIUser>>：查询到的 AI 数字人列表

**相关回调**

无

## <span id="proxyAIModelCall">proxyAIModelCall</span>

**接口描述**

向 LLM（Large Language Models）发起模型调用请求。数字人发送消息调用 [`sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendMessage)。

```JSON
{ "msg": "xxxx", "type": 0 }
```

- 若选择正常输出方式，请求发送成功后，SDK 会触发 AI 透传接口的响应的回调 `onProxyAIModelCall`。
- 若选择 **流式输出** 方式，请求发送成功后，SDK 会触发 AI 透传接口的流式响应的回调 `onProxyAIModelStreamCall`。

::: note note
- 发送前请确保 AI 数字人已被添加。详情请参考 [开通和添加 AI 数字人](https://doc.yunxin.163.com/console/concept/TYxMDEzNDg?platform=console)。
- 本接口为异步接口。
:::

**参数说明**

```dart
Future<NIMResult<void>> proxyAIModelCall( NIMProxyAIModelCallParams params ) =>
    _platform.proxyAIModelCall(params);
```

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `params` | [`NIMProxyAIModelCallParams`](https://doc.yunxin.163.com/messaging2/client-apis/zExMjk2NzY?platform=client#NIMProxyAIModelCallParams) | 是 | AI 数字人更新参数，包括输出方式、用户昵称、头像、签名、邮箱、性别、生日、手机号以及扩展信息。 |

**示例代码**

```dart
await NimCore.instance.aiService.proxyAIModelCall(params);
```

**返回值**

NIMResult\<void>

**相关回调**

- `onProxyAIModelCall`：AI 透传接口的响应的回调 
- `onProxyAIModelStreamCall`：AI 透传接口的流式响应的回调

## <span id="stopAIModelStreamCall">stopAIModelStreamCall</span>

**接口描述**

停止 AI 流式输出请求。

::: note note
本接口为异步接口。
:::

**参数说明**

```dart
Future<NIMResult<void>> stopAIModelStreamCall( NIMAIModelStreamCallStopParams params )
```

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `params` | [`NIMAIModelStreamCallStopParams`](https://doc.yunxin.163.com/messaging2/client-apis/zExMjk2NzY?platform=client#NIMAIModelStreamCallStopParams) | 是 | 停止流式输出配置参数，包括停止输出的 AI 数字人账号 ID。 |

**示例代码**

```Dart
await NimCore.instance.aiService.stopAIModelStreamCall(params);
```

**返回值**

NIMResult\<void>

**相关回调**

无