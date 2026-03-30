
<!-- keywords: 即时通讯,IM,登出, 注销登录, 登出IM -->

本文介绍如何实现注销 IM 登录。


## 功能介绍

一般情况下，如果您的应用生命周期跟 NIM SDK 生命周期一致，用户在退出应用前可以不登出，直接退出即可。

但某些特殊场景，例如用户仅在进入特定界面后才调用 NIM SDK 的能力，退出界面后不再调用，此时需要调用 NIM SDK 的登出接口注销 IM 登录。 登出后，用户将不再接收 IM 的消息。 

## 实现方法

用户在登出应用/注销自己的账号时需要调用<a href="https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/logout.html">`logout`</a>方法登出 IM ，该方法没有回调。

```java
class AuthService {
  Future<NIMResult<void>> logout();
}
```

:::note notice
建议不要频繁调用登录、登出方法，调用 `logout` 方法后，如需再调用 `login`  方法，其间隔至少要大于 3s。
:::

示例代码如下：

```dart
    NimCore.instance.authService
    .logout()
    .then(
      (result) {
        if (result.isSuccess) {
          /// 成功
        } else {
          /// 失败
        }
      }
    );
```