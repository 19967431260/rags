本文介绍如何将含圈组功能的网易云信即时通讯 SDK Web 版（简称 NIM Web SDK（含圈组））集成到您的 uni-app 项目。

## SDK 介绍

NIM Web SDK（含圈组）为 NIM Web SDK （以下简称为 **原版**）的重构版本。含圈组版继承了原版的特性，提供完善的即时通讯功能开发框架和简洁的 API 接口，方便您快速将即时通讯功能集成到您的 PC/移动 Web 应用及 NodeJS、微信小程序等跨平台应用。

<!-- NIM Web SDK（含圈组）为 NIM Web SDK （以下简称为**原版**）的重构版本。含圈组继承了原版的特性，提供完善的即时通讯功能开发框架和简洁的 API 接口，方便您快速将即时通讯功能集成到您的 PC/移动 Web 应用及 NodeJS、React Native、微信小程序、字节跳动小程序等跨平台应用。-->

相较于原版，含圈组版做了如下改进：

- 使用 TypeScript 重构（TypeScript 完全兼容 JavaScript 语法），API 出入参数定义更加完善。

    ::: note notice
    uni-app 不支持 TypeScript，目前仅支持在浏览器环境导出 TypeScript 声明。
    :::

- 使用 Promise API 替代回调函数。
- 支持更多开发环境：现支持 IE v11.0.0 及以上版本和 chrome v4.0.0 及以上版本等浏览器，以及微信小程序、支付宝小程序、uni-app 等跨平台开发环境。
    <!-- - 支持更多开发环境：现支持 IE v11.0.0 及以上版本和 chrome v4.0.0 及以上版本等浏览器，以及微信小程序、支付宝小程序、百度智能小程序和字节跳动小程序、uni-app 等跨平台开发环境。-->
- 结构更精简。包体积降至原版 SDK 的 40%。

## 前提条件

如果 uni-app 最终需要编译到 **小程序** 中运行，则开始集成前，需要满足以下条件。如果编译到其他终端运行，请忽略该前提。

确保已在 [微信公众平台](https://mp.weixin.qq.com/?token=&lang=zh_CN) 中进入 **小程序后台 > 开发 > 开发设置 > 服务器域名**，将以下域名填入指定的 **request 合法域名** / **socket 合法域名** / **uploadFile 合法域名** / **downloadFile 合法域名** 中。

微信小程序必须使用的 `lbs` 地址为 `https://lbs.netease.im/lbs/wxwebconf.jsp`。

更多相关说明，请参考《腾讯微信官网》[配置服务器域名](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html)。

::: note note
如果您需要在支付宝运行小程序，请在支付宝开发平台配置服务器域名。
:::

配置分类 | 域名 | 说明
---- | ---- | ----
request 合法域名 | https://lbs.netease.im | 请求 LBS 地址
^^ | https://wlnimsc0.netease.im | IM 必需
^^ | https://wlnimsc0.netease.im:443 | IM 必需
^^ | https://wlnimsc1.netease.im | 聊天室必需
^^ | https://wlnimsc1.netease.im:443 | 聊天室必需
^^ | https://statistic.live.126.net | 数据上报
^^ | https://abt-online.netease.im | 用于 A/B Test
socket 合法域名 | wss://wlnimsc0.netease.im | IM 必需
^^ | wss://wlnimsc1.netease.im | 聊天室必需
uploadFile 合法域名 | https://nos.netease.com<br>https://fileup.chatnos.com<br>https://oss.chatnos.com | 文件上传，如发送文件类消息
downloadFile 合法域名 | https://nim-nosdn.netease.im<br>https://nim.nosdn.127.net  | 文件下载，如下载语音

如果您需要为应用开启消息漫游功能，可以参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/jU3MDY4Njk?platform=console) 前往网易云信控制台开启。

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/3d2c70f816a3a9b0396231b1177dabaa/image.png" style="width:80%;border: 1px solid #BFBFBF;">

## 集成步骤

### 步骤 1：（可选）新建项目

参考 uni-app 官方文档 [新建一个 uni-app 项目](https://uniapp.dcloud.net.cn/faq.html#app%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)。

如果您需要集成到已有项目，请跳过本步骤。

### 步骤 2：安装 SDK

SDK 以 npm 包的形式提供，请前往 [nim-web-sdk-ng](https://www.npmjs.com/package/nim-web-sdk-ng) 获取 npm 包。

通过以下命令安装 SDK。

```Bash
npm install nim-web-sdk-ng@"<1"
```

SDK 结构如下：

```Bash
dist/
├── CHATROOM_BROWSER_SDK.js 聊天室浏览器适配版 UMD 格式
├── CHATROOM_MINIAPP_SDK.js 聊天室小程序适配版 UMD 格式
├── CHATROOM_UNIAPP_SDK.js   聊天室 uni-app 适配版 UMD 格式
├── NIM_BROWSER_SDK.js       IM 浏览器适配版 UMD 格式
├── NIM_MINIAPP_SDK.js       IM 小程序适配版 UMD 格式
├── NIM_UNIAPP_SDK.js        IM uni-app 适配版 UMD 格式
├── QCHAT_BROWSER_SDK.js     圈组浏览器适配版 UMD 格式
```

### 步骤 3：引入 SDK

执行以下命令，按需将适配 uni-app 的 SDK 组件引入到您的项目。

```JavaScript
// IM 能力，包括单聊、群聊、通讯录等
import NIMSDK from 'nim-web-sdk-ng/dist/NIM_UNIAPP_SDK'

// 聊天室相关能力
import ChatroomSDK from 'nim-web-sdk-ng/dist/CHATROOM_UNIAPP_SDK'
```

## 下一步

集成 SDK 后，需初始化 SDK 实例。NIM 实例和 Chatroom 实例需分别使用不同的初始化方法，具体参考：

- [初始化并登录 IM](https://doc.yunxin.163.com/messaging/guide/Tk5NzMyMTE?platform=uniapp)

- [初始化并登录聊天室](https://doc.yunxin.163.com/messaging/guide/zE5MTE4NzI?platform=uniapp)

## 常见问题

### npm 安装报错

Q：执行 npm 命令安装 SDK 失败，出现以下报错信息。

<img alt="download.png" src="https://yx-web-nosdn.netease.im/common/9bec37138d76e022b358ee35125b0e51/download.png" style="width:50%;border: 1px solid #BFBFBF;">

A：出现该问题是由用户侧环境导致，请按照提示执行 `npm fund` 和 `npm audit fix` 即可。

### uni-app 常见问题

请参考《uni-app》官网 [常见问题](https://uniapp.dcloud.net.cn/faq.html#app%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)。