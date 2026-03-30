本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）iOS 端开发版的更新日志，IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK iOS 版更新日志](https://doc.yunxin.163.com/messaging2/concept/TIxNTgxOTk?platform=client)。

## 近期重要更新

- 自 V9.6.1 起，新增全新的通用版 UI 组件，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件，具体请参考 [UIKit UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TU0NTc4MjM?platform=iOS)。
- 自 V9.5.0 起，会话模块支持音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话功能](https://doc.yunxin.163.com/messaging-uikit/guide/TA2MTk0Njg?platform=iOS)。
- 自 V9.3.0 起，会话模块支持地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/TE3MzA3ODk?platform=iOS)。

## <span id="9.7.4 (2025-04-03)">9.7.4 (2025-04-03)</span>

- 修复已知问题。
- 升级兼容的 IM SDK 至 [V9.17.0](https://doc.yunxin.163.com/messaging/concept/jQ3NzQ3NDI?platform=client#9170-2024-07-04)。

## <span id="9.7.3 (2024-11-14)">9.7.3 (2024-11-14)</span>

修复特定场景下，输入框中未自动填充 @xxx 的问题。

## <span id="9.7.2 (2024-08-09)">9.7.2 (2024-08-09)</span>

- 修复客户自定义消息无法解析的问题。
- 修复通用版皮肤-相册入口无法自定义的问题。
- 修复英文输入法候选词多次填入的问题。
- 修复复制粘贴丢失富文本样式的问题。
- 优化自定义场景下消息时间背景色显示。

## <span id="9.7.1 (2024-06-25)">9.7.1 (2024-06-25)</span>

修复输入框英文候选词重复输入的问题。

## <span id="[8.9.0] - 2024-02-22">8.9.0 (2024-02-22)</span>

基于 UIKit V9.7.0 适配 NIM SDK 8.9.124 版本。

**优化**

优化位置消息功能，采用静态图片方案。

**兼容 NIM SDK 版本**

V8.9.124

## <span id="9.7.0 (2024-01-25)">9.7.0 (2024-01-25)</span>

**新增特性**

- 新增从服务端查询用户信息的功能（先在本地查询，查询不到会向服务端查询）。
- 新增删除指定会话的历史消息功能，包括本地和云端历史消息。
- 新增群成员管理功能，包括群主添加或移除群组管理员、群主或管理员移除普通群成员。
- 新增消息多选操作功能，包括批量删除消息、合并转发消息功能。
- 新增富文本消息（换行消息）。
- 新增发送消息时被好友拉黑的提示。
- 新增创建空会话功能。
- 新增查询某个单聊或者群聊的最近会话是否存在功能。
- 标记列表新增单击查看功能（语音/视频/图片消息等支持查看和播放）。
- 输入框新增输入换行模式，即按下回车键不会立即提交消息，而是在输入框中插入一个换行符，用户可以继续输入下一行内容。
- 支持发送 GIF 图片。
- 支持删除被反垃圾的消息。
- 支持自定义消息的解析（通过新增的 `NECustomAttachment`、`NECustomAttachmentDecoder` 类和 `NECustomAttachmentProtocol` 协议实现）。
- 支持配置背景图片的拉伸参数（边距偏移）。
- 支持配置标记列表字体大小（文本类型）。
- 群聊中支持配置是否展示好友昵称。
- 支持群主或者管理员开启关闭普通群成员在群组中 @ 所有人权限。
- 支持配置是否展示群聊、是否允许通讯录异步进行远端加载（通过新增的 `IMKitConfigCenter` 配置类实现）。

**变更**

- 消息时间间隔将根据相邻消息的时间差进行显示隐藏，不再作为单独的数据 model 以及消息体 cell。
- 注册自定义消息解析器移至 `setupCoreKitIM` 初始化接口。
- 群成员列表页面按照成员入群时间排序，支持显示管理员身份，支持移除成员。
- 为了防止与用户设置的类名冲突，该版本将在所有对象前添加前缀，具体变更的类名如下：

    原类名 | 新类名
    ---- | ----
    UserInfo | NEKitUserInfo
    User | NEKitUser
    Gender | NEGender
    OperationType | NEOperationType
    AddFriendRequest | NEAddFriendRequest
    TeamType | NETeamType
    Team | NETeam
    NotificationType | NENotificationType
    IMHandleStatus | NEHandleStatus
    XNotification | NENotification

**修复**

- 修复已读未读消息列表在高版本 iOS 系统上异常问题。
- 修复非漫游云端语音消息无法播放问题。
- 修复单聊转发消息的成员选择列表无当前聊天对象的问题。
- 修复聊天页输入框中多条连续@高亮文本长按移动光标无法定位到中间问题。

**兼容的 NIM SDK 版本**

V9.14.2

## <span id="9.6.5 (2023-12-08)">9.6.5 (2023-12-08)</span>

**变更**

- 圈组相关内容拆分至 `NECoreQChatKit`，若需要使用圈组功能，请参考 [圈组 UIKit](https://doc.yunxin.163.com/messaging-uikit/concept/jc2MDU1MzY?platform=iOS)。
- repo 层提供单例 shared，不提供实例化接。
- 移除 `NEChatUITool` 类及类中的 `getSizeWithAtt()` 方法，推荐使用 String 类的 `finalSize()` 方法代替。
- 添加是否隐藏单聊设置页面创建群聊入口配置。
- 移除第三方依赖 UITextView+Placeholder （使用 NETextView）。
- 添加是否显示创建群聊入口配置。
- 好友名片页，单击 **聊天** 后移除当前页面（名片页）。

**修复**

- 修复文本中包含异常字符时，最后一个表情（emoji）识别不了的问题。
- 修复删除会话后，未读数未清空的问题。

**兼容的 NIM SDK 版本**

V9.14.0

## <span id="9.6.3 (2023-11-07)">9.6.3 (2023-11-07)</span>

**变更**

- `NECoreIMKit` 库中移除圈组相关内容。
- repo 层提供单例 `shared`，不提供实例化接口。
- 移除第三方依赖 UITextView+Placeholder 和 RSKPlaceholderTextView，使用 IM UIKit 自身 `NECommonKit` 库中的 `NETextView`。
- IM UIKit 兼容的 NIM SDK 版本升级到 V9.12.0。
- IM UIKit 兼容的呼叫组件版本升级到 V2.2.0。

**问题修复**

- 修复文本中包含异常字符时，最后一个 emoji 识别不了的问题。
- 修复删除会话后，未读数未清空的问题。
- 修复收到撤回通知后，消息长按菜单不收起的问题。

## <span id="9.6.1 (2023-07-11)">9.6.1 (2023-07-11)</span>

**升级必看**

自 V9.6.1 起，废弃 `NETeamKit`、`NEContactKit`、`NEConversationKit` 三个 Repository，其功能将全部合并至 `NEChatKit` 中。在引入组件时，直接引入 `NEChatKit` 使用即可。

对应的 UI 层 `NETeamUIKit`、`NEContactUIKit`、`NEConversationUIKit` 保留，都依赖于 `NEChatKit`。

**新增特性**

- 新增全新的通用版 UI 组件，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件，具体请参考 [UIKit UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TU0NTc4MjM?platform=iOS)。
- 消息长按功能项支持全局过滤、自定义配置。
- 删除会话列表本地最近会话同时删除服务端最近会话。
- 群设置页面根据群人数是否达到上限显示隐藏添加群成员。
- 群成员超过 200 人不显示已读/未读。

**优化**

按照消息类型合并界面 **左右两边** 的消息体，便于维护。

每种类型的消息体中都包含 **左右两边** 消息展示所需要的所有元素，并根据消息方向进行了布局，在展示前可以根据消息方向控制元素的显隐以及完成元素对象的赋值。

**变更**

- IM UIKit 兼容的 NIM SDK 版本升级到 V9.11.0。
- `ChatProvider` 和 `ChatRepo` 中新增 `sendForwardMessage` 方法，用于发送生成的转发消息。
- `ChatRepo` 中新增 `makeForwardMessage(message:, session:)` 方法，用于生成转发消息并转发。

**问题修复**

- 修复黑名单列表多端登录未同步的问题。
- 修复搜索好友搜索自己未跳转到个人详情页的问题。
- 修复底部功能区再次单击不能收起的问题。
- 播放语音消息过程接到音视频通话，语音消息未停止播放的问题。
- 修复其他已知问题。

## <span id="9.5.0 (2023-04-20)">9.5.0 (2023-04-20)</span>

**新增特性**

- 新增 @ 功能，支持在群组中 @ 群成员，在会话列表中收到 @ 消息会高亮展示。
- 会话相关页面新增标记（pin）列表，可查看所有标记的消息。
- 新增回复消息功能，采用非 Thread 模式实现。
- 新增系统通知合并展示功能。

**变更**

IM UIKit 兼容的 NIM SDK 版本升级到 V9.10.0。

**问题修复**

- 修复接收超长文本消息展示过多空白区域的问题。
- 修复好友列表数据较多时不展示好友列表数据的问题。
- 修复多端登录下断网重连会话置顶信息未同步的问题。
- 修复其他已知问题。

## <span id="9.4.0 (2023-03-10)">9.4.0 (2023-03-10)</span>

**新增特性**

- 会话模块支持音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话功能](https://doc.yunxin.163.com/messaging-uikit/guide/TA2MTk0Njg?platform=iOS)。
- 圈组中支持表情和语音消息。
- `conversationRepo` 核心类中新增接口 `clearAllUnreadCount`，用于清空所有未读数。

**变更**

- IM UIKit 兼容的 NIM SDK 版本升级到 V9.8.0。
- 离线消息支持 NIM SDK 的动态查询历史消息功能，避免出现历史消息拉取不完整的问题。更多详情请参考 [动态查询历史消息](https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS)。
- 撤回可编辑时间从五分钟调整为两分钟。

**优化**

- 对齐好友资料页面、验证消息页面和消息列表页面显示的头像逻辑。
- 首次登录或者切换账户会话列表数量异常优化。
- 优化通讯录好友列表排序规则。
- 个人名片页新增生日栏。

**问题修复**

- 修复滑动消息详情页面时，消息功能面板不会消失的问题。
- 修复长按更多操作框在有键盘弹出的逻辑下单击不生效的问题。
- 修复黑名单页好友昵称超长文案展示重叠的问题。
- 修复其他已知问题。

## <span id="9.3.1 (2023-01-05)">9.3.1 (2023-01-05)</span>

本版本修复 `NEMapKit` 组件的已知问题。

其他组件请使用 V9.3.0 版本。

## <span id="9.3.0 (2022-12-05)">9.3.0 (2022-12-05)</span>

**新增特性**

- 新增地理位置消息功能，具体实现方法参考 [实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/TE3MzA3ODk?platform=iOS)。
- 新增文件消息功能（升级后可直接使用）。

    <img alt="文件消息图.png" src="https://yx-web-nosdn.netease.im/common/2a8b159c6f3b05114ccb4a769f8a6c04/文件消息图.png" style="width:30%;border: 1px solid #BFBFBF;">

**问题修复**

- 修复更新讨论组/高级群头像失败的问题。
- 修复发送视频消息未显示首帧的问题。
- 修复表情和文案不一致的问题。
- 修复 **正在输入中** 的显示问题。
- 修复群聊消息已读按钮失效的问题。
- 修复其他已知问题。

## <span id="9.2.11 (2022-11-17)">9.2.11 (2022-11-17)</span>

**NIM SDK 版本兼容**

IM UIKit 兼容的 NIM SDK 版本升级到 V9.6.4。

**问题修复**

- 修复好友名片中未显示基本信息的问题。
- 修复视频消息加载问题。
- 修复更新自己群昵称失败的问题。
- 修复加入他人圈组服务器的按钮失效问题。
- 修复圈组频道成员列表和频道黑白名单成员列表的展示问题。
- 修复无法退出图片详情页的问题。
- 修复历史图片未展示缩略图的问题。
- 修复黑名单成员列表头像与好友头像不一致的问题。
- 修复其他已知问题。

## <span id="9.2.10 (2022-11-02)">9.2.10 (2022-11-02)</span>

修复 Xcode 14 编译错误问题。

## <span id="9.2.9 (2022-10-24)">9.2.9 (2022-10-24)</span>

**变更**

本版本将 `IMkitEngine` 核心类中的功能全部迁移至 `IMkitClient` 类中，涉及的 API 只变更其所属类，具体方法原型不变。

`IMKitEngine` 类即将废弃，无法调用，请使用新的核心类（`IMkitClient`）。

**优化**

- 优化自定义用户信息功能的 `IUserInfoDelegate`。
- 完善 Objective-C 工程（简称 OC）调用 UIKit 功能。
- 统一 pod 引用 名称，例如：
    - `import NEKitConversationUI` 更改为 `import NEConversationUIKit`。
    - `import NEKitChatUI` 更改为 `import NEChatUIKit`。

**问题修复**

- 修复 Xcode 14 源码集成报错问题。
- 修复其他已知问题。

## <span id="9.2.8 (2022-09-20)">9.2.8 (2022-09-20)</span>

**新增特性**

- 适配多语言环境，本版本支持中英文切换。
- `IMKitEngine` 核心类新增圈组登出接口 `IMKitEngine.instance.logoutQchat`。

**优化**

优化登录功能，统一初始化和登录模块。

**变更**

本版本将登录相关接口迁移至 `IMKitEngine` 核心类，涉及变更的 API 如下：

功能 | API 变更说明
---- | ----
登录 IM | `IMKitLoginManager.instance.loginIM` 变更为 `IMKitEngine.instance.loginIM`。
登录圈组 | `IMKitLoginManager.instance.loginQchat` 变更为 `IMKitEngine.instance.loginQchat`。
登出 IM | `IMKitLoginManager.instance.logout` 变更为 `IMKitEngine.instance.logout`。
自动登录 IM | `IMKitLoginManager.instance.autoLogin` 变更为 `IMKitEngine.instance.autoLogin`。

:::note note
- 涉及的 API 只变更其所属类，具体方法原型不变。
- `IMKitLoginManager` 类已废弃，无法调用，请使用新的调用方法。
:::

**问题修复**

- 修复已知页面展示问题。
- 相机相册请求权限修改。

## <span id="9.2.7 (2022-08-25)">9.2.7 (2022-08-25)</span>

**问题修复**

- 修复 Swift 版本编译问题。
- 修复相册选择图片时图片展示问题。
- 修复圈组频道身份组权限信息展示问题。

## <span id="9.2.4 (2022-06-28)">9.2.4 (2022-06-28)</span>

**优化**

- 优化补充自定义消息逻辑。
- 路由配置功能与 Android 端对齐。
- 修改 Toast 提示信息位置。

**问题修复**

修复下拉崩溃和消息重复问题。

## <span id="9.2.2 (2022-06-24)">9.2.2 (2022-06-24)</span>

**新增特性**

| <div style="width:30px">序号</div> | <div style="width:80px">新增特性</div> | <div style="width:100px">特性描述</div> |
| --- | --- | --- |
| 1 | UI 层支持个性化配置功能 | <div><ul><li>`NEKitChatUI` 中新增 `NEKitChatConfig`，支持自定义聊天界面 UI。</li><li>`NEKitConversationUI` 中新增 `NEKitConversationConfig`，支持设置会话列表界面的 UI 自定义。</li><li>`NEKitContactUI` 中新增 `NEKitContactConfig` 支持自定义通讯录界面 UI。</ul></div> |
| 2 | 初始化 | 在 `IMKitEngine` 模块中：<ul><li>新增 `setupCoreKitIM` 接口配置 IM 初始化相关操作。</li><li>新增 `getAppkey`（获取 App Key）、` isUsingDemoAppKey`（是否正在使用 Demo App Key）、`qchatWithOption` （设置圈组选项）、`updateApnsToken` （更新 APNS Token）、` updatePushKitToken` （更新 PushKit Token）等基础方法。 |
| 3 | 登录 | 新增 `IMKitLoginManager` 类，实现 IM 登录，自动登录，登出等功能。 |
| 4 | 项目混编支持 | <div><ul><li>支持核心类继承：`P2PChatViewController`、`GroupChatViewController`、`ConversationListViewController`、`ContactsViewController`、`QchatViewController`。</li><li>支持在 Objective-C 项目中调用 swift 的方法。 |

**NIM SDK 版本兼容**

IM UIKit 兼容的 NIM SDK 版本升级到 V9.2.5，圈组的系统通知增加新的通知类型，具体请参考 [NIM SDK 更新日志](https://doc.yunxin.163.com/messaging/concept/jQ3NzQ3NDI?platform=iOS#925-2022-6-13)。

**优化**

对 Repository 层的接口进行了调整和优化，涉及改动的模块包括 `ChatRepo`、`ContactRepo`、`ConversationRepo`、`TeamRepo`。

## <span id="9.0.2 (2022-05-29)">9.0.2 (2022-05-29)</span>

- 修复 `NEConversationUIKit`、`NEChatUIKit`、`NETeamUIKit`、`NEQChatUIKit` 和 `NEContactUIKit` 中作用域问题。
- 修复模拟器编译 pod 库失败问题。

## <span id="9.0.1 (2022-05-19)">9.0.1 (2022-05-19)</span>

**新增特性**

在 **我的** 模块中，**个人信息** 页面增加账号复制功能。

**问题修复**

- 修复头像被压缩问题。
- 修复视频消息的视屏压缩模糊问题。
- 修复搜索框背景色与高度问题。
- 修复会话列表首页弹窗阴影过重问题。
- 修复 alert 弹窗色值问题。
- 修复通讯录 icon 失真问题。
- 更新会话列表的 logo 和标题。
- 修复圈组聊天页键盘偶现不能弹起问题。
- 修复图片预览被压缩变形问题。

## <span id="9.0.0 (2022-05-09)">9.0.0 (2022-05-09)</span>

网易云信全新一代 IM UIKit 发布。

IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款即时通讯 UI 组件库，包括聊天、会话、圈组、搜索、群管理等组件。通过 IM UIKit，可快速集成包含 UI 界面的即时通讯应用。更多 IM UIKit 相关介绍请参考 [UIKit 简介](https://doc.yunxin.163.com/messaging-uikit/concept/zc3MDc4Nzk?platform=iOS) 和 [集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/TA5NzE3MzQ?platform=iOS)。

## <span id="8.5.0 (2021-06-22)">8.5.0 (2021-06-22)</span>

**新增特性**

- 支持撤回自己给自己发送的消息。

## <span id="8.4.0 (2021-04-29)">8.4.0 (2021-04-29)</span>

**新增特性**

- 获取群消息的已读回执失败时，从本地加载。

<a id="8.3.0 (2021-03-03)"></a>

## 8.3.0 (2021-03-03)

**新增特性**

- 适配 SDK 动态登录功能。

<a id="8.2.0 (2020-12-30)"></a>

## 8.2.0 (2020-12-30)

**修复**

- iOS 14 相册适配（NIMKit 依赖的 TZImagePickerController 升级版本）。

<a id="8.0.0 (2020-09-28)"></a>

## 8.0.0 (2020-09-28)

**新增特性**

- iOS 14 UI 的适配。
- iOS 14 相册受限权限的适配。

<a id="7.8.5 (2020-08-14)"></a>

## 7.8.5 (2020-08-14)

**修复**

- iCloud 同步状态时发送视频出现的崩溃问题。

<a id="7.8.4 (2020-08-14)"></a>

## 7.8.4 (2020-08-14)

**修复**

- 相机拍摄崩溃问题。

<a id="7.6.0 (2020-05-13)"></a>

## 7.6.0 (2020-05-13)

**新增特性**

- 消息回复功能演示。
- 收藏夹功能演示。
- 会话 PIN 标记功能演示。
- 消息快捷评论功能演示。
- 会话置顶功能演示。

<a id="7.4.0 (2020-03-11)"></a>

## 7.4.0 (2020-03-11)

**新增特性**

- IM Demo && NIMKit 英文国际化适配。

<a id="7.2.0 (2020-01-13)"></a>

## 7.2.0 (2020-01-13)

**新增特性**

- 超大群组功能演示。
- 会话搜索功能演示。
- 好友搜索功能演示。
- 增加 Emoji 表情使用功能演示。
- 增加会话服务功能演示。

<a id="7.0.0 (2019-11-13)"></a>

## 7.0.0 (2019-11-13)

**新增特性**

- 新增消息多选功能演示。
- 新增消息合并转发功能演示。
- 新增第三方视频 URL，截取第一帧作为封面。

<a id="6.1.0 (2019-01-22)"></a>

## 6.1.0 (2019-01-22)

**新增特性**

- 设置界面里新增历史消息迁移入口。
- 新增历史迁移功能演示，以及相应加解密功能演示。

<a id="5.7.0 (2018-10-11)"></a>

## 5.7.0 (2018-10-11)

**新增特性**

- 通信录里设置近期聊天置顶功能。

<a id="5.0.0 (2018-03-29)"></a>

## 5.0.0 (2018-03-29)

**新增特性**

- 群组已读功能。

**优化**

- 本地历史记录搜索后定位以及优化。

**修复**

- 云消息页面下拉后界面显示异常。

<a id="4.8.0 (2018-02-08)"></a>

## 4.8.0 (2018-02-08)

**新增特性**

- 新增历史记录搜索后定位到聊天页位置。
- 加入 Fabric 崩溃统计。

<a id="4.6.0 (2018-01-04)"></a>

## 4.6.0 (2018-01-04)

**新增特性**

- iPhoneX 适配。
- 新增允许群管理员撤回其他人的消息。

<a id="4.4.0 (2017-11-15)"></a>

## 4.4.0 (2017-11-15)

**新增特性**

- 大图预览器支持长图显示。
- 新增被拉黑后发消息的提示交互。
- 组件添加请求失败池，请求出现异常后不会重复请求。

**修复**

- 更新红包库，修正老版本红包库无法在 debug 模式下调试的问题。
- 组件重构，移除之前 plist 配置方式，抽出通用配置类 `NIMKitConfig`。

<a id="4.3.0 (2017-10-12)"></a>

## 4.3.0 (2017-10-12)

**新增特性**

- 新增批量清空所有未读数接口演示。
- 新增搜索历史图片/视频浏览界面。

**修复**

- 适配 iOS 11。
- 修正 NIMKitProgressView 可能会导致的崩溃问题。
- 组件数据提供者 dataProvider 重构。
- 组件 contentSize 计算方式重构。

<a id="4.2.0 (2017-09-12)"></a>

## 4.2.0 (2017-09-12)

**新增特性**

- 聊天室机器人演示。
- 升级相册控件至版本 V1.9.0。

<a id="4.1.0 (2017-08-08)"></a>

## 4.1.0 (2017-08-08)

**新增特性**

- 新增金融魔方红包示例。
- 好友账号搜索默认强转小写，防止与 SDK 账号匹配不上。

**修复**

- 修复好友选择器在某些情况下出现的样式问题。
- 修正 @ 顺序，修正一条消息里如果指明多个机器人，会随机一个机器人回复的问题。
- 修正非透明导航导致的键盘错位问题。

<a id="4.0.0 (2017-07-06)"></a>

## 4.0.0 (2017-07-06)

**新增特性**

- 机器人消息收发界面。
- 机器人模板解析。
- 新增机器人消息气泡的 UI 组件。