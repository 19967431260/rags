IM UIKit 的会话模块（`NEChatUIKit`）提供会话界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。会话消息模块（`NEChatUIKit`）提供以下两种方式对会话消息的 UI 进行个性化定制。

- 通过接口配置的方式自定义 UI。
- 通过源码修改的方式自定义 UI。

    ::: note note
    请优先使用接口配置方式。如果接口中的配置项满足您的界面个性化需求，请优先使用接口配置方式。
    :::

## 自定义功能概述

### UI 元素自定义

会话消息界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img src="https://yx-web-nosdn.netease.im/common/17603c554221947629d382b4afa9a816/消息界面新.png" style="width:60%;border: 2px solid #f2f2f2;" />

`ChatUIConfig` 是整个会话消息的配置文件，其中 UI 实例化对象类型为 `ChatUIConfig`。

您可通过 `ChatUIConfig` 中的个性化配置项修改会话界面 UI 元素，如消息体、输入按钮和消息长按菜单等，具体如下：
<div style="width:140px">属性</div> | 类型 | 说明
---- | ---- | ----
`messageItemClick` | (UITableViewCell, MessageContentModel?) -> Void | 用于设置消息体中的单击事件处理 |
`messageProperties` | MessageProperties | 消息页面的 UI 个性化定制，包括常用的字体颜色、大小、是否可见、背景色等属性等。单击 `MessageProperties` 左侧的 + 展开展示 **`MessageProperties` 个性化配置项** 更多信息。 |
  `selfMessageTextSize` | CGFloat | 自己发送的消息的字体大小(文本类型)。
  `receiveMessageTextSize` | CGFloat | 接收到的消息的字体大小(文本类型)。
  `selfMessageTextColor` | UIColor | 自己发送的消息的字体颜色(文本类型)。
  `receiveMessageTextColor` | UIColor | 接收到的消息的字体颜色(文本类型)。
  `selfMessageBgColor` | UIColor | 自己发送的消息体的背景色，具体自定义示例见下文的 [修改消息体背景色](#修改消息体背景色)。
  `receiveMessageBgColor` | UIColor | 接收到的消息体的背景色，具体自定义示例见下文的 [修改消息体背景色](#修改消息体背景色)。
  `selfMessageBgImage` | UIImage | 自己发送的消息体的背景气泡。
  `receiveMessageBgImage` | UIImage | 接收到的消息体的背景气泡。
  `backgroundImageCapInsets` | UIEdgeInsets | 背景图片拉伸参数（边距偏移）。
  `userNickColor` | UIColor | 不设置头像的用户所展示的文字头像中的文字颜色。
  `userNickTextSize` | CGFloat | 不设置头像的用户所展示的文字头像中的文字字体大小。
  `messageTextColor` | UIColor | 文本消息字体颜色。
  `messageTextSize` | CGFloat | 文本消息字体大小。
  `avatarType` | NEChatAvatarType | 头像类型，`NEChatAvatarType.rectangle` = 1 代表矩形，`NEChatAvatarType.cycle` 代表圆形。
  `avatarCornerRadius` | CGFloat | 头像的圆角大小，仅在 `avatarType` = `NEChatAvatarType.rectangle` 时生效。
  `timeTextSize` | CGFloat | 消息列表中，时间字体大小。
  `timeTextColor` | UIColor | 消息列表中，时间字体颜色。
  `signalBgColor` | UIColor | 被标记消息的背景色。
  `showP2pMessageStatus` | Bool | 单聊中是否展示已读未读状态。
  `showTeamMessageStatus` | Bool | 群聊中是否展示已读未读状态。
  `showTeamMessageNick` | Bool | 群聊中是否展示好友昵称。
  `showTitleBar` | Bool | 会话界面是否展示标题栏，具体自定义示例见下文的 [隐藏界面标题栏](#隐藏界面标题栏)。
  `showTitleBarRightIcon` | Bool | 是否展示标题栏右侧图标按钮。
  `titleBarRightRes` | UIImage | 设置标题栏右侧图标按钮展示图标，具体自定义示例见下文的 [修改界面标题右侧图标](#修改界面标题栏右侧图标)。
  `titleBarRightClick` | () -> Void | 标题栏右侧图标的单击事件。
  `chatViewBackground` | UIColor | 设置会话界面背景色，具体自定义示例见下文的 [修改会话界面背景色](#修改会话界面背景色)。
`customController` | (ChatViewController) -> Void | 消息页面中，获取页面的整个视图。可用于在页面中添加、移除或者修改布局元素。
`chatInputBar` | (inout [UIButton]) -> Void | 消息页面中，文本输入框下方 tab 按钮定制。
`chatInputMenu` | (inout [NEMoreItemModel]) -> Void | 消息页面中，输入框按钮定制。可用于修改输入框按钮以及更多中按钮的增加、修改和删除。
`chatPopMenu` | (inout [OperationItem], MessageContentModel?) -> Void | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单的增加、删除和修改。
`popMenuClick` | (OperationItem) -> Void | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单的单击事件的修改，可修改默认实现和自定义菜单的单击。
`fileSizeLimit` | Double | 消息页面中，发送文件大小限制(单位：MB)，默认 200。
`bodyTopView` | UIView | 消息列表界面上方的小块视图，可在子类直接获取视图进行样式修改。用于在消息详情和顶部标题视图中间增加新的 UI 元素，具体自定义示例见下文的 [会话消息标题栏下方扩展视图](#会话消息标题栏下方扩展视图)。
`bodyBottomView` | UIView | 输入框视图上方的小块视图，可在子类直接获取视图进行样式修改，用于在消息详情和底部输入框中间增加新的 UI 元素，具体自定义示例见下文的 [输入框上方区域扩展视图](#输入框上方区域扩展视图)。

### 界面布局自定义

除了界面的 UI 元素，您也可对界面的布局进行自定义。
在 `NEChatUIKit` 模块中，所有的 Cell 都继承于 `NEChatBaseCell`。
以基础版皮肤中的文本消息为例，其继承链路为：`ChatMessageTextCell` -> `NormalChatMessageBaseCell` -> `NEBaseChatMessageCell` -> `NEChatBaseCell`。

:::note notice
- 基础信息（如背景颜色，头像或者昵称）会在上层的 `NEBaseChatMessageCell` 中赋值，需要单独处理的逻辑需要在各自对应的业务 Cell 中完成。

- 每种类型的消息体中都包含左右两边消息展示所需要的所有元素，并根据消息方向进行了布局，在展示前可以根据消息方向控制元素的显隐以及完成元素对象的赋值。
:::

会话界面的默认布局如下图所示：

<img style="width:60%;border: 2px solid #f2f2f2;" src="https://yx-web-nosdn.netease.im/common/7bad48d354a31a43a4a663a19406ab9d/消息布局新.png" />

该界面各视图的说明如下：

<div style="width:140px">属性</div> | 类型 | 说明
---- | ---- | ----
`titleBarView` | UIView | 聊天界面标题，可通过 `navigationView` 来获取视图进行样式修改。
`navigationView` | TabNavigationView | 聊天界面的标题视图，可在子类直接获取视图进行样式修改，具体自定义示例请参考下文的 [自定义标题栏按钮](#自定义标题栏按钮)。
`bodyTopView` | UIView | 消息列表界面上方的小块视图，可在子类直接获取视图进行样式修改。用于在消息详情和顶部标题视图中间增加新的 UI 元素，具体自定义示例请参考下文的 [会话消息标题栏下方扩展视图](#会话消息标题栏下方扩展视图)。
`bodyView` | UIView | 消息列表的内容视图，可在子类直接获取视图进行样式修改。布局中包含 `brokenNetworkView` 错误提示视图和 `contentView` 列表视图。
`brokenNetworkView` | NEBrokenNetworkView | 聊天界面错误提示视图，可在子类直接获取视图进行样式修改。
`contentView` | UIView | 消息列表的列表视图，可在子类直接获取视图进行样式修改。布局中包含 `tableView` 消息列表和 `emptyView` 空数据提示视图。
`tableView` | UITableView | 消息详情列表，可在子类直接获取视图进行样式修改。
`emptyView` | NEEmptyDataView | 聊天界面空数据提示视图，可在子类直接获取视图进行样式修改。
`bottomView` | UIView | 消息列表底部视图，可在子类直接获取视图进行样式修改，布局中包含 `bodyBottomView` 扩展视图和 `chatInputView` 输入框视图。
`bodyBottomView` | UIView | 输入框视图上方的小块视图，可在子类直接获取视图进行样式修改，用于在消息详情和底部输入框中间增加新的 UI 元素，具体自定义示例请参考下文的 [输入框上方区域扩展视图](#输入框上方区域扩展视图)。
`chatInputView` | UIView | 聊天界面的底部输入框视图，可在子类中进行样式修改。具体自定义示例请参考下文的 [自定义输入框左右间距](#自定义输入框左右间距)<br> `chatInputView.stackView` 为输入框底部工具栏视图，可添加或删除按钮。具体自定义示例请参考下文的 [自定义底部工具条](#自定义底部工具条) 和 [自定义 **更多** 功能页](#自定义-更多-功能页)。

## 通过配置项自定义 UI 示例

::: note notice
会话消息的个性化 UI 样式需要在会话消息界面加载之前配置，例如您可以在 `IMKitClient` 的 `setupIM` 方法中设置个性化定制属性。
更多示例代码请参考 app/IMUIKitExample/Custom/CustomConfig.swift
:::

### 使用系统导航栏（不推荐）

UIKit 默认使用自定义导航栏，如果你需要使用系统导航栏，请在会话消息界面加载之前完成如下配置：

:::::: div custom-tabs
::: tab Swift
```Swift
// import NECommonUIKit
NEConfigManager.instance.setParameter(key: useSystemNav, value: true)
```
:::
::: tab Objective-C
```Objective-C
// #import <NECommonUIKit/NECommonUIKit-Swift.h>
[NEConfigManager.instance setParameterWithKey:@"useSystemNav" value:YES];
```
:::
::::::



### 修改界面标题栏右侧图标

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    ChatUIConfig.shared.ui.messageProperties.titleBarRightRes = UIImage(named: "image name")
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    ChatUIConfig.shared.ui.messageProperties.titleBarRightRes = [UIImage imageNamed:@"image name"];
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" title="默认" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情右侧按钮.png" src="https://yx-web-nosdn.netease.im/common/ea31a022987bf9540cf27b79e5342471/消息详情右侧按钮.png" style="width:55%;"> |

### 隐藏界面标题栏

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    ChatUIConfig.shared.ui.messageProperties.showTitleBar = false
    ```
    :::
    ::: tab Objective-C
    ```obj
    ChatUIConfig.shared.ui.messageProperties.showTitleBar = NO;
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情隐藏标题栏.png" src="https://yx-web-nosdn.netease.im/common/c40029028bbe94d2fb148827198c366e/消息详情隐藏标题栏.png" style="width:55%;">

### 修改会话界面背景色

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    ChatUIConfig.shared.ui.messageProperties.chatViewBackground = UIColor.red
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    ChatUIConfig.shared.ui.messageProperties.chatViewBackground = [UIColor redColor];
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情背景色.png" src="https://yx-web-nosdn.netease.im/common/b2b708fc001fc2a2c06b4ce09a28099f/消息详情背景色.png" style="width:55%;">

### 修改消息体背景色

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    //修改自己消息体背景色
    ChatUIConfig.shared.ui.messageProperties.selfMessageBgColor = UIColor.green
    ChatUIConfig.shared.ui.messageProperties.selfMessageBgImage = UIImage() // 隐藏气泡
    //修改对方消息体背景色
    ChatUIConfig.shared.ui.messageProperties.receiveMessageBgColor = UIColor.gray
    ChatUIConfig.shared.ui.messageProperties.receiveMessageBgImage = UIImage() // 隐藏气泡
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    //修改自己消息体背景色
    ChatUIConfig.shared.ui.messageProperties.selfMessageBgColor = [UIColor blueColor];
    ChatUIConfig.shared.ui.messageProperties.selfMessageBgImage = [UIImage new]; // 隐藏气泡
    //修改对方消息体背景色
    ChatUIConfig.shared.ui.messageProperties.receiveMessageBgColor = [UIColor blueColor];
    ChatUIConfig.shared.ui.messageProperties.receiveMessageBgImage = [UIImage new]; // 隐藏气泡
    ```
    :::
    ::::::

    ::: note notice
    会话消息的消息体背景色与气泡共存，若只需要实现纯色背景色效果，请将默认气泡图片隐藏（置为 nil）
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情消息背景色.png" src="https://yx-web-nosdn.netease.im/common/a0dc2119968ba46eac770f1b5594fb3f/消息详情消息背景色.png" style="width:55%;">

### 会话消息标题栏下方扩展视图

可在标题栏和消息详情中间插入扩展视图，例如显示群聊人数、在线状态，插入温馨提示等。

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    /// 消息列表的视图控制器回调，回调中会返回消息列表的视图控制器
    /// customTopView：自定义视图
    ChatUIConfig.shared.customController = { viewController in
        // 顶部bodyTopView中添加自定义view（需要设置bodyTopView的高度）
        self.customTopView.button.setTitle("通过配置项添加", for: .normal)
        viewController.bodyTopView.backgroundColor = .purple
        viewController.bodyTopView.addSubview(customTopView)
        viewController.bodyTopViewHeight = 80
    }
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    /// 消息列表的视图控制器回调，回调中会返回消息列表的视图控制器
    /// customTopView：自定义视图
    ChatUIConfig.shared.customController = ^(ChatViewController * _Nonnull viewController) {
        // 顶部bodyTopView中添加自定义view（需要设置bodyTopView的高度）
        [self.customTopView setTitle:@"通过配置项添加" forState:UIControlStateNormal];
        viewController.bodyTopView.backgroundColor = UIColor.purpleColor;
        [viewController.bodyTopView addSubview:customTopView];
        viewController.bodyTopViewHeight = 80;
    };
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情提示消息上.png" src="https://yx-web-nosdn.netease.im/common/2db94fd5ef69188f714bfc63b0ae2b88/消息详情提示消息上.png" style="width:55%;">

### 输入框上方区域扩展视图

可在输入框上方插入扩展视图，例如添加候选词条、个性化功能等。

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    /// 消息列表的视图控制器回调，回调中会返回消息列表的视图控制器
    /// customTopView：自定义视图
    ChatUIConfig.shared.customController = { viewController in
    // 底部bodyBottomView中添加自定义view（需要设置bodyBottomView的高度）
    self.customBottomView.button.setTitle("通过配置项添加", for: .normal)
    viewController.bodyBottomView.backgroundColor = .purple
    viewController.bodyBottomView.addSubview(customBottomView)
    viewController.bodyBottomViewHeight = 60
    }
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    /// 消息列表的视图控制器回调，回调中会返回消息列表的视图控制器
    /// customTopView：自定义视图
    ChatUIConfig.shared.customController = ^(ChatViewController * _Nonnull viewController) {
        // 底部bodyBottomView中添加自定义view（需要设置bodyBottomView的高度）
        [self.customTopView setTitle:@"通过配置项添加" forState:UIControlStateNormal];
        viewController.bodyBottomView.backgroundColor = UIColor.purpleColor;
        [viewController.bodyBottomView addSubview:customTopView];
        viewController.bodyBottomViewHeight = 60;
    };
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情提示消息下.png" src="https://yx-web-nosdn.netease.im/common/538fde32fac1e3725b11ff1797f06ae3/消息详情提示消息下.png" style="width:55%;">

## 源码介绍

### **会话消息**

`ChatViewController` 为会话消息的基类，内部封装了 `UITableView`。

所有类型的消息都以 Cell 形式展示，需要在 `cellRegisterDic` 注册列表中声明不同消息体对应的 Cell 类，用于 `UITableView` 的 Cell 注册。利用面向对象语言的多态性，不同类型的 Cell 重写了父类的 `setModel` 方法，且每种类型的 Cell 都有与之对应的数据模型。

默认的 `cellRegisterDic` 注册方法请参考 `ChatMessageHelper` 工具类中的 `getChatCellRegisterDic` 方法

对应关系如下:

:::::: div custom-tabs
::: tab 基础版 UI Cell

基础版 UI Cell 类别 | 数据模型 | 说明
---- | ---- | ----
ChatMessageTextCell | MessageTextModel | 文本消息类型
ChatMessageAudioCell | MessageAudioModel | 语音消息类型
ChatMessageImageCell | MessageImageModel | 图片消息类型
ChatMessageVideoCell | MessageVideoModel | 视频消息类型
ChatMessageFileCell | MessageFileModel | 文件消息类型
ChatMessageLocationCell | MessageLocationModel | 地理位置消息类型
ChatMessageCallCell | MessageCallRecordModel | 音视频消息类型
ChatMessageReplyCell | MessageTextModel | 回复（文本）消息类型
ChatMessageRevokeCell | MessageTextModel | 撤回（文本）消息类型
ChatMessageTipCell | MessageTipsModel | 提示消息类型
ChatMessageMultiForwardCell | MessageCustomModel | 合并转发消息类型
ChatMessageRichTextCell | MessageRichTextModel | 换行消息类型

:::
::: tab 通用版 UI Cell

通用版 UI Cell 类别 | 数据模型 | 说明
---- | ---- | ----
FunChatMessageTextCell | MessageTextModel | 文本消息类型
FunChatMessageAudioCell | MessageAudioModel | 语音消息类型
FunChatMessageImageCell | MessageImageModel | 图片消息类型
FunChatMessageVideoCell | MessageVideoModel | 视频消息类型
FunChatMessageFileCell | MessageFileModel | 文件消息类型
FunChatMessageLocationCell | MessageLocationModel | 地理位置消息类型
FunChatMessageCallCell | MessageCallRecordModel | 音视频消息类型
FunChatMessageReplyCell | MessageTextModel | 回复（文本）消息类型
FunChatMessageRevokeCell | MessageTextModel | 撤回（文本）消息类型
FunChatMessageTipCell | MessageTipsModel | 提示消息类型
FunChatMessageMultiForwardCell | MessageCustomModel | 合并转发（自定义）消息类型
FunChatMessageRichTextCell | MessageRichTextModel | 换行消息类型

:::
::::::

### **赋值处理**

1. 根据 `V2NIMMessage` 的 `messageType ` 类型，判断消息类型。
2. 针对不同的消息类型，使用对应的数据模型进行解析。

    ```swift
    public class ChatMessageHelper: NSObject {
        public static func modelFromMessage(message: NIMMessage) -> MessageModel {
            var model: MessageModel
            switch message.messageType {
            case .MESSAGE_TYPE_VIDEO:
            model = MessageVideoModel(message: message)
            case .MESSAGE_TYPE_TEXT:
            model = MessageTextModel(message: message)
            case .MESSAGE_TYPE_IMAGE:
            model = MessageImageModel(message: message)
            case .MESSAGE_TYPE_AUDIO:
            model = MessageAudioModel(message: message)
            case .MESSAGE_TYPE_NOTIFICATION, .MESSAGE_TYPE_TIP:
            model = MessageTipsModel(message: message)
            case .MESSAGE_TYPE_FILE:
            model = MessageFileModel(message: message)
            case .MESSAGE_TYPE_LOCATION:
            model = MessageLocationModel(message: message)
            case .MESSAGE_TYPE_CALL:
            model = MessageCallRecordModel(message: message)
            case .MESSAGE_TYPE_CUSTOM:
            if let type = NECustomAttachment.typeOfCustomMessage(message.attachment) {
                if type == customMultiForwardType {
                return MessageCustomModel(message: message, contentHeight: Int(customMultiForwardCellHeight))
                }
                if type == customRichTextType {
                return MessageRichTextModel(message: message)
                }

                // 注册过的自定义消息类型
                return MessageCustomModel(message: message, contentHeight: Int(customMultiForwardCellHeight))
            }
            fallthrough
            default:
            // 未识别的消息类型，默认为文本消息类型，text 为未知消息体
            message.text = chatLocalizable("msg_unknown")
            model = MessageTextModel(message: message)
            }
            return model
        }
    }
    ```

3. 在 `ChatViewController` 的 Cell 展示数据源方法中进行赋值。

    ```swift
    open func tableView(_ tableView: UITableView,
                        cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let model = viewModel.messages[indexPath.row]
        var reuseId = "\(NEBaseChatMessageCell.self)"
        if model.replyedModel?.isReplay == true,
            model.isRevoked == false {
            if model.customType == customRichTextType {
                reuseId = "\(MessageType.richText.rawValue)"
            } else {
                reuseId = "\(MessageType.reply.rawValue)"
            }
        } else {
            let key = "\(model.type.rawValue)"
            if model.type == .custom {
                if model.customType == customMultiForwardType {
                reuseId = "\(MessageType.multiForward.rawValue)"
                } else if model.customType == customRichTextType {
                reuseId = "\(MessageType.richText.rawValue)"
                } else if NEChatUIKitClient.instance.getRegisterCustomCell()["\(model.customType)"] != nil {
                reuseId = "\(model.customType)"
                } else {
                reuseId = "\(NEBaseChatMessageCell.self)"
                }
            } else if model.type == .notification || model.type == .tip {
                reuseId = "\(MessageType.time.rawValue)"
            } else if cellRegisterDic[key] != nil {
                reuseId = key
            } else {
                reuseId = "\(NEBaseChatMessageCell.self)"
            }
        }

        let cell = tableView.dequeueReusableCell(withIdentifier: reuseId, for: indexPath)
        if let c = cell as? NEBaseChatMessageTipCell {
            if let m = model as? MessageTipsModel {
                c.setModel(m)
            }
            return c
        } else if let c = cell as? NEBaseChatMessageCell {
            c.delegate = self

            ...

            if let m = model as? MessageContentModel {
                c.setModel(m, m.message?.isSelf ?? false)
                c.setSelect(m, isMutilSelect)
            }

            return c
        } else if let c = cell as? NEChatBaseCell, let m = model as? MessageContentModel {
            c.setModel(m, m.message?.isSelf ?? false)
            return cell
        } else {
            return NEBaseChatMessageCell()
        }
    }
    ```

### **子类继承**

协同版皮肤下，`P2PChatViewController` 和 `TeamChatViewController` 均继承于 `NormalChatViewController`，`NormalChatViewController` 则继承于 `ChatViewController`

这里以 `P2PChatViewController` 为例，具体如下:

```swift
@objcMembers
open class P2PChatViewController: NormalChatViewController {

    /// 重写父类的构造方法
    /// - Parameter conversationId: 会话 ID
    /// - Parameter anchor: 锚点消息
    public init(conversationId: String, anchor: V2NIMMessage?) {
        super.init(conversationId: conversationId)
        viewModel = P2PChatViewModel(conversationId: conversationId, anchor: anchor)
    }
    ...
}
```

```swift
@objcMembers
open class NormalChatViewController: ChatViewController {

    override public init(conversationId: String) {
        super.init(conversationId: conversationId)
        navigationView.backgroundColor = .white
        navigationController?.navigationBar.backgroundColor = .white
        cellRegisterDic = ChatMessageHelper.getChatCellRegisterDic(isFun: false)

        topMessageView.topImageView.image = UIImage.ne_imageNamed(name: "top_message_image")
        topMessageView.layer.borderColor = UIColor(hexString: "#E8EAED").cgColor
        topMessageView.layer.borderWidth = 1
    }
    ...
}
```

## 通过源码自定义 UI

布局中的内容概略如下：

```swift
//这里以 ChatMessageTextCell 为例。
open class ChatMessageTextCell: NormalChatMessageBaseCell {
    override public init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)
        commonUI()
    }

    public required init?(coder: NSCoder) {
        super.init(coder: coder)
    }

    open func commonUI() {
        bubbleImageLeft.addSubview(contentLabelLeft)
        NSLayoutConstraint.activate([
        contentLabelLeft.rightAnchor.constraint(equalTo: bubbleImageLeft.rightAnchor, constant: -chat_content_margin),
        contentLabelLeft.leftAnchor.constraint(equalTo: bubbleImageLeft.leftAnchor, constant: chat_content_margin),
        contentLabelLeft.topAnchor.constraint(equalTo: bubbleImageLeft.topAnchor, constant: chat_content_margin),
        contentLabelLeft.bottomAnchor.constraint(equalTo: bubbleImageLeft.bottomAnchor, constant: -chat_content_margin),
        ])

        bubbleImageRight.addSubview(contentLabelRight)
        NSLayoutConstraint.activate([
        contentLabelRight.rightAnchor.constraint(equalTo: bubbleImageRight.rightAnchor, constant: -chat_content_margin),
        contentLabelRight.leftAnchor.constraint(equalTo: bubbleImageRight.leftAnchor, constant: chat_content_margin),
        contentLabelRight.topAnchor.constraint(equalTo: bubbleImageRight.topAnchor, constant: chat_content_margin),
        contentLabelRight.bottomAnchor.constraint(equalTo: bubbleImageRight.bottomAnchor, constant: -chat_content_margin),
        ])
    }

    override open func showLeftOrRight(showRight: Bool) {
        super.showLeftOrRight(showRight: showRight)
        contentLabelLeft.isHidden = showRight
        contentLabelRight.isHidden = !showRight
    }

    override open func setModel(_ model: MessageContentModel, _ isSend: Bool) {
        super.setModel(model, isSend)
        let contentLabel = isSend ? contentLabelRight : contentLabelLeft
        if let m = model as? MessageTextModel {
        contentLabel.attributedText = m.attributeStr
        contentLabel.accessibilityValue = m.message?.text
        }
    }
}
```

### 自定义标题栏按钮

自定义导航栏需要使用 `navigationView` 来实现。

`navigationView` 采用固定按钮，包括左侧的返回按钮（`backButton`）和右侧的更多按钮（`moreButton`），此外还包含中间的导航栏标题（`navTitle`）和底部分割线(`titleBarBottomLine`)，具体定义请参考 `NENavigationView` 类，所有控件均可访问修改。

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    // 修改标题
    navigationView.navTitle.text = "title"

    // 修改右侧按钮文案
    navigationView.setMoreButtonTitle("clear")

    // 修改右侧按钮文案颜色
    navigationView.moreButton.setTitleColor(.red, for: .normal)

    // 修改右侧按钮单击事件
    navigationView.moreButton.addTarget(self, action: #selector(clearMessage), for: .touchUpInside)
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    // 修改标题
    navigationView.navTitle.text = @"title";

    // 修改右侧按钮文案
    [navigationView setMoreButtonTitle:@"clear"];

    // 修改右侧按钮文案颜色
    [navigationView.moreButton setTitleColor:[UIColor redColor] forState:UIControlStateNormal];

    // 修改右侧按钮单击事件
    [navigationView.moreButton addTarget:self action:@selector(clearMessage) forControlEvents:UIControlEventTouchUpInside];
    ```
    :::
    ::::::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情自定义右侧图标.png" src="https://yx-web-nosdn.netease.im/common/746ede517ebaec0dd3a02935a1a3b13c/消息详情自定义右侧图标.png" style="width:55%;">

### 自定义标题栏标题

- 示例代码（Swfit）
    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            super.viewDidLoad()

            // Do any additional setup after loading the view.
        }

        // 自定义标题
        override func getSessionInfo(sessionId: String, _ completion: @escaping () -> Void) {
            super.getSessionInfo(sessionId: sessionId) {
            self.title = "小易助手"
            completion()
            }
        }
    }
    ```
    ::: note note
    网易云信 IM 默认会在数据加载完成后设置会话消息页面标题，如需自定义标题，请重写 `getSessionInfo` 方法，并在父类方法调用之后设置其值。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情标题栏标题.png" src="https://yx-web-nosdn.netease.im/common/9df952e5a0ccc155a040540503e45e9d/消息详情标题栏标题.png" style="width:55%;"> |


### 会话消息标题栏下方扩展视图

可在标题栏和消息详情中间插入扩展视图，例如插入 **温馨提示**。

- 示例代码（Swfit）

    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        public lazy var customTopView: CustomView = {
            let view = CustomView(frame: CGRect(x: 0, y: 10, width: NEConstant.screenWidth, height: 40))
            view.backgroundColor = .blue
            return view
        }()

        override func viewDidLoad() {
            super.viewDidLoad()
            ...

            // 聊天页顶部导航栏下方扩展视图示例
            customTopView.btn.setTitle( **通过重写方式添加** , for: .normal)
            bodyTopView.addSubview(customTopView)
            bodyTopView.backgroundColor = .yellow
            bodyTopViewHeight = 80
        }
    }
    ```

    :::note note
    示例代码中 `bodyTopView` 为聊天页顶部标题栏下方预留的扩展视图，`bodyTopViewHeight` 为该扩展视图的高度，更改此变量会刷新页面布局。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情提示消息上.png" src="https://yx-web-nosdn.netease.im/common/2db94fd5ef69188f714bfc63b0ae2b88/消息详情提示消息上.png" style="width:55%;">

### 输入框上方区域扩展视图

用户可继承聊天界面详情页（`P2PChatViewController`/`TeamChatViewController`），在父类渲染页面之前更改输入框上方区域。

- 示例代码（Swfit）

    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            ...

            // 输入框上区域扩展视图示例
            customBottomView.btn.setTitle("通过重写方式添加", for: .normal)
            bodyBottomView.addSubview(customBottomView)
            bodyBottomView.backgroundColor = .yellow
            bodyBottomViewHeight = 60
        }
    }
    ```

    :::note note
    示例代码中 `bodyBottomView` 为输入框上方预留的扩展视图，`bodyBottomViewHeight` 为该扩展视图的高度，更改此变量会刷新页面布局。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情提示消息下.png" src="https://yx-web-nosdn.netease.im/common/538fde32fac1e3725b11ff1797f06ae3/消息详情提示消息下.png" style="width:55%;">

### 自定义输入框左右间距

用户可自定义输入框左右间距，从而实现在输入框左右添加控件。

- 示例代码（Swfit）

    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            ...
            // 聊天页输入框左右间距自定义
            chatInputView.textviewLeftConstraint?.constant = 100
            chatInputView.textviewRightConstraint?.constant = -100
        }
    }
    ```

    :::note note
    示例代码中 `textviewLeftConstraint/textviewRightConstraint` 表示输入框左侧/右侧距页面左边框/右边框的距离，即输入框左右间距，更改此变量会刷新页面布局。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情输入框间距.png" src="https://yx-web-nosdn.netease.im/common/7c56afb29900b5447839f1a56f7c402a/消息详情输入框间距.png" style="width:55%;">

### 自定义底部工具条

用户可自定义输入框底部工具条的按钮样式和单击事件。

- 示例代码（Swfit）

    ```swift
    // 通过配置项实现
        class CustomP2PChatViewController: P2PChatViewController {
            
            override func viewDidLoad() {

            /// 文本输入框下方 tab 按钮定制
            ChatUIConfig.shared.ui.chatInputBar = { [weak self] item in
            // 修改
            let takePicBtn = item[2]
            takePicBtn.setImage(nil, for: .normal)
            takePicBtn.setTitle("拍照", for: .normal)
            takePicBtn.setTitleColor(.blue, for: .normal)
            takePicBtn.removeTarget(takePicBtn.superview, action: nil, for: .allEvents)
            takePicBtn.addTarget(self, action: #selector(self?.customClick), for: .touchUpInside)

            // 新增
            let button = UIButton(type: .custom)
            button.setTitle("新增", for: .normal)
            button.setTitleColor(.blue, for: .normal)
            button.addTarget(self, action: #selector(self?.customClick), for: .touchUpInside)
            item.append(button)
            }

            ...

            super.viewDidLoad()
            }
        }
    ```

    ```swift
    // 通过重写实现
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            ...

            let subviews = chatInputView.stackView.subviews
            subviews.forEach { view in
                view.removeFromSuperview()
                chatInputView.stackView.removeArrangedSubview(view)
            }

                let titles = ["表情", "语音", "照片", "更多"]
            for i in 0 ..< titles.count {
                let button = UIButton(type: .custom)
                let title = titles[i]
                button.translatesAutoresizingMaskIntoConstraints = false
                button.addTarget(self, action: #selector(buttonEvent), for: .touchUpInside)
                button.tag = i
                button.setTitle(title, for: .normal)
                button.setTitleColor(.blue, for: .normal)
                chatInputView.stackView.addArrangedSubview(button)
            }
        }

            @objc func buttonEvent(_ btn: UIButton) {
            if btn.tag == 0 { // 表情
            layoutInputView(offset: bottomExanpndHeight, true)
            chatInputView.addEmojiView()
            } else if btn.tag == 1 { // 语音
            layoutInputView(offset: bottomExanpndHeight, true)
            chatInputView.addRecordView()
            } else if btn.tag == 2 { // 照片
            goPhotoAlbumWithVideo(self)
            } else if btn.tag == 3 { // 更多
            layoutInputView(offset: bottomExanpndHeight, true)
            chatInputView.addMoreActionView()
            }
        }
    }
    ```

    :::note note
    示例代码中，`chatInputView` 为输入框视图，`chatInputView.stackView` 为输入框底部工具栏视图，代码先将工具栏视图中的所有子视图（按钮）移除，然后依次添加自定义的子视图（按钮），并为按钮绑定单击事件 `buttonEvent`。`buttonEvent` 中利用 `tag` 对按钮进行区分，实现具体的逻辑。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情底部工具条按钮.png" src="https://yx-web-nosdn.netease.im/common/6decd7562874d063cc48780fe6a19ba2/消息详情底部工具条按钮.png" style="width:55%;">

### 自定义“更多”功能页

用户可根据业务需求，自定义聊天输入区域的 **更多** 功能区。

- 示例代码（Swfit）

    ```swift
    // 通过配置项实现
    class CustomP2PChatViewController: P2PChatViewController {

        /// 更多区域功能列表自定义示例
        ChatUIConfig.shared.ui.chatInputMenu = { [weak self] menuList in
            // 新增未知类型
            let itemNew = NEMoreItemModel()
            itemNew.customImage = UIImage(named: "mine_collection")
            itemNew.customDelegate = self
            itemNew.action = #selector(self?.customClick)
            itemNew.title = "新增"
            menuList.append(itemNew)

            // 覆盖已有类型
            // 遍历 menuList，根据 type 覆盖已有类型
            for item in menuList {
                if item.type == .rtc {
                item.customImage = UIImage(named: "mine_setting")
                item.customDelegate = self
                item.action = #selector(self?.customClick)
                item.type = .rtc
                item.title = "覆盖"
                }
            }

            // 移除已有类型
            // 遍历 menuList，根据 type 移除已有类型
            for (i, item) in menuList.enumerated() {
                if item.type == .file {
                menuList.remove(at: i)
                }
            }
        }

    ...

        // 需要在父类视图加载之前完成自定义
        super.viewDidLoad()
    }
    ```

    ```swift
    // 通过重写方式实现
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            /// **更多** 区域功能列表自定义示例

            // 新增未知类型
            let itemNew = NEMoreItemModel()
            itemNew.customImage = UIImage(named: "mine_collection")
            itemNew.customDelegate = self
            itemNew.action = #selector(customClick)
            itemNew.title = "新增"
            NEChatUIKitClient.instance.moreAction.append(itemNew)

            // 覆盖已有类型
            // 遍历 NEChatUIKitClient.instance.moreAction，根据 type 覆盖已有类型
            for (i, item) in NEChatUIKitClient.instance.moreAction.enumerated() {
                if item.type == .rtc {
                    let itemReplace = NEChatUIKitClient.instance.moreAction[i]
                    itemReplace.customImage = UIImage(named: "mine_setting")
                    itemReplace.customDelegate = self
                    itemReplace.action = #selector(customClick)
                    itemReplace.type = .rtc
                    itemReplace.title = "覆盖"
                }
            }

            // 移除已有类型
            // 遍历 NEChatUIKitClient.instance.moreAction，根据 type 移除已有类型
            for (i, item) in NEChatUIKitClient.instance.moreAction.enumerated() {
                if item.type == .file {
                    NEChatUIKitClient.instance.moreAction.remove(at: i)
                }
            }

            ...

            // 需要在父类视图加载之前完成自定义
            super.viewDidLoad()
        }
    }
    ```

    上述代码中的 `NEChatUIKitClient.instance.moreAction` 为全局 **更多** 功能列表，通过 `itemNew.customImage` 和 `itemNew.customDelegate` 共同组合来实现按钮的自定义单击事件。IM UIKit 默认实现的能力如下表所示，内部对这些类型的单击事件做了默认实现，可根据业务需要来决定是否覆盖。

    <div style="width:140px">标识 Action</div> | 说明
    ---- | ----
    `NEMoreActionType.takePicture` | 拍照
    `NEMoreActionType.file` | 发送文件
    `NEMoreActionType.rtc` | 音视频通话
    `NEMoreActionType.location` | 地理位置

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="消息详情页默认.png" src="https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png" style="width:55%;"> | <img alt="消息详情更多功能页.png" src="https://yx-web-nosdn.netease.im/common/6ee4a3d3d23cbbccb822222fba349cf7/消息详情更多功能页.png" style="width:55%;">

### 消息长按菜单过滤部分能力

长按消息功能弹窗可设置全局过滤列表或者针对单个功能项进行修改。

- 示例代码

    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            ...
            // 长按消息功能弹窗过滤列表（过滤列表中的能力会在整个页面中禁用）
            operationCellFilter = [.delete]
        }

        // 长按消息功能弹窗列表自定义（可针对不同 type 消息自定义长按功能项）
        override func setOperationItems(items: inout [OperationItem], model: MessageContentModel?) {
            if model?.type == .rtcCallRecord {
            items.append(OperationItem.replayItem())
            }
        }
    }
    ```

- 代码解读

    - 示例代码中的 `operationCellFilter` 为长按菜单过滤列表，其中的类型在整个会话详情页不会显示，最终的效果表现为：整个会话详情页的所有消息类型的长按菜单中均不显示 **删除** 功能。

    - 示例代码中的 `setOperationItems` 方法会返回每条消息的长按功能弹窗列表，可针对单条消息或者某种类型的消息进行长按功能项的自定义

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="长按原.png" src="https://yx-web-nosdn.netease.im/common/4bdf574b176365ea64aed49d2361ebc9/长按原.png" style="width:55%;"> | <img alt="长按新.png" src="https://yx-web-nosdn.netease.im/common/ee6e98fa344ddee6a90259e26be33d1f/长按新.png" style="width:55%;">

### 消息长按弹出菜单自定义

- 示例代码

    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            ...

            /// 消息长按弹出菜单自定义
            ChatUIConfig.shared.ui.chatPopMenu = { menuList, model in
                // 遍历 menuList，根据 type 覆盖已有类型
                // 将所有文本消息的 **复制** 替换成 **粘贴**
                if model?.type == .text {
                    for item in menuList {
                    if item.type == .copy {
                        item.text = "粘贴"
                    }
                    }
                }
            }

            /// 消息长按弹出菜单的单击事件回调，根据按钮类型进行区分
            ChatUIConfig.shared.ui.popMenuClick = { [weak self] item in
                switch item.type {
                case .copy:
                    // 更改 **复制** 类型按钮的单击事件
                    self?.customClick()
                default:
                    break
                }
            }
        }
    }
    ```

- 代码解读

    示例代码中的 `chatPopMenu` 为消息长按弹出菜单回调、`popMenuClick` 为消息长按弹出菜单的单击事件回调，可以根据 `type` 类型进行区分进而实现自定义。

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="未弹出.png" src="https://yx-web-nosdn.netease.im/common/2be7edc71aa19b2a34983e36b8f9ff5e/未弹出.png" style="width:55%;"> | <img alt="长按原.png" src="https://yx-web-nosdn.netease.im/common/4bdf574b176365ea64aed49d2361ebc9/长按原.png" style="width:55%;">