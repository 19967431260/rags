<!-- keywords: uni-app，demo，uni-app，Uniapp，示例项目, -->

IM uni-app Demo 是基于网易云信 IM UIKit（NEUIKit）的一款 uni-app Demo，托管在 GitHub 开源代码仓库 [nim-uikit-uniapp](https://github.com/netease-kit/nim-uikit-uniapp)。该 Demo 提供了一些通用的功能，包含会话、聊天、群组等，您可以基于源码搭建您的即时通讯业务逻辑。

## 效果预览

IM uni-app Demo 的部分界面效果如下：

<img alt="Demo.png" src="https://yx-web-nosdn.netease.im/common/75c8b5c0d4028ebf6a145f32de452995/image.png" style="width:100%;border: 1px solid #BFBFBF;">

<!-- <img alt="通讯模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/895963a051a2ae1fae685cfd1682a6bf/通讯模块主要界面.png" style="width:70%;border: 1px solid #BFBFBF;">

<img alt="Demo.png" src="https://yx-web-nosdn.netease.im/common/75977dbdcc69a4d549d17aa2007a765d/Demo.png" style="width:70%;border: 1px solid #BFBFBF;">
 -->

## 平台支持

当前 IM uni-app Demo 支持：Android、iOS、H5、小程序、鸿蒙。

## 前提条件

开始跑通 Demo 之前，请确保您已完成了以下操作：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，并获取 App Key。
- [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID 和 token。
- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，为应用开通 **消息漫游** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/jU3MDY4Njk?platform=console)。

    <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/3d2c70f816a3a9b0396231b1177dabaa/image.png" style="width:80%;border: 0px solid #BFBFBF;">

- 如果需要使用呼叫组件功能，请提前在 [网易云信控制台](https://app.yunxin.163.com/global/home) 为应用开通 **多端登录** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/jU3MDY4Njk?platform=console)。

  <img src="https://yx-web-nosdn.netease.im/common/6198c84eff4ac0c63c34e95648101b59/uniapp多端登录.png" style="width:50%;border: 0px solid #BFBFBF;">

- 调整本地开发环境，并满足如下要求：

    配置项 | 要求
    ---- | ----
    集成开发环境 | HBuilderX
    Vue.js 版本 | Vue 3
    开发语言 | TypeScript
    CSS 预处理器 | Sass（Sass-loader 版本 <= 10.1.1）
    Node.js 版本 | v16 及以上
    JavaScript 包管理器 | NPM（版本请与 Node.js 版本匹配）

## 第一步：创建 uni-app 项目

在 HBuilderX IDE 环境中，创建 uni-app 项目。详细步骤请参考《uni-app 官网文档》[通过 HBuilderX 可视化界面](https://uniapp.dcloud.net.cn/quickstart-hx.html)。

如果您已创建项目，请忽略本步骤。

## 第二步：下载 Demo 源码

运行以下命令将 NEUIKit GitHub 源码项目 [nim-uikit-uniapp.git](https://github.com/netease-kit/nim-uikit-uniapp.git) 下载到您的 uni-app 项目中：

```Bash
# 找一个目录，clone 组件项目
git clone https://github.com/netease-kit/nim-uikit-uniapp.git
# 在您的项目根目录下执行以下命令，拷贝组件
mkdir -p ./pages/NEUIKit
# macOS
mv ${组件项目路径}/NEUIKit/* ./pages/NEUIKit
# windows
move ${组件项目路径}/NEUIKit/* .\pages\NEUIKit
```

下载成功后，可根据您的业务需求对源码进行修改，具体的目录结构请参考 [工程结构](https://doc.yunxin.163.com/messaging-uikit/guide/TUzODYwNDY?platform=uniapp#工程结构)。

## 第三步：添加依赖和图片引入

1. 在您的项目根目录下添加依赖和图片引入。

    ```Bash
    npm init -y
    npm i nim-web-sdk-ng@10.9.40 @xkit-yx/im-store-v2@0.8.5 @xkit-yx/utils@0.7.2 dayjs@1.11.7 mobx@6.6.1 pinyin@3.1.0 --save
    ```

    依赖 | 说明
    --- | ---
    `nim-web-sdk-ng` | [网易云信 NIM SDK](https://doc.yunxin.163.com/messaging2/concept?platform=client)，提供了一整套即时通讯基础能力。
    `@xkit-yx/im-store-v2` | store 用于 **全局状态管理**，基于 MobX 和 NIM SDK 封装的全局上下文对象，它提供了数据和 UI 之间的双向绑定能力。<br>包含多个子模块，每个子模块负责管理不同的数据领域，如会话、消息、通讯录、群组等。通过 store，您可以方便地获取数据、响应数据变化，并更新 UI。更多 store 相关信息。请参见 [全局上下文](https://doc.yunxin.163.com/messaging-uikit/guide/jE5NzM1MjY?platform=uniapp)。
    `@xkit-yx/utils` | 项目中的工具库，提供 `getFileType`、`parseFileSize` 等函数。
    `pinyin` | 主要用于好友列表的拼音排序功能。

2. 在您的项目根目录下执行以下命令，将组件需要的图片复制到 `static` 目录下，若命令执行不成功，请按照路径手动复制。

    ```Bash
    mkdir -p static
    # macOS
    cp -r pages/NEUIKit/static static/YX_IMG
    # windows
    xcopy /E pages\NEUIKit\static static\YX_IMG
    ```

3. 当前静态资源放置在网易对象存储（Netease Object Storage，NOS） 中，您可通过链接的方式在组件中进行访问。

    :::note notice
    由于访问频率有限制，建议您将静态资源放置在您的 **业务服务器** 上，然后修改 `/pages/NEUIKit/components/Icon.vue` 组件中的链接即可。
    :::

## 第四步：集成并初始化组件

### 方式一：正常集成

在您的项目 `App.vue` 文件中引入 NEUIKit 组件，参考以下代码初始化 `nim` 和 `store`。

```TypeScript
<script lang="ts">
import RootStore from '@xkit-yx/im-store-v2'
import V2NIM, { V2NIMConst } from 'nim-web-sdk-ng/dist/v2/NIM_UNIAPP_SDK'

export default {
  onLaunch() {
    const imOptions = {
      appkey: '', // 请填写您的 appkey
      account: '', // 请填写您的 account
      token: '', // 请填写您的 token
    }
    if (imOptions) {
      this.initNim(imOptions)
    } else {
      // 需要登录, 跳转登录页
    }
  },
  methods: {
    initNim(opts) {
      const isWxApp = uni.getSystemInfoSync().uniPlatform == 'mp-weixin'
      // 初始化 nim sdk
      const nim = (uni.$UIKitNIM = V2NIM.getInstance(
        {
          appkey: opts.appkey,
          needReconnect: true,
          debugLevel: 'debug',
          apiVersion: 'v2',
        },
        {
          V2NIMLoginServiceConfig: {
            lbsUrls: isWxApp
              ? ['https://lbs.netease.im/lbs/wxwebconf.jsp']
              : ['https://lbs.netease.im/lbs/webconf.jsp'],
            linkUrl: isWxApp ? 'wlnimsc0.netease.im' : 'weblink.netease.im',
            /**
             * 使用固定设备 ID，
             */
            isFixedDeviceId: true,
          },
        }
      ))
      // 初始化 store
      const store = (uni.$UIKitStore = new RootStore(
        nim,
        {
          addFriendNeedVerify: false,
          // 是否需要显示 p2p 消息、p2p 会话列表消息已读未读，默认 false
          p2pMsgReceiptVisible: true,
          // 是否需要显示群组消息已读未读，默认 false
          teamMsgReceiptVisible: true,
          teamAgreeMode:
            V2NIMConst.V2NIMTeamAgreeMode.V2NIM_TEAM_AGREE_MODE_NO_AUTH,
          /**
             发送消息前的钩子函数，异步函数,可配置推送参数、拦截消息发送等，返回 false 则不发送消息
          */
          sendMsgBefore: async (options) => {
            const pushConfig = {}
            return { ...options, pushConfig }
          },
        },
        'UniApp'
      ))

      nim.V2NIMLoginService.login(opts.account, opts.token).then(() => {
        // 跳转至您需要展示的页面
      })
    },
    logout() {},
  },
}
</script>
<style>
uni-page-body {
  height: 100%;
}
uni-page-body > uni-view {
  height: 100%;
}
</style>
```

### 方式二：ESM 集成

自 V10.3.0 版本起，IM uniapp UIKit 支持 ESM 集成方式。

NIM SDK 默认导出 UMD（Universal Module Definition）格式的产物，这种格式的文件可以在多种环境中使用。当应用对包体积有更严格的要求，例如小程序应用，则可以使用 ESM（ECMAScript Module）格式的 SDK。ESM 是 JavaScript 的原生模块系统，允许更细粒度的模块控制和更有效的打包。再配合 webpack 实现 tree-shaking（一种去除代码中未引用部分的方式），从而进一步降低 NIM SDK 产物体积。

具体请参考 [ESM 引入](https://doc.yunxin.163.com/messaging2/guide/DcyMjA1Njk?platform=client#方式二esm-引入)。

下载 [sdk-release_im_uniApp.zip](https://yx-web-nosdn.netease.im/common/84755b430d4787e8c220dd5bdd13fa69/sdk-release_im_uniApp.zip)，该示例演示如何打包生成 ESM 版本的 NIM SDK。

::: note notice
完成 ESM 集成后，将 **NEUIKit/utils/nim.ts** 文件进行如下修改：
```
// esmNim.js 为您使用示例项目打包出的缩小体积后的nim js产物
import { V2NIMConst } from '../esmNim.js'
export { V2NIMConst }
```
:::

## 第五步：配置路由

1. 在 `pages/NEUIKit/utils/customNavigate.ts` 中，修改 `preUrl`：

    ```JavaScript
    const preUrl = '/pages/NEUIKit'
    ```

2. 在您项目的 `pages.json` 文件中的更新 `pages` 路由：

    :::note note
    以下是 IM UIKit 的所有页面路由，您可根据项目需要，选择适当的页面路由。具体的路由介绍请参考 [路由页面介绍](https://doc.yunxin.163.com/messaging-uikit/guide/TUzODYwNDY?platform=uniapp)。
    :::

    ```JSON
    {
      "pages": [
        {
          "path": "pages/NEUIKit/pages/Conversation/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/index/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Conversation/conversation-search/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Login/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/index",
          "style": {
            "navigationBarBackgroundColor": "#F6F8FA",
            "navigationBarTextStyle": "black",
            "navigationStyle": "custom",
            "enablePullDownRefresh": false,
            "app-plus": {
              "softinputNavBar": "none",
              "bounce": "none"
            }
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/video-play",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/message/p2p-set",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/message/pin-list",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/forward",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Chat/message-read-info",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-info-edit",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-name-edit",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-intro-edit",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-avatar-edit",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/nick-in-team",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-manage",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/transform-team",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/team-manager-list",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-set/add-team-manager",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-member/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-create/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Team/team-add/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Contact/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Contact/contact-list/group-list",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Contact/contact-list/valid-list",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/Contact/contact-list/black-list",
          "style": {
            "navigationStyle": "custom"
          }
        },

        {
          "path": "pages/NEUIKit/pages/User/friend/add-friend",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/friend/friend-edit",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/friend/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my/about",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my/setting",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my/collection-card",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my/collection-list",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/my-detail/index",
          "style": {
            "navigationStyle": "custom"
          }
        },
        {
          "path": "pages/NEUIKit/pages/User/detail-item/index",
          "style": {
            "navigationStyle": "custom"
          }
        }
      ],
      "globalStyle": {
        "navigationBarTextStyle": "black"
      },
      "tabBar": {
        "backgroundColor": "#F6F8FA",
        "color": "#999999",
        "selectedColor": "#337EFF",
        "height": "60px",
        "list": [
          {
            "text": "消息",
            "iconPath": "static/YX_IMG/conversation.png",
            "selectedIconPath": "static/YX_IMG/conversation-selected.png",
            "pagePath": "pages/NEUIKit/pages/Conversation/index"
            },
            {
            "text": "通讯录",
            "iconPath": "static/YX_IMG/contact.png",
            "selectedIconPath": "static/YX_IMG/contact-selected.png",
            "pagePath": "pages/NEUIKit/pages/Contact/index"
            },
            {
            "text": "我的",
            "pagePath": "pages/NEUIKit/pages/User/my/index",
            "iconPath": "static/YX_IMG/me.png",
            "selectedIconPath": "static/YX_IMG/me-selected.png"
            }
        ]
      }
    }
    ```

## 第六步：运行 Demo

在 uni-app IDE 中，运行 Demo：

<img alt="运行.png" src="https://yx-web-nosdn.netease.im/common/7e0fcdab7514cc6927333c8368f6c69d/运行.png" style="width:50%;border: 1px solid #BFBFBF;">

<!--
<img alt="uniappRunning.png" src="https://yx-web-nosdn.netease.im/common/a3e1c7033741fe848365871654d1adf4/uniappRunning.png" style="width:80%;border: 1px solid #BFBFBF;">
-->

## 自定义开发

### API 参考

IM uni-app Demo 基于 `UIKitStore` 开发，相关 API 详情请参考 [UIKitStore](https://doc.yunxin.163.com/messaging2/references/web/typedoc//IMUIKit/Latest/modules.html)。

例如，您想获取 IM uni-app UIKit 的会话未读数，示例代码如下：

```JavaScript
uni.$UIKitStore.conversationStore.totalUnreadCount
```

### 使用原生 SDK 中的方法

如果您需要自行实现目前 uni-app UIKit 还未实现，但原生的 [IM uni-app SDK](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client) 已提供的能力。您可以通过调用原生 IM uni-app SDK 中提供的接口来实现。原生 uni-app SDK 中的 API，请参考 [NIM Web SDK](https://doc.yunxin.163.com/messaging2/client-apis?platform=client)。

<!--
```JavaScript
uni.$UIKitNIM = new NimKitCore({
    initOptions: {
      appkey: '',
      lbsUrls: isWeixinApp
        ? ['https://lbs.netease.im/lbs/wxwebconf.jsp']
        : ['https://lbs.netease.im/lbs/webconf.jsp'],
      linkUrl: isWeixinApp ? 'wlnimsc0.netease.im' : 'weblink.netease.im',
      needReconnect: true,
      /**
       * 使用固定设备 ID，
       */
      isFixedDeviceId: true,
      // "reconnectionAttempts": 5,
      debugLevel: 'debug',
      ...opts,
    },
    platform: 'UniApp',
  })
```

const nim = (uni.$UIKitNIM = new NimKitCore({
      initOptions: {
        appkey: "", // 请填写您的 appkey
        account: "", // 请填写您的 account
        token: "", // 请填写您的 token
        lbsUrls: isWeixinApp
          ? ["https://lbs.netease.im/lbs/wxwebconf.jsp"]
          : ["https://lbs.netease.im/lbs/webconf.jsp"],
        linkUrl: isWeixinApp ? "wlnimsc0.netease.im" : "weblink.netease.im",
        needReconnect: true,
        /**
         * 使用固定设备 ID，
         */
        isFixedDeviceId: true,
        // "reconnectionAttempts": 5,
        debugLevel: "debug",
      },
      platform: "UniApp",
    })); -->

例如，您想对 IM uni-app UIKit 的消息历史进行全文检索（按时间分页搜索），可以调用原生 SDK 中的 `msgFtsInServerByTiming` 方法，示例代码如下：

```JavaScript
uni.$UIKitNIM.nim.searchCloudMessages({
  keyword: '您好',
})
```

:::note note
以上示例中的 `uni.$UIKitNIM.nim` 为原生 NIM uni-app SDK 的实例。
:::

## 常见问题

集成过程中如果遇到任何问题，请 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师或参考 [常见问题](https://doc.yunxin.163.com/messaging-uikit/guide/zE1MTg1NTg?platform=uniapp)。