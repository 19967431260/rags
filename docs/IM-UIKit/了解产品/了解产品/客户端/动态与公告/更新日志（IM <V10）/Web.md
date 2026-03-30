本文介绍网易云信含 UI 即时通讯（简称 IM UIKit）Web 端 0.0.1 (2022-8-3) ～ 9.x.x 版本的 IM UIKit 更新日志。IM UIKit 兼容的网易云信即时通讯 SDK（简称 NIM SDK）的变更记录请参考 [NIM SDK Web 版更新日志](https://doc.yunxin.163.com/messaging2/concept/DE2Mzk4MDg?platform=client)。

## 近期重要更新

- 从 9.8.4 起，支持发送视频消息。
- 从 9.6.0 起，消息页面（包括单聊和群聊）右侧设置栏按钮支持自定义，具体请参考 [自定义消息页面右侧设置栏按钮](https://doc.yunxin.163.com/messaging-uikit/guide/Tk2NDUxODc?#自定义消息页面右侧设置栏按钮)。

<a id="9.8.7 (2024-12-27)"></a>

## <span style=""><b>9.8.7 (2024-12-27)</b></span>

**新增**

- 消息滚动模式支持 nearest。
- 静态资源支持私有化。

**优化**

优化 @消息实现方案。

<a id="9.8.4 (2024-02-22)"></a>

## <span style=""><b>9.8.4 (2024-02-22)</b></span>

**新增特性**

支持发送视频消息。

**优化**

优化发送图片消息的交互。

**修复**

修复转让群组后通讯录列表未显示该群组的问题。

<a id="9.7.2 (2024-01-11)"></a>

## <span style=""><b>9.7.2 (2024-01-11)</b></span>

支持显示未漫游到的置顶消息。

<a id="9.6.5 (2023-11-24)"></a>

## <span style=""><b>9.6.5 (2023-11-24)</b></span>

**优化**

- 重发消息增加 loading。
- 删除好友时自动解除拉黑的逻辑修改为添加好友时自动解除拉黑。

**修复**

- Avatar 组件更新 bug fix。
- 修复 IMUIKit context 属性 undefined 问题。

**升级**

升级 im-store 库。

<a id="9.6.2 (2023-09-22)"></a>

## <span style=""><b>9.6.2 (2023-09-22)</b></span>

- 优化性能，提高会话切换的速度。
- 每个会话内的消息缓存数量调整到最新的 20 条。
- 图片消息增加 Blob 链接，提高加载速度和性能。

<a id="9.6.0 (2023-08-21)"></a>

## <span style=""><b>9.6.0 (2023-08-21)</b></span>

**新增特性**

- 消息页面（包括单聊和群聊）右侧设置栏按钮支持自定义，具体请参考 [自定义消息页面右侧设置栏按钮](https://doc.yunxin.163.com/messaging-uikit/guide/Tk2NDUxODc?platform=web#自定义消息页面右侧设置栏按钮)。
- 在输入框最右侧新增发送按钮，效果与键盘发送相同。

    <img alt="发送置灰加高亮.png" src="https://yx-web-nosdn.netease.im/common/33caa411b0240888f025e1669608f0c5/发送置灰加高亮.png" style="width:30%;border: 1px solid #BFBFBF;">

- 支持删除音视频通话消息操作。

    <img alt="删除话单.png" src="https://yx-web-nosdn.netease.im/common/069fa240db5a7898d77120735eafb682/删除话单.png" style="width:30%;border: 1px solid #BFBFBF;">

- 新增群管理员（默认最多设置 10 个）身份，实现群管理功能。

    <img alt="群管理功能.png" src="https://yx-web-nosdn.netease.im/common/20b119d6e8bd8057e93f460e86b29887/群管理功能.png" style="width:30%;border: 1px solid #BFBFBF;">

    :::note note
    新增的群管理员功能，支持自主开启/关闭显示，用来控制当身份为管理员时的主动操作是否展示，不影响其他管理员身份的显示。默认不显示（不可见），若需要，可在初始化时将 `localOptions.teamManagerVisible` 设置为 true。
    :::

**优化**

- 优化音视频通话和音视频消息播放冲突问题。
- 对齐 @ 消息的推送相关参数 `pushInfo`。
- 优化当没有消息时不显示撤回消息的问题。

**NIM SDK 版本兼容**

IM Web UIKit 兼容的 NIM SDK 版本：9.11.0

<a id="9.5.6 (2023-06-15)"></a>

## <span style=""><b>9.5.6 (2023-06-15)</b></span>

**升级必看**

UIKit 将 **显示单聊/群聊消息的已读未读标记** 的配置项（`p2pMsgReceiptVisible` & `teamMsgReceiptVisible`）从会话界面（`chat-kit`）移至初始化配置中（`localOptions`）。升级至该版本后，如涉及该功能，请及时修改相关代码。

**新增特性**

- 会话列表支持显示消息的已读未读状态。
- 群组成员列表支持搜索和群成员排序。
- 支持在线/离线状态的展示。
- 群组的群主身份支持转让。
- 支持自定义消息右键操作列表。
- @ 消息支持一键配置。
- 同意好友申请后，打招呼消息支持自定义配置。

**优化**

- 优化好友数量较多时的卡顿问题。
- 优化图片无边框效果。
- 优化源码集成引用路径。

**修复**

- 修复撤回功能相关问题。
- 修复个人头像修改失败的问题。
- 修复语音消息与视频消息同时播放的问题。
- 修复交互& UI 展示以及其他已知问题。

**NIM SDK 版本兼容**

IM Web UIKit 兼容的 NIM SDK 版本：V9.11.0

<a id="9.4.2 (2023-05-09)"></a>

## <span style=""><b>9.4.2 (2023-05-09)</b></span>

**功能新增**

- 会话模块支持一对一音视频通话功能。实现音视频通话的具体说明，请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/zI1NDYzNTg?platform=web)。
- 新增 @ 功能，支持在群聊中 @ 群成员。
- 支持将单条消息转发至会话。

**优化改进**

- 优化回复消息功能，采用非 Thread 模式实现。
- 优化好友验证逻辑。

<a id="9.3.4 (2023-03-22)"></a>

## <span style=""><b>9.3.4 (2023-03-22)</b></span>

- 包结构调整。
- 修复收不到离线系统通知的问题。
- `localOptions` 增加 `sendMsgBefore` 钩子函数，允许用户自定义消息发送前的参数。
- chat 组件支持自定义消息头像和昵称。

<a id="0.3.0 (2023-01-17)"></a>

## <span style=""><b>0.3.0 (2023-01-17)</b></span>

**组件变更**

- `chat-kit` 新增如下参数：

    - `p2pMsgReceiptVisible`：是否显示单聊消息的已读和未读标志，boolean 类型，默认 false。
    - `teamMsgReceiptVisible`：是否显示群聊消息的已读和未读标记，boolean 类型，默认 false。

- `localeConfig` 中新增字符串，具体参考 [语言设置](https://doc.yunxin.163.com/messaging-uikit/guide/jUxMDYxMTM?platform=web)。

**功能新增**

IM UIKit 新增如下默认支持的功能：

- 支持在 Demo 内进行中英文切换。

    <img alt="中英文切换.png" src="https://yx-web-nosdn.netease.im/common/8f39c297539947d91dffa51b4836bde8/中英文切换.png" style="width:50%;border: 1px solid #BFBFBF;">

- 支持设置在群里显示的昵称。

    <img alt="群昵称设置.png" src="https://yx-web-nosdn.netease.im/common/9353cbf05cd156efc6b30561ba71be9b/群昵称设置.png" style="width:50%;border: 1px solid #BFBFBF;">

- 支持单聊和群聊中的已读和未读标志。

    <img alt="Web 单聊已读未读标记.png" src="https://yx-web-nosdn.netease.im/common/d574c30d00329a5a563b658c91b499fb/Web单聊已读未读标记.png" style="width:50%;border: 1px solid #BFBFBF;">

- 支持针对某一条消息（包括文本、图片和文件消息）进行引用回复。

    <img alt="回复消息.png" src="https://yx-web-nosdn.netease.im/common/9a8ef0c6fc4c66079055455c20b1bd08/回复消息.png" style="width:50%;border: 1px solid #BFBFBF;">

    <img alt="Web 回复消息发送成功.png" src="https://yx-web-nosdn.netease.im/common/5e27a30ed1915f1fe3b333a4096668c3/Web回复消息发送成功.png" style="width:50%;border: 1px solid #BFBFBF;">

- 支持正常播放从移动端发来的语音消息和视频消息，并且可单击放大查看移动端发来的地理位置。

<a id="0.2.1 (2022-12-23)"></a>

## <span style=""><b>0.2.1 (2022-12-23)</b></span>

**功能新增**

- 多端登录：多端可同时在线登录，登录后消息同步接收、好友关系同步获取、群权限同步更改。
- 好友邀请与申请的处理。
- 好友备注。
- 会话置顶。
- **仅群主可邀请** 权限。
- 系统通知：群名称/头像变动、成员进出等。

**API 变更**

- 初始化新增 `localOptions` 参数。
- 通讯录组件（`contact-kit`）：
    - ContactList 关系导航组件新增 `onItemClick`，表示通通讯录导航单击事件。
    - ContactInfo 关系详情组件新增 `renderMsgListEmpty` 和 `renderMsgListHeader` 接口，分别用于 **自定义渲染消息中心为空时内容** 和 **自定义渲染消息中心头部内容**。
- 会话消息组件（`chat-kit`）：
    - 原来的自定义渲染聊天消息接口 `renderCustomMessage` 已废弃，新增 `renderP2pCustomMessage` 和 `renderTeamCustomMessage`，分别用于自定义渲染单聊自定义消息和群聊自定义消息。
    - 新增 `actions` 参数，表示消息发送按钮组配置，不传使用默认的配置。
    - 新增 `onSendText` 发送文本消息回调函数。
    - 新增 `renderTeamMemberItem` 接口，用于自定义渲染群成员 Item。
- 会话列表组件（`conversation-kit`）:
    - 新增 `onSessionItemStickTopChange` 会话置顶状态变化事件回调。
    - 新增 `renderSessionName`，用于自定义渲染会话名称。
    - 新增 `renderSessionMsg`，用于自定义渲染会话消息。
    - 新增 `renderP2pSessionAvatar`，用于自定义渲染单聊会话头像。
    - 新增 `renderTeamSessionAvatar`，用于自定义渲染群组会话头像。
- 搜索组件（`search-kit`）:
    - 新增 `renderEmpty` 和 `renderSearchResultEmpty`，分别用于渲染 **没有好友和群组时的状态展示** 和 **没有搜索结果时的自定义渲染**。

**其他**

[IM UIKit Store API 参考](https://doc.yunxin.163.com/messaging-uikit/client-apis/zg2NzI0NzI?platform=web) 上线。

<a id="0.2.0 (2022-11-15)"></a>

## <span style=""><b>0.2.0 (2022-11-15)</b></span>

- 新增 Vue Demo，具体说明参考 [体验 Demo](https://doc.yunxin.163.com/messaging-uikit/guide/jMwMzA5NjA?platform=web)。也可 [跑通 IM Demo 源码](https://doc.yunxin.163.com/messaging-uikit/guide/TMwMjkzNDU?platform=web) 体验网易云信的即时通讯能力。
- 支持基于所有 Web 开发框架（例如 Vue 和 Angular）或者原生 HTML 集成 IM UIKit。如果需要基于 React 以外的 Web 框架及原生 HTML 集成，请参考 [非 React 框架集成 IM UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/TY2OTg3OTY?platform=web)。

<a id="0.1.0 (2022-9-6)"></a>

## <span style=""><b>0.1.0 (2022-9-6)</b></span>

**功能新增**

- 新增用户资料组件 `MyAvatarContainer`。相关说明请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DAwOTczOTg?platform=web" target="_blank">集成用户资料组件</a>。

**优化改进**

- `useStateContext` 方法中原 `state` 返回值废弃，新增 `store` 返回值。基于 Mobx 的数据和 UI 双向绑定能力，`store` 提供 IM UIKit 内部数据驱动能力，减少用户调用该方法的心智成本。更多相关说明，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TIzNDI0OTc?platform=web" target="_blank">全局上下文</a>。
- `localeConfig` 中部分字符串变更与优化。当前的字符串请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jUxMDYxMTM?platform=web" target="_blank">语言设置</a>。
- `chat-kit` 组件中，原 `ChatProvider` 废弃，且组件参数变更，相关详情请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jMyMDYzMjk?platform=web" target="_blank">集成会话消息界面</a>。
- `contact-kit` 组件中，增加 `ContactInfo` 替代之前的 `FriendList`、`GroupList` 和 `BlackList`，且组件参数变更，相关详情请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jU3MTQ1NjQ?platform=web" target="_blank">集成通讯录界面</a>。

<a id="0.0.1 (2022-8-3)"></a>

## <span style=""><b>0.0.1 (2022-8-3)</b></span>

IM UIKit 首个版本发布，该版本支持注册与登录、通讯录、会话列表（单聊和群聊）、黑名单和消息收发（文本、表情、图片和文件）等功能，详细功能列表请参考 [IM UIKit 功能列表](https://doc.yunxin.163.com/messaging-uikit/concept/TQ0Njk3ODU?platform=web)。