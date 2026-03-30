网易云信在 GitHub 上提供一个开源的网易会议组件示例项目 [NEMeeting](https://github.com/netease-kit/NEMeeting/tree/main/SampleCode/MiniApp)。本文介绍如何快速跑通该示例项目，体验在线会议功能。示例代码中包含了详细的 API 调用场景、参数封装以及回调处理。

该示例项目包含的功能如下：

- 通过账号、Token 完成 NEMeeting 登录鉴权、注销登录。
- 加入会议、离开会议。
- 会议内提供的其他功能 (如置顶开启视频的成员，聊天等)。

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在控制台创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案。具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 开发环境

在开始运行示例项目之前，请您准备以下开发环境：

| 名称 | 具体要求 |
| ---- | ---- |
| Android 端的微信 App | 7.0.8 及以上版本 |
| iOS 端的微信 App | 7.0.9 及以上版本 |
| 小程序基础库 | 2.10.0 及以上版本 |
| 微信开发者工具 | 最新版本 |

::: note note
- 由于微信开发者工具不支持原生组件（即 `<live-pusher>` 和 `<live-player>` 标签），需要在真机上进行运行体验。
- 由于小程序测试号不具备 `<live-pusher>` 和 `<live-player>` 的使用权限，需要申请常规小程序账号进行开发。
- 不支持 uni-app 开发环境，请使用原生小程序开发环境。
:::

## 操作步骤

1. 配置示例项目。具体步骤如下。

    1. 访问 [NEMeetingKit](https://github.com/netease-kit/NEMeeting/tree/main/SampleCode/MiniApp) 地址，按需下载对应版本的组件源码压缩包至本地，建议下载最新版本。

    2. 下载 [微信开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html) 至本地。

    3. 用微信开发者工具打开小程序 SampleCode 文件夹，填入自己的 App ID（若无则可以暂时用测试号）打开小程序示例项目。

2. 在小程序示例项目的 **加入会议** 页面，输入申请的 App Key、已存在的会议 ID 和用户昵称，单击 **加入会议** 即可。