本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Android 端开发版的更新日志，IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK 安卓版更新日志](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client)。

## 近期重要更新

- 新增全新的通用版 UI 组件，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件，具体请参考 [UI 组件介绍](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=android)。
- 会话模块支持音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/Dk5ODUxMTA?platform=android)。
- 会话模块支持地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/DAyOTExMTY?platform=android)。

<a id="9.7.7 (2025-09-17)"></a>

## 9.7.7 (2025-09-17)

**功能优化**

- 适配 Android 系统，支持 16 KB 的页面大小，提升系统兼容性。

**兼容性**

- 升级呼叫组件版本至 [2.7.0](https://doc.yunxin.163.com/nertccallkit/concept/DMzOTI3NTA?platform=client)。
- 升级 NIM SDK 版本至 [9.20.15](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client#92015-2025-08-26)。

<a id="9.7.5 (2025-04-11)"></a>

## 9.7.5 (2025-04-11)

**优化**

针对图片消息，优化了图片选择器效果。

<a id="9.7.1 (2025-02-12)"></a>

## 9.7.1 (2025-02-12)

**修复**

修复群头像设置中选择本地图片问题。

## <span id="8.9.0 (2024-02-22)">8.9.0 (2024-02-22)</span>

基于 UIKit V9.7.0 适配 NIM SDK [V8.9.125](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client#8.9.125%20-%202024-02-02)。

**优化**

优化位置消息功能，采用静态图片方案。

**兼容性**

[V8.9.125](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client#8.9.125%20-%202024-02-02)

<a id="9.7.0 (2024-01-25)"></a>

## 9.7.0 (2024-01-25)

**新增**

- 新增群成员管理功能，包括群主添加或移除群组管理员、群主或管理员移除普通群成员。
- 新增消息多选操作功能，包括批量删除消息、合并转发消息功能。
- 新增富文本消息（换行消息）。
- 新增发送消息时被好友拉黑的提示。
- 标记列表新增单击查看功能（语音/视频/图片消息等支持查看和播放）。
- 输入框新增输入换行模式，即按下回车键不会立即提交消息，而是在输入框中插入一个换行符，用户可以继续输入下一行内容。
- 支持群主或者管理员开启关闭普通群成员在群组中 @ 所有人权限。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 V9.14.2。

**修复**

修复聊天页输入框中 @ 高亮文本问题。

<a id="9.6.3 (2023-11-03)"></a>

## 9.6.3 (2023-11-03)

**变更**

- 升级 NIM SDK 版本到 V9.12.0。
- Demo 工程依赖的呼叫组件版本升级到 V2.2.0。

**修复**

修复部分已知问题。

<a id="9.6.2 (2023-07-12)"></a>

## 9.6.2 (2023-07-12)

**升级必看**

自 V9.6.2 起：

- 废弃 `ConversationRepo`、`ContactRepo`、`TeamRepo`，将其功能全部合并至 `ChatKit` 包中。并将注册监听相关接口，按照功能分类，分别迁移至 `ChatObserverRepo`、`ContactObserverRepo`、`ConversationObserverRepo`、`TeamObserverRepo`。

- 废弃 `searchkit-ui`，将其功能合并至 `contactkit-ui` 中。

**新增**

新增全新的通用版 UI 组件，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件，具体请参考 [UI 组件介绍](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=android)。

**变更**

升级 NIM SDK 版本到 V9.11.0。

<a id="9.5.3 (2023-04-24)"></a>

## 9.5.3 (2023-04-24)

**新增**

- 新增@功能，支持在群组中@群成员，在会话列表中收到@消息会高亮展示。
- 会话相关页面新增标记（pin）列表，可查看所有标记的消息。
- 新增回复消息功能，采用非 Thread 模式实现。
- 新增系统通知合并展示功能。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 V9.10.0。

**修复**

修复部分已知问题。

<a id="9.4.1 (2023-03-17)"></a>

## 9.4.1 (2023-03-17)

修复 `IMKitClient` 中分步初始化接口 `config()` 和 `initSDK` 的调用异常问题。

<a id="9.4.0 (2023-02-28)"></a>

## 9.4.0 (2023-02-28)

**新增**

- 会话模块支持音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/Dk5ODUxMTA?platform=android)。
- 圈组中支持表情和语音消息。

**变更**

- 升级 NIM SDK 版本到 V9.8.0。

- 离线消息支持 NIM SDK 的动态查询历史消息能力，避免出现历史消息拉取不完整的问题。更多详情请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/guide/TI3NTU1NDA?platform=android#动态查询历史消息)。

**修复**

修复部分已知问题。

<a id="9.3.0 (2022-12-17)"></a>

## 9.3.0 (2022-12-22)

**新增**

- 新增地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/DAyOTExMTY?platform=android)。
- 新增文件消息功能（升级后可直接使用）。

    <img alt="文件消息图.png" src="https://yx-web-nosdn.netease.im/common/2a8b159c6f3b05114ccb4a769f8a6c04/文件消息图.png" style="width:30%;">

**变更**

集成会话界面（`chatkit-ui`）之前 **不再** 需要调用 `ChatKitClient.init` 方法对该模块进行初始化，相关文档参考 [集成会话界面](https://doc.yunxin.163.com/messaging-uikit/guide/DUxNDczMjg?platform=android)。

**修复**

修复部分已知问题。

<a id="9.2.11 (2022-11-23)"></a>

## 9.2.11 (2022-11-23)

**变更**

升级 NIM SDK 版本到 V9.6.4。

**修复**

修复圈组、群设置中拍照功能异常。

<a id="9.2.10 (2022-08-29)"></a>

## 9.2.10 (2022-11-04)

**新增**

- 新增 `IChatInputMenu` 类支持对会话界面（即聊天界面）输入框下方的按钮进行个性化配置，可通过 `ChatUIConfig` 进行配置。相关自定义示例请参考 [在界面底部菜单栏增加按钮](https://doc.yunxin.163.com/messaging-uikit/guide/zE0MDg5MzE?platform=android#在界面底部菜单栏增加按钮)。
- 新增 `IChatPopMenu` 类支持对会话界面的消息长按菜单进行个性化配置，可通过 `ChatUIConfig` 进行配置。相关自定义示例请参考 [不展示消息长按菜单](https://doc.yunxin.163.com/messaging-uikit/guide/zE0MDg5MzE?platform=android#不展示消息长按菜单)。
- `ChatKitClient` 中新增 `addCustomAttach` 和 `addCustomViewHolder` 方法，分别用于添加自定义消息附件和自定义消息的 ViewHolder。相关说明请分别参考 [自定义消息处理](https://doc.yunxin.163.com/messaging-uikit/guide/TMyNjI5Mjk?platform=android#步骤1-自定义消息处理)和[实现自定义消息的 UI 展示](https://doc.yunxin.163.com/messaging-uikit/guide/TMyNjI5Mjk?platform=android#步骤2-实现自定义消息的-ui-展示)。
- `MessageProperties` 中新增对界面标题的个性化定制能力。相关自定义示例请参考 [修改界面标题栏右侧图标](https://doc.yunxin.163.com/messaging-uikit/guide/zE0MDg5MzE?platform=android#修改标题栏图标)。
- `ContactUIConfig` 中新增 `IContactViewLayout` 支持对通讯录页面视图的个性化定制。相关自定义示例请参考 [在头部模块增加提示消息](https://doc.yunxin.163.com/messaging-uikit/guide/jM2NDMyMzE?platform=android#在头部模块增加提示消息)。
- 新增 `IConversationViewLayout` 支持个性化配置会话列表页面视图，可在 `ConversationUIConfig` 中配置。相关自定义示例请参考 [在会话列表顶部增加提示条](https://doc.yunxin.163.com/messaging-uikit/guide/zE0MDg5MzE?platform=android#在会话列表顶部增加提示条)。
- 新增 `SettingRepo` 类，提供通用配置方法，如通过 `setDeleteWithAlias` 方法可设置删除好友时删除昵称、通过 `setShowReadStatus` 方法设置是否展示已读未读状态等。

**优化**

- 长按 loading 和发送失败消息，展示回复转发等功能。
- 发送某些视频消息对端接收失败时，增加提示：网易云信 IM 视频下载失败。
- 发送 1s 语音消息撤回时，撤回通知消息换行展示。
- UI 和文案展示优化。

<a id="9.2.9 (2022-08-29)"></a>

## 9.2.9 (2022-09-01)

**新增 API**

- 新增 `MessageProperties` 类，可通过该类下的 `selfMessageRes` 设置当前用户发送消息的背景资源 ID。
- 新增 `MessageProperties` 类，可通过该类下的 `receiveMessageRes` 设置当前用户接收消息的背景资源 ID。

**变更**

- 未实现功能去除，包括：
    - 去除文件发送入口。
    - 去除多选选项。
    - 去除标记列表。
    - 去除 **我的** 界面的收藏选项和收藏的入口。
- 资源拆分：将依赖资源迁移到 UIKit 库中，不再依赖底层 Common 库的统一资源。

**修复**

- 多语言英文文案更新。
- 修复人员选择器选中的人员头像颜色不一致的问题。
- 修复通知消息界面头像颜色不一致的问题。
- 修复转发消息昵称过长且展示未对齐的问题。

<a id="9.2.7 (2022-06-30)"></a>

## 9.2.7 (2022-08-18)

**新增 API**

- 新增 `CommonRepo` 类，该类中包含用户数据获取方法 `getUserInfo` 方法和用户信息更新方法 `updateUserInfo`。
- 在 `ChatKit-ui` 模块中，支持传入会话 ID 进入会话界面（包括群聊界面和单聊界面），传入参数的 KEY 值为 `RouterConstant.CHAT_ID_KRY`。
- 增加国际化英文文案，跟随系统切换。

**修复**

- 修复黑名单中昵称展示问题。
- 修复 @ 功能名称展示问题。
- 修复发送视频失败的提示文案。
- 修复权限申请逻辑问题。

<a id="9.2.0 (2022-06-30)"></a>

## 9.2.6 (2022-08-11)

**新增 API**

- 在 `IMKitClient` 类中增加 `setUserInfoDelegate(IUserInfoDelegate delegate,boolean cache)` 方法，支持 `UserInfo` 信息由业务实现。
- 在 `IMKitClient` 类中增加 `removeUserInfoDelegate` 方法，移除设置的 `UserInfo` 代理类。
- 在 `ChatKitClient` 类中增加 `init(Context context)` 方法。`ChatKit` 模块初始化接口，需要在 Application 中进行初始化，完成自定义消息解析器 `CustomAttachParser` 的初始化。
- 在 `CustomAttachment` 类中中增加 `getContent` 方法，获取自定义消息的摘要信息，用于展示会话列表中最新消息展示。

**修复**

- 修复用户昵称或者群名称过长造成的 UI 展示问题。
- 修复用户信息获取，保证用户信息优先同步获取，如获取失败则采用异步获取。

<a id="9.2.0 (2022-06-30)"></a>

## 9.2.2 (2022-06-30)

修复自动登录接口中，登录信息同步异常的问题。

<a id="9.2.0 (2022-06-23)"></a>

## 9.2.0 (2022-06-23)

**新增**

| <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> |
| --- | --- |
| UI 层支持个性化配置能力 | <div><ul><li>`ChatKit-ui` 中：<ul><li>新增 `ChatUIConfig`，支持自定义聊天界面 UI。</li><li>新增 `ChatKitClient`，提供设置全局参数的接口。</li></ul></li><li>`ConversationKit-ui` 中：<ul><li>新增 `ConversationUIConfig`，支持设置会话列表界面的 UI 自定义。</li><li>新增 `ConversationKitClient` 提供设置全局参数的接口。</li></ul></li><li>`ContactKit-ui` 中：<ul><li> 新增 `ContactUIConfig` 支持自定义通讯录界面 UI。</li><li>新增 `ContactKitClient` 提供设置全局参数的接口。</li></li></ul></ul></div> |
| 分布初始化 | 新增 `config` 接口和 `initSDK` 接口，支持分布初始化。 |
| 通过扩展参数设置群组信息 | `TeamRepo` 新增 `createNormalTeam` 和 `createAdvanceTeam` 方法，支持传入扩展参数 `fieldsMap:Map<TeamFieldEnum, Serializable>` 设置群组信息。 |

**NIM SDK 版本兼容**

IM UIKit 兼容的 NIM SDK 版本升级到 v9.2.5，圈组的系统通知增加新的通知类型，具体请参考 [SDK 更新日志](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=android#925-2022-06-13)。

**优化**

对 Repository 层的接口进行了调整和优化，涉及改动的模块包括 `ChatMessageRepo`、`ContactRepo`、`ConversationRepo`、`TeamRepo`、`SearchRepo`。

**修复**

修复部分机型首次安装通讯录界面无法即时刷新的问题。

<a id="9.0.2 (2022-06-07)"></a>

## 9.0.2 (2022-06-07)

**新增 API**

- 在 `ChatMessageBean` 类中增加 `isSameMessage(ChatMessageBean bean)` 方法，判断消息体是否相同。
- 在 `ChatMessageAdapter` 类中增加私有方法 `removeSameMessage(List message)`，去除重复消息。

**变更 API**

- 在 `ChatMessageAdapter` 中的 `appendMessages` 和 `forwardMessages` 方法增加对 `removeSameMessage` 的调用，消息列表增加消息时进行去重。
- `MessageCommonBaseViewHolder` 从 Common 库中移除，ChatKitUI 中相关 UI 和逻辑移动到在 ChatKitUI 中 `ChatBaseMessageViewHolder`。
- `MessageCommonBaseViewHolder` 从 Common 库中移除，QChatKitUI 中相关 UI 和逻辑移动到 `QChatBaseMessageViewHolder`。

**修复**

- 修复重复提示群组创建成功的问题。

    创建讨论组和高级群之后，进入讨论组或高级群的会话界面（即聊天界面），部分机型出现重复展示创建成功的提示信息。
- 修复图片库加载图片失败的问题。

    在 `ContactAvatarView` 中增加图片库加载图片失败处理，图片加载失败按照纯生背景+昵称的头像模式展示。

<a id="9.0.1 (2022-05-19)"></a>

## 9.0.1 (2022-05-19)

在 **我的** 模块中，**个人信息** 页面增加账号复制功能。

<a id="9.0.0 (2022-05-09)"></a>

## 9.0.0 (2022-05-09)

网易云信全新一代 IM UIKit 发布。

IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款即时通讯 UI 组件库，包括聊天、会话、圈组、搜索、群管理等组件。通过 IM UIKit，可快速集成包含 UI 界面的即时通讯应用。更多 IM UIKit 相关介绍请参考 [什么是 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/concept/jkyNDc2Mjg?platform=android) 和 [快速集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/jI1MjMyMTY?platform=android)。

<a id="8.5.0 (2021-06-22)"></a>

## 8.5.0 (2021-06-22)

**新增**

- 支持撤回自己给自己发送的消息。
- 成员信息页面增加回调监听，实时更新页面。
- 群设置界面支持群禁言。
- 高级群设置界面新增转让并退出群功能。

<a id="8.4.0 (2021-04-29)"></a>

## 8.4.0 (2021-04-29)

**新增**

- 会话列表页面收到会话更新通知时，如果数据库中没有此会话，则不创建会话项。
- 获取群消息的已读回执失败时，从本地加载。

<a id="8.2.0 (2020-12-30)"></a>

## 8.2.0 (2020-12-30)

**变更**

- 对会话进行排序时，不再频繁从数据库读取置顶信息。

<a id="8.1.0 (2020-11-13)"></a>

## 8.1.0 (2020-11-13)

**变更**

- 登录页新增独立模式进入聊天室入口。

<a id="[7.8.0] -2020-7-21"></a>

## 7.8.0 (2020-7-21)

**变更**

- 手动登录页面可配置设备自定义类型。此类型只在此次登录中生效。
- 会话置顶会多端同步和漫游。

<a id="[7.4.0] -2020-3-9"></a>

## 7.4.0 (2020-3-9)

**变更**

- 长按消息菜单栏中添加单向删除接口。
- 长按消息菜单栏中的撤回，变更为通知计入未读数和通知不计入未读数的撤回。
- 会话界面（即聊天界面）中菜单栏的云消息记录变更为被清除消息入库和不入库两栏。
- 会话界面（即聊天界面）中菜单栏的清空本地消息记录变更为记录操作和不记录操作两栏。

<a id="[7.2.0] -2020-1-13"></a>

## 7.2.0 (2020-1-13)

**变更**

- 设置页增加配置会话合并类型的项。
- 合并转发外观调整。
- 会话服务展示。

<a id="[7.0.0] -2019-11-13"></a>

## 7.0.0 (2019-11-13)

**变更**

- 封装合并转发功能。

<a id="[6.5.0]-2019-5-24"></a>

## 6.9.0 (2019-9-17)

**变更**

- 修复收到推送通知，头像图片不显示的问题。
- 修改 `GlobalSearchActivity` 和 `SearchMessageAcivity` 的 `screenOrientation` 参数为 `behind`。

<a id="[6.5.0]-2019-5-24"></a>

## 6.5.0 (2019-5-24)

**变更**

- 修复发送图片崩溃问题。

<a id="[5.9.0]-2018-11-28"></a>

## 5.9.0 (2018-11-28)

**变更**

- 修复多处内存泄漏问题。

<a id="5.7.0 (2018-10-11)"></a>

## 5.7.0 (2018-10-11)

**新增**

- 设置页面新增通知的振动模式。

- 好友资料页新增置顶操作。

<a id="5.6.1 (2018-9-13)"></a>

## 5.6.1 (2018-9-13)

**新增**

- 播放音频时贴近耳朵，切换成听筒模式。

- 图片、音频、视频、文件消息在未下载成功前支持转发。

**变更**

- 修复视频聊天切换画面崩溃。

- 视频聊天结束释放资源。

<a id="5.1.1 (2018-05-21)"></a>

## 5.1.1 (2018-05-21)

**变更**

- 多人通话使用 `AVChatTextureViewRenderer` 替换 `AVChatSurfaceViewRenderer`。

<a id="5.0.0 (2018-03-29)"></a>

## 5.0.0 (2018-03-29)

**新增**

- 白板模块组件化 RTSKit。

- 新增群组已读功能演示。

<!--下线红包功能
<a id="4.8.0 (2018-02-09)"></a>

## 4.8.0 (2018-02-09)

**变更**

- 红包功能更新。

-->

<a id="4.6.0 (2018-01-04)"></a>

## 4.6.0 (2018-01-04)

**新增**

- 抽取音视频组件 avchatkit。

- 集成 fabric 崩溃收集工具。

- 允许管理员撤回其他成员消息。

<a id="4.4.0 (2017-11-16)"></a>

## 4.4.0 (2017-11-16)

**新增**

- 添加全面屏配置。

- 规避 oppo r11 Toast 崩溃的问题。

**变更**

- 更新 UIKit 图片库，升级 Glide 到 V4.2.0。

- 非透明的 png 资源转成 webp 格式，减小包体积。

- 被拉黑发消息失败后的交互调整。

- Demo 开发环境升级到 Android Studio 3.0, Gradle tool 3.0，compile 26，target 26，适配 O 版本。

- UIKit 组件重构。

<a id="4.3.0 (2017-10-12)"></a>

## 4.3.0 (2017-10-12)

**新增**

- 添加聊天室独立模式 Demo。

- 添加批量清空所有未读数接口演示。

- 添加搜索历史图片/视频浏览界面。

**变更**

- 猜拳文本演示改成图片演示。

- UIKit 去掉对 avcaht library 的依赖。

- UIKit Glide 图片库升级到 V4.0，解决 GIF 动画加载延迟问题。

<a id="4.2.0 (2017-09-12)"></a>

## 4.2.0 (2017-09-12)

**新增**

- 聊天室机器人 Demo 演示。

<a id="4.1.0 (2017-08-08)"></a>

## 4.1.0 (2017-08-08)

**新增**

- 添加金融魔方组件，集成金融魔方红包示例。

- UIKit 添加 App Icon 未读数红点更新接口 Bader，适配国内主流厂商机型，demo 演示最近会话未读数与 App icon 红点数同步。

- 添加多人音视频与 WebRtc 通信开关。

**变更**

- 音视频在锁屏被呼叫时自动亮屏并唤起呼叫界面。

- UIKit @ 功能重构，修复输入框 @ 遗留的问题。

- 修复 targetSdkVersion 24 及以上时，选择拍摄照片失败问题。

<a id="4 .0.0 (2017-07-06)"></a>

## 4.0.0 (2017-07-06)

**新增**

- 添加机器人同步、机器人收发消息功能。
- 添加机器人 UI 组件。