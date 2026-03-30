本文介绍如何基于 React 框架集成 IM UIKit，旨在让您快速了解如何集成网易云信即时通讯组件库（IM UIKit）。您可以参考本文体验集成 IM UIKit 的基本流程和 IM UIKit 提供的 UI 界面。您也可以前往 Github 参考 <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">IM UIKit 的源码</a>。

## 效果示例

<div style="display:flex;width:80%;justify-content:space-between;">
    <div style="width:80%; text-align:left;">
        <video style="width:100%;height:auto" src="https://yx-web-nosdn.netease.im/common/7c44168a7f38813b7d5dc0fc1615babc/WebUIKit.mp4" poster="https://yx-web-nosdn.netease.im/common/1326cd39feb91efa1d2e3ddef3d4a167/WebUIKit首帧图片.png" loop="loop" preload="auto" controls muted></video>
    </div>
</div>

::: note notice
- 如果需要基于 **<font color=blue>Vue</font>** 框架集成 IM UIKit，请参考 [Vue 框架集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/zE4MjQzOTQ?platform=web)。
- 为避免兼容性问题，针对 Electron 项目，不建议您集成 IM UIKit。您可以集成 IM SDK 实现需求，详情请参考 [集成并初始化 Electron SDK](https://doc.yunxin.163.com/messaging2/guide/DQ3OTM0MTM?platform=client)。
:::

## 前提条件

根据本文操作前，请确保您已经完成了以下设置：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/quick-start/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取到账号 ID（`account_id`）和密钥（`token`）。
- 确认 React 的版本：建议不低于 16.8.0（建议使用 16.8）
- 确认 React DOM 的版本：建议不低于 16.8.0（建议使用 16.8）

## 第一步：按需导入组件

1. 通过 NPM 方式将 IM UIKit 安装到您的 Web 项目中。

    示例代码如下：

    ```
    $ npm install @xkit-yx/im-kit-ui@10.x --save
    ```

    ::: note note
    目前仅支持 npm 方式集成，暂不支持 CDN 方式集成。
    :::

2. 将 IM UIKit 组件导入到您的 React 项目中。详细说明可参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TYyNjcyOTY?platform=web" target="_blank">组件导入</a>。

    以导入会话列表组件和会话消息组件为例，示例代码如下：

    ```JavaScript
    import {
      Provider, // 全局上下文
      ConversationContainer, // 会话列表组件
      ChatContainer, // 聊天（会话消息）组件
    } from '@xkit-yx/im-kit-ui'

    // 引入 V10 版本的 nim sdk：https://doc.yunxin.163.com/messaging2/guide/DcyMjA1Njk?platform=client
    import V2NIM from 'nim-web-sdk-ng'

    //如果您希望引入组件 css：
    import "@xkit-yx/im-kit-ui/es/style/css";
    //如果您希望引入组件 less：
    import "@xkit-yx/im-kit-ui/es/style";
    ```

    :::note note
    建议引入组件的 css 或 less（两者选其一）。
    :::

## 第二步：初始化

初始化 IM UIKit 需要传入必传参数 nim，值为 IM V10 SDK 的实例。更多初始化详情请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/Tg0NjMzMzg?platform=web：初始化" target="_blank">初始化</a>。

初始化示例代码如下：

```TSX
import React, { useMemo } from 'react'
import { Provider } from '@xkit-yx/im-kit-ui'
import V2NIM from 'nim-web-sdk-ng'

const initOptions = {
  appkey: '', // 传入您的 App Key
  account: '', // 传入您的网易云信 IM 账号
  token: '',   // 传入您的 Token
}

const App = () => {
  const nim = useMemo(() => {
    // 其余参数参考 IM V10 SDK 文档：https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client
    return V2NIM.getInstance({
      ...initOptions,
      debugLevel: 'debug', // 设置日志 level
      apiVersion: 'v2',
    })
  }, [])

  return (
    <Provider nim={nim}>
      <div className="app">……</div>
    </Provider>
  )
}
```

## 第三步：登录 IM

如上所述，完成初始化后，需要手动管理 IM 的登录和登出，示例代码如下：

```TSX
import React, { useMemo, useEffect } from 'react'
import { Provider } from '@xkit-yx/im-kit-ui'
import V2NIM from 'nim-web-sdk-ng'

const initOptions = {
  appkey: '', // 传入您的 App Key
  account: '', // 传入您的网易云信 IM 账号
  token: '',   // 传入您的 Token
}

const App = () => {
  const nim = useMemo(() => {
    // 其余参数参考 IM V10 SDK 文档：https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client
    return V2NIM.getInstance({
      ...initOptions,
      debugLevel: 'debug', // 设置日志 level
      apiVersion: 'v2',
    })
  }, [])

  useEffect(() => {
    // 当 App 完成渲染后，登录 IM
    nim.V2NIMLoginService.login(initOptions.account, initOptions.token, {
      retryCount: 5,
    })

    // 当 App 卸载时，登出 IM
    return () => {
      nim.V2NIMLoginService.logout()
    }
  }, [nim])

  return (
    <Provider nim={nim}>
      <div className="app">……</div>
    </Provider>
  )
}
```

## 第四步：搭建界面

IM UIKit 已提供会话列表页面和聊天消息等页面。IM UIKit 中提供的组件如下：

组件 | 描述
:---- | :----
会话列表组件 | 代码中的名称为 `ConversationContainer`，负责会话列表的展示与相关操作，相关集成说明请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/Dk1Mjc2NDY?platform=web" target="_blank">集成会话列表界面</a>。
聊天（会话）组件 | 代码中的名称为 `ChatContainer`，负责单聊、群聊相关的操作以及相关的权限管理，相关集成说明请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jMyMDYzMjk?platform=web" target="_blank">集成会话消息界面</a>。
通讯录组件 | 内含 `ContactListContainer`、`ContactInfoContainer` 等子组件，负责通讯录导航、好友列表、黑名单列表以及群组列表。相关集成说明请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jU3MTQ1NjQ?platform=web" target="_blank">集成通讯录界面</a>。
搜索组件 | 内含 `SearchContainer` 和 `AddContainer` 两个子组件，负责搜索好友、群组以及添加好友、群组。相关集成说明请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DkxODY2NjU?platform=web" target="_blank">集成搜索组件</a>。
用户资料组件 | 代码中的名称为 `MyAvatarContainer`，负责用户资料的显示与相关操作。相关集成说明请参考 [集成用户资料组件](https://doc.yunxin.163.com/messaging-uikit/guide/DAwOTczOTg?platform=web)。

组件默认提供自定义渲染函数，具体请参考各组件的详情说明。另外还提供自定义主题设置，详情请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/zgyMDk2NDY?platform=web" target="_blank">主题样式设置</a>。

以搭建会话列表界面和会话消息界面为例，搭建界面的示例代码如下：

```TSX
import React, { useMemo, useEffect } from 'react'
import {
  Provider,
  ConversationContainer,
  ChatContainer,
} from '@xkit-yx/im-kit-ui'

import V2NIM from 'nim-web-sdk-ng'

import '@xkit-yx/im-kit-ui/es/style'

import './index.less'

const initOptions = {
  appkey: '', // 传入您的 App Key
  account: '', // 传入您的网易云信 IM 账号
  token: '',   // 传入您的 Token
}

const App = () => {
  const nim = useMemo(() => {
    // 其余参数参考 IM V10 SDK 文档：https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client
    return V2NIM.getInstance({
      ...initOptions,
      debugLevel: 'debug', // 设置日志 level
      apiVersion: 'v2',
    })
  }, [])

  useEffect(() => {
    // 当 App 完成渲染后，登录 IM
    nim.V2NIMLoginService.login(initOptions.account, initOptions.token, {
      retryCount: 5,
    })

    // 当 App 卸载时，登出 IM
    return () => {
      nim.V2NIMLoginService.logout()
    }
  }, [nim])

  return (
    <Provider nim={nim}>
      <div className="app">
        <div className="conversation">
          <ConversationContainer />
        </div>
        <div className="chat">
        <ChatContainer />
        </div>
      </div>
    </Provider>
  )
}
```

调整界面尺寸的示例代码如下：

::: note notice
组件内部宽高默认 100%，使用时需要包裹在 `div` 内，`div` 需要设置组件的宽高等样式信息，如不设置会导致过长或者无法滚动等问题。
:::

```CSS
// index.less
.app {
  width: 100%;
  height: 100%;
}

.conversation {
  float: left;
  width: 30vw;
  height: 100%;
}

.chat {
  float: left;
  width: 70vw;
  height: 100%;
}
```

## 下一步

为保障通信安全，如果您在调试环境中的使用的是网易云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`account_id`）和 `token`。

## Demo 源码

网易云信在 Github 上提供了开源的 <a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">IM Demo 源码</a> 供您参考。

源码跑通流程说明，参考 [跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/quick-start/TMwMjkzNDU?platform=web)。

## 问题排查

如果遇到无法跑通的问题，可尝试把 `node_modules/@xkit-yx` 包以及 `package-lock.json` 文件删掉，并在 `package.json` 中将 `@xkit-yx/im-kit-ui` 包写死为最新版本重新安装。

如果尝试后仍无法解决，请 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。