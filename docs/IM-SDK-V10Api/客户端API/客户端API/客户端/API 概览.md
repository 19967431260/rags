本文介绍网易云信即时通讯 SDK（NetEase IM SDK，简称 NIM SDK）全量 API。

<!-- ## 支持平台

iOS | Android | macOS/Windows | Web/uni-app/小程序 | Node.js/Electron | HarmonyOS | Flutter
:----: | :----: | :----: | :----: | :----:| :----:| :----:
✔️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️ | ✔️️ -->

本文内容适用的开发平台或框架如下所示： <div class="platform-tabs"><div class="platform-tab"><span>iOS</span></div> <div class="platform-tab"><span>Android</span></div> <div class="platform-tab"><span>Web</span></div> <div class="platform-tab"><span>Windows</span></div> <div class="platform-tab"><span>MacOS</span></div> <div class="platform-tab"><span>HarmonyOS</span></div> <div class="platform-tab"><span>小程序</span></div> <div class="platform-tab"><span>Electron</span></div> <div class="platform-tab"><span>Flutter</span></div> <div class="platform-tab">uni-app</span></div></div>

<!--
## 使用说明

:::::: div linked-codes
::: code Android
调用其他接口前，必须先调用 `NIMClient#getService` 获取网易云信各服务。
:::
::: code iOS

:::
::::::
-->

## API 架构

:::::: div linked-codes
::: code iOS
以下为 NIM SDK iOS 端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [iOS SDK](https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/annotated.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/annotated.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code Android
以下为 NIM SDK 安卓端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [Android SDK](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/namespacecom_1_1netease_1_1nimlib_1_1sdk_1_1v2.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/namespacecom_1_1netease_1_1nimlib_1_1sdk_1_1v2.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code macOS/Windows/Linux
以下为 NIM SDK macOS/Windows/Linux 端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [macOS/Windows/Linux SDK](https://doc.yunxin.163.com/messaging2/references/pc/doxygen/Latest/zh/index.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/pc/doxygen/Latest/zh/index.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code Web/uni-app/小程序(NIM)
以下为 NIM SDK Web/uni-app/小程序端 NIM 模块的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [Web/uni-app/小程序(NIM)](https://doc.yunxin.163.com/messaging2/references/web/typedoc/Latest/zh/v2/nim/index.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/web/typedoc/Latest/zh/v2/nim/index.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code Web/uni-app/小程序(Chatroom)
以下为 NIM SDK Web/uni-app/小程序端 Chatroom 模块的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [Web/uni-app/小程序(Chatroom)](https://doc.yunxin.163.com/messaging2/references/web/typedoc/Latest/zh/v2/chatroom/index.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/web/typedoc/Latest/zh/v2/chatroom/index.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code Node.js/Electron
以下为 NIM SDK Node.js/Electron 端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [Node.js/Electron](https://doc.yunxin.163.com/messaging2/references/electron/typedoc/Latest/zh/index.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/electron/typedoc/Latest/zh/index.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code HarmonyOS
以下为 NIM SDK HarmonyOS 端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [HarmonyOS](https://doc.yunxin.163.com/messaging2/references/harmony/typedoc/Latest/zh/index.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/harmony/typedoc/Latest/zh/index.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::: code Flutter
以下为 NIM SDK Flutter 端的 API 文档的 \<iframe\> 预加载页面，您也可以前往 [Flutter](https://doc.yunxin.163.com/messaging2/references/flutter/Dartdoc/Latest/zh/nim_core_v2/nim_core_v2-library.html) 全屏查看。

<style>
  .parent-container {
    min-height: 500px; /* 设置最小高度 */
    overflow-y: auto; /* 如果内容超过高度，添加滚动条 */
  }

  iframe {
    width: 100%;
  }
</style>

<div class="parent-container">
  <iframe src="https://doc.yunxin.163.com/messaging2/references/flutter/Dartdoc/Latest/zh/nim_core_v2/nim_core_v2-library.html" width="100%" height="500" frameborder="1" scrolling="auto" allowfullscreen></iframe>
</div>
:::
::::::

## 初始化

请参考各端初始化指南：

- [iOS](https://doc.yunxin.163.com/messaging2/guide/jU5MTUwMDY?platform=client)

- [Android](https://doc.yunxin.163.com/messaging2/guide/TY4OTgyMDk?platform=client)

- [macOS/Windows/Linux](https://doc.yunxin.163.com/messaging2/guide/zE1MjkwNTc?platform=client)

- [Web/uni-app/小程序](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client)

- [Node.js/Electron](https://doc.yunxin.163.com/messaging2/guide/zA0ODU5Mzk?platform=client)

- [HarmonyOS](https://doc.yunxin.163.com/messaging2/guide/TY4MTAxNzE?platform=client)

- [Flutter](https://doc.yunxin.163.com/messaging2/guide/zY5NTAzMTI?platform=client)

## 登录

提供登录、登出、踢出其他设备端、注册登录连接状态监听器等接口。

### 登录相关监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addLoginListener](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#addLoginListener) | 注册登录状态监听器 | v10.2.0
[removeLoginListener](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#removeLoginListener) | 取消注册登录状态监听器 | v10.2.0
[addLoginDetailListener](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#addLoginDetailListener) | 注册登录连接状态监听器 | v10.2.0
[removeLoginDetailListener](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#removeLoginDetailListener) | 取消注册登录连接状态监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#on) | 注册登录相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#off) | 取消注册登录相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#listen) | 注册登录相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#cancel) | 取消注册登录相关监听器 | v10.3.0
:::
::::::

### 登录登出

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[login](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#login) | 登录 IM | v10.2.0
[logout](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout) | 登出 IM | v10.2.0
[getLoginUser](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginUser) | 获取当前登录的账号 | v10.2.0
[getLoginStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginStatus) | 获取当前登录状态 | v10.2.0
[getConnectStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getConnectStatus) | 获取当前登录连接状态 | v10.2.0
[getChatroomLinkAddress](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getChatroomLinkAddress) | 获取聊天室连接地址 | v10.2.0
[setReconnectDelayProvider](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#setReconnectDelayProvider) | 设置登录重连延时的回调函数 | v10.2.0
[getCurrentLoginClient](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getCurrentLoginClient) | 查询当前登录终端的相关信息 | v10.5.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[login](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#login) | 登录 IM | v0.5.0
[logout](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout) | 登出 IM | v0.5.0
[getLoginUser](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginUser) | 获取当前登录的账号 | v0.5.0
[getLoginStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginStatus) | 获取当前登录状态 | v0.5.0
[getConnectStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getConnectStatus) | 获取当前登录连接状态 | v0.5.0
[getChatroomLinkAddress](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getChatroomLinkAddress) | 获取聊天室连接地址 | v0.5.0
[setReconnectDelayProvider](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#setReconnectDelayProvider) | 设置登录重连延时的回调函数 | v0.5.0
[getCurrentLoginClient](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getCurrentLoginClient) | 查询当前登录终端的相关信息 | v10.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[login](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#login) | 登录 IM | v10.3.0
[logout](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#logout) | 登出 IM | v10.3.0
[getLoginUser](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getLoginUser) | 获取当前登录的账号 | v10.3.0
[getLoginStatus](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getLoginStatus) | 获取当前登录状态 | v10.3.0
[getConnectStatus](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getConnectStatus) | 获取当前登录连接状态 | v10.3.0
[getChatroomLinkAddress](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getChatroomLinkAddress) | 获取聊天室连接地址 | v10.3.0
[setReconnectDelayProvider](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#setReconnectDelayProvider) | 设置登录重连延时的回调函数 | v10.3.0
[getCurrentLoginClient](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getCurrentLoginClient) | 查询当前登录终端的相关信息 | v10.9.0
:::
::::::

### 多端登录与互踢

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[getLoginClients](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginClients) | 获取当前多端登录列表 | v10.2.0
[kickOffline](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#kickOffline) | 主动将同时在线的其他客户端踢下线 | v10.2.0
[getKickedOfflineDetail](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getKickedOfflineDetail) | 获取被踢下线的具体信息 | v10.2.0
[getDataSync](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getDataSync) | 获取当前多端登录同步详情 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[getLoginClients](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginClients) | 获取当前多端登录列表 | v0.5.0
[kickOffline](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#kickOffline) | 主动将同时在线的其他客户端踢下线 | v0.5.0
[getKickedOfflineDetail](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getKickedOfflineDetail) | 获取被踢下线的具体信息 | v0.5.0
[getDataSync](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getDataSync) | 获取当前多端登录同步详情 |v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[getLoginClients](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getLoginClients) | 获取当前多端登录列表 | v10.3.0
[kickOffline](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#kickOffline) | 主动将同时在线的其他客户端踢下线 | v10.3.0
[getKickedOfflineDetail](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getKickedOfflineDetail) |获取被踢下线的具体信息 | v10.3.0
[getDataSync](https://doc.yunxin.163.com/messaging2/client-apis/Dc3NDM0NTI?platform=client#getDataSync) |获取当前多端登录同步详情 | v10.3.0
:::
::::::

## 云端会话

- 提供创建、删除、更新、获取会话，会话未读数、置顶会话、注册会话监听等接口。
- 提供创建、删除、更新、获取会话分组，注册会话分组监听等接口。

### 云端会话监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addConversationListener](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#addConversationListener) | 注册会话相关监听器 | v10.2.0
[removeConversationListener](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#addConversationListener#removeConversationListener) | 取消注册会话相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#on) | 注册会话相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#off) | 取消注册会话相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#listen) | 注册云端会话相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#cancel) | 取消注册云端会话相关监听器 | v10.3.0
:::
::::::

### 云端会话操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#createConversation) | 创建一条空会话 | v10.2.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversation) | 删除一条会话 | v10.2.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversationListByIds) | 批量删除会话列表 | v10.2.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversation) | 获取单条会话 | v10.2.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList) | 获取会话列表 | v10.2.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByOption) | 获取指定会话列表 | v10.2.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByIds) | 根据会话 ID 批量获取会话列表 | v10.2.0
[updateConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversation) | 更新会话服务端扩展字段 | v10.2.0
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversationLocalExtension) | 更新会话本地扩展字段 | v10.2.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation) | 置顶会话 | v10.2.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getStickTopConversationList) | 查询当前置顶的全量云端会话列表 | <li>Android/iOS/Web：v10.9.0<li>macOS/Windows/Electron：v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#createConversation) | 创建一条空会话 | v0.5.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversation) | 删除一条会话 | v0.5.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversationListByIds) | 批量删除会话列表 | v0.5.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversation) | 获取单条会话 | v0.5.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList) | 获取会话列表 | v0.5.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByOption) | 获取指定会话列表 | v0.5.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByIds) | 根据会话 ID 批量获取会话列表 | v0.5.0
[updateConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversation) | 更新会话服务端扩展字段 | v0.5.0
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversationLocalExtension) | 更新会话本地扩展字段 |  v0.5.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation) | 置顶会话 | v0.5.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getStickTopConversationList) | 查询当前置顶的全量云端会话列表 | v10.9.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#createConversation) | 创建一条空会话 | v10.3.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#deleteConversation) | 删除一条会话 | v10.3.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#deleteConversationListByIds) | 批量删除会话列表 | v10.3.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getConversation) | 获取单条会话 | v10.3.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getConversationList) | 获取会话列表 | v10.3.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getConversationListByOption) | 获取指定会话列表 | v10.3.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getConversationListByIds) | 根据会话 ID 批量获取会话列表 | v10.3.0
[updateConversation](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#updateConversation) | 更新会话服务端扩展字段 | v10.3.0
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#updateConversationLocalExtension) | 更新会话本地扩展字段 | v10.3.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#stickTopConversation) | 置顶会话 | v10.3.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getStickTopConversationList) | 查询当前置顶的全量云端会话列表 | v10.9.0
:::
::::::

### 云端会话未读数

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getTotalUnreadCount) | 获取全部会话的消息总未读数 | v10.2.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getUnreadCountByIds) | 获取指定会话列表的消息总未读数 | v10.2.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的未读信息 | v10.2.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearTotalUnreadCount) | 清空所有会话总的未读数 | v10.2.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) | 清空指定会话列表的消息总未读数 | v10.2.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByTypes) | 根据会话类型清除指定会话类型的所有未读数 | v10.2.0
[clearUnreadCountByGroupId](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByGroupId) | 根据会话分组 ID 清除分组内所有会话的消息总未读数 | v10.2.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#subscribeUnreadCountByFilter) | 订阅过滤后的会话未读数变化 | v10.2.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅过滤后的会话未读数变化 | v10.2.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#markConversationRead) | 标记会话已读时间戳 | v10.3.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationReadTime) | 获取会话已读时间戳 | v10.3.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getTotalUnreadCount) | 获取全部会话的消息总未读数 | v0.5.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getUnreadCountByIds) | 获取指定会话列表的消息总未读数 | v0.5.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的未读信息 | v0.5.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearTotalUnreadCount) | 清空所有会话总的未读数 | v0.5.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) | 清空指定会话列表的消息总未读数 | v0.5.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByTypes) | 根据会话类型清除指定会话类型的所有未读数 | v0.5.0
[clearUnreadCountByGroupId](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByGroupId) | 根据会话分组 ID 清除分组内所有会话的消息总未读数 | v0.5.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#subscribeUnreadCountByFilter) | 订阅过滤后的会话未读数变化 | v0.5.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅过滤后的会话未读数变化 | v0.5.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#markConversationRead) | 标记会话已读时间戳 | v1.2.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationReadTime) | 获取会话已读时间戳 | v1.2.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getTotalUnreadCount) | 获取全部会话的消息总未读数 | v10.3.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getUnreadCountByIds) | 获取指定会话列表的消息总未读数 | v10.3.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的消息未读数 | v10.3.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#clearTotalUnreadCount) | 清空所有会话总的未读数 | v10.3.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#clearUnreadCountByIds) | 清空指定会话列表的消息总未读数 | v10.3.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#clearUnreadCountByTypes)| 根据会话类型清除指定会话类型的所有未读数|v10.3.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#subscribeUnreadCountByFilter) | 订阅过滤后的会话未读数变化 | v10.3.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅过滤后的会话未读数变化 | v10.3.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#markConversationRead) | 标记会话已读时间戳 | v10.3.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#getConversationReadTime) | 获取会话已读时间戳 | v10.3.0
[clearUnreadCountByGroupId](https://doc.yunxin.163.com/messaging2/client-apis/TgwNjUyODQ?platform=client#clearUnreadCountByGroupId)| 根据会话分组 ID 清除分组内所有会话的消息总未读数| v10.8.0
:::
::::::

### 云端会话分组监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addConversationGroupListener](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#addConversationGroupListener) | 注册会话分组监听器 | v10.2.0
[removeConversationGroupListener](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#removeConversationGroupListener) | 取消注册会话分组监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#on) | 注册会话分组监听器 | v10.2.0 | v0.6.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#off) | 取消注册会话分组监听器 | v10.2.0 | v0.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#listen) | 注册云端会话分组监听器 | v10.6.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#cancel) | 移除云端会话分组监听器 | v10.6.0
:::
::::::

### 云端会话分组操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#createConversationGroup) | 创建一个会话分组 | v10.2.0
[deleteConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#deleteConversationGroup) | 删除指定会话分组 | v10.2.0
[updateConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#updateConversationGroup) | 更新指定会话分组 | v10.2.0
[addConversationsToGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#addConversationsToGroup) | 将会话添加到分组 | v10.2.0
[removeConversationsFromGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#removeConversationsFromGroup) | 将会话从分组中移除 | v10.2.0
[getConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroup) | 获取单个指定会话分组信息 | v10.2.0
[getConversationGroupList](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroupList) | 获取全部会话分组列表 | v10.2.0
[getConversationGroupListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroupListByIds) | 批量获取指定会话分组列表 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#createConversationGroup) | 创建一个会话分组 | v0.6.0
[deleteConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#deleteConversationGroup) | 删除指定会话分组 | v0.6.0
[updateConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#updateConversationGroup) | 更新指定会话分组 | v0.6.0
[addConversationsToGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#addConversationsToGroup) | 将会话添加到分组 | v0.6.0
[removeConversationsFromGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#removeConversationsFromGroup) | 将会话从分组中移除 | v0.6.0
[getConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroup) | 获取单个指定会话分组信息 | v0.6.0
[getConversationGroupList](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroupList) | 获取全部会话分组列表 | v0.6.0
[getConversationGroupListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TAwNjM5MDc?platform=client#getConversationGroupListByIds) | 批量获取指定会话分组列表 | v0.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#createConversationGroup) | 创建一个云端会话分组 | v10.6.0
[deleteConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#deleteConversationGroup) | 删除指定云端会话分组 | v10.6.0
[updateConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#updateConversationGroup) | 更新指定云端会话分组 | v10.6.0
[addConversationsToGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#addConversationsToGroup) | 将云端会话添加到分组 | v10.6.0
[removeConversationsFromGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#removeConversationsFromGroup) | 将云端会话从分组中移除 | v10.6.0
[getConversationGroup](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#getConversationGroup) | 获取单个指定云端会话分组信息 | v10.6.0
[getConversationGroupList](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#getConversationGroupList) | 获取全部云端会话分组列表 | v10.6.0
[getConversationGroupListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zc2NDkxNjM?platform=client#getConversationGroupListByIds) | 批量获取指定云端会话分组列表 | v10.6.0
:::
::::::

## 本地会话

提供创建、删除、更新、获取、置顶本地会话，本地会话消息未读数相关、注册本地会话监听等接口。

### 本地会话监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addConversationListener](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#addConversationListener) | 注册本地会话相关监听器 | v10.8.0
[removeConversationListener](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#removeConversationListener) | 取消注册本地会话相关监听器 | v10.8.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#on) | 注册本地会话相关监听器 | v10.8.0 | v1.3.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#off) | 取消注册本地会话相关监听器 | v10.8.0 | v1.3.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#listen) | 注册本地会话相关监听器 | v10.6.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#cancel) | 取消注册本地会话相关监听器 | v10.6.0
:::
::::::

### 本地会话操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#createConversation) | 创建一条空本地会话 | v10.8.0
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#updateConversationLocalExtension) | 更新本地会话的本地扩展信息 | v10.8.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#deleteConversation) | 删除一条本地会话 | v10.8.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#deleteConversationListByIds) | 根据会话 ID 批量删除本地会话列表 | v10.8.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#stickTopConversation) | 置顶本地会话 | v10.8.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversation) | 根据会话 ID 获取单条本地会话 | v10.8.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationList) | 获取所有本地会话列表 | v10.8.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationListByIds) | 根据会话 ID 批量获取本地会话列表 | v10.8.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationListByOption) | 根据指定的筛选条件获取本地会话列表 | v10.8.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getStickTopConversationList) | 查询当前置顶的全量本地会话列表 | <li>Android/iOS/Web：v10.9.0<li>macOS/Windows/Electron：v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#createConversation) | 创建一条空本地会话 | v1.3.0
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#updateConversationLocalExtension) | 更新本地会话的本地扩展信息 | v1.3.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#deleteConversation) | 删除一条本地会话 | v1.3.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#deleteConversationListByIds) | 根据会话 ID 批量删除本地会话列表 | v1.3.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#stickTopConversation) | 置顶本地会话 | v1.3.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversation) | 根据会话 ID 获取单条本地会话 | v1.3.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationList) | 获取所有本地会话列表 | v1.3.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationListByIds) | 根据会话 ID 批量获取本地会话列表 | v1.3.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationListByOption) | 根据指定的筛选条件获取本地会话列表 | v1.3.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getStickTopConversationList) | 查询当前置顶的全量本地会话列表 | v10.9.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createConversation](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#createConversation) | 创建一条空本地会话 | v10.6.0 
[updateConversationLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#updateConversationLocalExtension) | 更新会话的本地扩展信息 | v10.6.0
[deleteConversation](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#deleteConversation) | 删除一条本地会话 | v10.6.0
[deleteConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#deleteConversationListByIds) | 根据会话 ID 批量删除本地会话列表 | v10.6.0
[stickTopConversation](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#stickTopConversation) | 置顶会话 | v10.6.0
[getConversation](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getConversation) | 根据会话 ID 获取单条本地会话 | v10.6.0
[getConversationList](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getConversationList) | 获取所有本地会话列表 | v10.6.0
[getConversationListByIds](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getConversationListByIds) | 根据会话 ID 批量获取本地会话列表 | v10.6.0
[getConversationListByOption](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getConversationListByOption) | 根据指定的筛选条件获取本地会话列表 | v10.6.0
[getStickTopConversationList](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getStickTopConversationList) | 查询当前置顶的全量本地会话列表 | v10.9.0
:::
::::::

### 本地会话未读数

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getTotalUnreadCount) | 获取全部本地会话的消息总未读数 | v10.8.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getUnreadCountByIds) | 根据会话 ID 获取指定本地会话的消息总未读数 |v10.8.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的本地会话的消息未读数 | v10.8.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearTotalUnreadCount) | 清除所有本地会话的消息总未读数 | v10.8.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearUnreadCountByIds) | 根据会话 ID 清除指定本地会话列表的消息未读数 | v10.8.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearUnreadCountByTypes) | 根据会话类型清除指定本地会话类型的消息未读数 | v10.8.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#subscribeUnreadCountByFilter) | 订阅指定过滤条件的本地会话消息未读数变化 | v10.8.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅指定过滤条件的本地会话消息未读数变化 | v10.8.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#markConversationRead) | 标记本地会话已读时间戳 | v10.8.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationReadTime) | 获取本地会话已读时间戳 | v10.8.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getTotalUnreadCount) | 获取全部本地会话的消息总未读数 | v1.3.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getUnreadCountByIds) | 根据会话 ID 获取指定本地会话的消息总未读数 | v1.3.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的本地会话的消息未读数 | v1.3.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearTotalUnreadCount) | 清除所有本地会话的消息总未读数 | v1.3.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearUnreadCountByIds) | 根据会话 ID 清除指定本地会话列表的消息未读数 | v1.3.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#clearUnreadCountByTypes) | 根据会话类型清除指定本地会话类型的消息未读数 | v1.3.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#subscribeUnreadCountByFilter) | 订阅指定过滤条件的本地会话消息未读数变化 | v1.3.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅指定过滤条件的本地会话消息未读数变化 | v1.3.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#markConversationRead) | 标记本地会话已读时间戳 | v1.3.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/TIyMDA1Nzg?platform=client#getConversationReadTime) | 获取本地会话已读时间戳 | v1.3.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[getTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getTotalUnreadCount) | 获取全部本地会话的消息总未读数 | v10.6.0
[getUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getUnreadCountByIds) | 根据会话 ID 获取指定本地会话的消息总未读数 | v10.6.0
[getUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getUnreadCountByFilter) | 根据过滤参数获取相应的消息未读数 | v10.6.0
[clearTotalUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#clearTotalUnreadCount) | 清除所有本地会话的消息总未读数 | v10.6.0
[clearUnreadCountByIds](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#clearUnreadCountByIds) | 根据会话 ID 清除指定本地会话列表的消息未读数 | v10.6.0
[clearUnreadCountByTypes](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#clearUnreadCountByTypes) | 根据会话类型清除指定本地会话类型的消息未读数 | v10.6.0
[subscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#subscribeUnreadCountByFilter) | 订阅指定过滤条件的本地会话消息未读数变化 | v10.6.0
[unsubscribeUnreadCountByFilter](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#unsubscribeUnreadCountByFilter) | 取消订阅指定过滤条件的本地会话消息未读数变化 | v10.6.0
[markConversationRead](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#markConversationRead) | 标记本地会话已读时间戳 | v10.6.0
[getConversationReadTime](https://doc.yunxin.163.com/messaging2/client-apis/DI2NTcwNTM?platform=client#getConversationReadTime) | 获取本地会话已读时间戳 | v10.6.0
:::
::::::

## 消息

- 提供消息构建接口，支持构建多种类型的消息。

- 提供消息操作接口，包括发送、回复、转发、删除、更新、获取消息，注册消息监听，以及 PIN 消息、快捷评论、收藏等进阶操作接口。

### 消息构建

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTextMessage) | 创建一条文本消息 | v10.2.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createImageMessage) | 创建一条图片消息 | v10.2.0 
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createAudioMessage) | 创建一条语音消息 | v10.2.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createVideoMessage) | 创建一条视频消息 | v10.2.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createFileMessage) | 创建一条文件消息 | v10.2.0 
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createLocationMessage) | 创建一条地理位置消息 | v10.2.0 
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessage) | 创建一条自定义消息 | v10.2.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createForwardMessage) | 创建一条转发消息 | v10.2.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTipsMessage) | 创建一条提示消息 | v10.2.0
[createCallMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCallMessage) | 创建一条话单消息 | <li>Android/iOS/Web：v10.2.6<li>macOS/Windows/Electron：v10.3.0
[createCustomMessageWithAttachment](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessageWithAttachment) | 构造自定义消息 | v10.5.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTextMessage) | 创建一条文本消息 | v0.5.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createImageMessage) | 创建一条图片消息 | v0.5.0
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createAudioMessage) | 创建一条语音消息 | v0.5.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createVideoMessage) | 创建一条视频消息 | v0.5.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createFileMessage) | 创建一条文件消息 | v0.5.0
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createLocationMessage) | 创建一条地理位置消息 | v0.5.0
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessage) | 创建一条自定义消息 | v0.5.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createForwardMessage) | 创建一条转发消息 | v0.5.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTipsMessage) | 创建一条提示消息 | v0.5.0
[createCallMessage](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCallMessage) | 创建一条话单消息 | v1.4.0
[createCustomMessageWithAttachment](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessageWithAttachment) | 构造自定义消息 | v10.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createTextMessage) | 创建一条文本消息 | v10.3.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createImageMessage) | 创建一条图片消息 | v10.3.0
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createAudioMessage) | 创建一条语音消息 | v10.3.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createVideoMessage) | 创建一条视频消息 | v10.3.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createFileMessage) | 创建一条文件消息 | v10.3.0
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createLocationMessage) | 创建一条地理位置消息 | v10.3.0
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createCustomMessage) | 创建一条自定义消息 | v10.3.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=clienthttps://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createForwardMessage) | 创建一条转发消息 | v10.3.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createTipsMessage) | 创建一条提示消息 | v10.3.0
[createCallMessage](https://doc.yunxin.163.com/messaging2/client-apis/zc4MjgwMTM?platform=client#createCallMessage) | 创建一条话单消息 | v10.3.0
:::
::::::

### 消息监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addMessageListener](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addMessageListener) | 注册消息相关监听器 | v10.2.0
[removeMessageListener](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeMessageListener) | 取消注册消息相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#on) | 注册消息相关监听器 | v10.2.0 |v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#off) | 取消注册消息相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#listen) | 注册消息相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#cancel) | 取消注册消息相关监听器 | v10.3.0
::: 
::::::

### 消息基础操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | 发送单条消息 | v10.2.0
[revokeMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage) | 撤回指定消息 | v10.2.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList) | 按条件分页获取会话内所有历史消息 | v10.2.0
[getMessageListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByIds) | 根据消息客户端 ID 获取历史消息（Web 端不支持） | v10.2.0
[deleteMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessage) | 删除单条消息 | v10.2.0
[deleteMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages) | 批量删除消息 | v10.2.0
[clearHistoryMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage) | 清空会话内历史消息 | v10.2.0
[updateMessageLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension) | 更新消息本地扩展字段（Web 端不支持） | v10.2.0
[insertMessageToLocal](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#insertMessageToLocal) | 插入一条本地消息（Web 端不支持） | v10.2.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v10.2.0
[modifyMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#modifyMessage) | 更新消息，对消息进行二次编辑 | v10.4.0
[getMessageListEx](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListEx) | 按条件分页获取会话内所有历史消息<br>注： 较 `getMessageList` 方法，返回中新增下次查询的锚点消息 | <li>Android/iOS/Web：v10.9.0<li>macOS/Windows/Electron：v10.9.10
[updateLocalMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateLocalMessage) | 更新本地插入的消息（Web 端不支持）| v10.9.10
[getCloudMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateLocalMessage) | 按条件分页获取会话内的云端消息 | v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | 发送单条消息 | v0.5.0 
[revokeMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage) | 撤回指定消息 | v0.5.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList) | 按条件分页获取会话内所有历史消息 | v0.5.0
[getMessageListByIds](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByIds) | 根据消息客户端 ID 获取历史消息 | v0.5.0
[deleteMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessage) | 删除单条消息 | v0.5.0
[deleteMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages) | 批量删除消息 | v0.5.0
[clearHistoryMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage) | 清空会话内历史消息 | v0.5.0
[updateMessageLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension) | 更新消息本地扩展字段 | v0.5.0
[insertMessageToLocal](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#insertMessageToLocal) | 插入一条本地消息 | v0.5.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v0.5.0
[modifyMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#modifyMessage) | 更新消息，对消息进行二次编辑 | v10.0.0
[getMessageListEx](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListEx) | 按条件分页获取会话内所有历史消息<br>注： 较 `getMessageList` 方法，返回中新增下次查询的锚点消息 | v10.9.0
[updateLocalMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateLocalMessage) | 更新本地插入的消息 | v10.9.10
[getCloudMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateLocalMessage) | 按条件分页获取会话内的云端消息 | v10.9.10
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendMessage) | 发送单条消息 | v10.3.0
[revokeMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#revokeMessage) | 撤回指定消息 | v10.3.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getMessageList) | 按条件分页获取会话内所有历史消息 | v10.3.0
[getMessageListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getMessageListByIds) | 根据消息客户端 ID 获取历史消息 | v10.3.0
[deleteMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#deleteMessage) | 删除单条消息 | v10.3.0
[deleteMessages](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#deleteMessages) | 批量删除消息 | v10.3.0
[clearHistoryMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#clearHistoryMessage) | 清空会话内历史消息 | v10.3.0
[updateMessageLocalExtension](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#updateMessageLocalExtension) | 更新消息本地扩展字段 | v10.3.0
[insertMessageToLocal](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#insertMessageToLocal) | 插入一条本地消息 | v10.3.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v10.3.0
[modifyMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#modifyMessage) | 更新消息，对消息进行二次编辑 | v10.5.0
[getMessageListEx](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getMessageListEx) | 按条件分页获取会话内所有历史消息<br>注： 较 `getMessageList` 方法，返回中新增下次查询的锚点消息 | v10.9.0
[updateLocalMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#updateLocalMessage) | 更新本地插入的消息 | v10.9.0
::: 
::::::

### 消息扩展操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[replyMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#replyMessage) | 回复指定消息 | v10.2.0
[getMessageListByRefers](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByRefers) | 根据消息参考信息批量获取消息列表 | v10.2.0
[pinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#pinMessage) | Pin 一条消息 | v10.2.0
[unpinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unpinMessage) | 取消 PIN 一条消息 | v10.2.0
[updatePinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updatePinMessage) | 更新一条 PIN 消息 | v10.2.0
[getPinnedMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getPinnedMessageList) | 获取会话内所有 PIN 消息 | v10.2.0
[addQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addQuickComment) | 添加一条快捷评论 | v10.2.0
[removeQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeQuickComment) | 移除一条快捷评论 | v10.2.0
[getQuickCommentList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getQuickCommentList) | 获取指定消息的快捷评论列表 | v10.2.0
[addCollection](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addCollection) | 添加一个收藏 | v10.2.0
[removeCollections](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeCollections) | 移除收藏 | v10.2.0
[updateCollectionExtension](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateCollectionExtension) | 更新收藏扩展字段 | v10.2.0
[getCollectionListByOption](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListByOption) | 根据条件分页获取收藏列表 | v10.2.0
[getCollectionListExByOption](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListExByOption) | 根据条件分页获取收藏列表<br>注：较 `getCollectionListByOption` 方法，回参新增 `totalCount` 字段，表示收藏总数 | v10.7.0 
[sendP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendP2PMessageReceipt) | 发送单聊消息已读回执 | v10.2.0
[getP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getP2PMessageReceipt) | 获取单聊消息已读回执 | v10.2.0
[isPeerRead](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#isPeerRead) | 获取单聊消息是否已读 | v10.2.0
[sendTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendTeamMessageReceipts) | 发送群组消息已读回执 | v10.2.0
[getTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceipts) | 获取群组消息已读回执数量 | v10.2.0
[getTeamMessageReceiptDetail](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceiptDetail) | 获取群组消息已读回执状态详情 | v10.2.0
[searchCloudMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages) | 全文搜索云端历史消息 | v10.2.0
[getThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getThreadMessageList) | 分页获取云端 Thread 历史消息列表 | <li>Android/iOS/Web：v10.2.6<li>macOS/Windows/Electron：v10.3.0 |
[getLocalThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getLocalThreadMessageList) | 分页获取本地 Thread 历史消息列表（除 Web 端） | <li>Android/iOS：v10.2.6<li>macOS/Windows/Electron：v10.3.0 |
[searchLocalMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchLocalMessages) | 全文搜索本地历史消息（除 Web 端） | v10.7.0
[searchCloudMessagesEx](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessagesEx) | 全文搜索云端历史消息<br>注： 较 `searchCloudMessages` 方法，入参支持传入多个 keyword | v10.8.30
[stopAIStreamMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#stopAIStreamMessage) | 打断 AI 数字人消息的流式输出，可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息 | v10.8.30
[regenAIMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#regenAIMessage) | 重新输出 AI 数字人消息 | v10.8.30
[setMessageFilter](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#setMessageFilter) | 消息过滤器（iOS 端不支持） | <li>Android/Web：v10.9.0<li>macOS/Windows/Electron：v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[replyMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#replyMessage) | 回复指定消息 | v0.5.0
[getMessageListByRefers](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByRefers) | 根据消息参考信息批量获取消息列表 |v0.5.0
[pinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#pinMessage) | Pin 一条消息 | v0.5.0
[unpinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unpinMessage) | 取消 PIN 一条消息 | v0.5.0
[updatePinMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updatePinMessage) | 更新一条 PIN 消息 | v0.5.0
[getPinnedMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getPinnedMessageList) | 获取会话内所有 PIN 消息 | v0.5.0
[addQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addQuickComment) | 添加一条快捷评论 | v0.5.0
[removeQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeQuickComment) | 移除一条快捷评论 | v0.5.0
[getQuickCommentList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getQuickCommentList) | 获取指定消息的快捷评论列表 | v0.5.0
[addCollection](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addCollection) | 添加一个收藏 | v0.5.0
[removeCollections](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeCollections) | 移除收藏 |v0.5.0
[updateCollectionExtension](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateCollectionExtension) | 更新收藏扩展字段 | v0.5.0
[getCollectionListByOption](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListByOption) | 根据条件分页获取收藏列表 | v0.5.0
[sendP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendP2PMessageReceipt) | 发送单聊消息已读回执 | v0.5.0
[getP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getP2PMessageReceipt) | 获取单聊消息已读回执 | v0.5.0
[isPeerRead](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#isPeerRead) | 获取单聊消息是否已读 | v0.5.0
[sendTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendTeamMessageReceipts) | 发送群组消息已读回执 | v0.5.0
[getTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceipts) | 获取群组消息已读回执 | v0.5.0
[getTeamMessageReceiptDetail](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceiptDetail) | 获取群组消息已读回执状态详情 | v0.5.0
[searchCloudMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages) | 全文搜索云端历史消息 | v0.5.0
[getThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getThreadMessageList) | 分页获取云端 Thread 历史消息列表 | v1.4.0
[getLocalThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getLocalThreadMessageList) | 分页获取本地 Thread 历史消息列表 | v1.4.0
[searchLocalMessages](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchLocalMessages) | 全文搜索本地历史消息 | v10.6.0
[searchCloudMessagesEx](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessagesEx) | 全文搜索云端历史消息<br>注： 较 `searchCloudMessages` 方法，入参支持传入多个 keyword | v10.8.30
[stopAIStreamMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#stopAIStreamMessage) | 打断 AI 数字人消息的流式输出，可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息 | v10.8.30
[regenAIMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#regenAIMessage) | 重新输出 AI 数字人消息 | v10.8.30
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[replyMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#replyMessage) | 回复指定消息 | v10.3.0
[getMessageListByRefers](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getMessageListByRefers) | 根据消息参考信息批量获取消息列表 | v10.3.0
[pinMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#pinMessage) | Pin 一条消息 | v10.3.0
[unpinMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#unpinMessage) | 取消 PIN 一条消息 | v10.3.0
[updatePinMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#updatePinMessage) | 更新一条 PIN 消息 | v10.3.0
[getPinnedMessageList](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getPinnedMessageList) | 获取会话内所有 PIN 消息 | v10.3.0
[addQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#addQuickComment) | 添加一条快捷评论 | v10.3.0
[removeQuickComment](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#removeQuickComment) | 移除一条快捷评论 | v10.3.0
[getQuickCommentList](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getQuickCommentList) | 获取指定消息的快捷评论列表 | v10.3.0
[addCollection](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#addCollection) | 添加一个收藏 | v10.3.0
[removeCollections](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#removeCollections) | 移除收藏 | v10.3.0
[updateCollectionExtension](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#updateCollectionExtension) | 更新收藏扩展字段 | v10.3.0
[getCollectionListByOption](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getCollectionListByOption) | 根据条件分页获取收藏列表 | v10.3.0
[sendP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendP2PMessageReceipt) | 发送单聊消息已读回执 | v10.3.0
[getP2PMessageReceipt](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getP2PMessageReceipt) | 获取单聊消息已读回执 | v10.3.0
[isPeerRead](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#isPeerRead) | 获取单聊消息是否已读 | v10.3.0
[sendTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendTeamMessageReceipts) | 发送群组消息已读回执 | v10.3.0
[getTeamMessageReceipts](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getTeamMessageReceipts) | 获取群组消息已读回执 | v10.3.0
[getTeamMessageReceiptDetail](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getTeamMessageReceiptDetail) | 获取群组消息已读回执状态详情 | v10.3.0
[searchCloudMessages](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#searchCloudMessages) | 全文搜索云端历史消息 | v10.3.0
[getThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getThreadMessageList) | 分页获取云端 Thread 历史消息列表 |v10.3.0 |
[getLocalThreadMessageList](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getLocalThreadMessageList) | 分页获取本地 Thread 历史消息列表 |v10.3.0 |
[stopAIStreamMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#stopAIStreamMessage) | 打断 AI 数字人消息的流式输出，可选择直接停止输出，也可以选择撤回/更新 AI 数字人消息 | v10.8.0
[regenAIMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#regenAIMessage) | 重新输出 AI 数字人消息 | v10.8.0
[getCollectionListExByOption](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#getCollectionListExByOption) | 根据条件分页获取收藏列表<br>注：较 `getCollectionListByOption` 方法，回参新增 `totalCount` 字段，表示收藏总数 | v10.9.0
[searchCloudMessages](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#searchCloudMessages) | 全文搜索云端历史消息 | v10.9.0
[setMessageFilter](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#setMessageFilter) | 消息过滤器 | v10.9.0
[searchCloudMessagesEx](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#searchCloudMessagesEx) | 全文搜索云端历史消息<br>注： 较 `searchCloudMessages` 方法，入参支持传入多个 `keyword` | v10.9.0
[searchLocalMessages](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#searchLocalMessages) | 全文搜索本地历史消息 | v10.9.0
::: 
::::::

### 消息解析相关

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[registerCustomAttachmentParser](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#registerCustomAttachmentParser) | 注册自定义消息附件解析器，解析自消息类型为 100 的消息附件 | v10.5.0 |
[unregisterCustomAttachmentParser](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unregisterCustomAttachmentParser) | 反注册自定义消息附件解析器 | v10.5.0 |
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[registerCustomAttachmentParser](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#registerCustomAttachmentParser) | 注册自定义消息附件解析器，解析自消息类型为 100 的消息附件 | v10.6.0 |
[unregisterCustomAttachmentParser](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unregisterCustomAttachmentParser) | 反注册自定义消息附件解析器 | v10.6.0 |
:::
::: code Flutter
暂不支持
:::
::::::

### 消息序列化

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[messageSerialization](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#messageSerialization) | 消息序列化为字符串 | v10.5.0 |
[messageDeserialization](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#messageSerialization) | 消息字符串转换为消息 | v10.5.0 |
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[messageSerialization](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#messageSerialization) | 消息序列化为字符串 | v10.6.0 |
[messageDeserialization](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#messageDeserialization) | 消息字符串转换为消息 | v10.6.0 |
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[messageSerialization](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#messageSerialization) | 消息序列化为字符串 | v10.5.0 |
[messageDeserialization](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#messageDeserialization) | 消息字符串转换为消息 | v10.5.0 |
:::
::::::

## 系统通知

提供自定义通知相关接口。

### 系统通知监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addNoticationListener](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#addNoticationListener) | 注册系统通知相关监听器 | v10.2.0
[removeNotificationListener](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#removeNotificationListener) | 取消注册系统通知相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#on) | 注册系统通知相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#off) | 取消注册系统通知相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/DQ5OTgxNjE?platform=client#listen) | 注册系统通知相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/DQ5OTgxNjE?platform=client#cancel) | 取消注册系统通知相关监听器 | v10.3.0
:::
::::::

### 系统通知发送

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[sendCustomNotification](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#sendCustomNotification) | 发送自定义系统通知 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[sendCustomNotification](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#sendCustomNotification) | 发送自定义系统通知 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[sendCustomNotification](https://doc.yunxin.163.com/messaging2/client-apis/DQ5OTgxNjE?platform=client#sendCustomNotification) | 发送自定义系统通知 | v10.3.0
:::
::::::

## 群组

提供群组相关接口，包括注册群组监听，创建、修改、退出、解散、加入群组、获取群组相关信息等接口。

### 群组监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addTeamListener](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#addTeamListener) | 注册群组相关监听器 | v10.2.0
[removeTeamListener](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#removeTeamListener) | 取消注册群组相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#on) | 注册群组相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#off) | 取消注册群组相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#listen) | 注册群组相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#cancel) | 取消注册群组相关监听器 | v10.3.0
:::
::::::

### 群组操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#createTeam) | 创建一个群组 | v10.2.0
[updateTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo) | 修改群组信息 | v10.2.0
[leaveTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam) | 退出群组 | v10.2.0
[getTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo) | 获取群组信息 | v10.2.0
[getTeamInfoByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfoByIds) | 根据群组 ID 批量获取群组信息 | v10.2.0
[dismissTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#dismissTeam) | 解散群组 | v10.2.0
[inviteMember](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember) | 邀请成员加入群组 | v10.2.0
[acceptInvitation](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation) | 接受入群邀请 | v10.2.0
[rejectInvitation](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation) | 拒绝入群邀请 | v10.2.0
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember) | 踢出群成员 | v10.2.0
[applyJoinTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam) | 申请加入群组 | v10.2.0
[acceptJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication) | 同意入群申请 | v10.2.0
[rejectJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication) | 拒绝入群申请 | v10.2.0
[updateTeamMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) | 修改群成员角色 | v10.2.0
[transferTeamOwner](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner) | 转让群主身份 | v10.2.0
[updateSelfTeamMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo) | 修改自己的群成员信息 | v10.2.0
[updateTeamMemberNick](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick) | 修改群成员昵称 | v10.2.0
[setTeamChatBannedMode](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode) | 设置群组禁言模式 | v10.2.0
[setTeamMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus) | 设置群成员聊天禁言状态 | v10.2.0
[getJoinedTeamList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList) | 获取当前已经加入的群组列表 | v10.2.0
[getJoinedTeamCount](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamCount) | 获取当前已经加入的群组数量 | v10.2.0
[getTeamMemberList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) | 分页获取群组成员列表 | v10.2.0
[getTeamMemberListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds) | 根据账号批量获取群组成员列表 | v10.2.0
[getTeamMemberInvitor](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberInvitor) | 根据账号获取群组成员邀请人 | v10.2.0
[getTeamJoinActionInfoList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamJoinActionInfoList) | 获取入群操作相关信息列表 | v10.2.0
[searchTeamByKeyword](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#searchTeamByKeyword) | 根据关键字搜索群信息（包括高级群和超大群） | v10.3.0
[searchTeamMembers](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#searchTeamMembers) | 根据关键字搜索群成员（包括高级群和超大群） | v10.3.0
[addTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#addTeamMembersFollow) | 添加特别关注的群成员列表 | v10.5.0
[removeTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#removeTeamMembersFollow) | 移除特别关注的群成员列表 | v10.5.0
[clearAllTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#clearAllTeamJoinActionInfo) | 清空所有入群申请 | v10.6.0
[deleteTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#deleteTeamJoinActionInfo) | 删除指定的入群申请 | v10.6.0
[inviteMemberEx](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMemberEx) | 邀请成员加入群组 | v10.8.10
[getJoinedTeamMembers](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamMembers) | 查询自己加入的群组的成员信息列表 | v10.9.10
[setTeamJoinActionInfoRead](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamJoinActionInfoRead) | 设置群申请已读 | v10.9.20
[getTeamJoinActionInfoUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamJoinActionInfoUnreadCount) | 获取未读的群申请/邀请数量 | v10.9.20
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#createTeam) | 创建一个群组 | v0.5.0
[updateTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo) | 修改群组信息 | v0.5.0
[leaveTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam) | 退出群组 | v0.5.0
[getTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo) | 获取群组信息 | v0.5.0
[getTeamInfoByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfoByIds) | 根据群组 ID 批量获取群组信息 | v0.5.0
[dismissTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#dismissTeam) | 解散群组 | v0.5.0
[inviteMember](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember) | 邀请成员加入群组 | v0.5.0
[acceptInvitation](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation) | 接受入群邀请 | v0.5.0
[rejectInvitation](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation) | 拒绝入群邀请 | v0.5.0
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember) | 踢出群成员 | v0.5.0
[applyJoinTeam](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam) | 申请加入群组 | v0.5.0
[acceptJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication) | 同意入群申请 | v0.5.0
[rejectJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication) | 拒绝入群申请 | v0.5.0
[updateTeamMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) | 修改群成员角色 | v0.5.0
[transferTeamOwner](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner) | 转让群主身份 | v0.5.0
[updateSelfTeamMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo) | 修改自己的群成员信息 | v0.5.0
[updateTeamMemberNick](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick) | 修改群成员昵称 | v0.5.0
[setTeamChatBannedMode](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode) | 设置群组禁言模式 | v0.5.0
[setTeamMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus) | 设置群成员聊天禁言状态 | v0.5.0
[getJoinedTeamList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList) | 获取当前已经加入的群组列表 | v0.5.0
[getJoinedTeamCount](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamCount) | 获取当前已经加入的群组数量 | v0.5.0
[getTeamMemberList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) | 分页获取群组成员列表 | v0.5.0
[getTeamMemberListByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds) | 根据账号批量获取群组成员列表 | v0.5.0
[getTeamMemberInvitor](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberInvitor) | 根据账号获取群组成员邀请人 | v0.5.0
[getTeamJoinActionInfoList](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamJoinActionInfoList) | 获取入群操作相关信息列表 | v0.5.0
[searchTeamByKeyword](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#searchTeamByKeyword) | 根据关键字搜索群信息（包括高级群和超大群） | v10.0.0
[searchTeamMembers](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#searchTeamMembers) | 根据关键字搜索群成员（包括高级群和超大群） |  v10.0.0
[addTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#addTeamMembersFollow) | 添加特别关注的群成员列表 | 10.9.20
[removeTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#removeTeamMembersFollow) | 移除特别关注的群成员列表 | 10.9.20
[clearAllTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#clearAllTeamJoinActionInfo) | 清空所有入群申请 | v10.6.0
[deleteTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#deleteTeamJoinActionInfo) | 删除指定的入群申请 | v10.6.0
[inviteMemberEx](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMemberEx) | 邀请成员加入群组 | v10.8.10
[getJoinedTeamMembers](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamMembers) | 查询自己加入的群组的成员信息列表 | v10.9.10
[setTeamJoinActionInfoRead](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamJoinActionInfoRead) | 设置群申请已读 | v10.9.20
[getTeamJoinActionInfoUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamJoinActionInfoUnreadCount) | 获取未读的群申请/邀请数量 | v10.9.20
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createTeam](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#createTeam) | 创建一个群组 | v10.3.0
[updateTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#updateTeamInfo) | 修改群组信息 | v10.3.0
[leaveTeam](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#leaveTeam) | 退出群组 | v10.3.0
[getTeamInfo](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamInfo) | 获取群组信息 | v10.3.0
[getTeamInfoByIds](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamInfoByIds) | 根据群组 ID 批量获取群组信息 | v10.3.0
[dismissTeam](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#dismissTeam) | 解散群组 | v10.3.0
[inviteMember](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#inviteMember) | 邀请成员加入群组 | v10.3.0
[acceptInvitation](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#acceptInvitation) | 接受入群邀请 | v10.3.0
[rejectInvitation](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#rejectInvitation) | 拒绝入群邀请 | v10.3.0
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#kickMember) | 踢出群成员 | v10.3.0
[applyJoinTeam](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#applyJoinTeam) | 申请加入群组 | v10.3.0
[acceptJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#acceptJoinApplication) | 同意入群申请 | v10.3.0
[rejectJoinApplication](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#rejectJoinApplication) | 拒绝入群申请 | v10.3.0
[updateTeamMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#updateTeamMemberRole) | 修改群成员角色 | v10.3.0
[transferTeamOwner](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#transferTeamOwner) | 转让群主身份 | v10.3.0
[updateSelfTeamMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#updateSelfTeamMemberInfo) | 修改自己的群成员信息 | v10.3.0
[updateTeamMemberNick](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#updateTeamMemberNick) | 修改群成员昵称 | v10.3.0
[setTeamChatBannedMode](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#setTeamChatBannedMode) | 设置群组禁言模式 | v10.3.0
[setTeamMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#setTeamMemberChatBannedStatus) | 设置群成员聊天禁言状态 | v10.3.0
[getJoinedTeamList](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getJoinedTeamList) | 获取当前已经加入的群组列表 | v10.3.0
[getJoinedTeamCount](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getJoinedTeamCount) | 获取当前已经加入的群组数量 | v10.3.0
[getTeamMemberList](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamMemberList) | 分页获取群组成员列表 | v10.3.0
[getTeamMemberListByIds](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamMemberListByIds) | 根据账号批量获取群组成员列表 | v10.3.0
[getTeamMemberInvitor](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamMemberInvitor) | 根据账号获取群组成员邀请人 | v10.3.0
[getTeamJoinActionInfoList](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#getTeamJoinActionInfoList) | 获取入群操作相关信息列表 | v10.3.0
[searchTeamByKeyword](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#searchTeamByKeyword) | 根据关键字搜索群信息（包括高级群和超大群） | v10.3.0
[searchTeamMembers](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#searchTeamMembers) | 根据关键字搜索群成员（包括高级群和超大群） | v10.3.0
[addTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#addTeamMembersFollow) | 添加特别关注的群成员列表 | v10.9.0
[removeTeamMembersFollow](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#removeTeamMembersFollow) | 移除特别关注的群成员列表 | v10.9.0
[clearAllTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#clearAllTeamJoinActionInfo) | 清空所有入群申请 | v10.9.0
[deleteTeamJoinActionInfo](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#deleteTeamJoinActionInfo) | 删除指定的入群申请 | v10.9.0	
[inviteMemberEx](https://doc.yunxin.163.com/messaging2/client-apis/DE1MjU0NzY?platform=client#inviteMemberEx) | 邀请成员加入群组 | v10.9.0
:::
::::::

## 用户

提供用户资料相关接口，包括注册用户资料监听，获取、更新用户资料，拉黑用户等接口。

### 用户资料监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addUserListener](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#addUserListener) | 注册用户资料相关监听器 | v10.2.0
[removeUserListener](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#removeUserListener) | 取消注册用户资料相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#on) | 注册用户资料相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#off) | 取消用户资料相关监听器 | v10.2.0 |　v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#listen) | 注册用户资料相关监听器 | v10.3.0 |
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#cancel) | 取消注册用户资料相关监听器 | v10.3.0 |
::: 
::::::

### 用户资料操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[getUserList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList) | 根据用户账号 ID 列表获取用户资料 | v10.2.0
[updateSelfUserProfile ](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#updateSelfUserProfile ) | 更新自己的用户资料 | v10.2.0
[addUserToBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#addUserToBlockList) | 添加指定用户进黑名单 | v10.2.0
[removeUserFromBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#removeUserFromBlockList) | 将指定用户移出黑名单 | v10.2.0
[getBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList) | 获取黑名单用户列表 | v10.2.0
[searchUserByOption](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#searchUserByOption) | 根据关键字信息搜索用户信息 | v10.2.2
[getUserListFromCloud](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserListFromCloud) | 根据用户账号列表从服务器获取用户信息 | <li>Android/iOS/Web：v10.2.6<li>macOS/Windows/Electron：v10.3.1
[checkBlock](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#checkBlock) | 查看指定用户是否在黑名单中 | <li>Android/iOS/Web：v10.9.0<li>macOS/Windows/Electron：v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[getUserList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList) | 根据用户账号 ID 列表获取用户资料 | v0.5.0
[updateSelfUserProfile ](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#updateSelfUserProfile ) | 更新自己的用户资料 | v0.5.0
[addUserToBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#addUserToBlockList) | 添加指定用户进黑名单 | v0.5.0
[removeUserFromBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#removeUserFromBlockList) | 将指定用户移出黑名单 | v0.5.0
[getBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList) | 获取黑名单用户列表 | v0.5.0
[searchUserByOption](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#searchUserByOption) | 根据关键字信息搜索用户信息 | v1.4.0
[getUserListFromCloud](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserListFromCloud) | 根据用户账号列表从服务器获取用户信息 | v1.4.0
[checkBlock](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#checkBlock) | 查看指定用户是否在黑名单中 | v10.9.0
:::
::: code  Flutter
API | 说明 | 起始版本
---- | ---- | ----
[getUserList](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#getUserList) | 根据用户账号 ID 列表获取用户资料 | v10.3.0
[updateSelfUserProfile](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#updateSelfUserProfile ) | 更新自己的用户资料 | v10.3.0
[addUserToBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#addUserToBlockList) | 添加指定用户进黑名单 | v10.3.0
[removeUserFromBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#removeUserFromBlockList) | 将指定用户移出黑名单 | v10.3.0
[getBlockList](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#getBlockList) | 获取黑名单用户列表 | v10.3.0
[searchUserByOption](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#searchUserByOption)| 根据关键字信息搜索用户信息 | v10.3.0
[getUserListFromCloud](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#getUserListFromCloud)| 根据用户账号列表从服务器获取用户信息 | v10.3.0
[checkBlock](https://doc.yunxin.163.com/messaging2/client-apis/jE0MTIzODg?platform=client#checkBlock) | 查看指定用户是否在黑名单中 | v10.9.0
::: 
::::::

## 用户状态订阅

提供用户状态订阅相关接口，包括注册用户状态订阅监听，获取、订阅用户状态，发布自定义状态等接口。

### 用户状态订阅监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addSubscribeListener](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#addSubscribeListener) | 注册用户状态订阅相关监听器 | v10.4.0 |
[removeSubscribeListener](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#removeSubscribeListener) | 取消注册用户状态订阅相关监听器 | v10.4.0 |
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#on) | 注册用户状态订阅相关监听器 | v10.4.0 | v10.6.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#off) | 取消用户状态订阅相关监听器 | v10.4.0 | v10.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#listen) | 注册用户状态订阅相关监听器 | v10.3.4 |
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#cancel) | 取消注册用户状态订阅相关监听器 | v10.3.4 |
:::
::::::

### 用户状态订阅操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[subscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#subscribeUserStatus) | 订阅用户状态 | v10.4.0
[unsubscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#unsubscribeUserStatus ) | 取消订阅用户状态 | v10.4.0
[publishCustomUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#publishCustomUserStatus) | 发布用户自定义状态 | v10.4.0
[queryUserStatusSubscriptions](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#queryUserStatusSubscriptions) | 查询用户状态订阅关系 | v10.4.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[subscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#subscribeUserStatus) | 订阅用户状态 | v10.6.0
[unsubscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#unsubscribeUserStatus ) | 取消订阅用户状态 | v10.6.0
[publishCustomUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#publishCustomUserStatus) | 发布用户自定义状态 | v10.6.0
[queryUserStatusSubscriptions](https://doc.yunxin.163.com/messaging2/client-apis/zY2MzAxNjQ?platform=client#queryUserStatusSubscriptions) | 查询用户状态订阅关系 | v10.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[subscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#subscribeUserStatus) | 订阅用户状态 | v10.3.4
[unsubscribeUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#unsubscribeUserStatus ) | 取消订阅用户状态 | v10.3.4
[publishCustomUserStatus](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#publishCustomUserStatus) | 发布用户自定义状态 | v10.3.4
[queryUserStatusSubscriptions](https://doc.yunxin.163.com/messaging2/client-apis/jA3NjI0ODQ?platform=client#queryUserStatusSubscriptions) | 查询用户状态订阅关系 | v10.3.4
:::
::::::

## 好友

提供好友关系相关接口，包括注册好友关系监听，添加、删除好友，接受、拒绝好友申请，获取、设置好友信息等接口。

### 好友关系监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addFriendListener](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriendListener) | 注册好友关系相关监听器 | v10.2.0
[removeFriendListener](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#removeFriendListener) | 取消注册好友关系相关监听器器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#on) | 注册好友关系相关监听器 | v10.2.0 | v0.5.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#off) | 取消注册好友关系相关监听器 | v10.2.0 | v0.5.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#listen) | 注册好友关系相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#cancel) | 取消注册好友关系相关监听器 | v10.3.0
:::
::::::

### 好友关系操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[addFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend) | 添加好友 | v10.2.0
[deleteFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteFriend) | 删除好友 | v10.2.0
[acceptAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#acceptAddApplication) | 接受好友申请 | v10.2.0
[rejectAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#rejectAddApplication) | 拒绝好友申请 | v10.2.0
[setFriendInfo ](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setFriendInfo ) | 设置好友信息 | v10.2.0
[getFriendList](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendList) | 获取好友列表 | v10.2.0
[getFriendByIds](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendByIds) | 根据账号 ID 获取好友信息列表 | v10.2.0
[checkFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#checkFriend) | 根据账号 ID 查询好友状态 | v10.2.0
[getAddApplicationList](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationList) | 获取申请添加好友信息列表 | v10.2.0
[getAddApplicationUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationUnreadCount) | 获取未读的好友申请数量 | <li>Android/iOS: v10.2.1<li>macOS/Windows/Web/Electron: v10.2.2
[setAddApplicationRead](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setAddApplicationRead) | 设置好友申请已读 | <li>Android/iOS: v10.2.1<li>macOS/Windows/Web/Electron: v10.2.2
[searchFriendByOption](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#searchFriendByOption) | 根据关键字信息搜索好友信息 | v10.2.2
[clearAllAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#clearAllAddApplication) | 清空所有好友申请 | v10.6.0
[deleteAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteAddApplication) | 删除指定的好友申请 | v10.6.0
[setAddApplicationReadEx](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setAddApplicationReadEx) | 设置好友申请已读 | v10.9.20
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[addFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend) | 添加好友 | v0.5.0
[deleteFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteFriend) | 删除好友 | v0.5.0
[acceptAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#acceptAddApplication) | 接受好友申请 |v0.5.0
[rejectAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#rejectAddApplication) | 拒绝好友申请 | v0.5.0
[setFriendInfo ](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setFriendInfo ) | 设置好友信息 | v0.5.0
[getFriendList](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendList) | 获取好友列表 | v0.5.0
[getFriendByIds](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendByIds) | 根据账号 ID 获取好友信息列表 | v0.5.0
[checkFriend](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#checkFriend) | 根据账号 ID 查询好友状态 | v0.5.0
[getAddApplicationList](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationList) | 获取申请添加好友信息列表 | v0.5.0
[getAddApplicationUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationUnreadCount) | 获取未读的好友申请数量 | v0.5.0
[setAddApplicationRead](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setAddApplicationRead) | 设置好友申请已读 | v0.5.0
[searchFriendByOption](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#searchFriendByOption) | 根据关键字信息搜索好友信息 | v1.4.0
[clearAllAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#clearAllAddApplication) | 清空所有好友申请 | v10.6.0
[deleteAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteAddApplication) | 删除指定的好友申请 | v10.6.0
[setAddApplicationReadEx](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setAddApplicationReadEx) | 设置好友申请已读 | v10.9.20
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[addFriend](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#addFriend) | 添加好友 | v10.3.0
[deleteFriend](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#deleteFriend) | 删除好友 | v10.3.0
[acceptAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#acceptAddApplication) | 接受好友申请 | v10.3.0
[rejectAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#rejectAddApplication) | 拒绝好友申请 | v10.3.0
[setFriendInfo ](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#setFriendInfo ) | 设置好友信息 | v10.3.0
[getFriendList](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#getFriendList) | 获取好友列表 | v10.3.0
[getFriendByIds](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#getFriendByIds) |根据账号 ID 获取好友信息列表 | v10.3.0
[checkFriend](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#checkFriend) | 根据账号 ID 查询好友状态 | v10.3.0
[getAddApplicationList](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#getAddApplicationList) | 获取申请添加好友信息列表 | v10.3.0
[getAddApplicationUnreadCount](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#getAddApplicationUnreadCount) | 获取未读的好友申请数量 | v10.3.0
[setAddApplicationRead](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#setAddApplicationRead) | 设置好友申请已读 | v10.3.0
[searchFriendByOption](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#searchFriendByOption) | 根据关键字信息搜索好友信息 | v10.3.0
[deleteAddApplication](https://doc.yunxin.163.com/messaging2/client-apis/TU2MTgyNzg?platform=client#deleteAddApplication) | 删除指定的好友申请 | v10.9.0
:::
::::::

## AI 数字人

提供 AI 数字人相关接口。数字人既可以是虚拟的 AI 对话伙伴、高效的协同工作助手、也可定制贴合业务所需更高安全性的本地大模型。

### AI 数字人监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addAIListener](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#addAIListener) | 注册 AI 数字人相关监听器 | v10.3.0
[removeAIListener](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#removeAIListener) | 取消注册 AI 数字人相关监听器器 | v10.3.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#on) | 注册 AI 数字人关系相关监听器 | v10.3.0 | v10.6.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#off) | 取消注册 AI 数字人关系相关监听器 | v10.3.0 | v10.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#listen) | 注册 AI 数字人相关监听器 | v10.3.0 |
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#cancel) | 取消注册 AI 数字人相关监听器 | v10.3.0 |
:::
::::::

### AI 数字人操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[getAIUserList](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#getAIUserList) | 根据用户账号 ID 列表获取 AI 数字人 | v10.3.0
[proxyAIModelCall](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#proxyAIModelCall) | AI 数字人向 LLM 发起查询请求 | v10.3.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | AI 数字人发送消息 | v10.3.0
[stopAIModelStreamCall](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求 | v10.8.30
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[getAIUserList](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#getAIUserList) | 根据用户账号 ID 列表获取 AI 数字人 | v10.6.0
[proxyAIModelCall](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#proxyAIModelCall) | AI 数字人向 LLM 发起查询请求 | v10.6.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) | AI 数字人发送消息 | v10.6.0
[stopAIModelStreamCall](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求 | v10.8.30
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[getAIUserList](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#getAIUserList) | 根据用户账号 ID 列表获取 AI 数字| v10.3.0
[proxyAIModelCall](https://doc.yunxin.163.com/messaging2/client-apis/DAyMDc1MjE?platform=client#proxyAIModelCall ) | AI 数字人向 LLM 发起查询请求 | v10.3.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#sendMessage) | AI 数字人发送消息 | v10.3.0
[stopAIModelStreamCall](https://doc.yunxin.163.com/messaging2/client-apis/TU1MDAxMjA?platform=client#stopAIModelStreamCall) | 停止 AI 流式输出请求 | v10.8.0
:::
::::::

## 系统设置

提供系统设置相关接口，包括设置单聊/群聊消息免打扰模式、获取单聊/群聊消息免打扰模式、获取单聊消息免打扰列表、获取会话消息的免打扰状态等接口。

### 系统设置监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addSettingListener](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#addSettingListener) | 注册系统设置相关监听器 | v10.2.0
[removeSettingListener](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#removeSettingListener) | 取消注册系统设置相关监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#on) | 注册系统设置相关监听器 | v10.2.0 | v0.6.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#off) | 取消注册系统设置相关监听器 | v10.2.0 | v0.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[listen](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#listen) | 注册系统设置相关监听器 | v10.3.0
[cancel](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#cancel) | 取消注册系统设置相关监听器 | v10.3.0
:::
::::::

### 系统设置操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[setP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setP2PMessageMuteMode) | 设置单聊消息免打扰模式 | v10.2.0
[getP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getP2PMessageMuteMode) | 获取单聊消息免打扰模式 | v10.2.0
[getP2PMessageMuteList](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getP2PMessageMuteList) | 获取开启单聊消息免打扰的用户列表 | v10.2.0
[setTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setTeamMessageMuteMode) | 设置群消息免打扰模式 | v10.2.0
[getTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getTeamMessageMuteMode) | 获取群消息免打扰模式 | v10.2.0
[getConversationMuteStatus](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getConversationMuteStatus) | 获取会话消息免打扰状态 | v10.2.0
[setAppBackground](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setAppBackground) | 设置应用前后台状态（仅 Web 端） | v10.2.0
[setPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setPushMobileOnDesktopOnline) | 设置当桌面端在线时，移动端是否需要推送 | v10.2.0
[setOfflinePushConfig](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setOfflinePushConfig) | 设置离线推送配置信息（仅 Web 端） | v10.2.0
[setDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setDndConfig) | 设置推送全局免打扰（除 Web 端） | v10.2.0
[getDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getDndConfig) | 获取推送免打扰配置信息（除 Web 端） | <li>Android/iOS：v10.2.4<li>macOS/Windows/Electron：v10.3.1
[getAllTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getAllTeamMessageMuteMode) | 查询自己所在的所有群组的消息免打扰模式 | v10.9.10
[getPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getPushMobileOnDesktopOnline) | 获取当桌面端在线时，移动端是否需要推送 | v10.9.10
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[setP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setP2PMessageMuteMode) | 设置单聊消息免打扰模式 | v0.6.0
[getP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getP2PMessageMuteMode) | 获取单聊消息免打扰模式 | v0.6.0
[getP2PMessageMuteList](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getP2PMessageMuteList) | 获取开启单聊消息免打扰的用户列表 | v0.6.0
[setTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setTeamMessageMuteMode) | 设置群消息免打扰模式 | v0.6.0
[getTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getTeamMessageMuteMode) | 获取群消息免打扰模式 | v0.6.0
[getConversationMuteStatus](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getConversationMuteStatus) | 获取会话消息免打扰状态 | v0.6.0
[setPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setPushMobileOnDesktopOnline) | 设置当桌面端在线时，移动端是否需要推送 | v0.6.0
[setDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setDndConfig) | 设置推送全局免打扰 | v0.6.0
[getDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getDndConfig) | 获取推送免打扰配置信息 | v0.6.0
[getAllTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getAllTeamMessageMuteMode) | 查询自己所在的所有群组的消息免打扰模式 | v10.9.10
[getPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getPushMobileOnDesktopOnline) | 获取当桌面端在线时，移动端是否需要推送 | v10.9.10
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[setP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setP2PMessageMuteMode) | 设置单聊消息免打扰模式 | v10.3.0
[getP2PMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getP2PMessageMuteMode) | 获取单聊消息免打扰模式 | v10.3.0
[getP2PMessageMuteList](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getP2PMessageMuteList) | 获取开启单聊消息免打扰的用户列表 | v10.3.0
[setTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setTeamMessageMuteMode) | 设置群消息免打扰模式 | v10.3.0
[getTeamMessageMuteMode](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getTeamMessageMuteMode) | 获取群消息免打扰模式 | v10.3.0
[getConversationMuteStatus](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getConversationMuteStatus) | 获取会话消息免打扰状态 | v10.3.0
[setPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setPushMobileOnDesktopOnline) | 设置当桌面端在线时，移动端是否需要推送 | v10.3.0
[setDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setDndConfig) | 设置推送全局免打扰 | v10.3.0
[getDndConfig](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getDndConfig) | 获取推送免打扰配置信息 | v10.3.0
[setAppBackground](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setAppBackground) | 设置应用前后台状态 | v10.9.0
[getPushMobileOnDesktopOnline](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#getPushMobileOnDesktopOnline) | 获取当桌面端在线时，移动端是否需要推送 | v10.9.0
<!--未做
[setOfflinePushConfig](https://doc.yunxin.163.com/messaging2/client-apis/DA5NDU0NTc?platform=client#setOfflinePushConfig) | 设置离线推送配置信息 | v10.3.0
-->
:::
::::::

## 存储服务

提供存储服务相关接口。

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[addCustomStorageScene](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#addCustomStorageScene) | 添加自定义存储场景 | v10.2.0
[getStorageSceneList](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getStorageSceneList) | 获取存储场景列表 | v10.2.0
[createUploadFileTask](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#createUploadFileTask) | 创建文件上传任务 | v10.2.0
[uploadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#uploadFile) | 上传文件 | v10.2.0
[cancelUploadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#cancelUploadFile) | 取消文件上传 | v10.2.0
[downloadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#downloadFile) | 下载文件（除 Web 端） | <li>Android/iOS：v10.2.6<li>macOS/Windows/Electron：10.3.0
[shortUrlToLong](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#shortUrlToLong) | 短链接转长链接 | <li>Android/iOS/Web：v10.2.3<li>macOS/Windows/Electron：10.3.0
[imageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#imageThumbUrl) | 生成图片缩略图链接 | <li>Android/iOS/Web：v10.2.6<li>macOS/Windows/Electron：10.3.0
[videoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#videoCoverUrl) | 生成视频封面图链接 | <li>Android/iOS/Web：v10.2.6<li>macOS/Windows/Electron：10.3.0
[downloadAttachment](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#downloadAttachment) | 下载消息附件 | v10.3.0
[getImageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getImageThumbUrl) | 获取图片消息中的缩略图链接 | v10.3.0
[getVideoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getVideoCoverUrl) | 获取视频消息中的视频封面链接 | v10.3.0
[uploadFileWithMetaInfo](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#uploadFileWithMetaInfo) | 上传文件并返回资源信息（仅 Web） | v10.6.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[addCustomStorageScene](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#addCustomStorageScene) | 添加自定义存储场景 | v0.5.0
[getStorageSceneList](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getStorageSceneList) | 获取存储场景列表 | v0.5.0
[createUploadFileTask](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#createUploadFileTask) | 创建文件上传任务 | v0.5.0
[uploadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#uploadFile) | 上传文件 | v0.5.0
[cancelUploadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#cancelUploadFile) | 取消文件上传 | v0.5.0
[downloadFile](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#downloadFile) | 下载文件 | v1.4.0
[shortUrlToLong](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#shortUrlToLong) | 短链接转长链接 | v1.4.0
[imageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#imageThumbUrl) | 生成图片缩略图链接 | v1.3.0
[videoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#videoCoverUrl) | 生成视频封面图链接 | v1.3.0
[downloadAttachment](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#downloadAttachment) | 下载消息附件 | v10.0.0
[getImageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getImageThumbUrl) | 获取图片消息中的缩略图链接 | v10.0.0
[getVideoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#getVideoCoverUrl) | 获取视频消息中的视频封面链接 | v10.0.0
:::
::: code  Flutter
API | 描述 | 起始版本
:---- | :-------------- | :-------------- 
[addCustomStorageScene](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#addCustomStorageScene) | 添加自定义存储场景 | v10.3.0
[getStorageSceneList](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#getStorageSceneList) | 获取存储场景列表 | v10.3.0
[createUploadFileTask](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#createUploadFileTask) | 创建文件上传任务 | v10.3.0
[uploadFile](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#uploadFile) | 上传文件 | v10.3.0
[cancelUploadFile](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#cancelUploadFile) | 取消文件上传 | v10.3.0
[downloadFile](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#downloadFile) | 下载文件 | v10.3.0
[shortUrlToLong](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#shortUrlToLong) | 短链接转长链接 | v10.3.0
[downloadAttachment](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#downloadAttachment)| 下载消息附件 | v10.3.0
[getImageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#getImageThumbUrl)| 获取图片消息中的缩略图链接 | v10.3.0
[getVideoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#getVideoCoverUrl)| 获取视频消息中的视频封面链接 | v10.3.0
[imageThumbUrl](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#imageThumbUrl) | 生成图片缩略图链接 | v10.9.0
[videoCoverUrl](https://doc.yunxin.163.com/messaging2/client-apis/TUwMzk0MDg?platform=client#videoCoverUrl) | 生成视频封面图链接 | v10.9.0
:::
::::::

## 聊天室

- 提供群组相关接口，包括注册/注销聊天室实例监听，创建、进入、退出、销毁聊天室等接口。

- 提供聊天室服务接口，包括注册/注销聊天室监听器、收发聊天室消息、管理聊天室成员、维护聊天室信息等。

- 提供聊天室消息构建接口，支持构建多种类型的聊天室消息。

### 聊天室实例监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addChatroomClientListener](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#addChatroomClientListener) | 注册聊天室实例监听器 | v10.2.0
[removeChatroomClientListener](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#removeChatroomClientListener) | 取消注册聊天室实例监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#on) | 注册聊天室实例监听器 | v10.2.0 | v1.0.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#off) | 取消注册聊天室实例监听器 | v10.2.0 | v1.0.0
:::
::: code Flutter 
API | 说明 | 起始版本
---- | ---- | ----
[addChatroomClientListener](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#addChatroomClientListener) | 注册聊天室实例监听器 | v10.5.0
[removeChatroomClientListener](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#removeChatroomClientListener) | 取消注册聊天室实例监听器 | v10.5.0
:::
::::::

### 聊天室实例

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[newInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#newInstance) | 构造一个新的聊天室实例 | v10.2.0
[destroyInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyInstance) | 销毁指定聊天室实例 | v10.2.0
[getInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstance) | 获取指定聊天室实例 | v10.2.0
[getInstanceList](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstanceList) | 获取当前已经存在的聊天室实例列表 | v10.2.0
[destroyAll](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyAll) | 销毁当前的所有聊天室实例 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[newInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#newInstance) | 构造一个新的聊天室实例 | v1.0.0
[destroyInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyInstance) | 销毁指定聊天室实例 | v1.0.0
[getInstance](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstance) | 获取指定聊天室实例 | v1.0.0
[getInstanceList](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstanceList) | 获取当前已经存在的聊天室实例列表 | v1.0.0
[destroyAll](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyAll) | 销毁当前的所有聊天室实例 | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[newInstance](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#newInstance) | 构造一个新的聊天室实例 | v10.5.0
[destroyInstance](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#destroyInstance) | 销毁指定聊天室实例 | v10.5.0
[getInstance](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getInstance) | 获取指定聊天室实例 | v10.5.0
[getInstanceList](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getInstanceList) | 获取当前已经存在的聊天室实例列表 | v10.5.0
[destroyAll](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#destroyAll) | 销毁当前的所有聊天室实例 | v10.5.0
:::
::::::

### 聊天室监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addChatroomListener](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#addChatroomListener) | 注册聊天室监听器 | v10.2.0
[removeChatroomListener](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#removeChatroomListener) | 取消注册聊天室监听器 | v10.2.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | Web/uni-app/小程序/Node.js/Electron 起始版本 | HarmonyOS 起始版本
---- | ---- | ---- | ----
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#on) | 注册聊天室监听器 | v10.2.0 | v1.0.0
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#off) | 取消注册聊天室监听器 | v10.2.0 | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[addChatroomListener](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#addChatroomListener) | 注册聊天室监听器 | v10.5.0
[removeChatroomListener](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#removeChatroomListener) | 取消注册聊天室监听器 | v10.5.0
:::
::::::

### 聊天室操作

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[enter](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#enter) | 进入聊天室 | v10.2.0
[exit](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#exit) | 退出聊天室 | v10.2.0
[getChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getChatroomInfo) | 获取聊天室信息 | v10.2.0
[getInstanceId](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstanceId) | 获取聊天室实例 ID | v10.2.0
[getChatroomService](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getChatroomService) | 获取聊天室服务（除 Web 端） | v10.2.0
[getStorageService](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getStorageService) | 获取 IM 存储服务（除 Web 端） | v10.2.0
[getChatroomQueueService](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getChatroomQueueService) | 获取聊天室队列服务（除 Web 端） | v10.6.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[enter](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#enter) | 进入聊天室 | v1.0.0
[exit](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#exit) | 退出聊天室 | v1.0.0
[getChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getChatroomInfo) | 获取聊天室信息 | v1.0.0
[getInstanceId](https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstanceId) | 获取聊天室实例 ID | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[enter](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#enter) | 进入聊天室 | v10.5.0
[exit](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#exit) | 退出聊天室 | v10.5.0
[getChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getChatroomInfo) | 获取聊天室信息 | v10.5.0
[getInstanceId](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getInstanceId) | 获取聊天室实例 ID | v10.5.0
[getChatroomService](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getChatroomService) | 获取聊天室服务 | v10.5.0
[getStorageService](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getStorageService) | 获取 IM 存储服务 | v10.5.0
[getChatroomQueueService](https://doc.yunxin.163.com/messaging2/client-apis/zE5NTI4MjU?platform=client#getChatroomQueueService) | 获取聊天室队列服务 | v10.5.0
:::
::::::

### 聊天室消息

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createTextMessage) | 创建一条文本消息 | v10.2.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createImageMessage) | 创建一条图片消息 | v10.2.0
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createAudioMessage) | 创建一条语音消息 | v10.2.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createVideoMessage) | 创建一条视频消息 | v10.2.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createFileMessage) | 创建一条文件消息 | v10.2.0
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createLocationMessage) | 创建一条地理位置消息 | v10.2.0
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createCustomMessage) | 创建一条自定义消息 | v10.2.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createForwardMessage) | 创建一条转发消息 | v10.2.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createTipsMessage) | 创建一条提示消息 | v10.2.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#sendMessage) | 发送聊天室消息 | v10.2.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v10.2.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageList) | 分页获取聊天室历史消息 | v10.2.0
[getMessageListByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageListByTag) | 根据标签分页获取聊天室消息列表 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createTextMessage) | 创建一条文本消息 | v1.0.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createImageMessage) | 创建一条图片消息 | v1.0.0
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createAudioMessage) | 创建一条语音消息 | v1.0.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createVideoMessage) | 创建一条视频消息 | v1.0.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createFileMessage) | 创建一条文件消息 | v1.0.0
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createLocationMessage) | 创建一条地理位置消息 | v1.0.0
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createCustomMessage) | 创建一条自定义消息 | v1.0.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createForwardMessage) | 创建一条转发消息 | v1.0.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/jE1MTA1MDY?platform=client#createTipsMessage) | 创建一条提示消息 | v1.0.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#sendMessage) | 发送聊天室消息 | v1.0.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v1.0.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageList) | 分页获取聊天室历史消息 | v1.0.0
[getMessageListByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageListByTag) | 根据标签分页获取聊天室消息列表 | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[createTextMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createTextMessage) | 创建一条文本消息 | v10.5.0
[createImageMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createImageMessage) | 创建一条图片消息 | v10.5.0
[createAudioMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createAudioMessage) | 创建一条语音消息 | v10.5.0
[createVideoMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createVideoMessage) | 创建一条视频消息 | v10.5.0
[createFileMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createFileMessage) | 创建一条文件消息 | v10.5.0
[createLocationMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createLocationMessage) | 创建一条地理位置消息 | v10.5.0
[createCustomMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createCustomMessage) | 创建一条自定义消息 | v10.5.0
[createForwardMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createForwardMessage) | 创建一条转发消息 | v10.5.0
[createTipsMessage](https://doc.yunxin.163.com/messaging2/client-apis/TAxMjQ2Mzk?platform=client#createTipsMessage) | 创建一条提示消息 | v10.5.0
[sendMessage](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#sendMessage) | 发送聊天室消息 | v10.5.0
[cancelMessageAttachmentUpload](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#cancelMessageAttachmentUpload) | 取消文件类附件上传 | v10.5.0
[getMessageList](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMessageList) | 分页获取聊天室历史消息 | v10.5.0
[getMessageListByTag](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMessageListByTag) | 根据标签分页获取聊天室消息列表 | v10.5.0
:::
::::::

### 聊天室成员

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#kickMember) | 将成员踢出聊天室 | v10.2.0
[getMemberListByOption](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByOption) | 分页获取聊天室成员列表 | v10.2.0
[getMemberByIds](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberByIds) | 批量获取聊天室成员列表 | v10.2.0
[getMemberListByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByTag) | 根据标签分页获取聊天室成员列表 | v10.2.0
[getMemberCountByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberCountByTag) | 根据标签获取聊天室成员数量 | v10.2.0
[updateMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateMemberRole) | 更新聊天室成员角色 | v10.2.0
[setMemberBlockedStatus](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberBlockedStatus) | 设置聊天室成员黑名单状态 | v10.2.0
[setMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberChatBannedStatus) | 设置聊天室成员禁言状态 | v10.2.0
[setMemberTempChatBanned](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberTempChatBanned) | 设置聊天室成员临时禁言状态 | v10.2.0
[setTempChatBannedByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setTempChatBannedByTag) | 设置指定标签下的聊天室成员临时禁言状态 | v10.2.0
[updateSelfMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateSelfMemberInfo) | 更新本人的聊天室成员信息 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#kickMember) | 将成员踢出聊天室 | v1.0.0
[getMemberListByOption](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByOption) | 分页获取聊天室成员列表 | v1.0.0
[getMemberByIds](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberByIds) | 批量获取聊天室成员列表 | v1.0.0
[getMemberListByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByTag) | 根据标签分页获取聊天室成员列表 | v1.0.0
[getMemberCountByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberCountByTag) | 根据标签获取聊天室成员数量 | v1.0.0
[updateMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateMemberRole) | 更新聊天室成员角色 | v1.0.0
[setMemberBlockedStatus](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberBlockedStatus) | 设置聊天室成员黑名单状态 | v1.0.0
[setMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberChatBannedStatus) | 设置聊天室成员禁言状态 | v1.0.0
[setMemberTempChatBanned](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberTempChatBanned) | 设置聊天室成员临时禁言状态 | v1.0.0
[setTempChatBannedByTag](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setTempChatBannedByTag) | 设置指定标签下的聊天室成员临时禁言状态 | v1.0.0
[updateSelfMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateSelfMemberInfo) | 更新本人的聊天室成员信息 | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[kickMember](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#kickMember) | 将成员踢出聊天室 | v10.5.0
[getMemberListByOption](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMemberListByOption) | 分页获取聊天室成员列表 |v10.5.0
[getMemberByIds](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMemberByIds) | 批量获取聊天室成员列表 | v10.5.0
[getMemberListByTag](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMemberListByTag) | 根据标签分页获取聊天室成员列表 | v10.5.0
[getMemberCountByTag](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#getMemberCountByTag) | 根据标签获取聊天室成员数量 | v10.5.0
[updateMemberRole](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#updateMemberRole) | 更新聊天室成员角色 | v10.5.0
[setMemberBlockedStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#setMemberBlockedStatus) | 设置聊天室成员黑名单状态 | v10.5.0
[setMemberChatBannedStatus](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#setMemberChatBannedStatus) | 设置聊天室成员禁言状态 | v10.5.0
[setMemberTempChatBanned](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#setMemberTempChatBanned) | 设置聊天室成员临时禁言状态 | v10.5.0
[setTempChatBannedByTag](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#setTempChatBannedByTag) | 设置指定标签下的聊天室成员临时禁言状态 | v10.5.0
[updateSelfMemberInfo](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#updateSelfMemberInfo) | 更新本人的聊天室成员信息 | v10.5.0
:::
::::::

### 聊天室信息

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron
API | 说明 | 起始版本
---- | ---- | ----
[updateChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomInfo) | 更新聊天室信息 | v10.2.0
[updateChatroomLocationInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomLocationInfo) | 更新聊天室坐标信息 | v10.2.0
[updateChatroomTags](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomTags) | 更新聊天室标签信息 | v10.2.0
:::
::: code HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[updateChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomInfo) | 更新聊天室信息 | v1.0.0
[updateChatroomLocationInfo](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomLocationInfo) | 更新聊天室坐标信息 | v1.0.0
[updateChatroomTags](https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomTags) | 更新聊天室标签信息 | v1.0.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[updateChatroomInfo](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#updateChatroomInfo) | 更新聊天室信息 | v10.5.0
[updateChatroomLocationInfo](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#updateChatroomLocationInfo) | 更新聊天室坐标信息 | v10.5.0
[updateChatroomTags](https://doc.yunxin.163.com/messaging2/client-apis/TQzMTI2MjU?platform=client#updateChatroomTags) | 更新聊天室标签信息 | v10.5.0
:::
::::::

### 聊天室队列监听

:::::: div linked-codes
::: code Android/iOS/macOS/Windows
API | 说明 | 起始版本
---- | ---- | ----
[addQueueListener](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#addQueueListener) | 注册聊天室队列监听器 | v10.6.0
[removeQueueListener](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#removeQueueListener) | 取消注册聊天室队列监听器 | v10.6.0
:::
::: code Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | 起始版本 
---- | ---- | ---- 
[on("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#on) | 注册聊天室队列监听器 | v10.6.0 
[off("EventName")](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#off) | 取消注册聊天室队列监听器 | v10.6.0 
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[addQueueListener](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#addQueueListener) | 注册聊天室队列监听器 | v10.6.1
[removeQueueListener](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#removeQueueListener) | 取消注册聊天室队列监听器 | v10.6.1
:::
::::::

### 聊天室队列

:::::: div linked-codes
::: code Android/iOS/macOS/Windows/Web/uni-app/小程序/Node.js/Electron/HarmonyOS
API | 说明 | 起始版本
---- | ---- | ----
[queueOffer](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queueOffer) | 在队列中新增或更新元素 | v10.6.0
[queuePoll](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queuePoll) | 在队列中取出头元素或指定的元素 | v10.6.0
[queueList](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queueList) | 排序列出所有元素 | v10.6.0
[queuePeek](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queuePeek) | 查看队列的头元素 | v10.6.0
[queueDrop](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queueDrop) | 清空队列 | v10.6.0
[queueInit](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queueInit) | 初始化队列 | v10.6.0
[queueBatchUpdate](https://doc.yunxin.163.com/messaging2/client-apis/Dk5MjczOTQ?platform=client#queueBatchUpdate) | 批量更新队列元素 | v10.6.0
:::
::: code Flutter
API | 说明 | 起始版本
---- | ---- | ----
[queueOffer](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queueOffer) | 在队列中新增或更新元素 | v10.6.1
[queuePoll](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queuePoll) | 在队列中取出头元素或指定的元素 | v10.6.1
[queueList](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queueList) | 排序列出所有元素 | v10.6.1
[queuePeek](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queuePeek) | 查看队列的头元素 | v10.6.1
[queueDrop](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queueDrop) | 清空队列 | v10.6.1
[queueInit](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queueInit) | 初始化队列 | v10.6.1
[queueBatchUpdate](https://doc.yunxin.163.com/messaging2/client-apis/jU2NTkxNDE?platform=client#queueBatchUpdate) | 批量更新队列元素 | v10.6.1
:::
::::::

## 圈组

请参考 NIM SDK V9 API 文档：

- [Android SDK API](https://doc.yunxin.163.com/messaging2/client-apis/zg0MzYzNzY?platform=android#圈组)

- [iOS SDK API](https://doc.yunxin.163.com/messaging2/client-apis/jY3NTQ0NTU?platform=iOS#圈组)

- [macOS/Windows SDK API](https://doc.yunxin.163.com/messaging2/client-apis/jE3MTEyODM?platform=pc)

- [Web Elite SDK API](https://doc.yunxin.163.com/messaging2-enhanced/docs/Tc5NTI4NzE?platform=web)

## 相关参考

- 如需查看 API 所属类及相关数据结构，请参考 **类/枚举**。
- 如需查看和处理调用 API 时返回的错误码，请参考 [错误码](https://doc.yunxin.163.com/messaging2/client-apis/DUxNjU3MzU?platform=client)。


<style>
    .platform-tabs {
        display: flex;
        justify-content: center;
        align-items: left;
        gap: 14px; /* 间距 */
        margin-top: 20px;
        justify-content: flex-start;：子元素靠左对齐。
        // flex-wrap: wrap; /* 允许标签在必要时换行 */
    }

    .platform-tab {
        display: flex;
        align-items: center;
        padding: 8px 16px; /* 调整内边距 */
        height: 38px; /* 设置固定高度 */
        border: 1px solid #ccc;
        border-radius: 5px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        background-color: #0000;
        font-family: 'Inter', sans-serif;
        font-size: 14px; /* 调整字体大小 */
        cursor: arrow;
        transition: all 0.3s ease;
        white-space: nowrap; /* 防止文字换行 */
    }

    .platform-tab:hover {
        box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
        transform: translateY(-2px);
    }

    .platform-tab img {
        width: 24px;
        height: 24px;
        margin-right: 8px;
    }

    .platform-tab span {
        margin-left: 5px;
        margin-right: 5px;
    }
</style>