网易云信为您提供在线的即时通讯 Demo 与 Demo 源码。您可以访问在线 Demo，快速了解和体验网易云信 IM 即时通讯服务的多项能力，如会话（单聊与群聊）、会话列表和通讯录。

## 第一步：进入 Demo 界面

网易云信提供了基于 React 和 Vue 框架的两种 Web Demo，您可按需体验。

:::::: div linked-codes
::: code React Demo

访问 [React Demo 在线体验地址](https://yiyong.netease.im/yiyong-xkit/iframe.html?args=&id=im-ui-kit-%E7%A4%BA%E4%BE%8B--primary&viewMode=story) 即可直接体验。
:::

::: code Vue Demo
1. 登录 <a href="https://id.grow.163.com/?h=media&t=media&clueFrom=nim&from=nim&locale=zh_CN&referrer=https%3A%2F%2Fapp.yunxin.163.com&i18nEnable=true" target="_blank">网易云信控制台</a>，[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取应用 App Key 和 App Secret，用于识别开发者身份。
2. 调用服务端接口 [`/nimserver/user/create.action`](https://doc.yunxin.163.com/messaging/server-apis/DQ3Nzk1MTY?platform=server) 注册一个或多个 IM 账号，获取到用户账号 ID（`accid`）和 Token，用于应用登录。

3. 访问 [Vue 在线 Demo](https://yiyong.netease.im/yiyong-static/statics/im-vue/index.html#/)，配置如下参数，并单击 **初始化**，即可开始体验。

    参数 | 说明
    ---- | ----
    appkey | 输入第一步中获取到的 App Key。
    account | 输入第二步中获取到的账号 ID（`accid`）。
    token | 输入第二步中获取到的 Token。
    sdkVersion | 设置对应的 SDK 版本，只能输入 1 或 2 <ul><li>1：表示使用 NIM Web SDK</li><li>2：表示使用 IM Web SDK 含圈组版（即 NIM Web Elite SDK）</li></ul>
:::
::::::

## 第二步：发送第一条消息

1. 获取对方的 IM Demo 账号（参照如下视频，对方可在个人信息窗口中复制账号）。
2. 添加对方为好友。
3. 输入消息后，单击键盘的 Enter 键发送消息。

    <div style="display:flex;width:80%;justify-content:space-between;">
        <div style="width:80%; text-align:left;">
            <video style="width:100%;border: 1px solid #BFBFBF;height:auto" src="https://yx-web-nosdn.netease.im/common/2c36c617b6fe118cb465a3c5ad9c6418/WebIMDemo发送第一条消息.mp4" poster="https://yx-web-nosdn.netease.im/common/c90079bc4cfe3e98f6722cc8a88b4137/跑通源码进入的界面.png" loop="loop" preload="auto" muted controls></video>
        </div>
    </div>

## Demo 源码

网易云信在 [Github](https://github.com/netease-kit/nim-uikit-web) 上提供简易的 IM Demo 源码。

您可 <a href="https://doc.yunxin.163.com/messaging/guide/DE5NzY4NjQ?platform=web" target="_blank">跑通 IM Demo 源码</a> 快速体验 SDK 的能力，例如会话列表、好友添加、消息收发和通讯录等功能。