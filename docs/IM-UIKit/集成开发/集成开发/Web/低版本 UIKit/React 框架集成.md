

本文旨在让新手快速了解如何集成云信即时通讯组件库（IM UIKit）。在本教程中，您可以体验集成 IM UIKit 的基本流程和 IM UIKit 提供的 UI 界面。您也可以前往 Github 参考 <a href="https://github.com/netease-kit/nim-uikit-web/tree/release/9.8.0" target="_blank">IM UIKit 的源码</a>。


本文介绍如何基于 React 框架集成 IM UIKit。


::: note notice
如果需要基于 **<font color=blue>Vue</font>** 或其他 Web 开发框架集成 IM UIKit，请参见 [Vue 框架集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/TY2OTg3OTY?platform=web)。
:::

## 集成效果示例




<div style="display:flex;width:120%;justify-content:space-between;">
    <div style="width:80%; text-align:left;">
        <video style="width:100%;height:auto"  src="https://yx-web-nosdn.netease.im/common/7c44168a7f38813b7d5dc0fc1615babc/WebUIKit.mp4" poster="https://yx-web-nosdn.netease.im/common/1326cd39feb91efa1d2e3ddef3d4a167/WebUIKit首帧图片.png" autoplay="autoplay" loop="loop" preload="auto" muted></video>
    </div>
</div>  

## 前提条件

开始前，请确保您已：

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/jEyNDg5NTU?platform=web#4-注册-im-账号)，获取 accid 和 token。
- 已准备如下开发环境：
    - React 建议使用版本： 16.8.0 <= 建议版本
    - React DOM 建议使用版本： React DOM 16.8.0 <= 建议版本





## 实现流程


### 步骤1：按需导入组件

1. 通过 NPM 方式将 IM UIKit 安装到您的 Web 项目中。

    示例代码如下：


    ```
    $ npm install @xkit-yx/im-kit-ui --save
    ```



    ::: note note 
    目前仅支持 npm 方式集成，暂不支持 CDN 方式集成。
    :::


2. 将 IM UIKit 组件导入到您的 React 项目中。详细说明可参考<a href="https://doc.yunxin.163.com/messaging-uikit/guide/TM0ODQxMTM?platform=web" target="_blank">组件导入</a>。


    以导入会话列表组件和会话消息组件为例，示例代码如下：

    ```
    import {
      Provider, // 全局上下文
      ConversationContainer, // 会话列表组件
      ChatContainer, // 聊天（会话消息）组件
    } from '@xkit-yx/im-kit-ui'

    //如果您希望引入组件 css：
    import "@xkit-yx/im-kit-ui/es/style/css";
    //如果您希望引入组件 less：
    import "@xkit-yx/im-kit-ui/es/style";
    ```

    :::note note 
    建议引入组件的 css 或 less（两者选其一）。
    :::



### 步骤2：初始化

初始化 IM UIKit 需要传入必传参数 `sdkVersion` 和 `initOptions`。更多初始化详情请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/zcwOTQzNTM?platform=web#步骤2：初始化" target="_blank">初始化</a>。

- `sdkVersion`：传入`1`或`2`选择基于哪个 IM SDK 集成 IM UIKit。`1` 表示基于 NIM Web SDK；`2`表示基于 NIM Web SDK 的含圈组版（NIM Web Elite SDK）
- `initOptions`：用于初始化的参数

初始化示例代码如下：


```tsx
import React from 'react'
import { Provider } from '@xkit-yx/im-kit-ui'

const App = () => {
  const initOptions = {
    appkey: '',  // 传入您的App Key
    account: '', // 传入您的云信 IM 账号
    token: '',   // 传入您的 Token 
    debugLevel: 'debug', // 设置日志level
    // 参考 NIM SDK 的 initOptions
  }

  return (
    <Provider initOptions={initOptions} sdkVersion={1}>
      <div className="app">……</div>
    </Provider>
  )
}
```


### 步骤3：登录 IM

如上文的[初始化](https://doc.yunxin.163.com/messaging-uikit/guide/zcwOTQzNTM?platform=web#步骤2：初始化)所述，当`Provider`渲染和销毁时，IM UIKit 内部会完成登录和登出云信 IM 服务端（即与云信 IM  服务端建立连接或断开连接）。

如需手动连接，请参考<a href="https://doc.yunxin.163.com/messaging-uikit/guide/DAxNTg1NjM?platform=web" target="_blank">登录登出</a>。


### 步骤4：搭建界面



IM UIKit 已提供会话列表页面和聊天消息等页面。IM UIKit 中提供的组件如下：



 组件 | 描述
 :-------------- | :---------
 会话列表组件 | 代码中的名称为`ConversationContainer`，负责会话列表的展示与相关操作，相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/Dk1Mjc2NDY?platform=web" target="_blank">集成会话列表界面</a>
 聊天（会话）组件 | 代码中的名称为`ChatContainer`，负责单聊、群聊相关的操作以及相关的权限管理，相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jMyMDYzMjk?platform=web" target="_blank">集成会话消息界面</a>
 通讯录组件   | 内含 `ContactListContainer`、`ContactInfoContainer` 等子组件，负责通讯录导航、好友列表、黑名单列表以及群组列表。相关集成说明请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jU3MTQ1NjQ?platform=web" target="_blank">集成通讯录界面</a>
 搜索组件  |   内含 `SearchContainer` 和 `AddContainer` 两个子组件，负责搜索好友、群组以及添加好友、群组。相关集成说明详见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/DkxODY2NjU?platform=web" target="_blank">集成搜索组件</a>
 用户资料组件 | 代码中的名称为`MyAvatarContainer`，负责用户资料的显示与相关操作。相关集成说明请参见[集成用户资料组件](https://doc.yunxin.163.com/messaging-uikit/guide/DAwOTczOTg?platform=web)。
 


 

组件默认提供自定义渲染函数，具体请参考各组件的详情说明。另外还提供自定义主题设置，详情请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/zgyMDk2NDY?platform=web" target="_blank">主题样式设置</a>。



以搭建会话列表界面和会话消息界面为例，搭建界面的示例代码如下：

```tsx
import React, { useMemo } from 'react'
import {
  Provider,
  ConversationContainer,
  ChatContainer,
} from '@xkit-yx/im-kit-ui'

import '@xkit-yx/im-kit-ui/es/style'

import './index.less'

const App = () => {
  const initOptions = useMemo(() => {
    return {
      appkey: '',
      account: '',
      token: '',
      debugLevel: 'debug',
      // ……
    }
  }, [])

  return (
    <Provider initOptions={initOptions} sdkVersion={2}>
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
组件内部宽高默认 100%，使用时需要包裹在`div`内，`div`需要设置组件的宽高等样式信息，如不设置会导致过长或者无法滚动等问题。
:::

<br>

```
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

## 后续步骤





为保障通信安全，如果您在调试环境中的使用的是云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`accid`）和 `token`。


## 相关参考

### Demo 源码
网易云信在 Github 上提供了开源的<a href="https://github.com/netease-kit/nim-uikit-web" target="_blank">IM Demo 源码</a>供您参考。

源码跑通流程说明，参见[跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/guide/TMwMjkzNDU?platform=web)。




### 问题排查

如果遇到无法跑通的问题，可尝试把`node_modules/@xkit-yx`包以及`package-lock.json`文件删掉，并在`package.json`中将`@xkit-yx/im-kit-ui`包写死为最新版本重新安装。

如果尝试后仍无法解决，请联系云信技术支持或点击下方的**提交工单**。 