<!-- keywords: 离线推送,APNs,p12,推送证书,APPID -->
<!-- description: 网易云信IM即时通讯离线推送功能,离线推送客户端开发指南-->


NIM SDK 支持 APNs 离线推送功能。

当您的程序在后台被挂起、被系统/用户杀死，或网络异常，NIM SDK 与云信服务端的长连接会因为超时而断开，此时云信服务端会通过 APNs 通道为目标用户发送离线推送的消息。

如果您需要通过云信向 App 发送离线推送，需要先向云信提供 APNs 信息（App ID、证书等），授权云信服务端与 APNs 通信，从而实现离线推送功能。



## 技术原理

云信 IM 实现离线推送的技术原理如下：


<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/f10485b0345c5ca0ff322386b7571a9a/APNs离线推送技术原理.png" />




## 前提条件

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/docs/TU3NDk1OTI?platform=flutter#4-注册-im-账号)，获取 accid 和 token。

- 开发环境满足如下要求：
    - Flutter-dart 2.17.0 及以上版本
    - Xcode 11.0 及以上版本
    - iOS 11.0 及以上版本设备
    - 项目已设置有效的开发者签名

## 实现流程

### 步骤 1：集成 APNs 推送服务

请参考[集成 APNs 推送服务](https://doc.yunxin.163.com/messaging/docs/jEzNjk3NTM?platform=iOS)，实现云信服务端与 APNs 通信。

### 步骤 2：集成 NIM SDK

请参考[集成 SDK](https://doc.yunxin.163.com/messaging/docs/Dg5NjI4MDg?platform=flutter) 将 NIM SDK 集成至您的项目。

### 步骤 3：初始化 NIM SDK

调用 [`initialize`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/initialize.html) 初始化 NIM SDK。在初始化参数 [`NIMIOSSDKOptions`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NIMIOSSDKOptions-class.html) 中传入推送证书名称（对应云信控制台配置的推送证书）。

```
final options = Platform.isAndroid
    ? NIMAndroidSDKOptions(
        appKey: 'appkey',
        /// 其他 通用/Android 配置
    )
    : NIMIOSSDKOptions(
        appKey: 'appkey',
        apnsCername: 'apnsCername', //推送证书名
        /// 其他通用配置/iOS 配置
    );
NimCore.instance.initialize(options)
    .then((result){
        if (result.isSuccess) {
            /// 初始化成功
        } else {
            /// 初始化失败
        }
    });  
```

:::note note
推送证书名称，不超过 32 个字符，否则登录时会报 500 错误。
:::


### 步骤 4：上传 devicetoken 至云信服务端


1. 在原生层获取 deviceToken，并将 deviceToken 上传到 dart 层。

    在 **Runner** 工程下的 **AppDelegate.swift** 文件中添加如下代码：

    ```
    override func application(_ application: UIApplication, didRegisterForRemoteNotificationsWithDeviceToken deviceToken: Data) {
        
        let flutterData = FlutterStandardTypedData.init(bytes: deviceToken)
        let controller : FlutterViewController = window?.rootViewController as! FlutterViewController
        let methodChannel = FlutterMethodChannel(name: "com.netease.NIM.demo/settings",
                                                  binaryMessenger: controller.binaryMessenger)
        methodChannel.invokeMethod("updateAPNsToken", arguments: flutterData)
    }
    ```

    :::note notice
    其中 `com.netease.NIM.demo/settings` 为 `methodChannel` 名字，客户自己定义即可，但需要同 dart 层保持一致。
    :::

    ![Flutter.png](https://yx-web-nosdn.netease.im/common/46d971fd9c3ee40ffdc7a2a8822a6754/Flutter.png)

2. 在 dart 层注册 `methodChannel`，并接收原生层上传的 deviceToken。

    ```
    MethodChannel('com.netease.NIM.demo/settings')
            .setMethodCallHandler((call) async {
        if (call.method == 'updateAPNsToken') {
            print('update APNs token');
            _deviceToken = call.arguments as Uint8List;
        }
        return null;
    });
    ```

3. 在 dart 层初始化 `nim_core` 成功之后，调用 [`updateAPNSToken`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/SettingsService/updateAPNSToken.html) 方法更新 deviceToken。

    ```
    void updateAPNsToken() {
    if (NimCore.instance.isInitialized &&
        Platform.isIOS &&
        _deviceToken != null) {
        NimCore.instance.settingsService.updateAPNSToken(_deviceToken!, null);
        }
    }
    ```

    :::note notice
    如需设置自定义推送文案（`customContentKey`），需要提前在控制台开通自定义推送文案功能，并提前添加好自定义的推送文案。具体如何实现，请参见[推送文案]()。
    :::

### 步骤 5：测试离线推送


**消息发送方：**

发送消息或自定义系统通知给接收方（离线），具体的收发流程可参见[消息收发](https://doc.yunxin.163.com/messaging/docs/zI0NTgwNDY?platform=flutter)和[自定义系统通知](https://doc.yunxin.163.com/messaging/docs/zIzNjg5OTI?platform=flutter#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%B3%BB%E7%BB%9F%E9%80%9A%E7%9F%A5)。
    
这里以发送文本消息为例，通过调用 [`createTextMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createTextMessage.html) + [`sendMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageService/sendMessage.html) 实现。发送的消息默认需要推送，如需设置推送文案，推送角标，推送文案前缀等，请参见[配置消息的推送属性](https://doc.yunxin.163.com/messaging/docs/Dc3ODY4NjU?platform=flutter)。

```
MessageBuilder.createTextMessage(sessionId: 'sessionId', sessionType: NIMSessionType.p2p, text: 'text').then((value){
      if(value.isSuccess && value.data != null){
        var message = value.data!;
        message.pushPayload = {"sessionId":"sessionId","sessionType":"p2p"};
        NimCore.instance.messageService.sendMessage(message: message);
      }
    });
```

**消息接收方：**

接收方将会在登录后接收到离线推送。


:::note note
- 离线推送支持配置免打扰时间，具体请参见[设置推送全局免打扰](https://doc.yunxin.163.com/messaging/docs/DI0NDU5MTM?platform=flutter)
- 离线推送支持配置多端推送策略，即支持推送至同一账号的多个客户端，具体请参见[设置多端推送策略](https://doc.yunxin.163.com/messaging/docs/jE4NzkxMjA?platform=fluuter)。
:::



## 推送相关文档

- [推送问题排查](https://doc.yunxin.163.com/messaging/docs/DY2Njg3MTQ?platform=iOS)
- [推送 payload 配置](https://doc.yunxin.163.com/messaging/docs/DQyNjc5NjE?platform=server)


## 常见问题

Q：触发离线推送的条件是什么？

A：iOS 切换到后台，或者用户主动杀死 App，触发推送条件。因此，要测试 iOS 推送问题，请登录后杀死 App，或将其切换到后台。

<br>


Q：哪些场景下不会触发推送？


A： IM 账号未登录/已登出/被踢下线，不会触发推送。App 在前台，不会触发推送。用户登录 IM 账号，并且未主动登出或者没有被踢下线，可能触发推送。

<br>


Q：推送为什么会出现报错信息：`query token with exception must not refer to a null object`？

A：可能没有在 Application 主进程里面注册推送，请检查推送 SDK 的初始化时机，也可以参考 Demo 示例代码。


<br>


Q：对于同一个消息，其他用户的推送正常，为什么个别用户推送异常？

A：请确认以下三点：

- 发送者和接收者两者是否是好友关系，控制台是否有设置非好友关系允许发送消息。
- 双方是否有拉黑情况。
- 接收方是否有设置发送免打扰，如果是强制推送的情况下可忽略。