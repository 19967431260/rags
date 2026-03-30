<!-- keywords: 即时通讯,IM,登出, 注销登录, 登出IM -->

本文介绍如何实现注销 IM 登录。


## 功能介绍

一般情况下，如果您的应用生命周期跟 NIM SDK 生命周期一致，用户在退出应用前可以不登出，直接退出即可。

但某些特殊场景，例如用户仅在进入特定界面后才调用 NIM SDK 的能力，退出界面后不再调用，此时需要调用 NIM SDK 的登出接口注销 IM 登录。 登出后，用户将不再接收 IM 的消息。 

## 实现方法

用户在登出应用/注销自己的账号时需要调用[`logout`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#aaa048a03d2f8fce4c31b0f8a3945a09b)方法登出 IM ，该方法没有回调。



- 接口原型

```java
/**
 * 注销接口
 */
public void logout();
```

- 示例代码

```java
NIMClient.getService(AuthService.class).logout();
```


:::note notice
- 请不要在 Activity(Fragment) 的 `onDestroy` 调用`logout`方法。

- 建议不要频繁调用登录、登出方法，调用 `logout` 方法后，如需再调用 `login`  方法，其间隔至少要大于 3s。
:::


