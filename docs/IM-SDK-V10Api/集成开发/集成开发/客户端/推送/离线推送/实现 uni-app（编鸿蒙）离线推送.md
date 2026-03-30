为了提高消息送达率，网易云信即时通讯 SDK（简称 NIM SDK）引入手机系统厂商（uni-app 编鸿蒙）原生推送能力，支持离线推送消息功能。

## 概述

您可以通过集成移动端设备厂商的原生推送 SDK，与 NIM SDK 搭配使用，实现离线推送功能。

实现离线推送消息功能后，当出现以下用户行为时，会触发离线推送，使用手机厂商系统级推送告知用户有消息需要接收：

- 当应用被切换到后台，并且 App 资源被系统回收时。
- 用户登录账号后，主动关闭 App 时。
- 网络不稳定等，导致 NIM SDK 无法与网易云信服务器保持正常连接时。

本文主要介绍如何实现 uni-app 编鸿蒙离线推送。

::: note note 
若需要使用 uni-app Android/iOS 平台的推送功能，请参考 [实现 uni-app 离线推送](https://doc.yunxin.163.com/messaging2/guide/zc4MTg5MDY?platform=client)。
:::

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

- 集成 uni-app SDK **V10.9.76** 及以上版本。
- [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#4-注册-im-账号)。
- 在 HBuilderX 开发工具中，新建了对应的 uni-app 项目。
- 调整项目开发环境，满足以下要求：

    要求 | 说明 |
    :---- | :---- |
    DevEco Studio | 5.0 及以上版本 |
    API 版本 | API 11 及以上版本 |
    uni-app | 支持 UTS 编译的版本（uni-app x） |

## 第一步：上传鸿蒙推送证书

1. 在对应客户端设备厂商的推送平台上，注册应用获取应用信息，并开启推送服务。具体请参考 [创建鸿蒙推送证书](https://doc.yunxin.163.com/messaging2/guide/TkyNTI3OTg?platform=client)。

2. 将获取到的应用信息和推送证书，上传至 [网易云信控制台](https://app.yunxin.163.com/global/home)，完成移动端设备厂商推送服务与网易云信服务的通信。

## 第二步：集成鸿蒙推送插件

鸿蒙推送插件内置于 `nim-web-sdk-ng` 中：

- `npm install nim-web-sdk-ng@">=10.9.76"` 安装 NIM SDK。
- 插件路径：`node_modules/nim-web-sdk-ng/dist/plugin/uniApp/harmony`。
- 把 uni-nimnativepush 插件需复制到 uniapp 项目 (比如说项目名叫 uni-offline-push-demo) `uni-offline-push/uni_modules/uni-nimnativepush/` 目录。
- 插件目录如下：

    ```
    uni-offline-push/uni_modules/ 项目的 uni 依赖目录
    └── uni-nimnativepush  插件名
        ├── changelog.md
        ├── package.json
        ├── readme.md
        └── utssdk  插件代码目录
            ├── app-android    AOS的接口实现-仅供调试，实现无效
            ├── app-harmony    鸿蒙系统的实现
            ├── app-ios        iOS的接口实现-仅供调试，实现无效
            ├── interface.uts  提供的接口定义
            ├── unierror.uts   错误定义
            └── web            Web的接口实现-仅供调试，实现无效
    ```

::: note note
- 推送插件必须放在 `uni_modules/` 下，否则无法被 UTS 编译识别。
- Android/iOS/Web 实现仅为调试用途，**实际生效的是 `app-harmony/` 目录下的 UTS 代码**。
- 条件编译支持鸿蒙平台：**仅 APP-HARMONY 和 APP 可命中鸿蒙平台；APP-PLUS 无法命中鸿蒙平台**。 建议鸿蒙相关逻辑用 `#ifdef APP-HARMONY` 包裹。
- 插件接口定义了在 Uni 中的一个 `NIMNativePush` 对象。`getDeviceToken` 方法支持配置和回调 token。

    ```
    interface Uni {
    NIMNativePush: {
        getDeviceToken(options: GetDeviceTokenOptions, callback: GetDeviceTokenCallback): void
    }
    }
    ```
:::

## 第三步：配置推送信息

[初始化](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client#实现初始化) 时，设置厂商的推送证书等推送配置。

:::note note
代码中厂商的证书需要和 [网易云信控制台](https://app.yunxin.163.com/global/home) 中配置的证书名称保持一致。
:::

```
let nim = V2NIM.getInstance({
  // 省略初始化配置...
})

const OFFLINE_PUSH_CONFIG = {
  // 各个 android 平台的配置
  miPush: {
    appId: '2882*****40056',
    appKey: '518*****056',
    certificateName: '***_MI_PUSH'
  },
  ...
  // ios 的配置
  apns: {
    certificateName: 'NIM****_DEV'
  },

  // 鸿蒙的配置
  harmonyPush: {
    certificateName: "DEMO_HMOS_PUSH"
  }
}

// 注意, 要在初始化后注入推送模块, 该插件已经往 uni 对象上注册了 NIMNativePush.

// #ifdef APP-HARMONY
const sysInfo = uni.getSystemInfoSync();
nim.V2NIMSettingService.setOfflinePushConfig(uni.NIMNativePush, {
  harmonyPush: {
    certificateName: "DEMO_HMOS_PUSH" // 该证书名实际的值, 该去 NIM 后台配置.
  }
})
// #endif

await nim.V2NIMLoginService.login(
  // 省略登录配置....
)
```

## 第四步：测试离线推送

### 消息发送方测试

发送消息或自定义系统通知给接收方（离线），具体的收发流程可参考 [消息收发](https://doc.yunxin.163.com/messaging2/guide/DYzMjA0Njc?platform=client) 和 [自定义系统通知收发](https://doc.yunxin.163.com/messaging2/guide/TYyNDk1ODk?platform=client)。

**发送端以发送文本消息为例，实现的示例代码如下**：

```JavaScript
const messageBeforeSend = nim.V2NIMMessageCreator.createTextMessage("一段需要被推送的脚本")
const conversationId = nim.V2NIMConversationIdUtil.p2pConversationId(
  "TARGET_ACCOUNT_ID"
)
nim.V2NIMMessageService.sendMessage(
  messageBeforeSend,
  conversationId,
  {
    // 推送配置
    "pushConfig": {
      "pushEnabled": true,
      // 固定的鸿蒙推送配置
      "pushPayload": `{"harmonyField":{"payload": {"notification": {"category": "IM","clickAction": {"actionType": 0}}},"pushOptions": {"testMessage": true}}}`
    },
    "clientAntispamEnabled": true,
    "clientAntispamReplace": "******"
  }
)
```

### 消息接收方测试

在发送方发消息前，在 uni-app 编译的原生 app 里登录 IM，然后杀死进程。

待发送方发送消息后，观察接收端能否接收到离线推送消息。

<a id="keynote"></a>

## 通用常见问题

### 调试&日志信息

```
// 成功注入插件
[NIM 818 info 1-30 15:30:15:378] setOfflinePushConfig plugin {"getDeviceToken":{}} config {"harmonyPush":{"certificateName":"DEMO_HMOS_PUSH"}}

[NIM 818 info 1-30 15:30:16:86] OfflinePushService: setToken, deviceClientId: d68efa9209c611fa3e70cb79fd5f5d0c
[NIM 818 info 1-30 15:30:16:88] OfflinePushService: setToken plugin is provided
// 成功从服务器拿到推荐通道 12, 即鸿蒙厂商通道.
[NIM 818 info 1-30 15:30:16:90] OfflinePushService: setToken pushType is:  12
[NIM 818 info 1-30 15:30:16:118] OfflinePushService: os harmonyos
// 准备去获取 deviceToken
[NIM 818 info 1-30 15:30:16:121] OfflinePushService:: prepare to get device token. suggestPushType: 12
[NIM 818 info 1-30 15:30:16:123] OfflinePushService push config {} platform UNIAPP

// 成功获取 deviceToken
15:30:16.142 [NIM 818 info 1-30 15:30:16:164] OfflinePushService:: token is :MAM0LgXL******AGQAAAAAAA************DKS7go2J9xF7*****LlnS4J
```

当出现 `os harmonyos`、`pushType is: 12`、`token is : xxxxx`（获取到有效 `deviceToken`），可视为成功。