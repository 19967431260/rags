离线推送是指当用户清理掉应用进程（被冻结、主动关闭）、网络不稳定等导致客户端 SDK 无法与云信服务器保持正常连接时，使用手机厂商系统级推送，将主叫用户的呼叫邀请信息推送给被叫用户。本文介绍通过呼叫组件配置推送的属性，包括推送标题、推送文案等。

## 前提条件

已在 NIM SDK [实现离线推送](https://doc.yunxin.163.com/messaging2/guide/TMwNjM5NDI?platform=client)。

## 背景信息

呼叫组件不提供推送功能，只支持配置推送消息，离线推送能力由云信 NIM SDK 提供。

## 实现方法

呼叫组件在发起呼叫时，通过呼叫中的参数 `NECallParams` 的 `pushConfig` 参数，配置推送的属性。

示例代码如下：

```dart
NECallParams? params = NECallParams();
params.pushConfig = NECallPushConfig(
  pushTitle: "pushTitle",
  pushContent: "pushContent",
  pushPayload: "pushPayload",
  needPush: "needPush");
params.pushConfig
NECallKitUI.instance.call(
    "calledAccId", NECallType.audio, params: params);
```