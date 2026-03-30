本文介绍了网易云信即时通讯（NIM）提供的 UI 组件（UI Kit）适配 uni-app 开发框架的更新日志，后续简称 IM UIKit。有关如何集成 UIKit，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp">快速集成 uni-app 源码（Vue 3）</a>。

## 10.4.1 (2026-01-09)

- 优化在线离线状态。
- 优化消息推送，兼容超长文本。
- 优化好友名片页面，支持展示备注。
- 升级底层兼容的呼叫组件。

## 10.4.0 (2025-07-24)

- 新增在线状态功能。支持实时查看对方是否在线，适用于需要即时回应的工作沟通或客户服务场景。
- 支持讨论组功能。支持创建专题讨论组，提升团队协作体验。
- 消息回复升级为底层 NIM SDK [`replyMessage`](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client#实现消息回复) 接口实现，简化开发流程。采用 IM Thread 方式，使对话更有条理，适合复杂多话题讨论场景。
- 优化登录流程。
- 升级底层依赖的 IM SDK 版本至 [10.9.30](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)。

## 10.3.0 (2025-04-08)

- 新增鸿蒙应用编译支持，扩展跨平台兼容性。
- 减小微信小程序编译包体积，提供 ESM 模块化版本。
- 新增本地会话功能，支持会话本地/云端切换。
- 优化通讯录人员选择界面，提升用户体验。

## 10.2.1 (2025-01-20)

- 优化表情消息实现<!-- ，与其他端对齐 -->。
- 优化艾特（@）消息实现方案。
- 优化登录流程。
- 升级底层依赖的 IM SDK 版本至 [10.6.0](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1060-2024-11-20)。
- 支持切换国际化语言展示。

## 10.2.0 (2024-10-31)

- 会话页新增搜索框，方便用户搜索会话内容。
- 新增收藏消息功能。
- 优化日志打印模式，支持配置是否展示日志。
- 撤回消息时，支持配置撤回时间。

## 10.1.0 (2024-10-18)

- 消息支持已读回执。
- 群组会话支持设置免打扰。
- 支持标记消息，方便用户收藏关键消息。
- 支持发送文件消息。
- 好友名片支持添加备注。
- 群组信息支持设置群头像和群介绍。

## 10.0.1 (2024-09-13)

- 网易云信即时通讯 UIKit 适配 uni-app 开发框架的全新 10.0.1 版本发布。
- 底层适配 [NIM Web SDK v10.4.0](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client#1040-2024-08-21)。如何集成新版 UIKit，请参考《开发指南（V10）》[快速集成 uni-app 源码（Vue 3）](https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp)。

::: details 单击展开查看 v1.0.0 (2023-08-07) ~ v1.5.1 (2024-05-28) 版本 IM UIKit 的更新日志。

<note type="note">
v1.0.0 ~ v1.5.1 版本 IM UIKit 底层适配了 <a href="https://doc.yunxin.163.com/messaging/concept/zcyNTgyMzE?platform=client">uni-app 0.1x.x NIM SDK</a>。如何集成 UIKit，请参考《开发指南（V9）》<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jQyNzk0Nzk?platform=uniapp">快速集成 uni-app 源码（Vue 3）</a>。其中 V9 概指低于 V10  系列 NIM SDK 的版本。
</note>

<a id="1.5.1 (2024-05-28)"></a>

⭐**1.5.1 (2024-05-28)**

详细优化接口注释，提升接入效率。

<a id="1.5.0 (2024-04-29)"></a>

⭐**1.5.0 (2024-04-29)**

全新上线呼叫能力，支持在单聊中拨打音视频。

<a id="1.4.0 (2024-03-27)"></a>

⭐**1.4.0 (2024-03-27)**

- 支持语音消息录制、播放、发送。
- 支持视频消息发送、播放。
- 支持群管理。
- 支持群主转让。
- 支持群昵称设置。

<a id="1.3.0 (2024-03-04)"></a>

⭐**1.3.0 (2024-03-04)**

IM UIKit 同时支持两种不同版本的 Vue.js 框架（Vue2 和 Vue3），兼容并协同工作。

<a id="1.2.0 (2024-01-05)"></a>

⭐**1.2.0 (2024-01-05)**

支持 IM UIKit uni-app 适配 Vue2。

<a id="1.1.1 (2023-11-30)"></a>

⭐**1.1.1 (2023-11-30)**

解决 H5 火狐浏览器运行问题。

<a id="1.1.0 (2023-11-24)"></a>

⭐**1.1.0 (2023-11-24)**

- IM uni-app demo 支持安卓、iOS、H5、微信小程序。
- 好友关系管理。
- 黑名单管理。
- 消息回复功能。
- 消息转发能力。
- 群聊 @ 功能。
- 群成员列表更新。
- 系统通知优化。
- 支持单聊直接创群。

<a id="1.0.0 (2023-08-07)"></a>

⭐**1.0.0 (2023-08-07)**

发布 IM UIKit uni-app 1.0.0 版本，实现通用即时通讯单聊、群聊能力场景。
:::