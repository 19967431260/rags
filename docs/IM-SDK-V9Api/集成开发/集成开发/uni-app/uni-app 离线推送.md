::: note notice
V9 的 uniapp 离线推送已不再维护，如需要，请升级成 V10，并参考 [实现 uni-app 离线推送](https://doc.yunxin.163.com/messaging2/guide/zc4MTg5MDY?platform=client)。
:::

<br>
为了提高消息送达率，网易云信即时通讯 SDK（简称 NIM SDK）引入手机系统厂商原生推送能力，支持离线推送消息功能。

## 适用场景

您可以通过集成各移动端设备厂商的原生推送 SDK，与 NIM SDK 搭配使用，实现离线推送功能。

实现离线推送消息功能后，当出现以下用户行为时，会触发离线推送，使用手机厂商系统级推送告知用户有消息需要接收：

- 当应用被切换到后台，并且 App 资源被系统回收时。
- 用户登录账号后，主动关闭 App 时。
- iOS 系统应用被切换到后台时。
- 网络不稳定等，导致 NIM SDK 无法与网易云信服务器保持正常连接时。

## 设备类型

NIM SDK 支持离线推送消息功能的移动端设备厂商包括：小米、华为、vivo、OPPO、魅族、谷歌 FCM（Firebase Cloud Messaging）、荣耀。

## 前提条件

<style>
table th:first-of-type {
    width: 50%;
}
table th:nth-of-type(2) {
    width: 50%;
}
</style>

根据本文操作前，请确保您已经完成以下操作：

- [创建 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)。
- 在 HBuilderX 开发工具中，新建了对应的 uni-app 项目。
- 调整项目开发环境，满足如下要求：

    Android | iOS |
    ---- | ---- |
    - Android 4.4 及以上版本 | - Xcode 13 及以上版本 |\
    - 自 v6.9.0 起，改用 AndroidX 支持库，Target API 修改为 28，不再支持 support 库 | - iOS 9.0.0 及以上版本 |

## 下载资源

- [plugin_V1.1.2.zip](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/im/sdk/android/uniapp/plugin_V1.1.2.zip)
- [uni-offline-push.git](https://github.com/netease-im/uni-offline-push)

## 第一步：上传推送证书

1. 在对应移动端设备厂商的推送平台上，注册应用获取应用信息，并开启推送服务。

    :::note note
    有关小米、华为、vivo、OPPO、魅族、谷歌 FCM、荣耀各厂商在获取应用信息和开启推送服务的最佳实践，请参考下文 [注意事项](#keynote)。
    :::

2. 将获取到的应用信息和推送证书，上传至 [网易云信控制台](https://app.yunxin.163.com/global/home)，完成移动端设备厂商推送服务与网易云信服务的通信。

    :::note note
    具体步骤请参考 [实现 Android 离线推送](https://doc.yunxin.163.com/messaging/guide/zc1OTI2MTM?platform=android#步骤-1集成第三方厂商离线推送服务) 和 [实现 APNs 离线推送](https://doc.yunxin.163.com/messaging/guide/DMxMjU0MDY?platform=iOS#步骤-1集成-apns-推送服务) 的步骤 1。
    :::

## 第二步：设置 uni-app 工程

### 引入 uni-app 插件

1. 在 uni-app 工程中，引入网易云信 uni-app 插件。

    1. 在 uni-app 应用根目录下，新建 `nativeplugins` 文件夹。
    2. 将下载的 [plugin_V1.1.2.zip](https://yx-web-nosdn.netease.im/quickhtml/assets/yunxin/im/sdk/android/uniapp/plugin_V1.1.2.zip) 置于 `nativeplugins` 文件夹下。

        <img src="https://yx-web-nosdn.netease.im/common/39094073466b5f068e7edbdd507efe12/uniapp.png" style="width:40%;border: 1px solid #BFBFBF;"/>

        :::note note
        华为注册厂商推送服务时，包含 `agconnect-services.json` 文件。您需要下载该文件，并将其放至您的 uni-app 应用根目录下的 `nativeplugins/NIMUniPlugin/android/assets` 文件夹下。
        :::

2. 配置 uni-app 支持推送。选择 **App 模块配置**，勾选 **Push（消息推送）**。

    :::note note
    仅勾选 **Push（消息推送）**，不要勾选 **uniPush 1.0** 或者 **uniPush 2.0**。
    :::

    <img src="https://yx-web-nosdn.netease.im/common/6a8d0a13efb0f3f5077c7f214cf6a7d1/勾选push.png" style="width:40%;border: 1px solid #BFBFBF;"/>

3. 添加推送插件。

    选择本地插件（`NIMUniPlugin`）并填入第三方厂商的推送鉴权字段。

    <img src="https://yx-web-nosdn.netease.im/common/5bb57ac33c6d98f3b4f323774e13e73e/本地插件.png" style="width:40%;border: 0px solid #BFBFBF;"/>

    ::: note note
    vivo 的应用信息还需要在插件参数中配置（如下图所示），其它厂商不需要。

    <img src="https://yx-web-nosdn.netease.im/common/fa9acda702f88c11066fd92302e8720c/uniapp-offline-plugin-vivo.png" style="width:40%;border: 1px solid #BFBFBF;"/>
    :::

<a id="base"></a>

### 构建自定义基座

自定义基座是 uni-app 程序运行的底层原生环境。由于使用了原生层插件，因此需要打包自定义基座，并再基于自定义基座运行。

:::note note
打包自定义基座时，需要提供安卓/苹果平台签名证书。安卓平台签名证书是您后续更新升级已发布 APK 的凭证。您需要自行生成证书文件并保管，具体请参考 [生成安卓平台签名证书](https://ask.dcloud.net.cn/article/35777) 和 [生成 iOS 证书](https://ask.dcloud.net.cn/article/152)。
:::

1. 在 HBuilderX 中打开当前项目，选择 **运行 > 运行到手机或模拟器 > 制作自定义调试基座**。

    <img src="https://yx-web-nosdn.netease.im/common/6df43c2c625d70ec33b7928ec0da06b3/制作自定义调试基座.png" style="width:80%;border: 1px solid #BFBFBF;"/>

2. 在弹窗中填写以下信息：

    :::::: div linked-codes
    ::: code Android 自定义基座打包的信息

    - Android 包名：必填，您的安卓应用包名
    - 证书别名：必填，生成打包证书时填入的 alias
    - 证书私钥密码：必填
    - 证书文件：必填
    - 选择传统打包

        <img src="https://yx-web-nosdn.netease.im/common/f8016247b0bdceb6eb8c5bf20da1149a/打包.png" style="width:40%;border: 0px solid #BFBFBF;"/>
    :::
    ::: code iOS 自定义基座打包的信息

    - bundleId：必填，您的 iOS 应用的 bundleId
    - 证书私钥密码：必填
    - 证书 profile 文件：必填
    - 私钥证书：必填
    - 选择传统打包

        <img src="https://yx-web-nosdn.netease.im/common/e774663ef3fb1ccaa8f689f3bc783098/iOS基座.png" style="width:40%;border: 0px solid #BFBFBF;"/>
    :::
    ::::::

3. 打包过程需要 DCloud 账户和一些插件，按照提示运行即可。一般打包需要 5-20 分钟（取决于排队时间）。

4. 在真机运行。

    1. 插入真机，选择开发者模式，并允许 USB 安装调试。
    2. 打开 HBuilderX，选择 **运行 > 运行到手机或模拟器 > 选择 Android/iOS 基座运行**。
    3. 选择自定义基座运行应用。

        <img src="https://yx-web-nosdn.netease.im/common/3748eae4117cc5a7dab4faf8bca212bf/真机运行.png" style="width:400px" />

## 第三步：实现离线推送

1. 安装并引入 `nim-web-sdk-ng`。

    ```Bash
    //1.安装 nim-web-sdk-ng
    npm install nim-web-sdk-ng@"<1"
    //2.打开页面 vue 文件，引入 nim uni-app 脚本
    const NIMSDK = require('nim-web-sdk-ng/dist/NIM_UNIAPP_SDK')
    ```

2. [初始化](https://doc.yunxin.163.com/messaging/guide/Tk5NzMyMTE?platform=uniapp) 时，设置各厂商的推送证书等推送配置。

    :::note note
    代码中各个厂商的证书，如 `xmCertificateName`、`hwCertificateName` 等需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 中配置的证书名称保持一致。
    :::

    ```JavaScript
    const nim = NIMSDK.getInstance({
        /**
         * 使用固定设备 ID，
         */
        isFixedDeviceId: true,
        /**
         * 其它参数
         */
    })
    const app = getApp()
    app.globalData.nim = nim

    const nimPushPlugin = uni.requireNativePlugin('NIMUniPlugin-PluginModule')
    nim.offlinePush.setOfflinePushConfig({
        plugin: nimPushPlugin,
        authConfig: {
            xmAppId: "11111",
            xmAppKey : "22222",
            xmCertificateName : "XIAOMI_PUSH_CERT",
            hwAppId : "33333",
            hwCertificateName : "HUAWEI_PUSH_CERT",
            oppoAppId: "44444",
            oppoAppKey: "aaabbb",
            oppoAppSecret: "cccdddd",
            oppoCertificateName: "OPPO_PUSH_CERT",
            vivoCertificateName: "VIVO_PUSH_CERT",
            fcmCertificateName: "FCM_PUSH_CERT",
            mzAppId: "66666",
            mzAppKey: "77778888dddd",
            mzCertificateName: "MEIZU_PUSH_CERT",
            apnsCertificateName: "IOS_PUSH_CERT",
            honorCertificateName: 'HONOR_PUSH_CERT'
        }
    })

    await nim.connect()
    ```

3. 在 `App.vue` 中，监听应用是否退至后台，并通过 `updateAppBackground` 接口告知网易云信服务器应用状态。

    当应用退至后台时：

    - Android 应用仍可以收到 NIM SDK 的消息，您可以根据这些设置应用通知。
    - iOS 应用则无法激活 NIM SDK 的回调函数。因此，iOS 退至后台时，应该通过下面代码告知网易云信服务器，然后网易云信服务器会给处于后台的 iOS 应用发送离线推送。

        ```JavaScript
        onShow: function() {
            const app = getApp()
            app && app.globalData.nim && app.globalData.nim.offlinePush.updateAppBackground({
                isBackground: false
            })},
        onHide: function() {
            const app = getApp()
            app && app.globalData.nim && app.globalData.nim.offlinePush.updateAppBackground({
                isBackground: true
            })}
        ```

## 第四步：测试离线推送

### 消息发送方测试

发送消息或自定义系统通知给接收方（离线），具体的收发流程可参考 [消息收发](https://doc.yunxin.163.com/messaging-enhanced/guide/TQ2NTUxNTM?platform=web) 和 [自定义系统通知](https://doc.yunxin.163.com/messaging-enhanced/guide/DIyMDE2NDM?platform=web#自定义系统通知)。

以发送文本消息为例，通过调用 `sendTextMsg` 接口实现的示例代码如下：

```JavaScript
await nim.msg.sendTextMsg({
  "scene": "p2p",
  "to": "cs6",
  "body": "hello, world",
  "pushInfo": {
    "needPush": true,
    "pushContent": "hello, this is a push content for testing"
  }
})
```

### 消息接收方测试

登录 IM 账号，强制停止应用，或者 iOS 系统将应用切换到后台时，确认能否接收到离线推送消息。

<a id="keynote"></a>

## 注意事项

### 通用

- [厂商推送通道限制说明](https://doc.yunxin.163.com/messaging/guide/DY1MzgzOTk?platform=android)：第三方厂商推送通道的流控。
- [第三方推送厂商通道错误码](https://doc.yunxin.163.com/messaging/guide/DY4NzY5ODU?platform=android#%E5%8E%82%E5%95%86%E9%80%9A%E9%81%93%E9%94%99%E8%AF%AF%E7%A0%81%E6%96%87%E6%A1%A3)：小米、华为、oppo、vivo、魅族、荣耀、FCM 厂商的通道错误码。
- [推送载体（payload）配置](https://doc.yunxin.163.com/messaging/guide/DQyNjc5NjE?platform=server)：自定义消息的推送配置。

### **华为**

- 华为应用配置的 **常规** 页面包含 **项目** 和 **应用** 的 Client ID 和 Client Secret，两者对应的参数不一致，请下拉至页面底部，获取 **应用** 的 Client ID 和 Client Secret。
- 必须添加打包的 SHA256 证书指纹，SHA256 证书指纹需与自己的打包证书一致。
- 华为注册厂商推送服务时，包含 `agconnect-services.json` 文件。您需下载该文件，并将其放至项目原生插件目录下 `nativeplugins/NIMUniPlugin/android/assets/` 文件夹下。
- 若修改项目、应用信息、开发服务设置，都需要重新下载配置 `agconnect-services.json` 文件。配置 `agconnect-services.json` 文件后，您需要重新构建 [自定义基座](#base)。
- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 配置证书时，需要使用华为应用的 `clientId` 和 `clientKey`。
- 未上架的应用，一天只能够接收两条推送。
- 通过透传参数，可以设置消息透传为测试服透传，这样一天能够测试 500 条消息：

    ```JSON
    nim.msg.sendTextMsg({
        "scene": "p2p",
        "to": "testAccount",
        "body": "this is a tex23424t 111",
        "pushInfo": {
            "pushPayload": '{"pushTitle":"bonjour 2","hwField":{"androidConfig":{"target_user_type":1}}}'
            }
    })
    ```

### **vivo**

- vivo 每日推送限制为 5 条消息。
- 必须在 `manifest.json` 文件中设置 `PUSH_VIVO_APPID` 与 `PUSH_VIVO_APPKEY`。
- 如果是离线打包，您需要在工程的 `AndroidManifest.xml` 的 `Application` 节点中添加以下代码：

    ```XML
    <meta-data
      android:name="api_key"
      android:value="xxxx" />
    <meta-data
      android:name="app_id"
      android:value="xxxx" />
    ```

### **OPPO**

- 每日能够推送用户数量（安卓应用用户数量） * 2 条消息。
- 可以添加测试设备，然后使用私信通道多次推送。
- 如果返回 `RegistrationId Invalid`，可以检查 OPPO 账号是否注册并登录。

### **FCM**

- FCM 只能够通过离线打包方式构建。
- FCM 需要在安卓工程下添加 `google-services.json` 文件。

### **iOS**

- 自定义基座的 bundle ID 应该与 [苹果开发者平台](https://developer.apple.com/cn/) 中 `identifiers` 的 bundle ID 保持一致。
- 苹果开发者平台设置 `identifiers` 时，需要打开 **Push Notifications**。且该 Notification 的证书设置需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置的证书一致。

## 常见问题

### 调用 `updatePushToken` 报错 `Malformed UTF-8 data`？

可能是插件的版本比较旧导致。旧版本插件未进行 cr4 加密。而 JS 代码默认会对 token 进行 cr4 解密。由于无法解密，所以 JS 会报错。

### 基座等待长时间后制作失败？

可能是推送证书导致，请检查上传的推送证书是否有误。

### 安卓平台调用 `getDeviceToken` 接口未返回 token？

查看 JS 日志，若日志中存在 **开始获取设备 token** 且不存在"收到了 token"，则说明调用 `getDeviceToken` 未返回结果。您可以打开 Android Studio，新建一个工程，然后查看 Logcat 打印的日志中是否有其他有效的报错信息。

目前导致上述问题可能的原因包括：

- 未选择带有插件的基座导致，即当前运行的基座不包含原生插件 `NIMUniPlugin`，请在 manifest 中配置该插件，重新制作包括该原生插件的自定义运行基座。
- `java.lang.Integer cannot be casted into java.lang.String:`，即各个厂商的推送鉴权信息错误，如果是纯数字，需要加转义符号: "\"。
- 其他问题，请仔细检查 manifest 中，厂商的推送鉴权信息是否设置，或者是否设置正确。

### iOS 平台 `DeviceToken` 无法获取？

请检查 uni-app 自定义基座的 bundle ID 是否和 [苹果开发者平台](https://developer.apple.com/cn/) 中 identifiers 的 bundle ID 保持一致。

### 服务器推送时，日志显示 MissingProviderToken 异常？

苹果开发者平台设置 identifiers 时，需要打开 Push Notifications。且该 Notification 的证书设置需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置的证书一致。

### 一条消息收到重复推送？

请在初始化参数重设置 `isFixedDeviceId` 为 `true`，避免设备在服务器重复注册。

### 无法收到推送消息？

若无法收到推送消息，请优先检查以下情况：

- 检查 NIM SDK 是否已集成最新版本，最新版本号请访问 [资源下载](https://doc.yunxin.163.com/messaging2/resource?platform=uniapp)。
- 检查是否对会话开启免打扰。若开启，则接收不到推送通知，请先关闭。
- 检查手机端是否开启应用通知接收权限。若未开启，则接收不到推送通知，请开启。