离线推送是指当用户清理掉应用进程（被冻结、主动关闭）、网络不稳定等导致客户端 SDK 无法与云信服务器保持正常连接时，使用手机厂商系统级推送，将主叫用户的呼叫邀请信息推送给被叫用户。本文介绍通过呼叫组件配置推送的属性，包括推送标题、推送文案等。

## 前提条件

已在 NIM SDK [实现离线推送](https://doc.yunxin.163.com/messaging2/guide/TMwNjM5NDI?platform=client)。

## 背景信息

呼叫组件不提供推送功能，只支持配置推送消息，离线推送能力由云信 NIM SDK 提供。

## 实现方法

呼叫组件在发起呼叫时，通过呼叫中的参数 `NECallParams` 的 `pushConfig` 参数，配置推送的属性。

示例代码如下：

```dart
final pushConfig = NECallPushConfig(
  pushTitle: 'custom push title',      // 自定义推送标题
  pushContent: 'custom push content',   // 自定义推送内容
  pushPayload: '{"key": "value"}',      // 推送自定义字段（JSON 字符串）
  needBadge: true,                      // 是否计入未读计数，默认 true
  needPush: true,                       // 是否需要推送，默认 true
);

// 创建通话参数
final params = NECallParams();
params.pushConfig = pushConfig;

// 发起视频通话
final result = await NECallKitUI.instance.call(
  'remote accId',           // 对方账号ID
  NECallType.video,         // 通话类型：video（视频）或 audio（音频）
  params,                   // 通话参数，包含推送配置
);

if (result.code == 0) {
  print('呼叫成功');
} else {
  print('呼叫失败: ${result.message}');
}
```