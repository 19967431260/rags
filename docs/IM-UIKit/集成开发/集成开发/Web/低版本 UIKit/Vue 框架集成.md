本文介绍如何基于 React 框架以外的其他 Web 开发框架（例如 Vue 和 Angular）或者原生 HTML 集成 IM UIKit。




## 前提条件

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/jEyNDg5NTU?platform=android#4-注册-im-账号)，获取 accid 和 token。
- 已准备如下开发环境：
    - React 建议使用版本： 16.8.0 <= 建议版本
    - React DOM 建议使用版本： React DOM 16.8.0 <= 建议版本
- 支持 Vue 2/Vue 3。


## 使用限制

集成 IM UIKit 后，如果需要自定义渲染，自定义渲染的逻辑需要使用 JSX 编写, 并使用如下工具将 JSX 转换成 JS。



工具 | 说明
:---- | :--------------
jsx-web-compiler | 云信提供的转换函数，请前往 [jsx-web-compiler](https://www.npmjs.com/package/jsx-web-compiler) 下载该工具


## 实现流程



将所需的组件引入您的项目，并初始化。初始化过程默认已包含登录 IM 服务端。

1. 通过 NPM 方式将 IM UIKit 安装到您的 Web 项目中。
    ```
    $ npm install @xkit-yx/im-kit-ui react@16.8 react-dom@16.8 --save
    ```
    :::note note 
    目前仅支持 npm 方式集成，暂不支持 CDN 方式集成。
    :::

2. 引入`IMUIKit`类，并按需引入组件。

    IM UIKit 中提供的组件如下：

    组件 | 描述
    :-------------- | :---------
    会话列表组件 | 代码中的名称为`ConversationContainer`，负责会话列表的展示与相关操作，相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/Dk1Mjc2NDY?platform=web" target="_blank">集成会话列表界面</a>
    聊天（会话）组件 | 代码中的名称为`ChatContainer`，负责单聊、群聊相关的操作以及相关的权限管理，相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jMyMDYzMjk?platform=web" target="_blank">集成会话消息界面</a>
    通讯录组件   | 内含 `ContactListContainer`、`ContactInfoContainer` 等子组件，负责通讯录导航、好友列表、黑名单列表以及群组列表。相关集成说明请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jU3MTQ1NjQ?platform=web" target="_blank">集成通讯录界面</a>
    搜索组件  |   内含 `SearchContainer` 和 `AddContainer` 两个子组件，负责搜索好友、群组以及添加好友、群组。相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/DkxODY2NjU?platform=web" target="_blank">集成搜索组件</a>
    用户资料组件 | 代码中的名称为`MyAvatarContainer`，负责用户资料的显示与相关操作。相关集成说明请参见[集成用户资料组件](https://doc.yunxin.163.com/messaging-uikit/guide/DAwOTczOTg?platform=web)。


    此处以引入会话列表组件`ConversationContainer`和聊天（会话）组件`ChatContainer`为例，示例代码如下： 
  
    <br>
  
    ```
    import { IMUIKit, ConversationContainer, ChatContainer } from '@xkit-yx/im-kit-ui'
    ```
3. 引入组件的 css 或 less 样式（两者选其一）。

    - 如果您希望引入组件 css：
    
        ```
        import "@xkit-yx/im-kit-ui/es/style/css";
        ```
    - 如果您希望引入组件 less：
    
        ```
        import "@xkit-yx/im-kit-ui/es/style";
        ```

4. 初始化 IM UIKit 实例。 

    初始化参数如下：



    <div style="width:100px">参数</div> | <div style="width:80px">类型</div> |说明
    ---- | -----| --------- 
    `initOptions` |  Object | 初始化配置项，包括必传项`appkey`、`account`、`token`以及重连配置等其他可选项，具体见如下示例代码的注释
    `singleton`  | boolean   | 是否开启单实例模式。基于 React 框架以外的 Web 框架开发时，**必须** 设置为`true`，开启单实例模式    <note type=note>IM UIKit 的内部上下文由 Provider 提供，后者通过 `React.Context API` 获取上下文。基于 React 框架开发时，每一个 Provider 都会生成新的 `NimKitCore` 与 `Store` 实例，以保证多个 Provider 互相隔离。因此，如果基于其他 Web 框架开发，初始化时请**务必**将`singleton`设置为`true`，开启单实例模式。开启后 `NimKitCore` 与 `Store` 都使用单实例模式，以保证多个 Provider 数据一致、行为一致。 </note>
    `sdkVersion` |  `1|2`   | 1 或 2。1 为 NIM Web SDK；2 为 NIM Web Elite SDK（IM 即时通讯含圈组版 Web SDK）


    ```
    const uikit = new IMUIKit({
    initOptions: {
        appkey: '',  // 传入您的应用的 App Key，必传
        account: '',  // 传入 accid，必传
        token: '', // 传入 token，必传
        lbsUrls: '', // lbs 地址，非必传。默认为云信公网提供的链接，SDK 连接时会向 lbs 地址请求得到 socket 连接地址。为防止 lbs 链接被网络运营商劫持，可传入自己代理的地址做备份，格式如 ['公网地址', '代理地址']
        linkUrl: '', // socket 备用地址，非必传。当 lbs 请求失败时，尝试直接连接 socket 备用地址。如不传，SDK 会有内部默认的备用地址
        debugLevel: 'debug', // 日志级别，非必传。可选值包括off、error、warn、log和debug"
        needReconnect: true, // 是否开启断网自动重连，非必传
        reconnectionAttempts: 5, // 自动重连的最大次数，非必传
    },
    singleton: true, // 单实例模式，需要传入 true，开启后内部 NimKitCore 和 Store 都会使用单实例模式
    sdkVersion: 1,
    })
    ```

5. 获取 DOM 节点。此处以 “待获取的 DOM 节点的 ID 为`wrapper1`和`wrapper2`” 为例。


    ```
    const wrapper1 = document.getElementById('wrapper1')
    const wrapper2 = document.getElementById('wrapper2')
    ```

6. 调用`render`方法，将待渲染组件指定到 DOM 节点中进行渲染，完成组件的默认界面的搭建。

    ::: note note
    如下示例代码中的`null`参数指使用对应组件自定义参数的默认值。以会话列表组件和会话组件为例，其具体自定义参数可分别参见[会话列表界面 UI 自定义参数](https://doc.yunxin.163.com/messaging-uikit/guide/Dk3ODA3ODM?platform=web#自定义参数概览)和[会话消息界面 UI 自定义参数](https://doc.yunxin.163.com/messaging-uikit/guide/Tk2NDUxODc?platform=web#自定义参数概览)。
    :::

    <br>

    ```
    uikit.render(ConversationContainer, null, wrapper1) // null 表示使用默认参数
    uikit.render(ChatContainer, null, wrapper2) // null 表示使用默认参数
    ```

7. （可选）通过 uikit 初始化后的实例获取上下文，具体可参见[全局上下文](https://doc.yunxin.163.com/messaging-uikit/guide/TIzNDI0OTc?platform=web)）。

    ```
    // 从 uikit 实例上获取
    const { store, nim } = uikit.getStateContext()
    ```

8. （可选）调用`unmount`方法卸载组件。

    ```
    uikit.unmount(wrapper1)
    uikit.unmount(wrapper2)
    ```


**完整示例代码:**

```javascript
// 引入组件和 IMUIKit 类
import { IMUIKit, ConversationContainer, ChatContainer } from '@xkit-yx/im-kit-ui'

// 引入样式
import '@xkit-yx/im-kit-ui/es/style';
import 'antd/dist/antd.less';

// 初始化实例，传入初始化参数
const uikit = new IMUIKit({
  initOptions: {
    appkey: '',
    account: '',
    token: '',
    lbsUrls: '',
    linkUrl: '',
    debugLevel: 'debug',
    needReconnect: true,
    reconnectionAttempts: 5,
  },
  singleton: true, // 单实例模式，需要传入 true 开启，开启后内部 NimKitCore 和 Store 都会使用单实例模式
  sdkVersion: 1,
})

// 获取 dom 节点  （您也可以通过vue的ref获取dom）
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







## 后续步骤


为保障通信安全，如果您在调试环境中的使用的是云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/TM5MzM5Njk/docs/DQ3Nzk1MTY?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`accid`）和 `token`。


## 相关参考



### Demo 源码


网易云信在 Github 上提供了开源的 <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">IM Demo 源码（Vue）</a>供您参考。

源码跑通流程说明，参见[跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/guide/TMwMjkzNDU?platform=web)。



### 自定义渲染示例


如果您需要在非 React 框架下对界面进行自定义渲染，可参考[非 React 框架自定义渲染](https://doc.yunxin.163.com/messaging-uikit/guide/DA2MDUyMzE?platform=web)中的示例。

