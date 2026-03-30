为了提高消息送达率，网易云信即时通讯 SDK（简称 NIM SDK）引入手机系统厂商原生推送能力，支持离线推送消息功能。

## 适用场景

您可以通过集成各移动端设备厂商的原生推送 SDK，与 NIM SDK 搭配使用，实现离线推送功能。

实现离线推送消息功能后，当出现以下用户行为时，会触发离线推送，使用手机厂商系统级推送告知用户有消息需要接收：

- 当应用被切换到后台，并且 App 资源被系统回收时。
- 用户登录账号后，主动关闭 App 时。
- iOS 系统应用被切换到后台时。
- 网络不稳定等，导致 NIM SDK 无法与网易云信服务器保持正常连接时。

## 设备类型

NIM SDK 支持离线推送消息功能的移动端设备厂商包括：小米、华为、vivo、OPPO、魅族、谷歌 FCM（Firebase Cloud Messaging）、荣耀、鸿蒙。

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

- [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#4-注册-im-账号)。
- 在 HBuilderX 开发工具中，新建了对应的 uni-app 项目。
- 调整项目开发环境，满足如下要求：

    Android | iOS |
    ---- | ---- |
    - Android 4.4 及以上版本 | - Xcode 13 及以上版本 |\
    - 自 6.9.0 起，改用 AndroidX 支持库，Target API 修改为 28，不再支持 support 库 | - iOS 9.0.0 及以上版本 |

## 第一步：上传推送证书

1. 在对应移动端设备厂商的推送平台上，注册应用获取应用信息，并开启推送服务。

    :::note note
    有关小米、华为、vivo、OPPO、魅族、谷歌 FCM、荣耀、鸿蒙各厂商在获取应用信息和开启推送服务的最佳实践，请参考下文 [注意事项](#keynote)。
    :::

2. 将获取到的应用信息和推送证书，上传至 [网易云信控制台](https://app.yunxin.163.com/global/home)，完成移动端设备厂商推送服务与网易云信服务的通信。

    <img alt="" src="https://yx-web-nosdn.netease.im/common/be0bf8aaab65bbb9de0ae8c03514bb1e/华为推送.png" style="width:60%;border: 1px solid #BFBFBF;">

    :::note note
    具体步骤请参考以下文档：
    - [集成华为推送](https://doc.yunxin.163.com/messaging/guide/jg2ODQxMjU?platform=android#第二步添加推送证书)
    - [集成小米推送](https://doc.yunxin.163.com/messaging/guide/zg2NDE4ODM?platform=android#第二步添加小米推送证书)
    - [集成 OPPO 推送](https://doc.yunxin.163.com/messaging/guide/zI4ODc0MTE?platform=android#第二步在网易云信控制台添加-oppo-推送证书)
    - [集成 vivo 推送](https://doc.yunxin.163.com/messaging/guide/zY0MjM0OTc?platform=android#第二步添加-vivo-推送证书)
    - [集成荣耀推送](https://doc.yunxin.163.com/messaging/guide/DMwMjc5MDM?platform=android#第二步添加荣耀推送证书)
    - [集成魅族推送](https://doc.yunxin.163.com/messaging/guide/DcwMjI1MTI?platform=android#第二步添加魅族推送证书)
    - [集成谷歌推送](https://doc.yunxin.163.com/messaging/guide/zY2Nzc4MjY?platform=android#步骤-2在云信控制台添加-fcm-推送证书)
    - [集成 APNs 推送服务](https://doc.yunxin.163.com/messaging/guide/jEzNjk3NTM?platform=iOS#步骤-3上传推送证书至云信)
    - [创建鸿蒙推送证书]([#harmony-cert](https://doc.yunxin.163.com/messaging2/guide/TkyNTI3OTg?platform=client))
    :::

## 第二步：设置 uni-app 工程

<a id="resource"></a>

### 下载资源

在开始设置 uni-app 工程前，您可以按需下载以下资源：

- **uni-app 推送插件包**：[uniapp_plugin_V1.1.4.zip](https://yx-web-nosdn.netease.im/common/c2e2203ec8a0ce4c602a08e848079a4b/uniapp_plugin_V1.1.4.zip)
  - 这是网易云信提供的 uni-app 插件包，包含了所需的推送功能。
  - 当前插件版本为 1.1.4，需要解压后放置到您项目的 `nativeplugins` 目录中。
  - 此插件支持 Android 和 iOS 平台的推送集成。

- **示例工程代码库**：[uni-offline-push.git](https://github.com/netease-im/uni-offline-push)
  - 这是一个完整的演示项目，展示了如何在 uni-app 中集成和使用网易云信推送功能。
  - GitHub 项目中包含了详细的集成示例和使用方法，您可以参考其结构和代码，以便更好地理解集成步骤。
  - GitHub 项目中存放了 **uni-app 推送插件包**，位于项目文件夹的 `nativeplugins` 目录下。

### 引入 uni-app 插件

1. 在 uni-app 工程中，引入网易云信 uni-app 插件。

   1. 在 uni-app 应用根目录下，新建 `nativeplugins` 文件夹。
   2. 将下载的 [plugin_1.1.4.zip](https://yx-web-nosdn.netease.im/common/c2e2203ec8a0ce4c602a08e848079a4b/uniapp_plugin_V1.1.4.zip) 置于 `nativeplugins` 文件夹下。

      <img src="https://yx-web-nosdn.netease.im/common/39094073466b5f068e7edbdd507efe12/uniapp.png" style="width:40%;border: 1px solid #BFBFBF;"/>

      :::note note
      - 华为注册厂商推送服务时，包含 `agconnect-services.json` 文件。您需要下载该文件，并将其放至您的 uni-app 应用根目录下的 `nativeplugins/NIMUniPlugin/android/assets` 文件夹下。
      - 荣耀注册厂商推送服务时，包含 mcs-services.json 文件。您需下载该文件，并将其放至您的 uni-app 应用根目录下的 `nativeplugins/NIMUniPlugin/android/assets` 文件夹下。
      - FCM 注册厂商推送服务时，包含 `google-services.json` 文件。您需下载该文件，并将其放至您的 uni-app 应用根目录下的 `nativeplugins/NIMUniPlugin/android/assets` 文件夹下。
        :::

2. 配置 uni-app 支持推送。选择 **App 模块配置**，勾选 **Push（消息推送）**。

   :::note note
   仅勾选 **Push（消息推送）**，不要勾选 **uniPush 1.0** 或者 **uniPush 2.0**。
   :::

   <img src="https://yx-web-nosdn.netease.im/common/4a5ca8551eeea2a469a828f12bc2f5d0/消息推送选项.png" style="width:40%;border: 1px solid #BFBFBF;"/>

3. 添加推送插件。

   选择本地插件（`NIMUniPlugin`）并填入第三方厂商的推送鉴权字段。

   <img src="https://yx-web-nosdn.netease.im/common/675a0ec8adc68b2870250e879eaea1e4/本地插件选择.png" style="width:40%;border: 0px solid #BFBFBF;"/>

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

    - **Android 包名**：必填，您的安卓应用包名
    - **证书别名**：必填，生成打包证书时填入的 alias
    - **证书私钥密码**：必填
    - **证书文件**：必填
    - 选择传统打包

    <img src="https://yx-web-nosdn.netease.im/common/9f534855c5144ab536540f988e6a014d/基座打包.png" style="width:40%;border: 0px solid #BFBFBF;"/>

    :::
    ::: code iOS 自定义基座打包的信息

    - **bundleId**：必填，您的 iOS 应用的 bundleId
    - **证书私钥密码**：必填
    - **证书 profile 文件**：必填
    - **私钥证书**：必填
    - 选择传统打包

    <img src="https://yx-web-nosdn.netease.im/common/00dc549750704fac8c06df2a3079dbdf/iOS基座打包.png" style="width:40%;border: 0px solid #BFBFBF;"/>
    :::
    ::::::

3. 打包过程需要 DCloud 账户和一些插件，按照提示运行即可。一般打包需要 5-20 分钟（取决于排队时间）。

4. 在真机运行。

    1. 插入真机，选择开发者模式，并允许 USB 安装调试。
    2. 打开 HBuilderX，选择 **运行 > 运行到手机或模拟器 > 选择 Android/iOS 基座运行**。
    3. 选择自定义基座运行应用。

    <img src="https://yx-web-nosdn.netease.im/common/8c1ef0749140f036fbacd678a40445af/真机运行.png" style="width:400px" />

## 第三步：实现离线推送

1. 安装并引入 `nim-web-sdk-ng`。

   ```Bash
   //1.安装 nim-web-sdk-ng
   npm install nim-web-sdk-ng@">=10"
   //2.打开页面 vue 文件，引入 nim uni-app 脚本
   const NIMSDK = require('nim-web-sdk-ng/dist/v2/NIM_UNIAPP_SDK')
   ```

2. [初始化](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client#实现初始化) 时，设置各厂商的推送证书等推送配置。

    ::: note note
    代码中各个厂商的证书，如 `xmCertificateName`、`hwCertificateName` 等需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 中配置的证书名称保持一致。
    :::

    ```JavaScript
    const nim = NIMSDK.getInstance(param1, {
        /**
        * 设置固定设备 ID。这样 IM 推送服务可以绑定当前设备
        */
        V2NIMLoginServiceConfig: {
          isFixedDeviceId: true
        }
    })
    const app = getApp()
    app.globalData.nim = nim

    // 推送配置对象
    const OFFLINE_PUSH_CONFIG = {
        // Android 厂商通道
        miPush: {
            appId: 'xxx',
            appKey: 'yyy',
            certificateName: 'XIAOMI_PUSH_CERT'
        },
        vivoPush: {
            certificateName: 'VIVO_PUSH_CERT'
        },
        oppoPush: {
            appId: 'xxx',
            appKey: 'yyy',
            secret: 'zzz',
            certificateName: 'OPPO_PUSH_CERT'
        },
        hwPush: {
            appId: 'xxx',
            certificateName: 'HUAWEI_PUSH_CERT'
        },
        fcmPush: {
            certificateName: 'FCM_PUSH_CERT'
        },
        mzPush: {
            appId: 'xxx',
            appKey: 'yyy',
            certificateName: 'MEIZU_PUSH_CERT'
        },
        honorPush: {
            certificateName: 'HONOR_PUSH_CERT'
        },
        // iOS
        apns: {
            certificateName: 'APPLE_PUSH_CERT'
        },
        // 鸿蒙
        harmonyPush: {
            certificateName: "DEMO_HMOS_PUSH" 
        }
    }

    // #ifdef APP-PLUS
    // Android/iOS 平台使用原生插件方式
    const nimPushPlugin = uni.requireNativePlugin('NIMUniPlugin-PluginModule')
    nim.V2NIMSettingService.setOfflinePushConfig(
        nimPushPlugin,
        OFFLINE_PUSH_CONFIG
    )
    // #endif

    // #ifdef APP-HARMONY
    // 鸿蒙平台使用 UTS 插件方式
    const sysInfo = uni.getSystemInfoSync()
    nim.V2NIMSettingService.setOfflinePushConfig(
        uni.NIMNativePush, // 插件已自动注册到 uni 对象
        OFFLINE_PUSH_CONFIG
    )
    // #endif

    await nim.V2NIMLoginService.login(accountId, token)
    ```

    ::: note notice
    `setOfflinePushConfig` 必须在 `nim` 初始化之后、登录之前执行！
    :::

3. （可选）监听应用后台状态。

    在 `App.vue` 中，监听应用是否退至后台，并通过 `updateAppBackground` 接口告知网易云信服务器应用状态。

    当应用退至后台时：

    - Android 应用仍可以收到 NIM SDK 的消息，您可以根据这些设置应用通知。
    - iOS 应用则无法激活 NIM SDK 的回调函数。因此，iOS 退至后台时，应该通过下面代码告知网易云信服务器，然后网易云信服务器会给处于后台的 iOS 应用发送离线推送。

    ```JavaScript
    onShow: function() {
        // #ifdef APP-PLUS
        const app = getApp()
        app && app.globalData.nim && app.globalData.nim.V2NIMSettingService.setAppBackground(false)
        // #endif
    },
    onHide: function() {
        // #ifdef APP-PLUS
        const app = getApp()
        app && app.globalData.nim && app.globalData.nim.V2NIMSettingService.setAppBackground(true)
        // #endif
    }
    ```

4. <span id="onLaunch">（可选）推送拉起跳转指定会话。</span>

    若需要推送拉起跳转指定到会话中，请参照下文，在 `App.vue` 的 `onLaunch` 中监听函数 `nimPushPlugin.addOpenNotificationListener`，确保每次应用显示都能正确监听设置推送拉起。

    :::note note
    下载并集成了 [uni-app 推送插件](#resource) 然后更新到 1.1.4 或更高版本后，若点击通知打开应用后未触发监听事件，请参考下文 [点击通知打开应用后，监听事件不触发](#addOpenNotificationListener)。
    :::

    ```JavaScript
    // App.vue
    // #ifdef APP-PLUS
    /** 推送插件 */
    const nimPushPlugin = uni.requireNativePlugin("NIMUniPlugin-PluginModule");
    // #endif

    export default {
      onLaunch: function () {
        console.log('App Launch')
        // #ifdef APP-PLUS
        if (nimPushPlugin) {
          // 打印插件版本便于调试
          uni.showToast({
            title: '推送插件版本: ' + (nimPushPlugin.version || '未知'),
            icon: 'none'
          });

          // 添加通知单击监听 - 移至 onShow 中以确保每次应用显示都能正确监听
          nimPushPlugin.addOpenNotificationListener((result) => {
            // result aos 真实调通返回值
            // {
            //     "mipush_notified": "true",
            //     "pushTargetComponent": "true",
            //     "sessionId": "cs1",
            //     "messageId": "smm6490575310016323890",
            //     "eventMessageType": "1000",
            //     "sessionType": "0"
            // }
            if (typeof result === 'object') {
              console.log('=====addOpenNotificationListener success:', JSON.stringify(result))
              // todo 自行组装和跳转, 有关于 sessionType 和 sessionId 如何组出正确的 v2 会话 ID 可以参照下文的 navigateToPullPage 方法
              /** uni.navigateTo({
                  url: `/pages/index?sessionId=${result.sessionId}&sessionType=${result.sessionType}`, // 通过 URL 传参
                  success: () => console.log('跳转成功'),
                  fail: (err) => console.error('跳转失败', err)
              }) */
            } else {
              console.log('=====addOpenNotificationListener unexpected:', result)
            }

            //获取数据，进行跳转
          });
        }
        // #endif
      },
      // ... 省略前文的 onHide
      methods: {
        // async navigateToPullPage() {
        //   const app = getApp()
        //   if (!(app && app.globalData.nim)) {
        //     return
        //   }
        //   let conversationId = ''
        //   switch (+pushInfo.sessionType) {
        //     case 0:
        //       conversationId =
        //         app.globalData.nim.V2NIMConversationIdUtil.p2pConversationId(
        //           pushInfo.sessionId
        //         )
        //       break
        //     case 1:
        //       conversationId =
        //         app.globalData.nim.V2NIMConversationIdUtil.teamConversationId(
        //           pushInfo.sessionId
        //         )
        //       break
        //     case 5:
        //       conversationId =
        //         app.globalData.nim.V2NIMConversationIdUtil.superTeamConversationId(
        //           pushInfo.sessionId
        //         )
        //       break
        //     default:
        //       console.log(
        //         `=======navigateToPullPage unexpected v1 sessionType ${pushInfo.sessionType}`
        //       )
        //       return
        //   }
        //   console.log('=============navigateToPullPage to ', conversationId)
        //   uni.navigateTo({
        //     url: `/pages/Chat/index?conversationId=${conversationId}`,
        //   })
        // },
      }
    }
    ```

## 第四步：测试离线推送

### 消息发送方测试

发送消息或自定义系统通知给接收方（离线），具体的收发流程可参考 [消息收发](https://doc.yunxin.163.com/messaging2/guide/DYzMjA0Njc?platform=client) 和 [自定义系统通知收发](https://doc.yunxin.163.com/messaging2/guide/TYyNDk1ODk?platform=client)。

- **发送端以发送文本消息为例，实现的示例代码如下**：

    ```JavaScript
    const message = nim.V2NIMMessageCreator.createTextMessage('hello world')
    const res = await nim.V2NIMMessageService.sendMessage(message, 'senderId|1|receiverId', {
      pushConfig: {
        pushEnabled: true,
        // "pushNickEnabled": true, // 可以选择是否推送昵称
        // "pushContent": "您有新消息请查收", // 可以指定推送内容
      }
    })
    ```

- **如果需要推送拉起跳转指定到会话中，则需要对发送的消息进行设置，可以参考 [uni-offline-push.git](#resources) 演示工程中 [index.vue](https://github.com/netease-im/uni-offline-push/blob/master/pages/index/index.vue) 构造的 `sendMessage` 示例**，具体步骤如下：

    1. 将 `PACKAGE_NAME` 换成自己的包名。
    2. 注意 `intent_uri` 中组装的格式 `i.sessionType` 代表传入一个数字类型的 `sessionType`, `S.sessionid` 代表传入一个字符串类型的 `sessionId`. 用它来组装拉起推送跳转时要进入的会话 ID。

        ```JavaScript
        const message = nim.V2NIMMessageCreator.createTextMessage('hello world')
        const senderId = nim.V2NIMLoginService.getLoginUser() // 发送者
        const receiverId = 'receiverId' // 接收者
        const conversationType = 1 // 1: 单聊，2：群聊，3：超级群
        /** 组织推送跳转内容 pushPayload 需要的参数 */
        // 单聊 p2p 会话, sessionId 要填本账号 ID. 群聊要填群 ID.
        const sessionId =
        conversationType === 1
            ? senderId
            : receiverId
        // 兼容原生 App 的老版本 IM, 所以映射关系为 老版本的 0: 单聊，1：群聊，5：超级群
        const sessionType =
        conversationType === 1 ? '0' : conversationType === 2 ? '1' : '5'
        // 需要换成自己的包名
        const PACKAGE_NAME = 'com.netease.nim.demo'
        const pushPayload = JSON.stringify({
        // xiaomi
        notify_effect: '2', //可选项，预定义通知栏消息的单击行为。1：通知栏单击后打开 app 的 Launcher Activity，2：通知栏单击后打开 app 的任一 Activity（开发者还需要传入 intent_uri），3：通知栏单击后打开网页（开发者还需要传入 web_uri）
        intent_uri: `intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=${PACKAGE_NAME}/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=${sessionType};S.sessionId=${sessionId};end`, //可选项，打开当前 app 的任一组件。
        // huawei
        hwField: {
            click_action: {
            //必填，消息单击行为
            type: 1, //必填，消息单击行为类型，取值如下：1：打开应用自定义页面 2：单击后打开特定 URL 3：单击后打开应用
            // 自定义页面中 intent 的实现，请参考指定 intent 参数​。当 type 为 1 时，字段 intent 和 action 至少二选一。scheme 方式和指定 activity 方式都可以
            intent: `intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=${PACKAGE_NAME}/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=${sessionType};S.sessionId=${sessionId};end`,
            },
            androidConfig: {
            category: 'IM', //可选项，标识消息类型，用于标识高优先级透传场景，请参考官方文档 AndroidConfig.category
            },
        },
        // 荣耀
        honorField: {
            notification: {
            // AndroidNotification
            clickAction: {
                //必填，消息单击行为
                type: 1, //必填，消息单击行为类型，取值如下：1：打开应用自定义页面 2：单击后打开特定 URL 3：单击后打开应用
                //自定义页面中 intent 的实现，请参考指定 intent 参数。当 type 为 1 时，字段 intent 和 action 至少二选一。
                intent: `intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=${PACKAGE_NAME}/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=${sessionType};S.sessionId=${sessionId};end`,
            },
            importance: 'NORMAL', //可选项，Android 通知消息分类，决定用户设备消息通知行为，取值如下：LOW：资讯营销类消息 NORMAL：服务与通讯类消息
            },
        },
        // vivo
        vivoField: {
            skipType: '4', //必填，单击跳转类型 1：打开 App 首页 2：打开链接 3：自定义 4:打开 app 内指定页面，默认为 1
            skipContent: `intent:#Intent;action=com.netease.nimlib.uniapp.push.NotificationClickActivity;component=${PACKAGE_NAME}/com.netease.nimlib.uniapp.push.NotificationClickActivity;launchFlags=0x04000000;i.sessionType=${sessionType};S.sessionId=${sessionId};end`,
            classification: '1', //可选项，消息类型 0：运营类消息，1：系统类消息。默认为 0
            category: 'IM', // 可选项，二级分类
        },
        // oppo
        oppoField: {
            channel_id: '', //可选项，指定下发的通道 ID
            category: 'IM', //可选项，通道类别名
            notify_level: 2, //通知栏消息提醒等级，1-通知栏。2-通知栏+锁屏。16-通知栏+锁屏+横幅+震动+铃声
            click_action_type: '1', //单击通知栏后触发的动作类型。0（默认 0.启动应用。1.跳转指定应用内页（action 标签名）。2.跳转网页。4.跳转指定应用内页（全路径类名）。5.跳转 Intent scheme URL: "",
            click_action_activity:
            'com.netease.nimlib.uniapp.push.NotificationClickActivity',
            action_parameters: JSON.stringify({
            sessionType: sessionType,
            sessionId: sessionId,
            }),
        },
        fcmFieldV1: {
            message: {
            android: {
                priority: 'high',
                data: {
                    sessionType: sessionType,
                    sessionId: sessionId,
                },
                notification: {
                    click_action: 'com.netease.nimlib.uniapp.push.NotificationClickActivity',
                },
            },
            },
        },

        // 特别声明: 魅族暂不可用, 需要 IM 服务器支持

        // iOS 通用
        sessionId: sessionId,
        sessionType: sessionType,
        })
        const res = await nim.V2NIMMessageService.sendMessage(message, `${senderId}|${conversationType}|${receiverId}`, {
        pushConfig: {
            pushEnabled: true,
            // "pushNickEnabled": true, // 可以选择是否推送昵称
            // "pushContent": "您有新消息请查收", // 可以指定推送内容
            pushPayload: pushPayload
        }
        })
        ```

### 消息接收方测试

在发送方发消息前：

- **Android**：在 uni-app 编译的原生 app 里登录 IM，然后杀死进程。
- **iOS**：除了杀死进程外，还可以将应用切换到后台。

待发送方发送消息后，观察接收端能否接收到离线推送消息。

<a id="keynote"></a>

## 注意事项

### 通用

- **[厂商推送通道限制说明](https://doc.yunxin.163.com/messaging2/guide/TQyOTE4Nzk?platform=client#%E5%8E%82%E5%95%86%E9%80%9A%E9%81%93%E9%99%90%E6%B5%81)**：第三方厂商推送通道的流控。
- **[第三方推送厂商通道错误码](https://doc.yunxin.163.com/messaging2/guide/TQyOTE4Nzk?platform=client#%E5%8E%82%E5%95%86%E9%80%9A%E9%81%93%E9%94%99%E8%AF%AF%E7%A0%81%E6%96%87%E6%A1%A3)**：小米、华为、oppo、vivo、魅族、荣耀、FCM 厂商的通道错误码。
- **[推送载体（pushPayload）配置](https://doc.yunxin.163.com/messaging/server-apis/DQyNjc5NjE?platform=server)**：自定义消息的推送配置。

### 华为

- 华为应用配置的 **常规** 页面包含 **项目** 和 **应用** 的 Client ID 和 Client Secret，两者对应的参数不一致，请下拉至页面底部，获取 **应用** 的 Client ID 和 Client Secret。
- 必须添加打包的 SHA256 证书指纹，SHA256 证书指纹需与自己的打包证书一致。
- 华为注册厂商推送服务时，包含 `agconnect-services.json` 文件。您需下载该文件，并将其放至项目原生插件目录下 `nativeplugins/NIMUniPlugin/android/assets/` 文件夹下。
- 若修改项目、应用信息、开发服务设置，都需要重新下载配置 `agconnect-services.json` 文件。配置 `agconnect-services.json` 文件后，您需要重新构建 [自定义基座](#base)。
- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 配置证书时，需要使用华为应用的 `clientId` 和 `clientKey`。
- 未上架的应用，一天只能够接收两条推送。
- 通过透传参数，可以设置消息透传为测试服透传，这样一天能够测试 500 条消息：

  ```JavaScript
  await nim.V2NIMMessageService.sendMessage(message, 'senderId|1|receiverId', {
      pushConfig: {
          pushPayload: '{"pushTitle":"bonjour 2","hwField":{"androidConfig":{"target_user_type":1}}}'
      }
  })
  ```

### 荣耀

必须在 `manifest.json` 文件中设置 `PUSH_HONOR_APPID`。

### vivo

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

### OPPO

- 每日能够推送用户数量（安卓应用用户数量） * 2 条消息。
- 可以添加测试设备，然后使用私信通道多次推送。
- 如果返回 `RegistrationId Invalid`，可以检查 OPPO 账号是否注册并登录。

### iOS

- 自定义基座的 bundle ID 应该与 [苹果开发者平台](https://developer.apple.com/cn/) 中 `identifiers` 的 bundle ID 保持一致。
- 苹果开发者平台设置 `identifiers` 时，需要打开 **Push Notifications**。且该 Notification 的证书设置需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置的证书一致。

## 通用常见问题

### 调用 `updatePushToken` 报错 `Malformed UTF-8 data`？

可能是插件的版本比较旧导致。旧版本插件未进行 cr4 加密。而 JS 代码默认会对 token 进行 cr4 解密。由于无法解密，所以 JS 会报错。

### 基座等待长时间后制作失败？

可能是推送证书导致，请检查上传的推送证书是否有误。

### 无法收到推送消息？

若无法收到推送消息，请优先检查以下情况：

- 检查 NIM SDK 是否已集成最新版本，最新版本号请访问 [资源下载](https://doc.yunxin.163.com/messaging2/resource?platform=uniapp)。
- 检查是否对会话开启免打扰。若开启，则接收不到推送通知，请先关闭。
- 检查手机端是否开启应用通知接收权限。若未开启，则接收不到推送通知，请开启。
- 检查证书是否配置正确。
  - 是否在 uni-app 的 dcloud 后台应用信息里添加 AOS 和 iOS 的包信息。
  - 是否在 SDK 执行 `nim.V2NIMSettingService.setOfflinePushConfig` 时传入正确的证书名，需要去 [网易云信控制台](https://app.yunxin.163.com/global/home) 检查证书名是否配置正确。
  - 证书是否过期。

### 一条消息收到重复推送？

请在初始化参数重设置 `isFixedDeviceId` 为 `true`，避免设备在服务器重复注册。

## 安卓常见问题

### 安卓平台调用 `getDeviceToken` 接口未返回 token？

查看 JS 日志，若日志中存在 **开始获取设备 token** 且不存在"收到了 token"，则说明调用 `getDeviceToken` 未返回结果。您可以打开 Android Studio，新建一个工程，然后查看 Logcat 打印的日志中是否有其他有效的报错信息。

目前导致上述问题可能的原因包括：

- 未选择带有插件的基座导致，即当前运行的基座不包含原生插件 `NIMUniPlugin`，请在 manifest 中配置该插件，重新制作包括该原生插件的自定义运行基座。
- `java.lang.Integer cannot be casted into java.lang.String:`，即各个厂商的推送鉴权信息错误，如果是纯数字，需要加转义符号："\"。
- 其他问题，请仔细检查 manifest 中，厂商的推送鉴权信息是否设置，或者是否设置正确。

<a id="addOpenNotificationListener"></a>

### 点击通知打开应用后，监听事件不触发？

**问题症状**：下载并集成了 [uni-app 推送插件](#resource) 然后在更新到 1.1.4 或更高版本后，使用 `addOpenNotificationListener` 监听推送通知点击事件时，点击推送通知打开应用后，监听事件没有触发。

**可能原因**：

- 插件更新不当：直接替换文件而非完整更新流程。
- 未重新打包自定义基座：旧基座中仍使用的是旧版插件。
- 监听事件配置位置不正确：应当在 `onLaunch` 中添加监听。
- 推送参数配置有误：如包名与应用不匹配。

**解决方案**：

1. 正确更新插件：
   - 先删除 `manifest.json` 中旧版本插件配置。
   - 删除项目中旧版本插件文件。
   - 添加新版本插件文件。
   - 在 `manifest.json` 中重新勾选插件。
   - 重新打包自定义基座。

2. 在 `App.vue` 的 `onLaunch` 中添加监听代码，详情请参考上文步骤 [推送拉起跳转指定到会话](#onLaunch)。

3. 确认推送配置正确：
   - 检查 `pushPayload` 格式。
   - 确保包名配置正确。
   - 检查 `intent_uri` 中的 `component` 参数是否与应用包名一致。

## iOS 常见问题

### iOS 平台 `DeviceToken` 无法获取？

请检查 uni-app 自定义基座的 bundle ID 是否和 [苹果开发者平台](https://developer.apple.com/cn/) 中 identifiers 的 bundle ID 保持一致。

### 服务器推送时，日志显示 MissingProviderToken 异常？

苹果开发者平台设置 identifiers 时，需要打开 Push Notifications。且该 Notification 的证书设置需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置的证书一致。