本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Flutter 端开发版的更新日志，IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK Flutter 更新日志](https://doc.yunxin.163.com/messaging2/concept/DMwMjA0MDI?platform=client)。

## **近期重要更新**

- 新增@功能，支持在群组中@群成员，在会话列表中收到@消息会高亮展示。
- 会话相关页面新增标记（pin）列表，可查看所有标记的消息。
- 会话模块支持地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/zYwNDU1MDg?platform=flutter)。

----
## <span id="[9.7.3] - 2024-09-30">9.7.3 (2024-09-30)</span>

- 优化群成员管理逻辑。
- 升级第三方组件。

## <span id="[9.7.2] - 2024-06-20">9.7.2 (2024-06-20)</span>

内部优化。

## <span id="[9.7.1] - 2024-02-21">9.7.1 (2024-02-21)</span>

**新增特性**

- 适配 Flutter V3.16 版本。
- 位置消息功能实现插件化。
- 更新了 `nim_chatkit_ui` 和插件 `nim_chatkit_location`，其他的没有更新。

## <span id="[9.7.0] - 2024-01-25">9.7.0 (2024-01-25)</span>

**新增特性**

- 支持消息多选功能。
- 支持合并转发，逐条转发，批量删除。
- 支持设置群管理员，管理群成员，并支持权限设置。
- 支持换行消息。

**优化**

优化搜索页面交互体验。

**修复**

- 修复@功能输入框编辑错误的问题。
- 修复特殊头像背景色设置的问题。
- 其他已知 UI 问题。

## <span id="[1.2.0] - 2023-11-08">1.2.0 (2023-11-08)</span>

**新增特性**

- 新增@功能，支持在群组中@群成员，在会话列表中收到@消息会高亮展示。
- 会话相关页面新增标记（pin）列表，可查看所有标记的消息。
- 图片消息支持 GIF 格式。
- 支持群聊列表的排序和群成员的排序。

**优化**

- 地理位置信息拆分，独立成 package，并优化地理位置信息的展示。
- 优化进入群组的规则和逻辑。
- 优化黑名单内部逻辑。
- 优化性能，提高会话切换速度。
- 优化界面 UI。

**修复**

- 修复卡顿问题。
- 修复其他已知问题。

## <span id="[1.1.2] - 2023-08-08">1.1.2 (2023-08-08)</span>

- 优化获取消息的内部逻辑，现使用动态查询方式。
- 升级第三方组件。
    - 升级 `image_picker` 到 `1.0.1`。
    - 升级 `audioplayers` 到 `5.0.0`。
    - 升级 `flutter_svg` 到 `2.0.7`。
    - 升级 `image_gallery_saver` 到 `2.0.3`。
    - 升级 `connectivity_plus` 到 `4.0.1`。
- 修复已知问题。

## <span id="[1.1.1] - 2023-06-12">1.1.1 (2023-06-12)</span>

- 适配 Flutter V3.10.0 以上版本。
- 适配 Android 13 的权限管理变更。

## <span id="[1.1.0] - 2023-06-02">1.1.0 (2023-06-02)</span>

**新增特性**

- 会话模块支持地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/zYwNDU1MDg?platform=flutter)。
- 支持发送文件消息，目前支持的消息类型请参考 [基本消息类型](https://doc.yunxin.163.com/messaging-uikit/guide/zg5ODU0MTk?platform=flutter#基本消息类型)。
- 新增回复消息功能，采用非 Thread 模式实现。
- 支持发送消息时配置扩展信息。
- 新增系统通知合并展示功能。

**优化**

- UI 和文案展示优化。
- 优化语音消息播放逻辑。
- 优化邀请成员入群和好友验证的内部逻辑。

**修复**

- 修复 UIKit iOS 端，好友数量较多时好友列表展示不全的问题。
- 修复 iOS 端，群成员退群后，群人数不变的问题。
- 修复个人头像无法展示问题。
- 修复 UIKit 首次安装或打开文件没有请求授权的问题。
- 修复其他已知问题。

**NIM SDK 版本兼容**

IM Flutter UIKit 兼容的 NIM SDK 版本：nim_core 1.6.1

## <span id="[1.0.0] - 2022-09-30">1.0.0 (2022-09-30)</span>

网易云信全新一代 IM UIKit 发布。

IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款即时通讯 UI 组件库，包括聊天、会话列表、搜索、群管理等组件。通过 IM UIKit，可快速集成包含 UI 界面的即时通讯应用。更多 IM UIKit 相关介绍请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/concept/zQxMjk5NzI?platform=flutter" target="_blank">IM UIKit 简介</a>、<a href="https://doc.yunxin.163.com/messaging-uikit/concept/jYyMDE3MDE?platform=flutter" target="_blank">IM UIKit 功能概述</a> 和 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DA2MzEzNTA?platform=flutter" target="_blank">集成 IM UIKit</a>。