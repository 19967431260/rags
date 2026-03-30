本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Android 端 10.x.x 及以上版本的 IM UIKit 更新日志，您可以 [下载 Demo](https://doc.yunxin.163.com/messaging-uikit/resource?platform=all) 安装体验最新功能。IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK 安卓版更新日志](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client)。

## **近期重要更新**

- 自 10.8.1 起，新增回复灵感、用户在线状态、消息回复功能。
- 自 10.2.0 起，新增消息收藏功能和群聊消息置顶功能。
- 全新 IM UIKit 组件 **10.0.0 版本** 发布。该版本底层适配新版 IM。
- 会话模块支持音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/jgxOTUyMjQ?platform=android)。
- 会话模块支持地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/zY3OTQxMzU?platform=android)。

<a id="10.9.10 (2026-03-11)"></a>

## 10.9.10 (2026-03-11)

**新增功能**

- 单聊和群聊新增检索功能。包括：
    - 图片/视频/文件消息检索能力。
    - 群成员&日期检索能力。
    - 文本消息全文检索能力。
- 支持单聊和群聊的聊天页面新消息提醒的快速定位功能。

    当单聊和群聊的聊天页面有新消息时，右下角会显示 “N条新消息” 提示，点击提示或输入框即可一键跳到最新消息。

**问题修复**

修复部分已知问题。

**兼容性**

- 适配至 NIM SDK [10.9.71](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 版本。
- 适配至呼叫组件 [3.7.1](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client) 版本。

<a id="10.9.1 (2025-11-21)"></a>

## 10.9.1 (2025-11-21)

**新增功能**

消息发送命中反垃圾后新增失败提示。

**兼容性**

- 适配至 NIM SDK [10.9.52](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 版本。
- 适配至呼叫组件 [3.7.1](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client) 版本。

<a id="10.8.9 (2025-10-18)"></a>

## 10.8.9 (2025-10-18)

**新增功能**

- 升级图片选择器。
- 语音消息播放模式支持菜单切换。

**兼容性**

- 适配至 NIM SDK [10.9.52](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#10945-2025-09-09) 版本。
- 适配至呼叫组件 [3.7.1](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client) 版本。

<a id="10.8.5 (2025-09-15)"></a>

## 10.8.5 (2025-09-15)

**新增功能**
- **链接识别增强**：文本消息中的链接将自动识别，并支持点击跳转。
- **自定义消息气泡**：支持自定义消息气泡背景与样式。
- **文本消息样式配置**：文本消息颜色与字体大小支持灵活配置。
- **全局返回按钮自定义**：全局返回按钮可根据需求自定义。

**兼容性**
- 适配至 NIM SDK [10.9.45](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#10945-2025-09-09) 版本。
- 适配至呼叫组件 [3.6.1](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client) 版本。


<a id="10.8.2 (2025-06-30)"></a>

## 10.8.2 (2025-06-30)

**新增功能**

- 新增在线通知跳转逻辑。当用户处于在线状态时，收到通知后，点击通知可以精准跳转到会话页面查看和处理消息。您可以参考 Demo 代码，快速实现跳转逻辑。
- 新增群邀请和申请流程。群主可以通过该流程邀请新成员加入群聊，或者审批成员的入群申请，让群组管理更加高效。

**兼容性**

适配至 NIM SDK [10.9.10](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#10910-2025-06-18) 版本。

<a id="10.8.1 (2025-06-13)"></a>

## 10.8.1 (2025-06-13)

**新增功能**

- **单聊在线状态功能**：新支持实时查看对方是否在线，适用于需要即时回应的工作沟通或客户服务场景。
- **AI 回复灵感功能**：当用户不知道如何回复时，采用 AI 助聊提供的 **回复灵感** 根据聊天上下文提供回复建议。详情请参考 [实现 AI 助聊（回复灵感）](https://doc.yunxin.163.com/messaging-uikit/guide/DM1NTIzMDE?platform=android)。

**功能优化**

消息回复升级为底层 NIM SDK [replyMessage](https://doc.yunxin.163.com/messaging2/guide/jQ2MTkzODg?platform=client#%E5%AE%9E%E7%8E%B0%E6%B6%88%E6%81%AF%E5%9B%9E%E5%A4%8D) 接口实现，简化开发流程。采用 IM Thread 方式，使对话更有条理，适合复杂多话题讨论场景。

**兼容性**

适配至 NIM SDK [10.8.30](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#10830-2025-04-24) 版本。

<a id="10.8.0 (2025-04-27)"></a>

## 10.8.0 (2025-04-27)

**新增特性**

- IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。
- 群组支持配置管理员人数。

**兼容性**

适配至 NIM SDK [10.8.30](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 版本。

<a id="10.6.3 (2025-03-27)"></a>

## 10.6.3 (2025-03-27)

**新增特性**

支持在初始化 SDK 时配置是否开启 **云端会话功能**，默认不开启，即默认使用本地会话功能。详情请参考 [集成 IM UIKit（V10）](https://doc.yunxin.163.com/messaging-uikit/guide/DU4NzAzNzQ?platform=android)。

**兼容性**

适配 IM SDK [10.8.21](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#10821-2025-03-24) 版本。

<a id="10.6.1 (2025-02-19)"></a>

## 10.6.1 (2025-02-19)

**新增特性**

新增本地会话组件。集成方式请参考 [集成 IM UIKit（V10）](https://doc.yunxin.163.com/messaging-uikit/guide/DU4NzAzNzQ?platform=android)。

**兼容性**

- 适配呼叫组件 [3.5.0](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client#350-2025-02-18) 版本。
- 适配 IM SDK [10.8.0](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client#1080-2025-02-17) 版本。

<a id="10.5.2 (2025-01-07)"></a>

## 10.5.2 (2025-01-07)

优化群成员信息查询逻辑。

<a id="10.5.1 (2024-12-17)"></a>

## 10.5.1 (2024-12-17)

优化图片选择逻辑。

<a id="10.5.0 (2024-12-09)"></a>

## 10.5.0 (2024-12-09)

**新增**

- 新增语音转文字功能。
- 支持动态切换语言。
- 新增安全提示语。

**修复**

- 修复已知问题。

**升级**

- 呼叫组件升级至 3.0.0 版本。
- IM SDK 版本升级至 10.6.0 版本。

<a id="10.4.0 (2024-11-04)"></a>

## 10.4.0 (2024-11-04)

**新增**

- 新增发送消息前消息状态的回调。
- 支持配置消息的可撤回时间。
- 支持自定义配置推送 payload。

**优化**

优化通过配置项实现自定义 UI 的 Sampe Code。

**升级**

升级底层 NIM SDK 至 10.5.0。

<a id="10.3.2 (2024-09-02)"></a>

## 10.3.2 (2024-09-02)

**修复**

修复已知问题。

<a id="10.3.0 (2024-07-16)"></a>

## 10.3.0 (2024-07-16)

**新增**

新增 AI 数字人功能，支持包括 AI 聊、AI 划词和 AI 翻译功能。详情请参考 [AI 数字人概述](https://doc.yunxin.163.com/messaging-uikit/guide/jM1MzUyNjQ?platform=android)。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 10.3.0。

**修复**

修复已知问题。


<a id="10.2.0 (2024-06-19)"></a>

## 10.2.0 (2024-06-19)

**新增**

- 消息收藏功能。
- 群聊消息置顶功能。

**修复**

修复已知问题。

<a id="10.1.2 (2024-05-23)"></a>

## 10.1.2 (2024-05-31)

**新增**

- 转发功能支持转发到最近会话、好友、我的群组。
- 转发功能支持选择最近转发记录。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 10.2.6。

**修复**

修复已知问题。

<a id="10.0.0 (2024-05-23)"></a>

## 10.0.0 (2024-05-23)

- 全新 IM UIKit 组件 **10.0.0 版本** 发布。
- 该版本底层适配 10.0.0 NIM SDK。如何集成新版 UIKit，请参考 [IM UIKit 引入（V10）](https://doc.yunxin.163.com/messaging-uikit/guide/jI1MjMyMTY?platform=android)。