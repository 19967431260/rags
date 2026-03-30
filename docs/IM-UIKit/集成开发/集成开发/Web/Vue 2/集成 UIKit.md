网易云信 IM UIKit 是基于 [网易云信 IM SDK（简称 NIM SDK）](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client) 开发的一款 [即时通讯 UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=client)，功能涵盖了聊天、会话、群管理。

本文介绍如何集成基于 Vue 2 框架开发的 Web IM UIKit。

## 前提条件

在开始集成 IM UIKit 前，请确保您已完成以下操作：

- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取 account_id 和 token。
- 调整本地开发环境，并满足如下要求：

    配置项 | 要求
    ---- | ----
    集成开发环境 | vuecli/vite
    Vue.js 版本 | Vue 2
    开发语言 | TypeScript
    Node.js 版本 | v16 及以上
    JavaScript 包管理器 | NPM（版本请与 Node.js 版本匹配）

## 实现步骤

### 第一步：创建项目

您可以使用 vuecli 或者 vite 创建项目，详细步骤请参考 [Vue 官网文档](https://vuejs.org/guide/quick-start.html)。

如果您已创建项目，请忽略本步骤。

### 第二步：下载组件

1. 手动下载 [NEUIKit.zip](https://yx-web-nosdn.netease.im/common/2b810583786b847b162fe425eeab5603/NEUIKit.zip) IM UIKit 组件。

2. 在下载的资源包中找到 **NEUIKit** 文件夹，将该文件夹复制到您项目的 **components** 目录下，例如：

    ![源码下载目录.png](https://yx-web-nosdn.netease.im/common/717ffa68a294a23c0dbbec62eaae29f6/源码下载目录.png)

3. 执行以下命令安装 NEUIKit 需要的依赖。

    ```
    npm i nim-web-sdk-ng@10.9.70  @xkit-yx/utils@0.7.2 vue-virtual-scroller@1.1.2  dayjs@1.11.7 mobx@6.12.0 mitt@3.0.1 --save
    ```

    依赖 | 说明 |
    --- | --- |
    `nim-web-sdk-ng` | [网易云信 NIM SDK](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client)，提供了一整套即时通讯基础能力。|
    `@xkit-yx/im-store-v2` | store 用于 **全局状态管理**，基于 MobX 和 NIM SDK 封装的全局上下文对象，它提供了数据和 UI 之间的双向绑定能力。<br>包含多个子模块，每个子模块负责管理不同的数据领域，如会话、消息、通讯录、群组等。通过 store，您可以方便地获取数据、响应数据变化，并更新 UI。<!--更多 store 相关信息，请参见 [全局上下文]()。-->
    `@xkit-yx/utils` | 项目中的工具库，提供 getFileType、parseFileSize 等函数。 |
    `@vue-virtual-scroller` | 虚拟列表库。 | 

下载组件成功后，可根据您的业务需求对源码进行自定义修改。

### 第三步：集成并初始化组件

1. 在您项目需要展示 IM UIKit 的位置处引入 NEUIKit 组件，参考以下 **init** 函数初始化 IM UIKit。

    - 从 **NEUIKit/utils/init** 引入 `initIMUIKit`，传入您的 AppKey 进行初始化，获取返回的 nim 对象。

        ::: note note
        若需要进行初始化相关配置（例如配置云端会话），可在 **NEUIKit/utils/init.ts** 文件的 `initIMUIKit` 中配置 `V2NIM.getInstance`，具体配置请参见 [IM SDK 初始化](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client)。
    
    - 在 `nim.loginService.login` 传入您业务服务器返回的 `account_id` 和 `token` 进行登录，然后跳转至聊天页面。

    ```
    <template>
    <div v-if="showUiKit" class="app-container">
        <router-view></router-view>
    </div>
    </template>

    <script>
    import { initIMUIKit } from "./components/NEUIKit/utils/init.js";
    import { STORAGE_KEY } from "./components/NEUIKit/utils/constants";
    import { showToast } from "./components/NEUIKit/utils/toast";
    export default {
    name: "App",
    components: {},
    data() {
        return {
        showUiKit: false,
        };
    },

    methods: {
        init(opts) {
        const { nim } = initIMUIKit(opts.appkey);

        nim.V2NIMLoginService.login(opts.account, opts.token)
            .then(() => {
            if (this.$route.path !== "/chat") {
                this.$router.push("/chat");
            }
            this.showUiKit = true;
            })
            .catch((error) => {
            if (error.code === 102422) {
                // 账号被封禁
                showToast({
                message: "当前账号已被封禁",
                type: "info",
                });
            }
            // 登录信息无效，清除并跳转到登录页
            sessionStorage.removeItem(STORAGE_KEY);
            if (this.$route.path !== "/login") {
                this.$router.push("/login");
            }
            });
        },
    },
    mounted() {
        this.init({
        appkey: "", // 请填写你的appkey
        account: "", // 请填写你的account
        token: "", // 请填写你的token
        });
    },
    };
    </script>

    <style>
    .app-container {
    height: 100%;
    width: 100%;
    box-sizing: border-box;
    background-image: url("./assets/bg.png");
    }
    </style>
    ```

2. 在 **main.ts** 中注册虚拟列表。

    ```
    import Vue from "vue";
    import App from "./App.vue";
    import { RecycleScroller } from "vue-virtual-scroller";
    import router from "./router";
    import "./global.css";

    Vue.config.productionTip = false;
    Vue.component("RecycleScroller", RecycleScroller);

    new Vue({
    router,
    render: (h) => h(App),
    }).$mount("#app");
    ```

### 第四步：运行项目

根据您的业务需求，在合适的时机，通过 `npm run dev`，或者您项目的自定义运行命令启动聊天页面。

## 下一步

为保障通信安全，如果您在调试环境中的使用的是网易云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`account_id`）和 `token`。

## API 参考

IM Web Demo 基于 UIKitStore 开发，相关 API 详情请参考 [UIKitStore](https://doc.yunxin.163.com/messaging2/references/web/typedoc//IMUIKit/Latest/modules.html)。