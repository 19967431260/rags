网易云信在 GitHub 上提供开源的 IM Demo 源码。您可参考 Demo 源码，在您的本地项目中快速构建即时通讯应用。

本文介绍如何快速跑通基于 React 和 Vue 框架的 IM Demo 源码。

## 前提条件

在开始运行示例项目之前，请确保：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取应用密钥（App Key）。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（Token）。
- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 为应用开通 **云端会话** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/TQ2NzE5MzQ?platform=console)。

    <img alt="开通云端会话.png" src="https://yx-web-nosdn.netease.im/common/d80e78c7f8d0a5b7f0452e7f5d9c6b47/开通云端会话.png" style="width:40%;border: 1px solid #BFBFBF;">

## 环境要求

- 您的开发环境需要满足以下要求：

    环境要求 | 说明 |
    ---- | ---- |
    React | 16.8.0 <= 建议版本 < React 18.0.0 |
    React DOM | React DOM 16.8.0 <= 建议版本 < React DOM 18.0.0 |

- 您的 **运行** 环境需要满足以下要求：

    环境要求 | 说明 |
    ---- | ---- |
    Node 版本 | v16.0.0 及以上版本，推荐使用 Node.js 官方 LTS 版本 16.17.0 |
    浏览器 | Chrome v103.0.5060.134 及以上版本 |

## 跑通流程

:::::: div linked-codes
::: code 跑通 React Demo 源码

1. 前往 GitHub <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">下载 Demo 源码</a>。

    React Demo 源码的主要目录结构如下：

    ```
    ├── src
    │   └── YXUIKit
    │       └── im-kit-ui // IM UI 组件源码
    │   └── components
    │       └── IMApp // IM UIKit 使用示例
    │   └── pages
    │       └── index.tsx // 项目入口
    ```

2. 执行如下命令安装依赖。

    ```bash
    $ npm install
    ```

3. 在 `react/src/pages/index.tsx` 中配置 `appkey`、`account`、和 `token`。

    ```TypeScript
    import IMApp from "../components/IMApp";

    export default function HomePage() {

      const initOptions = {

        appkey: "", // 请填写您的 appkey
        account: "", // 请填写您的 account
        token: "", // 请填写您的 token
      };

    return <IMApp {...initOptions}></IMApp>;
    }
    ```

4. 执行如下命令启动项目。

    ```bash
    $ npm run start
    ```

5. 执行如下命令构建项目。

    ```bash
    $ npm run build
    ```

    IM Demo 使用 umi.js 搭建，目前没有内置登录，构建项目后您将直接进入 Demo 主界面。

    ::: note note
    如果您在源码引入时发生 ts 类型检查错误，您可在项目工程的 `tsconfig.json` 的 `exclude` 配置项中，跳过对 IMUIKit 源码的类型检查。
    :::

:::
::: code 跑通 Vue Demo 源码

1. 前往 GitHub <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">下载 Demo 源码</a>。

2. 配置项目。

    ```typescript
    // 请到下面路径的文件配置
    // src/App.vue
    this.initIMUiKit({
    appkey: "", // 请填写你的appkey
    account: "", // 请填写你的account
    token: "", // 请填写你的token
    });
    ```

3. 运行项目。

    ```bash
    npm install
    npm run dev
    ```

    构建项目后您将直接进入 Demo 主界面。

:::

::::::

## 下一步

参照如下步骤发送您的第一条消息。

1. 获取对方的 IM Demo 账号（参照如下视频，对方可在个人信息窗口中复制账号）。
2. 添加对方为好友。
3. 输入消息后，单击键盘的 Enter 键发送消息。

    <div style="display:flex;width:120%;justify-content:space-between;">
        <div style="width:80%; text-align:left;">
            <video style="width:40%;height:auto;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/2c36c617b6fe118cb465a3c5ad9c6418/WebIMDemo 发送第一条消息.mp4" poster="https://yx-web-nosdn.netease.im/common/c90079bc4cfe3e98f6722cc8a88b4137/跑通源码进入的界面.png" autoplay="autoplay" loop="loop" preload="auto" muted></video>
        </div>
    </div>

## 故障排查

在 Vue.js 框架中通过 `npm run dev` 运行 Demo 时，报如下错误：

```
No mactching export in "node_modules/react-virtualized/dist/es/WindowScroller/WindowScroller.js" for improt "bpfrpt_proptype_WindowsScroller"
```

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/78fe781ee649c0d6697ed784f4992848/image.png" style="width:80%;border: 1px solid #BFBFBF;">

解决方法请参考 [VUE.js 框架引入 V10 IM UIKit Demo 遇到 windowScroller 报错](https://doc.yunxin.163.com/messaging-uikit/faq/TQ5ODgwNzI)。