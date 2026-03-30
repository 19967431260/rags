本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Flutter 端 10.x.x 及以上版本的 IM UIKit 更新日志。IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK Flutter 更新日志](https://doc.yunxin.163.com/messaging2/concept/DMwMjA0MDI?platform=client)。

<!-- ## 近期重要更新

版本很少的情况下，暂不用列举近期重要更新

- 全新 IM UIKit 组件 **V10.0.0 版本** 发布。该版本底层适配新版 IM。
 -->

## 10.7.0 (2026-01-15)

**新增特性**

- 新增消息收藏功能。
- 新增消息检索功能。
    - 消息全文检索。
    - 按照消息类型（文本/图片/视频/文件）检索。
    - 在群组中根据消息发送者检索消息。
- 优化新消息滚动逻辑。

## 10.6.1 (2025-12-04)

- 优化语音视频呼叫接入方式，具体请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/zQzMjAxNzk?platform=flutter)。
- 增加反垃圾结果展示。

## 10.6.0 (2025-11-26)

**版本说明：**

该版本适配鸿蒙操作系统（HarmonyOS）。

**环境要求：**

使用该版本需要满足以下条件：

- 已配置 Flutter 鸿蒙开发环境（ 参考 [鸿蒙官方文档](https://gitcode.com/openharmony-tpc/flutter_flutter/tree/master)）。
- Flutter 版本：**3.27.5-ohos-0.0.2**。

**引入方式：**

该版本接入方式采用 **源码依赖**，请自行下载 [Github 源码](https://github.com/netease-kit/nim-uikit-flutter-ohos.git) | [Gitee 源码](https://gitee.com/netease-yunxin/nim-uikit-flutter-ohos)。

## 10.5.0 (2025-10-23)

**新增特性**

- **语音视频呼叫**：接入音视频呼叫功能，提升用户实时交互体验。
- **图片选择器**：升级图片选择器，简化用户图片上传和分享流程。
- **语音消息播放选项**：新增设置，允许用户选择通过扬声器或听筒播放语音消息。
- **权限请求优化**：增加权限请求时的用途说明。

**兼容**

兼容 go_router。

## 10.4.0 (2025-09-22)

**新增特性**

- **转发选择器**：新增消息转发功能，支持便捷选择转发对象。
- **智能链接识别**：自动识别并高亮显示消息中的手机号码和 URL 链接，支持点击交互。
- **富文本配置**：支持自定义文字消息的背景色、字体颜色和字号大小。
- **导航栏定制**：新增全局返回按钮配置选项，提升界面一致性。
- **在线状态功能**：新增用户在线状态显示开关，可根据需求灵活控制。
- **安全性提升**：创建群组时默认头像链接更新为安全链接，增强数据传输安全性。

**升级说明**

为了适配 **video_player** 组件，云信 IM Flutter UIKit 最低支持的 Dart 版本已调整为 3.6。请确保您的项目已升级至 Dart 3.6 或更高版本，以避免潜在兼容性问题。

## 10.3.1 (2025-07-18)

修复兼容问题。

## 10.3.0 (2025-06-27)

**新增特性**

- 支持查看用户在线状态。
- 支持群组验证。
- 支持国际语言设置。

## 10.2.0 (2025-05-26)

**新增特性**

- 新增 AI 数字人功能，支持包括 AI 聊和 AI 翻译功能。<!--详情请参考 [AI 数字人概述]()。-->
- IM AI 数字人支持流式输出模式，通过实时分片传输 AI 生成的内容，降低响应延迟、支持中断控制，显著改善用户交互体验。

**升级说明**

通过 pub 依赖的旧版本，如果自动升级到 10.2.0，可能会出现兼容问题。如 `Unhandled Exception: Bad state: GetIt: Object/factory with type IMLoginService is not registered inside GetIt.` 报错，请参考 [IM Flutter UIKit 10.2.0 升级报错故障排查](https://doc.yunxin.163.com/messaging-uikit/faq/DUxODM2MDk?platform=client)。

## 10.1.0 (2025-04-21)

支持本地会话组件，会话默认存储在用户设备本地。您可以参考 [集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/Dk0OTEzOTY?platform=flutter) 选择会话模式。

## 10.0.0 (2025-03-25)

- 全新 IM UIKit 组件 **v10.0.0 版本** 发布。
- 该版本底层适配 V10.0.0 NIM SDK。如何集成新版 UIKit，请参考 [IM UIKit 引入（V10）](https://doc.yunxin.163.com/messaging-uikit/guide/Dk0OTEzOTY?platform=flutter)。