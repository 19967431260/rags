网易云信 IM SDK（NetEase Instant Messaging SDK，简称 NIM SDK）为开发者提供完善的即时通讯能力，精心屏蔽了底层复杂实现细节，向外呈现简洁易用的 API，助您轻松快速地将即时通讯功能整合到应用中。

本文介绍如何快速将 NIM SDK 集成到您的项目中，开启高效通讯体验。

<style>
table th:first-of-type {width: 20%;}
table th:nth-of-type(2) {width: 20%;}
table th:nth-of-type(3) {width: 20%;}
table th:nth-of-type(4) {width: 20%;}
table th:nth-of-type(5) {width: 20%;}
</style>


::: note note 
本文主要介绍底层 Web/uni-app/小程序/RN SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 Web UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/jMzMzQ0MDk?platform=web) | [集成 uni-app UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp) | [集成 H5 UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/zIzOTk1MDI?platform=h5)。
:::

## 环境支持

NIM SDK 全面支持以下开发环境，更详细的版本信息，请参考 [平台兼容性](https://doc.yunxin.163.com/messaging2/concept/TkzNDE2MzA?platform=client#web-%E4%B8%8E%E8%B7%A8%E5%B9%B3%E5%8F%B0%E6%A1%86%E6%9E%B6)：

| 平台 | Web 浏览器 | uni-app | 小程序 | React Native |
| --- | --- | --- | --- | ---
| **环境要求** | - 微软 IE（11+） | uin-app 支持的编译产物： | - 微信小程序 | React Native |\
|  | - 谷歌 Chrome（7+） | - iOS、Android、鸿蒙| - 支付宝小程序 | |\
|  | - 微软 Edge（12+） | - 微信、阿里小程序| - 百度小程序 | |\
|  | - Mozilla Firefox（11＋） | - web（推荐 chrome 浏览器） | - 抖音小程序 | |\
|  | - 苹果 Safari（5+） | | | |

<a id="Demo"></a>

## 体验 Demo

立即下载演示应用，体验 NIM SDK 的核心功能：

| Web/uni-app/小程序 | React Native |
| --- | --- |
| 目前仅提供 IM SDK API Sample，演示如何调用和使用 API 实现 IM 功能，并进行渲染，具体请参考 [nim-web-samples](https://github.com/netease-im/nim-web-samples)  | 包含账号登录、会话列表、消息面板、发送消息功能的含 UI Demo，请下载 [NIM_RN_DEMO.zip](https://yx-web-nosdn.netease.im/common/059ebc5f7f191a29805ffa79a8d04daf/NIM_RN_DEMO.zip) 进行体验

## 域名配置

本配置步骤仅适用于小程序项目及最终编译为小程序的 uni-app 项目：

- 请登录 [微信公众平台](https://mp.weixin.qq.com/?token=&lang=zh_CN)，依次进入 **小程序后台 > 开发 > 开发设置 > 服务器域名**，将以下域名添加至对应的 **request 合法域名**、**socket 合法域名**、**uploadFile 合法域名**、**downloadFile 合法域名** 中。详细配置指南请参考《微信官方文档》[配置服务器域名](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html)。

- 若您需要在支付宝环境运行小程序，请前往 [支付宝开放平台](https://open.alipay.com/module/miniApp) 进行相应域名配置。

    配置分类 | 域名 | 说明
    ---- | ---- | ----
    request 合法域名 | https://lbs.netease.im | 请求 LBS 地址。
    ^^ | https://wlnimsc0.netease.im | IM 必需。
    ^^ | https://wlnimsc0.netease.im:443 | IM 必需。
    ^^ | https://wlnimsc1.netease.im | 聊天室必需。
    ^^ | https://wlnimsc1.netease.im:443 | 聊天室必需。
    ^^ | https://statistic.live.126.net | 数据上报。
    ^^ | https://abt-online.netease.im | 用于 A/B Test。
    socket 合法域名 | wss://wlnimsc0.netease.im | IM 必需。
    ^^ | wss://wlnimsc1.netease.im | 聊天室必需。
    uploadFile 合法域名 | https://oss.chatnos.com | 文件上传，如发送文件类消息。
    ^^ | https://fileup.chatnos.com | ^^
    ^^ | https://nos.netease.com | ^^
    ^^ | https://upload.chatnos.com | ^^ 
    downloadFile 合法域名 | https://nim-nosdn.netease.im | 文件下载，如下载语音。
    ^^ | https://nim.nosdn.127.net | ^^

## 方式一：正常集成

1. 通过如下 NPM 命令安装最新版 SDK：

    ```NPM
    npm install nim-web-sdk-ng@">=10"
    ```

2. 通过 `import` 或者 `require` 引入入口模块。根据开发环境不同，您应该选择不同的产物。

    :::::: div linked-codes
    ::: code Web 浏览器
    ```TypeScript
    // 引入方式一：引入默认路径
    import NIM from 'nim-web-sdk-ng'
    // 引入方式二：指定引入路径。该路径等效于默认路径
    import NIM from 'nim-web-sdk-ng/dist/v2/NIM_BROWSER_SDK'

    // 业务场景对应关系：
    // IM 浏览器 - NIM_BROWSER_SDK - NIM.getInstance
    // Chatroom 浏览器 - CHATROOM_BROWSER_SDK - CHATROOM.newInstance
    ```
    :::
    ::: code uni-app
    ```TypeScript
    import NIM from 'nim-web-sdk-ng/dist/v2/NIM_UNIAPP_SDK'

    // 业务场景对应关系：
    // IM uni-app - NIM_UNIAPP_SDK - NIM.getInstance
    // Chatroom uni-app - CHATROOM_UNIAPP_SDK - CHATROOM.newInstance
    ```
    :::
    ::: code 小程序
    ```TypeScript
    // 由于小程序构建 NPM 之后，只有默认路径文件才会被复制到 `miniprogram_npm` 中，
    // 而 IM SDK 小程序包不是默认路径。因此，您需要将 `nim-web-sdk-ng/dist/v2`
    // 拷贝到项目的其它目录中，然后引入：

    import NIM from '{相对路径}/NIM_MINIAPP_SDK'

    // 业务场景对应关系：
    // IM 小程序 - NIM_MINIAPP_SDK - NIM.getInstance
    // Chatroom 小程序 - CHATROOM_MINIAPP_SDK - CHATROOM.newInstance
    ```
    :::
    ::: code React Native
    ```TypeScript
    import NIM, { V2NIM } from 'nim-web-sdk-ng/dist/v2/NIM_RN_SDK'

    // 业务场景对应关系：
    // IM React Native - NIM_RN_SDK - NIM.getInstance
    // Chatroom React Native - CHATROOM_RN_SDK - CHATROOM.newInstance
    ```
    :::
    ::::::

## 方式二：ESM 引入

当应用对包体积有更严格的要求，例如小程序应用，可以使用 ESM（ECMAScript Module）格式的 SDK。ESM 是 JavaScript 的原生模块系统，允许更细粒度的模块控制和更有效的打包。再配合 webpack 实现 tree-shaking（一种去除代码中未引用部分的方式），从而进一步降低 NIM SDK 产物体积。

[下载 NIM SDK](https://doc.yunxin.163.com/messaging2/resource?platform=web) 后，ESM 产物路径在 `nim-web-sdk-ng/dist/esm/nim.js` 中。截至 [10.5.0 NIM SDK](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1050-2024-10-15)，ESM 产物导出了所有 V2NIM 模块，共有 550kb，只引入消息与会话有关的功能模块则约为 400kb。有关 ESM 引入并集成的完整示例，请参考以下的演示示例：

::: note note
以下示例仅演示如何通过 ESM 方式引入 NIM SDK。
:::

- Web 浏览器示例：[browser.zip](https://yx-web-nosdn.netease.im/common/6fe6c595cf5ad73bc790e94880b59f9c/browser.zip) 
- uni-app 示例：[uniApp.zip](https://yx-web-nosdn.netease.im/sdk-release/im/uniApp.zip) 
- 微信小程序示例：[wxMiniApp.zip](https://yx-web-nosdn.netease.im/sdk-release/im/wxMiniApp.zip) 

1. 选择适配器，以确保 NIM SDK 能在不同环境中正确运行。

    - `browserAdapters`：为浏览器环境准备的适配器。如果您的代码需要在浏览器中运行，可能需要一些特定的适配代码来处理不同浏览器之间的兼容性问题。
    - `uniAppAdapters`：为 uni-app 框架准备的适配器。uni-app 是一个使用 Vue.js 开发跨平台应用的前端框架，可以编译到 iOS、Android、鸿蒙、Web（包括 PC 和移动端）、以及各种小程序（微信/支付宝/百度等）平台。
    - `wxAdapters`：为微信小程序准备的适配器。
    - `aliAdapters`：为支付宝小程序准备的适配器。
    - `baiduAdapters`：为百度小程序准备的适配器。
    - `ttAdapters`：为抖音小程序准备的适配器。

    :::::: div linked-codes
    ::: code Web 浏览器
    ```JavaScript
    /** lib.js */
    import { NIM, setAdapters, browserAdapters, V2NIMMessageService, V2NIMLocalConversationService, V2NIMConst } from 'nim-web-sdk-ng/dist/esm/nim'

    // 设置浏览器环境的适配器
    setAdapters(browserAdapters)
    ```
    :::
    ::: code uni-app
    ```JavaScript
    /** lib.js */
    import { NIM, setAdapters, uniAppAdapters, V2NIMMessageService, V2NIMLocalConversationService, V2NIMConst } from 'nim-web-sdk-ng/dist/esm/nim'

    // 设置 uni-app 环境的适配器
    setAdapters(uniAppAdapters)
    ```
    :::
    ::: code 小程序
    ```JavaScript
    /** lib.js */
    // 根据小程序环境选择对应的适配器
    import { NIM, setAdapters, wxAdapters, V2NIMMessageService, V2NIMLocalConversationService, V2NIMConst } from 'nim-web-sdk-ng/dist/esm/nim'

    // 微信小程序
    setAdapters(wxAdapters)

    // 其他小程序环境请使用对应适配器：
    // 支付宝小程序: aliAdapters
    // 百度小程序: baiduAdapters
    // 抖音小程序: ttAdapters
    ```
    :::
    ::: code React Native
    ```JavaScript
    /** lib.js */
    import { NIM, setAdapters, V2NIMMessageService, V2NIMLocalConversationService, V2NIMConst } from 'nim-web-sdk-ng/dist/esm/nim'

    // React Native 环境一般无需考虑包体积问题，不需要特殊适配器，此处仅列出以作参考
    ```
    :::
    ::::::

2. 调用 `registerService` 注册所需模块，以及环境变量。可供注册的模块如下：

    - `V2NIMLocalConversationService`：本地会话模块。
    - `V2NIMConversationService`：云端会话模块。
    - `V2NIMConversationGroupService`：云端会话分组模块。
    - `V2NIMMessageService`：消息模块。包含发送消息等功能。
        - `V2NIMMessageLogUtil`：消息记录相关工具类。包含查询消息历史等功能。
        - `V2NIMMessageExtendUtil`：扩展功能。包含 pin 消息，收藏消息等功能。
        - `V2NIMMessageConverter`：消息序列化能力。
    - `V2NIMStorageService`：云端存储模块，包含上传文件能力。
    - `V2NIMTeamService`：群组模块。
    - `V2NIMUserService`：用户模块。
    - `V2NIMFriendService`：好友模块。
    - `V2NIMNotificationService`：通知模块服务。
    - `V2NIMSettingService`：设置模块。包含推送配置，会话免打扰设置等。
    - `V2NIMAIService`：AI 数字人模块。
    - `V2NIMSignallingService`：信令模块。
    - `V2NIMSubscriptionService`：用户状态订阅模块，如上下线状态通知订阅。
    - `V2NIMPassthroughService`：服务代理相关。

    ```JavaScript
    /**
    * 消息模块.
    *
    * 影响 API 包含 V2NIMMessageService 下全部接口.
    */
    NIM.registerService(V2NIMMessageService, 'V2NIMMessageService')

    /**
    * 消息模块-消息记录相关工具类. 包含查询消息历史等功能.
    *
    * 影响 API 包含 V2NIMMessageService 的部分接口, 举例:
    *   getMessageList, getMessageListEx,
    *   getMessageListByRefers, clearHistoryMessage
    */
    NIM.registerService(V2NIMMessageLogUtil, 'V2NIMMessageLogUtil')

    /**
    * 消息模块-扩展功能. 包含 pin 消息, 收藏消息等功能
    *
    * 影响 API 包含 V2NIMMessageService 的部分接口, 举例:
    *   pinMessage, unpinMessage, updatePinMessage, voiceToText,
    *   getPinnedMessageList, addQuickComment, removeQuickComment, getQuickCommentList, addCollection,
    *   removeCollections, updateCollectionExtension, getCollectionListByOption,
    *   getCollectionListExByOption, searchCloudMessages, searchCloudMessagesEx
    */
    NIM.registerService(V2NIMMessageExtendUtil, 'V2NIMMessageExtendUtil')

    /**
    * 消息序列化与反序列化工具
    *
    * 影响 API 包含 V2NIMMessageConverter 的全部接口.
    */
    NIM.registerService(V2NIMMessageConverter, 'V2NIMMessageConverter')

    /**
    * 云端存储模块, 包含上传文件能力
    *
    * 影响 API 包含 V2NIMMessageService 的部分接口, 举例:
    *   V2NIMMessageService.sendMessage (发图片/文件类型的消息时)
    *   V2NIMMessageService.cancelMessageAttachmentUpload (取消文件消息的上传)
    *
    * 影响 API 包含 V2NIMStorageService 的全部接口.
    */
    NIM.registerService(V2NIMStorageService, 'V2NIMStorageService')

    /**
    * 云端会话模块.
    *
    * 影响 API 包含 V2NIMConversationService 的全部接口.
    */
    NIM.registerService(V2NIMConversationService, 'V2NIMConversationService')

    /**
    * 云端会话分组模块.
    *
    * 影响 API 包含 V2NIMConversationGroupService 的全部接口.
    */
    NIM.registerService(V2NIMConversationGroupService, 'V2NIMConversationGroupService')

    /**
    * 本地会话模块.
    *
    * 影响 API 包含 V2NIMLocalConversationService 的全部接口.
    */
    NIM.registerService(V2NIMLocalConversationService, 'V2NIMLocalConversationService')

    /**
    * 群组模块.
    *
    * 影响 API 包含 V2NIMSettingService 的部分接口, 举例:
    *   setTeamMessageMuteMode, getTeamMessageMuteMode, getAllTeamMessageMuteMode
    *
    * 影响 API 包含 V2NIMTeamService 的全部接口.
    */
    NIM.registerService(V2NIMTeamService, 'V2NIMTeamService')

    /**
    * 用户模块.
    *
    * 影响 API 包含 V2NIMSettingService 的部分接口, 举例:
    *   getConversationMuteStatus, setP2PMessageMuteMode
    *
    * 影响 API 包含 V2NIMUserService 的全部接口.
    */
    NIM.registerService(V2NIMUserService, 'V2NIMUserService') // 用户模块

    /**
    * 好友模块.
    *
    * 影响 API 包含 V2NIMFriendService 的全部接口.
    */
    NIM.registerService(V2NIMFriendService, 'V2NIMFriendService')

    /**
    * 通知模块.
    *
    * 影响 API 包含 V2NIMNotificationService 的全部接口.
    */
    NIM.registerService(V2NIMNotificationService, 'V2NIMNotificationService')

    /**
    * 设置模块.
    *
    * 影响 API 包含 V2NIMSettingService 的全部接口.
    * - 包含推送配置, 会话免打扰设置.
    * - 与会话免打扰有关的设置需要引入群, 用户模块
    */
    NIM.registerService(V2NIMSettingService, 'V2NIMSettingService')

    /**
    * AI 数字人模块.
    *
    * 影响 API 包含 V2NIMMessageService 的部分接口与事件:
    *   sendMessage (发送参数 aiConfig, 配置 AI 相关)
    *   onReceiveMessages (收消息事件, 回调的 V2NIMMessage 消息体参考属性 aiConfig 与 streamConfig 流式输出)
    *   onReceiveMessagesModified (消息更新事件, 回调的 V2NIMMessage 消息体参考属性 aiConfig 与 streamConfig 流式输出)
    *
    * 影响 API 包含 V2NIMAIService 的全部接口.
    */
    NIM.registerService(V2NIMAIService, 'V2NIMAIService')

    /**
    * 订阅模块, 如上下线状态通知订阅.
    *
    * 影响 API 包含 V2NIMSubscriptionService 的全部接口.
    */
    NIM.registerService(V2NIMSubscriptionService, 'V2NIMSubscriptionService')

    /**
    * 信令模块
    *
    * 影响 API 包含 V2NIMSignallingService 的全部接口.
    */
    NIM.registerService(V2NIMSignallingService, 'V2NIMSignallingService')

    /**
    * 服务代理相关
    *
    * 影响 API 包含 V2NIMPassthroughService 的全部接口.
    */
    NIM.registerService(V2NIMPassthroughService, 'V2NIMPassthroughService')

    /**
    * 此外某些模块包含工具类, 只需要引入对应模块服务, 就能直接使用该工具类, 关系如下
    *
    * V2NIMConversationIdUtil(会话 ID 工具类) => V2NIMMessageService, V2NIMConversationService
    * V2NIMClientAntispamUtil(客户端反垃圾工具类) => V2NIMMessageService
    * V2NIMMessageCreator(消息构造工具类) => V2NIMMessageService
    */

    export { NIM, V2NIMConst }
    ```

3. 构建和引入。

    :::::: div linked-codes
    ::: code Web 浏览器
    浏览器环境，开发者已经使用 webpack 或 rollup 等现代打包工具的，可以直接引入上文的 `lib.js`。

    ```JavaScript
    import { NIM, V2NIMConst } from './lib'

    const nim = NIM.getInstance({
    appkey: 'YOUR_Netease_IM_APPKEY',
    debugLevel: 'debug',
    apiVersion: 'v2'
    })
    ```
    :::
    ::: code uni-app
    uni-app 环境需要提前 tree-shaking 构建，引入构建后的产物。

    ```JavaScript
    import { NIM, V2NIMConst } from './dist/nim'

    const nim = NIM.getInstance({
    appkey: 'YOUR_Netease_IM_APPKEY',
    debugLevel: 'debug',
    apiVersion: 'v2'
    })
    ```
    :::
    ::: code 小程序
    小程序环境需要提前 tree-shaking 构建，引入构建后的产物。

    ```JavaScript
    import { NIM, V2NIMConst } from './dist/nim'

    const nim = NIM.getInstance({
    appkey: 'YOUR_Netease_IM_APPKEY',
    debugLevel: 'debug',
    apiVersion: 'v2'
    }, {
    V2NIMLoginServiceConfig: {
        "lbsUrls": [
        "https://lbs.netease.im/lbs/wxwebconf.jsp"
        ],
        "linkUrl": "wlnimsc0.netease.im"
    }
    })
    ```
    :::
    ::: code React Native
    React Native 环境一般无需考虑包体积问题，此处仅列出以作参考

    ```JavaScript
    import { NIM, V2NIMConst } from './dist/nim'

    const nim = NIM.getInstance({
    appkey: 'YOUR_Netease_IM_APPKEY',
    debugLevel: 'debug',
    apiVersion: 'v2'
    })
    ```
    :::
    ::::::

## 初始化实例

将 NIM SDK 集成到客户端后，您需要先完成 NIM 实例的初始化才能使用其他功能。

:::::: div linked-codes
::: code Web 浏览器
```TypeScript
const nim = NIM.getInstance({
  appkey: "YOUR_Netease_IM_APPKEY",
  debugLevel: "debug",
  apiVersion: "v2"
})
```
:::
::: code uni-app
根据 uni-app 最终编译应用的运行环境，选择对应的初始化方式：

- **运行在非小程序环境**：

    ```TypeScript
    const nim = NIM.getInstance({
    appkey: "YOUR_Netease_IM_APPKEY",
    debugLevel: "debug",
    apiVersion: "v2"
    })
    ```

- **运行在小程序环境**：

    ```TypeScript
    const nim = NIM.getInstance({
    appkey: "YOUR_Netease_IM_APPKEY",
    debugLevel: "debug",
    apiVersion: "v2"
    }, {
    V2NIMLoginServiceConfig: {
        "lbsUrls": [
        "https://lbs.netease.im/lbs/wxwebconf.jsp"
        ],
        "linkUrl": "wlnimsc0.netease.im"
    }
    })
    ```
:::
::: code 小程序
```TypeScript
const nim = NIM.getInstance({
  appkey: "YOUR_Netease_IM_APPKEY",
  debugLevel: "debug",
  apiVersion: "v2"
}, {
  V2NIMLoginServiceConfig: {
    "lbsUrls": [
      "https://lbs.netease.im/lbs/wxwebconf.jsp"
    ],
    "linkUrl": "wlnimsc0.netease.im"
  }
})
```
:::
::: code React Native
```TypeScript
class NIMStore {
  nim: V2NIM | null = null
  isInitialized: boolean = false

  constructor() {
    makeAutoObservable(this)
    this.initNIM()
  }

  // 初始化 NIM 实例
  initNIM = async () => {
    try {
      const nimInstance: V2NIM = NIM.getInstance(
        {
          appkey: 'YOUR_Netease_IM_APPKEY',
          debugLevel: 'debug',
          apiVersion: 'v2',
          enableV2CloudConversation: true,
          binaryWebsocket: false
        }
      )

      runInAction(() => {
        this.nim = nimInstance
        this.isInitialized = true
      })
    } catch (error) {
      console.error('NIM 实例初始化失败', error)
    }
  }
}
```
:::
::::::

## 登录和消息发送

登录 NIM 并发送消息的示例代码：

```TypeScript
// 监听登录状态变化
nim.V2NIMLoginService.on('onLoginStatus', function(arg1) {
  console.log('收到 V2NIMLoginService 模块的 onLoginStatus 事件', arg1)
})

// 登录
await nim.V2NIMLoginService.login("YOUR_ACCOUNT", "YOUR_TOKEN")

// 创建并发送文本消息
const message = nim.V2NIMMessageCreator.createTextMessage("hello")
const res = await nim.V2NIMMessageService.sendMessage(message, 'YOUR_ACCOUNT|1|RECEIVER_ACCOUNT')
```

## 下一步

完成 SDK 集成后，请参考 [初始化](https://doc.yunxin.163.com/messaging2/docs/zY4OTcyODQ?platform=client) 和 [登录 IM](https://doc.yunxin.163.com/messaging2/docs/Dk1MTY4MzA?platform=client) 进行集成开发。