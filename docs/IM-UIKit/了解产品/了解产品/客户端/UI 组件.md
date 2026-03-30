网易云信即时通讯 IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款即时通讯 UI 组件库，提供一些通用的 UI 组件，包括聊天、会话、圈组、搜索、群管理等。通过 IM UIKit，您可快速集成包含 UI 界面的即时通讯应用。

## UI 版本

自 iOS v9.6.1 和 Android v9.6.2 起，网易云信 IM UIKit 新增全新的通用版 UI 组件，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件。

:::::: div linked-codes
::: code 通用版
<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/2947fb266e5041a173d051beeae78dc1/image.png" style="width:65%;border: 0px solid #BFBFBF;">
:::
::: code 基础版
<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/01039b54183c565a3edfe1845690586a/image.png" style="width:65%;border: 0px solid #BFBFBF;">
:::
::::::

## 模块

IM UIKit 为 iOS 和 Android 应用提供了 UI 子组件，每个 UI 组件负责不同的功能，分别为：
- iOS：通讯录 `NEContactUIKit`、消息 `NEChatUIKit`、云端会话 `NEConversationUIKit`、本地会话 `NELocalConversationUIKit`、群组 `NETeamUIKit`、地理位置 `NEMapUIKit`。
- Android：通讯录 `contactkit-ui`、消息 `chatkit-ui`、云端会话 `conversationkit-ui`、本地会话 `localconversationkit-ui`、群组 `teamkit-ui`、地理位置 `locationkit`。

## 通讯录

通讯录（iOS：`NEContactUIKit`、Android：`contactkit-ui`）主要用于展示联系人、设置权限等通讯录界面。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="通讯录模块.png" src="https://yx-web-nosdn.netease.im/common/a9cdf450aa580b1e8b9de1f6be97a844/通讯录模块.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::: code 基础版

<img alt="通讯模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/895963a051a2ae1fae685cfd1682a6bf/通讯模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

## 云端会话

云端会话（iOS：`NEConversationUIKit`、Android：`conversationkit-ui`）主要用于展示云端的会话列表、编辑云端会话列表等。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="会话通用版.png" src="https://yx-web-nosdn.netease.im/common/38bad9fd8b895eca500fff4419f66666/会话通用版.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::: code 基础版

<img alt="会话基础版.png" src="https://yx-web-nosdn.netease.im/common/e4745050e049fa9ebbc232ef63377f3d/会话基础版.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

## 本地会话

本地会话（iOS：`NELocalConversationUIKit`、Android：`localconversationkit-ui`）主要用于展示本地的会话列表、编辑本地会话列表等。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="会话通用版.png" src="https://yx-web-nosdn.netease.im/common/38bad9fd8b895eca500fff4419f66666/会话通用版.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::: code 基础版

<img alt="会话基础版.png" src="https://yx-web-nosdn.netease.im/common/e4745050e049fa9ebbc232ef63377f3d/会话基础版.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

## 消息

消息（iOS：`NEChatUIKit`、Android：`chatkit-ui`）主要用于展示消息界面。可以直接发送不同类型的消息、对消息长按撤回/回复/复制/转发/标记、查询消息已读回执详情等。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="会话消息界面.png" src="https://yx-web-nosdn.netease.im/common/c9a1792140c6cc8dabebd70d401bf40b/会话消息界面.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::: code 基础版

<img alt="消息模块主要.png" src="https://yx-web-nosdn.netease.im/common/417042baf58dcc002f9452424141ed8a/消息模块主要.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

## 群组

群组（iOS：`NETeamUIKit`、Android：`teamkit-ui`）主要用于管理群成员、群信息、设置权限等。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="群组模块.png" src="https://yx-web-nosdn.netease.im/common/605ff62591fcc2a23116d5d07e3c7703/群组模块.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::: code 基础版

<img alt="群聊模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/18bccb037fe47b0ac2d3e79b03fec89e/群聊模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

## 地理位置

地理位置（iOS：`NEMapUIKit`、Android：`locationkit`）主要用于发送地理位置消息功能，展示当前定位。界面效果如下图所示：

:::::: div linked-codes
::: code 通用版

<img alt="地理位置管理.png" src="https://yx-web-nosdn.netease.im/common/f70b68311f652b44a267b3c68b591c45/地理位置管理.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::: code 基础版

<img alt="地理位置管理界面.png" src="https://yx-web-nosdn.netease.im/common/d51da6c81dcc7f0962de82dff5c25da4/地理位置管理界面.png" style="width:80%;border: 1px solid #BFBFBF;">

:::
::::::

<!-- ## 集成 UI 组件

- [集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/jI1MjMyMTY?platform=android)

## Demo 体验

- [DEMO 体验](https://doc.yunxin.163.com/messaging-uikit/guide/Dg4MTg2MTM?platform=android)

## 快速开始教程

- [跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/guide/zk0MjE5Mjk?platform=android)
- [跑通圈组 Demo 源码](https://doc.yunxin.163.com/messaging-uikit/guide/zM0Mjg1MzA?platform=android) -->