

为了提高消息送达率，云信引入手机系统厂商推送。手机系统级别的厂商推送（如小米、华为、vivo、OPPO、魅族等）的优势在于其拥有稳定的系统级长连接，可以做到随时接收推送。

## 功能概述

NIM SDK 支持离线推送消息功能。

当用户清理掉应用进程（被冻结、主动关闭）、网络不稳定等导致客户端 SDK 无法与云信服务器保持正常连接时，将使用手机厂商系统级推送来告知用户有消息需要接收。

您可以通过集成各手机厂商推送 SDK，与 NIM SDK 搭配使用，实现离线推送功能。


## 技术原理


云信 IM 实现离线推送的技术原理如下：


<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/76ff7bea6bf4bfe6bdbab0d4e101c460/Android离线推送技术原理.png" />






## 前提条件

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/docs/TU3NDk1OTI?platform=flutter#4-注册-im-账号)，获取 accid 和 token。
- 开发环境满足如下要求：
    - Flutter-dart 2.17.0 及以上版本
    - Android Studio 3.5 及以上版本
    - App 要求 Android 5.0 API 19 及以上版本设备
    - 1.5.21以上版本的 `kotlin-gradle-plugin`

## 实现流程

### 步骤 1：集成第三方厂商离线推送服务

请参考具体厂商的推送集成文档，集成需要使用到的第三方厂商离线推送 SDK，接入各厂商的离线推送服务。

目前支持以下第三方推送厂商：

|第三方厂商|当前兼容版本|集成指南|
|:----|:----|:-----|
|小米| `MiPush_SDK_Client_6_0_1`|[集成小米推送](https://doc.yunxin.163.com/messaging/guide/zg2NDE4ODM?platform=android)
|华为| `com.huawei.hms:push: 6.12.0.300`|[集成华为推送](https://doc.yunxin.163.com/messaging/guide/jg2ODQxMjU?platform=android)
|荣耀| `com.hihonor.mcs:push:7.0.61.303`|[集成荣耀推送](https://doc.yunxin.163.com/messaging/guide/DMwMjc5MDM?platform=android)
|OPPO| `com.heytap.msp-push-3.5.1.aar`|[集成 OPPO 推送](https://doc.yunxin.163.com/messaging/guide/zI4ODc0MTE?platform=android)
|vivo|`vivo_pushsdk_v4.0.0.0_500`|[集成 vivo 推送](https://doc.yunxin.163.com/messaging/guide/zY0MjM0OTc?platform=android)
|魅族|`com.meizu.flyme.internet:push-internal:4.3.0`|[集成魅族推送](https://doc.yunxin.163.com/messaging/guide/DcwMjI1MTI?platform=android)
|谷歌 FCM| `firebase-bom:32.3.1`<br/>具体版本：`firebase-messaging：23.0.0`，`firebase-analytics: 20.0.0`|[集成谷歌推送](https://doc.yunxin.163.com/messaging/guide/zY2Nzc4MjY?platform=android)

### 步骤 2：集成 NIM SDK


请参见[集成 NIM SDK](https://doc.yunxin.163.com/messaging/docs/Dg5NjI4MDg?platform=flutter) 完成 NIM Flutter SDK 的集成。


### 步骤 3：初始化 NIM SDK 

在[初始化 NIM SDK](https://doc.yunxin.163.com/messaging/docs/jk1MTg0NjM?platform=flutter) 时，完成厂商的推送证书配置，并选择推送渠道。

1. 需要将推送证书的信息配置到初始化参数 `NIMAndroidSDKOptions.mixPushConfig` 中。


    :::::: div custom-tabs
    ::: tab 小米
    ```
    final xmPushConfig = NIMMixPushConfig(  
      xmAppId: '小米AppId',
      xmAppKey: '小米AppKey',
      xmCertificateName: '小米证书',
    );
    // 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        // 其他初始化参数
        // ...
        mixPushConfig: xmPushConfig,
      ),
    );
    ```
    :::
    ::: tab 华为
    ```
    final hwPushConfig = NIMMixPushConfig(  
      hwAppId: '华为AppId',
      hwCertificateName: '华为证书',
    );
    // 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        // 其他初始化参数
        // ...
        mixPushConfig: hwPushConfig,
      ),
    );
    ```
    :::
    ::: tab 荣耀
    ```
    final xmPushConfig = NIMMixPushConfig(
      honorCertificateName: '荣耀证书'
    );
    // 初始化时指定推送配置
    NimCore.instance.initialize(
    NIMAndroidSDKOptions(
    appKey: appKey,
    // 其他初始化参数
    // ...
    mixPushConfig: xmPushConfig,
    ),
    );
    ```
    :::
    ::: tab vivo
    ```
    final vivoPushConfig = NIMMixPushConfig(
      vivoCertificateName: 'vivo证书',
    );
    /// 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        /// 其他初始化参数
        mixPushConfig: vivoPushConfig,
      ),
    );
    ```
    :::
    ::: tab OPPO
    ```
    final oppoPushConfig = NIMMixPushConfig(
      oppoAppId: 'oppoAppId',
      oppoAppKey: 'oppoAppKey',
      oppoAppSecret: 'oppoAppSecret',
      oppoCertificateName: 'oppo证书',
    );
    /// 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        /// 其他初始化参数
        mixPushConfig: oppoPushConfig,
      ),
    );
    ```
    :::
    ::: tab 魅族
    ```
    final mzPushConfig = NIMMixPushConfig(
      mzAppId: 'mzAppId',
      mzAppKey: 'mzAppKey',
      mzCertificateName: 'mz证书',
    );
    /// 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        /// 其他初始化参数
        mixPushConfig: mzPushConfig,
      ),
    );
    ```
    :::
    ::: tab 谷歌
    ```
    //传入云信控制台上配置的谷歌推送证书名,谷歌推送的  AppSecret 请在 AndroidManifest.xml 文件中配置
    final fcmPushConfig = NIMMixPushConfig(
      fcmCertificateName: 'fcm证书',
    );
    /// 初始化时指定推送配置
    NimCore.instance.initialize(
      NIMAndroidSDKOptions(
        appKey: appKey,
        /// 其他初始化参数
        mixPushConfig: fcmPushConfig,
      ),
    );
    ```
    :::
    ::::::

    :::note note
    推送证书名长度不超过 32 个字符，否则登录时会报错 500。
    :::


2. 选择推送渠道。

    - 如果[`NIMAndroidSDKOptions.mixPushConfig.autoSelectPushType`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NIMMixPushConfig/autoSelectPushType.html)为 false（默认），则 SDK 直接选择服务端推荐的推送渠道。

    - 如果配置`NIMAndroidSDKOptions.mixPushConfig.autoSelectPushType`为 true，则 SDK 根据实际的 token 的获取情况确定推送渠道，此时服务端推荐的推送渠道为最高优先级。需要确定推送渠道时，先进行本地支持性判断，然后将向所有可能支持的推送厂商申请 token，并在成功拿到的 token 中选择优先级更高的渠道。

    :::note note
    SDK 默认 Google FCM 推送的优先级最低，即如果同时接入了 FCM 和其他厂商推送，则会优先走其他厂商推送通道。但是如果您的应用用户主要分布在海外，在云信控制台已设置 **FCM 推送优先**（**控制台：应用详情 > 更多 > 证书管理**），那么同时接入 FCM 和其他厂商推送 SDK 的场景下，优先走 FCM 推送通道。
    :::

3. 在 `Application#onCreate` 中启用华为和 OPPO 的推送服务，即对华为、OPPO 推送服务进行初始化。其他厂商推送服务无需额外初始化，可忽略该步骤。

    :::::: div custom-tabs
    ::: tab 华为
    ```
    public class FlutterIMApplication extends Application {
        ...
        @Override
        public void onCreate() {
            ...
            if (NIMUtil.isMainProcess(this)) {
                ...
                // 在此处添加以下代码
                com.huawei.hms.support.common.ActivityMgr.INST.init(this);
                ...
            }
        }
    }
    ```
    :::
    ::: tab 荣耀
    ```
    public class NimApplication extends Application {
        ...
        @Override
        public void onCreate() {
            ...
            if (NIMUtil.isMainProcess(this)) {
                ...
                // 在此处添加以下代码
                HonorPushClient.getInstance().init(getApplicationContext(), true);
                ...
            }
        }
    }
    ```
    :::
    ::: tab OPPO
    ```
    public class FlutterIMApplication extends Application {
        ...
        @Override
        public void onCreate() {
            ...
            if (NIMUtil.isMainProcess(this)) {
                ...
                // 在此处添加以下代码
                com.heytap.msp.push.HeytapPushManager.init(this, true);
                ...
            }
        }
    }
    ```
    
    :::
    ::::::


若您正确集成第三方推送（已传相关推送 token 至云信服务器），SDK 日志会打印以下相应记录。其中`pushType`和`type`表示推送类型（5 小米、6 华为、7 魅族、8 谷歌FCM、9 vivo、10 OPPO、11 荣耀、0 不支持），`tokenName`表示推送证书名称，`token`表示推送 token。

```
[ui]mix_push: after login, mix push state=MixPushState{pushType=5, hasPushed=0, lastDeviceId=''}
[ui]mix_push: commit mix push token:type 5 tokenName PUSH_CER_NAME token y7ssE..................sLxnU
```


### 步骤 4：测试离线推送

**消息发送方：**

发送消息或自定义系统通知给接收方（离线），具体的收发流程可参见[消息收发](https://doc.yunxin.163.com/messaging/docs/zI0NTgwNDY?platform=flutter)和[自定义系统通知收发](https://doc.yunxin.163.com/messaging/docs/zIzNjg5OTI?platform=flutter#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%B3%BB%E7%BB%9F%E9%80%9A%E7%9F%A5)。

这里以发送文本消息为例，通过调用 sendMessage 实现。发送的消息默认需要推送，如需设置推送文案，推送角标，推送文案前缀等，请参见[配置消息的推送属性](https://doc.yunxin.163.com/messaging/docs/jA0MTg0NTU?platform=flutter)。


```
// 该帐号为示例
String account = 'testAccount';
// 以单聊类型为例
NIMSessionType sessionType = NIMSessionType.p2p;
String text = 'this is an example';
// 创建并且发送一个文本消息
Future<NIMResult<NIMMessage>> result = MessageBuilder.createTextMessage(
    sessionId: account, sessionType: sessionType, text: text)
    .then((value) => value.isSuccess
    ? NimCore.instance.messageService
        .sendMessage(message: value.data!, resend: false)
    : Future.value(value));
```


**消息接收方：**

接收方将会在登录后接收到离线推送。

:::note note
- 离线推送支持配置免打扰时间，具体请参见[设置推送全局免打扰]()。
- 离线推送支持配置多端推送策略，即支持推送至同一账号的多个客户端，具体请参见[设置多端推送策略]()。
:::


### （可选）步骤 5：关闭/开启离线推送服务

NIM SDK 的第三方推送服务功能默认开启，无需单独调用开启服务接口。若后续不想使用第三方推送服务，可调用 [`enablePushService`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/enablePushServiceAndroid.html) 方法进行关闭。

```
NimCore.instance.settingsService.enablePushService(false);
```


## 推送相关文档


- [推送问题排查](https://doc.yunxin.163.com/messaging/docs/DY4NzY5ODU?platform=android)

- 第三方厂商推送通道存在流控，具体请参见[厂商推送通道限制说明](https://doc.yunxin.163.com/messaging/docs/DY1MzgzOTk?platform=android)

- 若您想直接使用 SDK 中注册的 Channel 来作为第三方厂商（小米、OPPO）的申请 Channel，可参考[SDK 中的 Channel 信息](https://doc.yunxin.163.com/messaging/docs/DY4NzY5ODU?platform=android#SDK%E9%80%9A%E9%81%93Channel)

- [第三方推送厂商通道错误码参考](https://doc.yunxin.163.com/messaging/docs/DY4NzY5ODU?platform=android#%E5%8E%82%E5%95%86%E9%80%9A%E9%81%93%E9%94%99%E8%AF%AF%E7%A0%81%E6%96%87%E6%A1%A3)

- [推送 payload 配置](https://doc.yunxin.163.com/messaging/docs/DQyNjc5NjE?platform=server)

## 常见问题

Q：触发离线推送的条件是什么？

A：Android 切换到后台并且等 app 被系统回收时，或者用户主动关闭 app，才能触发推送条件。因此，若要测试 Android 推送问题，请登录后关闭 app，确保满足推送条件。

<br>

Q：哪些场景下不会触发推送？

A： IM 账号未登录/已登出/被踢出，不会触发推送。App 在前台，也不会触发推送。用户登录 IM 账号，并且未主动登出或者没有被踢出，可能触发推送。




