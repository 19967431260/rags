

本文介绍如何实现注销 IM 登录。




## 功能介绍

一般情况下，如果您的应用生命周期跟 NIM SDK 生命周期一致，用户在退出应用前可以不登出，直接退出即可。

但某些特殊场景，例如用户仅在进入特定界面后才调用 NIM SDK 的能力，退出界面后不再调用，此时需要调用 NIM SDK 的登出接口注销 IM 登录。 登出后，用户将不再接收 IM 的消息。

## 实现方法

用户登出应用（注销自己的账号）时需要调用[`logout:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a60f99812a55cecb9069e748ed586513b)方法，该操作会同时通知云信服务端进行 APNs 推送的解绑操作，避免用户已登出但依然将消息推送到当前设备。


```objc
@protocol NIMLoginManager <NSObject>
- (void)logout:(nullable NIMLoginHandler)completion
@end
```

考虑到用户体验，登出的超时时间会比其他请求短一些。无论登出请求是否成功，上层应用在 UI 表现上都应该做出登出行为。如果登出失败，应用也需要跳转到登录界面。导致登出失败的原因是云信服务端解绑 APNs 推送信息失败，但此时本地信息是清理成功的。

示例:

```objc
[[[NIMSDK sharedSDK] loginManager] logout:^(NSError *error) {
    //jump to login page
}];
```