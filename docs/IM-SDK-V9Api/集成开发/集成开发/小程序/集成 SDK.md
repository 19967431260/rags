

本文介绍如何将支持了小程序平台的 NIM Web SDK（含圈组）集成到您的微信或支付宝小程序项目。 


## SDK 简介
NIM Web SDK（含圈组）为 NIM Web SDK （以下简称为“原版”）的重构版本。含圈组版继承了原版的特性，提供完善的即时通讯功能开发框架和简洁的 API 接口，方便您快速将即时通讯功能集成到您的 PC/移动 Web 应用及 NodeJS、微信小程序等跨平台应用。


<!-- NIM Web SDK（含圈组）为 NIM Web SDK （以下简称为“原版”）的重构版本。含圈组版继承了原版的特性，提供完善的即时通讯功能开发框架和简洁的 API 接口，方便您快速将即时通讯功能集成到您的 PC/移动 Web 应用及 NodeJS、React Native、微信小程序、字节跳动小程序等跨平台应用。 -->

相较于原版，含圈组版做了如下改进：

- 使用 TypeScript 重构（TypeScript 完全兼容 JavaScript 语法），API 出入参数定义更加完善。
- 使用 Promise API 替代回调函数。 
- 支持更多开发环境：现支持 IE v11.0.0 及以上版本和 chrome v4.0.0 及以上版本等浏览器，以及微信小程序、支付宝小程序、uni-app 等跨平台开发环境。
<!-- - 支持更多开发环境：现支持 IE v11.0.0 及以上版本和 chrome v4.0.0 及以上版本等浏览器，以及微信小程序、支付宝小程序、百度智能小程序和字节跳动小程序、uniapp等跨平台开发环境。 -->
- 结构更精简。包体积降至原版 SDK 的 40%。



::: note notice
- 小程序不支持 TypeScript，目前仅支持在浏览器环境导出 TypeScript 声明。
- 暂未支持百度小程序和字节跳动小程序。 
:::




## 前提条件


开始集成前，请确保已在[微信公众平台](https://mp.weixin.qq.com/?token=&lang=zh_CN)中进入**小程序后台 > 开发 > 开发设置 > 服务器域名**，将以下域名填入指定的 “request 合法域名” / “socket 合法域名” / “uploadFile 合法域名” / “downloadFile 合法域名” 中。

微信小程序必须使用该 `lbs` 地址: `https://lbs.netease.im/lbs/wxwebconf.jsp`。

更多相关说明，请参见[配置服务器域名](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html)。

::: note note 
如果您需要在支付宝运行小程序，请在支付宝开发平台配置服务器域名。
:::

配置分类| 域名 | 说明
---- | -------------- | ---------
request 合法域名 |  https://lbs.netease.im | 请求 LBS 地址
^^ |  https://wlnimsc0.netease.im  | IM 必需
^^ |  https://wlnimsc0.netease.im:443  | IM 必需
^^  | https://wlnimsc1.netease.im  | 聊天室必需
^^  | https://wlnimsc1.netease.im:443  | 聊天室必需
^^  | https://statistic.live.126.net   | 数据上报
^^   | https://abt-online.netease.im   | 用于 A/B Test 
socket 合法域名 | wss://wlnimsc0.netease.im |  IM 必需
^^ | wss://wlnimsc1.netease.im| 聊天室必需
uploadFile 合法域名 |https://nos.netease.com<br>https://fileup.chatnos.com<br>https://oss.chatnos.com | 文件上传，如发送文件类消息
downloadFile合法域名 | https://nim-nosdn.netease.im<br>https://nim.nosdn.127.net |  文件下载，如下载语音


## 集成步骤



### (可选) 步骤1：新建项目

新建小程序项目。如果需要集成到已有项目，请忽略本步骤。
- [新建微信小程序项目](https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/getstart.html)
- [新建支付宝小程序项目](https://opendocs.alipay.com/mini/developer/getting-started#1.%20%E6%96%B0%E5%BB%BA%E9%A1%B9%E7%9B%AE)


### 步骤2：安装 SDK 

SDK 以 npm 包的形式提供，请前往 [nim-web-sdk-ng](https://www.npmjs.com/package/nim-web-sdk-ng) 获取 npm 包。

通过以下命令安装 SDK。
```
npm install nim-web-sdk-ng@"<1"
```

SDK 结构如下：
```
dist/
├── CHATROOM_BROWSER_SDK.js  聊天室浏览器适配版 UMD 格式
├── CHATROOM_MINIAPP_SDK.js  聊天室小程序适配版 UMD 格式
├── CHATROOM_UNIAPP_SDK.js   聊天室 UNIAPP 适配版 UMD 格式
├── NIM_BROWSER_SDK.js       IM 浏览器适配版 UMD 格式
├── NIM_MINIAPP_SDK.js       IM 小程序适配版 UMD 格式
├── NIM_UNIAPP_SDK.js        IM UNIAPP 适配版 UMD 格式
├── QCHAT_BROWSER_SDK.js     圈组浏览器适配版 UMD 格式
```


::: note notice
这里的小程序适配版，仅支持微信和支付宝小程序。
:::

### 步骤3：引入 SDK 




:::::: div custom-tabs
::: tab 微信小程序

1. 按需将 node_modules/nim-web-sdk-ng/dist/NIM_MINIAPP_SDK，或者 node_modules/nim-web-sdk-ng/dist/CHATROOM_MINIAPP_SDK 拷贝到项目路径中，比如放到 utils 文件。
2. 在文件中引入 IM SDK。如果只需要 NIM 则引入 NIM_MINIAPP_SDK，如果只需要 聊天室能力则引入 CHATROOM_MINIAPP_SDK。
    ```
    // IM
    const NIM = require('utils/NIM_MINIAPP_SDK')

    // 聊天室
    const Chatroom = require('utils/Chatroom_MINIAPP_SDK')
    ```
:::
::: tab 支付宝小程序

1. 打开 mini.project.json，添加如下配置：
    ```
    "node_modules_es6_whitelist": [ 
        "nim-web-sdk-ng"
    ]
    ```
2.  在代码中引入 IM SDK。如果只需要 NIM 则引入 NIM_MINIAPP_SDK，如果只需要 聊天室能力则引入 CHATROOM_MINIAPP_SDK。
    ```
    // IM
    const NIM = require('nim-web-sdk-ng/dist/NIM_MINIAPP_SDK')

    // 聊天室
    const Chatroom = require('nim-web-sdk-ng/dist/Chatroom_MINIAPP_SDK')
    ```
:::
::::::
  





### 后续步骤

NIM SDK 和 ChatroomSDK 需分别使用不同的初始化方法，具体参见：

- [初始化并登录 IM](https://doc.yunxin.163.com/messaging/guide/zIyNzIwOTc?platform=miniProgram)

- [初始化并登录聊天室](https://doc.yunxin.163.com/messaging/guide/jA3MzM2MTY?platform=miniProgram)


## 常见问题

### 已知问题及处理建议


IM 含圈组版已兼容小程序环境，但该平台环境存在一些问题和限制，具体参见[已知问题及处理建议](https://doc.yunxin.163.com/messaging/guide/Dk5MzQyOTM?platform=miniProgram)。



### npm 安装报错

Q：执行 npm 命令安装 SDK 失败，出现以下报错信息。

![download.png](https://yx-web-nosdn.netease.im/common/9bec37138d76e022b358ee35125b0e51/download.png)

A：出现该问题是由用户侧环境导致，请按照提示执行 `npm fund`和`npm audit fix`即可。



