本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Web 端（React） 10.x.x 及以上版本的 IM UIKit 更新日志。IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK Web 版更新日志](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)。

## **近期重要更新**

从 10.0.0 起，全新 IM UIKit 组件发布，该版本底层适配新版 NIM SDK，即 [10.0.0](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA)。

<a id="10.9.0 (2025-12-4)"></a>

## 10.9.0 (2025-12-04)

- 上传文件、视频、图片时，实时显示上传进度条。
- 支持取消正在上传的文件、视频、图片。

<a id="10.8.4 (2025-08-29)"></a>

## 10.8.4 (2025-08-29)

消息列表加载优化。

<a id="10.8.2 (2025-07-08)"></a>

## 10.8.2 (2025-07-08)

**新增功能**

- 新增在线状态功能。支持实时查看对方是否在线，适用于需要即时回应的工作沟通或客户服务场景。
- 新增群消息已读/未读详情查看功能。支持查看群消息的已读/未读详情，实时掌握信息传达情况。
- 新增群邀请和申请流程。群主可以通过该流程邀请新成员加入群聊，或者审批成员的入群申请，让群组管理更加高效。
- 支持讨论组功能。支持创建专题讨论组，提升团队协作体验。
- 支持配置是否允许发送视频。

**功能优化**

- 消息回复升级为底层 NIM SDK [`replyMessage`](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client#实现消息回复) 接口实现，简化开发流程。采用 IM Thread 方式，使对话更有条理，适合复杂多话题讨论场景。
- 优化收藏消息功能的界面交互。

**兼容性**

适配至 NIM SDK [10.9.10](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client) 版本。

<a id="10.8.0 (2025-04-27)"></a>

## 10.8.0 (2025-04-27)

**新增特性**

- IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
- 支持自定义头像点击事件。

**优化**

- 优化消息已读/未读逻辑。
- 优化图片、视频消息的 UI 展示。

**兼容性**

适配至 NIM SDK [10.8.30](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client) 版本。

<a id="10.7.1 (2025-03-12)"></a>

## 10.7.1 (2025-03-12)

**变更**

- 在开启或关闭本地会话能力时，改为遵从底层 SDK 初始化设置。即初始化 [NIM SDK](https://doc.yunxin.163.com/messaging2/guide/zY4OTcyODQ?platform=client) 时，设置 `enableV2CloudConversation` 为 `true` 即开启云端会话。
- 优化消息已读未读。

**兼容性**

适配至 NIM SDK [10.8.10](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#10810-2025-03-10) 版本。

**升级说明**

如果您在 10.7.0 开启了云端会话，从 10.7.0 升级至 10.7.1 时，需要同时升级 NIM SDK 至依赖的 10.8.10 版本，同时初始化 NIM SDK 时，设置 `enableV2CloudConversation` 为 `true` 即开启云端会话。

```TypeScript
// 初始化 IM SDK 实例
    const nim = V2NIM.getInstance({
      appkey: initOptions.appkey,
      account: initOptions.account,
      token: initOptions.token,
      // 是否开启云端会话，默认不开启
      enableV2CloudConversation: true,
      debugLevel: "debug",
      apiVersion: "v2",
    });
```

<a id="10.7.0 (2025-02-26)"></a>

## 10.7.0 (2025-02-26)

**新增**

- 优化会话列表渲染效果。
- 新增本地会话能力，且默认开启。
    ::: note note
    本地会话是指会话数据存储在客户端设备本地，与云端会话相对。两种会话模式适用于不同即时通讯场景。
    :::
    <!-- 您可以在 `localOptions` 中配置 `enableLocalConversation` 为 `true` 即开启本地会话。 -->

**兼容性**

适配至 NIM SDK [10.8.0](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1080-2025-02-17) 版本。

<a id="10.6.0 (2024-12-27)"></a>

## 10.6.0 (2024-12-27)

**新增**

- 消息滚动支持最近（`nearest`）模式。
- 静态资源支持私有化。

**优化**

- 优化表情实现方案。
- 优化 @消息实现方案。
- 优化收藏消息页面。

<a id="10.5.0 (2024-11-27)"></a>

## 10.5.0 (2024-11-27)

**新增特性**

- 支持发送粘贴的图片。
- 支持群消息免打扰。
- 支持语音转文字。

**优化**

- 优化会话列表、群聊等性能。
- 兼容 Firefox 浏览器。

<a id="10.4.0 (2024-10-31)"></a>

## 10.4.0 (2024-10-31)

- 优化日志打印模式，支持配置是否展示日志。
- 撤回消息时，支持配置撤回时间。
- 添加消息发送前回调。

<a id="10.3.3 (2024-08-30)"></a>

## 10.3.3 (2024-08-30)

优化切换账号的内部逻辑。

<a id="10.3.0 (2024-07-16)"></a>

## 10.3.0 (2024-07-16)

**新增**

- 新增 AI 数字人功能，支持 AI 聊、AI 划词和 AI 翻译功能。详情请参考 [AI 数字人概述](https://doc.yunxin.163.com/messaging-uikit/guide/Tc2ODA1Mjk)。
- 支持置顶消息。
- 支持收藏消息。
- 转发支持多选。
- 优化消息发送性能。
- 优化在群组中，陌生人账号首次只有账号 ID（accid）的问题。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 10.3.0-beta 版本。

<a id="10.0.1 (2024-06-03)"></a>

## 10.0.1 (2024-06-03)

升级底层 NIM SDK。

<a id="10.0.0 (2024-05-17)"></a>

## 10.0.0 (2024-05-17)

全新 IM UIKit 组件 **10.0.0 版本发布**。该版本底层适配新版 IM。

若需要使用该版本，直接引入 @xkit-yx/im-kit-ui 10.0.0 版本即可。

新版本较历史版本，存在部分接口和参数变更，若出现异常，请及时调整，详情请参考 [升级指南](https://doc.yunxin.163.com/messaging-uikit/guide/TkyNDU3ODU?platform=web)。