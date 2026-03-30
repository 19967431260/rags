<!-- keywords: uni-app，demo，uniapp，Uniapp，示例项目, -->

IM uni-app Demo 是基于网易云信 IM UIKit（NEUIKit）的一款 uni-app Demo，托管在 GitHub 开源代码仓库 [nim-uikit-uniapp](https://github.com/netease-kit/nim-uikit-uniapp)。该 Demo 提供了一些通用的功能，包含会话、聊天、群组等，您可以基于源码搭建您的即时通讯业务逻辑。本文描述适用于 Vue.js 2.x 版本项目。

## 版本说明

- v1.0.0 ~ v1.5.1 版本 IM UIKit 底层适配了 <a href="https://doc.yunxin.163.com/messaging/concept/zcyNTgyMzE?platform=client">uni-app 0.1x.x NIM SDK</a>。其中 V9 概指低于 V10  系列 NIM SDK 的版本。

- 网易云信即时通讯 UIKit 适配 uni-app 开发框架的全新 10.0.1 版本已发布。底层适配了 [NIM Web SDK v10.4.0](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1040-2024-08-21)。新版不仅承袭了前代的优质特性，更融入了多项创新技术与用户反馈，致力于提供更流畅、更稳定的即时通讯沟通解决方案。如何集成新版 UIKit，请参考《开发指南（V10）》[快速集成 uni-app 源码（Vue 3）](https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp)。

## 效果预览

IM uni-app Demo 的部分界面效果如下：

<img alt="Demo.png" src="https://yx-web-nosdn.netease.im/common/75c8b5c0d4028ebf6a145f32de452995/image.png" style="width:100%;border: 1px solid #BFBFBF;">

<!-- <img alt="通讯模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/895963a051a2ae1fae685cfd1682a6bf/通讯模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

<img alt="Demo.png" src="https://yx-web-nosdn.netease.im/common/75977dbdcc69a4d549d17aa2007a765d/Demo.png" style="width:80%;border: 1px solid #BFBFBF;"> -->

## 平台支持

当前 IM uni-app Demo 支持：Android、iOS、H5、小程序。

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
    Vue.js 版本 | Vue 2 <note type="note">Vue 2 暂时不支持 vue cli 创建的工程集成。</note>
    开发语言 | TypeScript
    CSS 预处理器 | Sass（Sass-loader 版本 <= 10.1.1）
    Node.js 版本 | 12.13.0 ~ 17.0.0（推荐 LTS 版本 16.17.0）
    JavaScript 包管理器 | NPM（版本请与 Node.js 版本匹配）

## 第一步：创建 uni-app 项目

创建 uni-app 项目，详情参考 [uni-app 官网](https://uniapp.dcloud.net.cn/quickstart-hx.html)。

如已创建项目，请忽略本步骤。

## 第二步：下载 Demo 源码

运行以下命令将 NEUIKit GitHub 源码项目下载到您的 uni-app 项目中：

- V10 源码地址：[nim-uikit-uniapp.git](https://github.com/netease-kit/nim-uikit-uniapp/tree/main)
- V9 源码地址：[nim-uikit-uniapp.git](https://github.com/netease-kit/nim-uikit-uniapp/tree/release/1.5.0)

```Bash
# 找一个目录，clone IMUIKit 组件项目，使用 V9 需要将分支切至 1.5.0 版本
git clone https://github.com/netease-kit/nim-uikit-uniapp

# 在您的项目根目录下执行以下命令，拷贝组件
mkdir -p ./pages/NEUIKit

# macOS
mv ${IMUIKit 组件项目路径}/NEUIKit/* ./pages/NEUIKit
# windows
move ${IMUIKit 组件项目路径}/NEUIKit/* .\pages\NEUIKit
```

下载成功后，目录结构如下图所示：

<img src="https://yx-web-nosdn.netease.im/common/4f2809cf96faec6fc646d8a05f3b17f3/vue2目录.png" style="width:50%;border: 1px solid #BFBFBF;">

## 第三步：添加依赖和图片引入

1. 在您的项目根目录下添加依赖和图片引入。

    ```Bash
    npm init -y
    npm i @xkit-yx/core-kit@0.14.3 @xkit-yx/im-store@0.4.5 @xkit-yx/utils@0.5.6 dayjs@1.11.7 mobx@6.6.1 pinyin@3.1.0 --save
    npm i unplugin-vue2-script-setup @vue/composition-api
    ```

2. 在您的项目根目录下执行以下命令，将组件需要的图片复制到 `static` 目录下，若命令执行不成功，请按照路径手动复制。

    ```Bash
    mkdir -p static
    ```

3. 当前静态资源放置在网易对象存储（Netease Object Storage，NOS） 中，您可通过链接的方式在组件中进行访问。

    :::note notice
    由于访问频率有限制，建议您将静态资源放置在您的 **业务服务器** 上，然后修改组件中的链接即可。
    :::

    ```Bash
    # macOS
    cp -r pages/NEUIKit/static static/YX_IMG
    # windows
    xcopy /E pages\NEUIKit\static static\YX_IMG
    ```

4. 在根目录下创建 `vue.config.js`。

    ```JavaScript
    const ScriptSetup = require('unplugin-vue2-script-setup/webpack').default;
    module.exports = {
      parallel: false,
      configureWebpack: {
        plugins: [
          ScriptSetup({
            /* options */
          }),
        ],
      },
      chainWebpack(config) {
        // disable type check and let `vue-tsc` handles it
        config.plugins.delete('fork-ts-checker');
      },
    };
    ```

## 第四步：引入并初始化组件

### 初始化 NEUIKit 组件

1. 在您的项目 App.vue 文件中引入 NEUIKit 组件并进行初始化。

    ```JSX
    <script>
    import RootStore from '@xkit-yx/im-store'
    import { NimKitCore } from '@xkit-yx/core-kit/dist/uniapp-nim-core'
    import { getMsgContentTipByType } from './pages/NEUIKit/utils/msg'
    import { getUniPlatform } from './pages/NEUIKit/utils'
    // #ifdef APP-PLUS
    const nimPushPlugin = uni.requireNativePlugin('NIMUniPlugin-PluginModule')
    // #endif
    export default {
      onLaunch: function () {
        const isWeixinApp = getUniPlatform() === 'mp-weixin'
        // @ts-ignore
        const nim = uni.$UIKitNIM = new NimKitCore({
          initOptions: {
            "appkey": "", // 请填写您的 appkey
            "account": "", // 请填写您的 account
            "token": "", // 请填写您的 token
            "lbsUrls": isWeixinApp ? [
              "https://lbs.netease.im/lbs/wxwebconf.jsp"
            ] : [
              "https://lbs.netease.im/lbs/webconf.jsp"
            ],
            "linkUrl": isWeixinApp ? 'wlnimsc0.netease.im' : 'weblink.netease.im',
            "needReconnect": true,
            /**
            * 使用固定设备 ID，
            */
            isFixedDeviceId: true,
            // "reconnectionAttempts": 5,
            debugLevel: 'debug',
          },
          platform: 'UniApp',
        })
        // @ts-ignore
        const store = uni.$UIKitStore = new RootStore(nim, {
          addFriendNeedVerify: false,
          teamBeInviteMode: 'noVerify',
          teamJoinMode: 'noVerify',
          teamUpdateExtMode: 'all',
          teamUpdateTeamMode: 'all',
          teamInviteMode: 'all',
          sendMsgBefore: async (options, type) => {
            const pushContent = getMsgContentTipByType({ body: options.body, type })
            const yxAitMsg = options.ext ? options.ext.yxAitMsg : { forcePushIDsList: '[]', needForcePush: false }

            // 如果是 at 消息，需要走离线强推
            const { forcePushIDsList, needForcePush } = yxAitMsg
              // @ts-ignore
              ? store.msgStore._formatExtAitToPushInfo(yxAitMsg, options.body)
              : { forcePushIDsList: '[]', needForcePush: false }

            console.log('forcePushIDsList: ', forcePushIDsList)

            // 不同产商的推送消息体
            const { scene, to } = options
            const pushPayload = JSON.stringify({
              // oppo
              oppoField: {
                "click_action_type": 4, // 参考 oppo 官网
                "click_action_activity": '', // 各端不一样 TODO
                "action_parameters": { "sessionId": scene, "sessionType": to } // 自定义
              },

              // vivo
              vivoField: {
                "pushMode": 0 //推送模式 0：正式推送。1：测试推送，不填默认为 0。
              },

              // huawei
              hwField: {
                click_action: {
                  'type': 1,
                  'action': '' // 各端不一样 TODO
                },
                androidConfig: {
                  'category': 'IM',
                  'data': JSON.stringify({ 'sessionId': to, 'sessionType': scene })
                }
              },

              // 通用
              sessionId: to,
              sessionType: scene
            })

            const pushInfo = {
              needPush: true,
              needPushBadge: true,
              pushPayload: '{}',
              pushContent,
              needForcePush,
              forcePushIDsList,
              forcePushContent: pushContent,
            }
            return { ...options, pushInfo }
          },
        })
        // #ifdef APP-PLUS
        // 注册推送
        nim.getNIM().offlinePush.setOfflinePushConfig({
          plugin: nimPushPlugin,
          authConfig: {
            // xiaomi
            xmAppId: "",
            xmAppKey: "",
            xmCertificateName: "KIT_UNIAPP_MI_PUSH",

            // huawei
            hwAppId: "",
            hwCertificateName: "KIT_UNIAPP_HW_PUSH",

            // oppo
            oppoAppId: "",
            oppoAppKey: "",
            oppoAppSecret: "",
            oppoCertificateName: "KIT_UNIAPP_OPPO_PUSH",

            /**
            * 注意 vivo 的 appid 和 appkey 需要同时在此处，以及 manifest.json(即插件参数配置)中配置
            */
            vivoAppId: "",
            vivoAppKey: "",
            vivoCertificateName: "KIT_UNIAPP_VIVO_PUSH",

            // fcm
            fcmCertificateName: "KIT_UNIAPP_FCM_PUSH",

            // meizu
            mzAppId: "",
            mzAppKey: "",
            mzCertificateName: "KIT_UNIAPP_MZ_PUSH",

            // iOS
            apnsCertificateName: "dis_im_uniapp"
          }
        })
        // #endif

        nim.connect()

      },
      onShow: function () {
        console.log('App Show')
      },
      onHide: function () {
        console.log('App Hide')
      }
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

2. 在 `main.js` 中添加 `VueCompositionAPI`。

    ```JavaScript
    import App from './App'

    // #ifndef VUE3
    import Vue from 'vue'
    import './uni.promisify.adaptor'
    import VueCompositionAPI from "@vue/composition-api";
    Vue.use(VueCompositionAPI);

    Vue.config.productionTip = false
    App.mpType = 'app'
    const app = new Vue({
      ...App
    })
    app.$mount()
    // #endif

    // #ifdef VUE3
    import { createSSRApp } from 'vue'
    export function createApp() {
      const app = createSSRApp(App)
      return {
        app
      }
    }
    // #endif
    ```

### 初始化 NimKitCore

在初始化 `NimKitCore` 时，您需要根据是否是微信小程序，传入不同的 `lbsUrls` 和 `linkUrl`。

```JavaScript
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
  }));
```

## 第五步：配置路由

在 `pages/NEUIKit/utils/customNavigate.ts` 中，修改 `preUrl`：

```JavaScript
const preUrl = '/pages/NEUIKit'
```

在您项目的 `pages.json` 文件中的更新 `pages` 路由：

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
      "path": "pages/NEUIKit/pages/Login/index",
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
      "path": "pages/NEUIKit/pages/Group/group-set/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/group-info-edit",
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
      "path": "pages/NEUIKit/pages/Group/group-member/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-create/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-add/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Friend/add-friend/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/user-card/friend/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/user-card/my/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/user-card/my/setting",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/user-card/my-detail/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/user-card/detail-item/index",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/nick-in-team",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/group-manage",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/transform-team",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/group-manager-list",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Group/group-set/add-group-manager",
      "style": {
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/NEUIKit/pages/Chat/forward",
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
          "pagePath": "pages/NEUIKit/pages/user-card/my/index",
          "iconPath": "static/YX_IMG/me.png",
          "selectedIconPath": "static/YX_IMG/me-selected.png"
        }
      ]
    }
}
```

## 第六步：运行 Demo

在 uni-app IDE 中，运行 Demo：

<img alt="运行 demo.png" src="https://yx-web-nosdn.netease.im/common/e41ad7897d226903af150e1112c61e9e/image.png" style="width:50%;border: 1px solid #BFBFBF;">

## 自定义开发

### API 参考

IM uni-app Demo 基于 UIKitStore 开发，相关 API 详情请参考 [UIKitStore](https://doc.yunxin.163.com/messaging/references/web/typedoc/UIKit/Latest/zh/modules.html)。

**例如，您想获取 IM uni-app UIKit 的会话未读数，示例代码如下：**

```JavaScript
const unRead = store.uiStore.sessionUnread
```

### 使用原生 SDK 中的方法

如果您需要自行实现目前 uni-app UIKit 还未实现，但原生的 IM uni-app SDK 已提供的能力。您可以通过调用原生 IM uni-app SDK 中提供的接口来实现。原生 uni-app SDK 中的接口请参考对应的 [API 文档](https://doc.yunxin.163.com/messaging/references/web/typedoc/Latest/zh/NIM/index.html)。
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
``` -->

例如，您想对 IM uni-app UIKit 的消息历史进行全文检索（按时间分页搜索），可以调用原生 SDK 中的 `msgFtsInServerByTiming` 方法，示例代码如下：

```JavaScript
uni.$UIKitNIM.nim.msgFtsInServerByTiming({
  keyword: '您好',
})
```

:::note note
以上示例中的 `uni.$UIKitNIM.nim` 为原生 NIM uni-app SDK 的实例。
:::

## 常见问题

集成过程中如果遇到任何问题，请 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师或参考 [常见问题](https://doc.yunxin.163.com/messaging-uikit/guide/zE1MTg1NTg?platform=uniapp)。