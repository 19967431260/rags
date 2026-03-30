本文介绍如何基于 React 框架以外的其他 Web 开发框架（例如 Vue 和 Angular）或者原生 HTML 集成 IM UIKit。

:::note notice
- 该版本的 UIKit 底层实际由 React 框架开发，通过 JSX-compiler 让其能在 Vue2/Vue3 调用。因此，若需要实现其他功能，请参考 **React 框架目录** 下的集成文档。
- 为避免兼容性问题，针对 Electron 项目，不建议您集成 IM UIKit。您可以集成 IM SDK 实现需求，详情请参考 [集成并初始化 Electron SDK](https://doc.yunxin.163.com/messaging2/guide/DQ3OTM0MTM?platform=client)。
:::

## 前提条件

根据本文操作前，请确保您已经完成了以下设置：

- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取 account_id 和 token。
- 已准备如下开发环境：

    - React 建议使用版本：16.8.0 <= 建议版本
    - React DOM 建议使用版本：React DOM 16.8.0 <= 建议版本

- 支持 Vue 2/Vue 3。

## 资源下载

集成 IM UIKit 后，如果需要自定义渲染，自定义渲染的逻辑需要使用 JSX 编写，并使用如下工具将 JSX 转换成 JS。

工具 | 说明
:---- | :----
jsx-web-compiler | 网易云信提供的转换函数工具，请前往 NPM (Node Package Manager) 的官方网站下载 [jsx-web-compiler](https://www.npmjs.com/package/jsx-web-compiler)。

## 实现流程

集成 IM UIKit 是将您所需的组件引入项目，并初始化。初始化过程默认已包含登录 IM 服务端。

1. 通过 NPM 方式将 IM UIKit 安装到您的 Web 项目中。

    ```NPM
    $ npm install @xkit-yx/im-kit-ui@10.x react@16.8 react-dom@16.8 --save
    ```

    :::note note
    目前仅支持 NPM 方式集成，暂不支持 CDN 方式集成。
    :::

2. 引入 `IMUIKit` 类，并按需引入组件。IM UIKit 提供的组件如下表所示：

    组件 | 代码描述 | 功能 | 参考文档
    :---- | :---- | :---- | :---- 
    会话列表组件 | 代码中的名称为 `ConversationContainer`。 | 会话列表的展示与相关操作。 | <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DA3MDMxMzg?platform=web" target="_blank">集成会话列表界面</a>
    聊天（会话）组件 | 代码中的名称为 `ChatContainer`。 | 单聊、群聊相关的操作以及相关的权限管理。 | <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DgzMDkwODI?platform=web" target="_blank">集成会话消息界面</a>
    通讯录组件 | 内含 `ContactListContainer`、`ContactInfoContainer` 等子组件。 | 通讯录导航、好友列表、黑名单列表以及群组列表。 | <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TM1OTYzNjc?platform=web" target="_blank">集成通讯录界面</a>
    搜索组件 | 内含 `SearchContainer` 和 `AddContainer` 两个子组件。 | 搜索好友、群组以及添加好友、群组。 | <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TIzMzA1MzI?platform=web" target="_blank">集成搜索组件</a>

    此处以引入会话列表组件 `ConversationContainer` 和聊天（会话）组件 `ChatContainer` 为例，示例代码如下：

    ```JavaScript
    import { IMUIKit, ConversationContainer, ChatContainer } from '@xkit-yx/im-kit-ui'
    ```

3. 引入 IM V10 SDK。

    ```JavaScript
    import V2NIM from 'nim-web-sdk-ng'
    ```

4. 引入组件的 css 或 less 样式（两者选其一）。

    - 如果您希望引入组件 css：

        ```JavaScript
        import "@xkit-yx/im-kit-ui/es/style/css";
        ```

    - 如果您希望引入组件 less：

        ```JavaScript
        import "@xkit-yx/im-kit-ui/es/style";
        ```

5. 初始化 IM UIKit 实例。

    初始化参数如下：

    <div style="width:100px">参数</div> | <div style="width:80px">类型</div> | 说明
    ---- | ---- | ----
    `nim` | Object | IM V10 SDK 初始化后的实例，具体请参考 [初始化 IM SDK](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client)。
    `singleton` | boolean | 是否开启单实例模式。基于 React 框架以外的 Web 框架开发时，**必须** 设置为 `true`，开启单实例模式。<note type=note>IM UIKit 的内部上下文由 Provider 提供，后者通过 `React.Context API` 获取上下文。基于 React 框架开发时，每一个 Provider 都会生成新的 `Store` 实例，以保证多个 Provider 互相隔离。因此，如果基于其他 Web 框架开发，初始化时请 **务必** 将 `singleton` 设置为 `true`，开启单实例模式。开启后 `Store` 将使用单实例模式，以保证多个 Provider 数据一致、行为一致。</note>

    ```JavaScript
    // 初始化 IM V10 SDK
    const nim = V2NIM.getInstance({
      appkey: '', // 传入您的应用的 App Key，必传
      account: '', // 传入用户账号 ID，必传
      token: '', // 传入 token，必传
      debugLevel: 'debug',
      apiVersion: 'v2',
    })

    // IM 登录
    nim.V2NIMLoginService.login(initOptions.account, initOptions.token, {
      retryCount: 5,
    })

    // 初始化 UIKit 实例
    const uikit = new IMUIKit({
      nim,
      singleton: true, // 单实例模式，需要传入 true，开启后内部 Store 会使用单实例模式
    });
    ```

6. 获取 DOM 节点。此处以 **待获取的 DOM 节点的 ID 为 `wrapper1` 和 `wrapper2`** 为例。

    ```
    const wrapper1 = document.getElementById('wrapper1')
    const wrapper2 = document.getElementById('wrapper2')
    ```

7. 调用 `render` 方法，将待渲染组件指定到 DOM 节点中进行渲染，完成组件的默认界面的搭建。

    ::: note note
    如下示例代码中的 `null` 参数指使用对应组件自定义参数的默认值。以会话列表组件和会话组件为例，其具体自定义参数可分别参考 [会话列表界面 UI 自定义参数](https://doc.yunxin.163.com/messaging-uikit/guide/DI1Mzk4ODg?platform=web) 和 [会话消息界面 UI 自定义参数](https://doc.yunxin.163.com/messaging-uikit/guide/Tk0NTAxNzA?platform=web)。
    :::

    ```JavaScript
    uikit.render(ConversationContainer, null, wrapper1) // null 表示使用默认参数
    uikit.render(ChatContainer, null, wrapper2) // null 表示使用默认参数
    ```

8. （可选）通过 UIKit 初始化后的实例获取上下文，具体可参考 [全局上下文](https://doc.yunxin.163.com/messaging-uikit/guide/DI1NzE1ODA?platform=web)）。

    ```JavaScript
    // 从 uikit 实例上获取
    const { store, nim } = uikit.getStateContext()
    ```

9. （可选）调用 `unmount` 方法卸载组件。

    ```JavaScript
    uikit.unmount(wrapper1)
    uikit.unmount(wrapper2)
    ```

## **完整示例代码**

```JavaScript
// 引入组件和 IMUIKit 类
import { IMUIKit, ConversationContainer, ChatContainer } from '@xkit-yx/im-kit-ui'
// 引入 IM V10 SDK
import V2NIM from 'nim-web-sdk-ng'

// 引入样式
import '@xkit-yx/im-kit-ui/es/style';
import 'antd/dist/antd.less';

// 初始化 IM V10 SDK
const nim = V2NIM.getInstance({
    appkey: '', // 传入您的应用的 App Key，必传
    account: '', // 传入用户账号 ID，必传
    token: '', // 传入 token，必传
    debugLevel: 'debug',
    apiVersion: 'v2',
})

// IM 登录
nim.V2NIMLoginService.login(initOptions.account, initOptions.token, {
    retryCount: 5,
})

// 初始化实例，传入初始化参数
const uikit = new IMUIKit({
  nim,
  singleton: true, // 单实例模式，需要传入 true 开启，开启后内部 Store 会使用单实例模式
})

// 获取 dom 节点 （您也可以通过 vue 的 ref 获取 dom）
const wrapper1 = document.getElementById('wrapper1')
const wrapper2 = document.getElementById('wrapper2')

// 渲染需要渲染的组件到指定的 dom 节点中，完成组件的默认界面搭建
uikit.render(ConversationContainer, null, wrapper1)
uikit.render(ChatContainer, null, wrapper2)

// 获取上下文
const { store, nim } = uikit.getStateContext()

// 卸载组件
uikit.unmount(wrapper1)
uikit.unmount(wrapper2)
```

## 下一步

为保障通信安全，如果您在调试环境中的使用的是网易云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`account_id`）和 `token`。

## Demo 源码

网易云信在 Github 上提供了开源的 <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">IM Demo 源码（Vue）</a> 供您参考。

源码跑通流程说明，参考 [跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/quick-start/TMwMjkzNDU?platform=web)。

## 故障排查

当在 Vue.js 框架中通过 `npm run dev` 运行 Demo 时，报如下错误时，请参考 [VUE.js 框架引入 V10 IM UIKit Demo 遇到 windowScroller 报错](https://doc.yunxin.163.com/messaging-uikit/faq/TQ5ODgwNzI?platform=web) 解决。

```
No mactching export in "node_modules/react-virtualized/dist/es/WindowScroller/WindowScroller.js" for improt "bpfrpt_proptype_WindowsScroller"
```

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/78fe781ee649c0d6697ed784f4992848/image.png" style="width:80%;border: 1px solid #BFBFBF;">