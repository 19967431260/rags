
IM UIKit 的会话模块（`NEChatUIKit`）提供会话界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。

会话消息模块（`NEChatUIKit`）提供以下两种方式对会话消息的 UI 进行个性化定制。
- 通过接口配置的方式自定义 UI。
- 通过源码修改的方式自定义 UI。

::: note note
如果接口中的配置项满足您的界面个性化需求，请优先使用接口配置方式。
:::


## 自定义功能概述

### UI 元素自定义

会话消息界面可自定义的 UI 元素包括但不限于下图中的标注项。


<img src="https://yx-web-nosdn.netease.im/common/17603c554221947629d382b4afa9a816/消息界面新.png" style="width:80%" />


`NEKitChatConfig`是整个会话消息的配置文件，其中 UI 实例化对象类型为 `ChatUIConfig`。

您可通过`ChatUIConfig`中的个性化配置项修改会话界面 UI 元素，如消息体、输入按钮和消息长按菜单等，具体如下：
<div style="width:140px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`messageItemClick` | (UITableViewCell, MessageContentModel?) -> Void |用于设置消息体中的点击事件处理
`messageProperties` | MessageProperties | 消息页面的UI个性化定制，包括常用的字体颜色、大小、是否可见、背景色等属性等，具体见下文的 **MessageProperties 个性化配置项**
`customController` | (ChatViewController) -> Void | 消息页面中，获取页面的整个视图。可用于在页面中添加、移除或者修改布局元素。
`chatInputBar` | (inout [UIButton]) -> Void | 消息页面中，文本输入框下方 tab 按钮定制。
`chatInputMenu` | (inout [NEMoreItemModel]) -> Void | 消息页面中，输入框按钮定制。可用于修改输入框按钮以及更多中按钮的增加、修改和删除。
`chatPopMenu` | (inout [OperationItem], MessageContentModel?) -> Void | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单的增加、删除和修改。
`popMenuClick` | (OperationItem) -> Void | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单点击事件的修改，可修改默认实现和自定义菜单的点击。
`fileSizeLimit` | Double | 消息页面中，发送文件大小限制(单位：MB)，默认200。

- **MessageProperties 个性化配置项**

<div style="width:140px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`selfMessageBg` | UIColor |自己发送的消息体的背景色，具体自定义示例见下文的[修改消息体背景色](#修改消息体背景色)
`receiveMessageBg` | UIColor | 接收到的消息体的背景色，具体自定义示例见下文的[修改消息体背景色](#修改消息体背景色)
`backgroundImageCapInsets` | UIEdgeInsets | 背景图片拉伸参数（边距偏移）
`userNickColor` | UIColor | 不设置头像的用户所展示的文字头像中的文字颜色
`userNickTextSize` | CGFloat | 不设置头像的用户所展示的文字头像中的文字字体大小
`messageTextColor` | UIColor | 文本消息字体颜色
`messageTextSize` | CGFloat | 文本消息字体大小
`avatarType` | NEChatAvatarType | 头像类型，NEChatAvatarType.rectangle = 1 代表矩形，NEChatAvatarType.cycle 代表圆形 
`avatarCornerRadius` | CGFloat | 头像的圆角大小，仅在avatarType = NEChatAvatarType.rectangle 时生效 
`timeTextSize` | CGFloat | 消息列表中，时间字体大小
`timeTextColor` | UIColor | 消息列表中，时间字体颜色
`signalBgColor` | UIColor | 被标记消息的背景色
`showP2pMessageStatus` | Bool | 单聊中是否展示已读未读状态
`showTeamMessageStatus` | Bool | 群聊中是否展示已读未读状态
`showTeamMessageNick` | Bool | 群聊中是否展示好友昵称
`showTitleBar` | Bool | 会话界面是否展示标题栏，具体自定义示例见下文的[隐藏界面标题栏](#隐藏界面标题栏)
`showTitleBarRightIcon` | Bool | 是否展示标题栏右侧图标按钮 
`titleBarRightRes` | UIImage | 设置标题栏右侧图标按钮展示图标，具体自定义示例见下文的[修改界面标题右侧图标](#修改界面标题栏右侧图标)
`titleBarRightClick` | () -> Void | 标题栏右侧图标的点击事件
`chatViewBackground` | UIColor | 设置会话界面背景色，具体自定义示例见下文的[修改会话界面背景色](#修改会话界面背景色)



### 界面布局自定义

除了界面的 UI 元素，您也可对界面的布局进行自定义。在 `NEChatUIKit` 模块中，所有的 Cell 都继承于 `NEChatBaseCell`，会话消息界面分成左右会话两部分。以文本消息为例，整个会话消息界面分为 `ChatTextLeftCell` 和 `ChatTextRightCell`，其父类分别为 `ChatBaseLeftCell` 和 `ChatBaseRightCell`。

:::note notice
- 基础信息（如背景颜色，头像或者昵称）会在上层的 `BaseCell` 中赋值，需要单独处理的逻辑需要在各自对应的业务 Cell 中完成。
- 自V9.6.1，IM UIKit 按照消息类型合并界面左右两边的消息体，便于后期维护。

    - 每种类型的消息体中都包含左右两边消息展示所需要的所有元素，并根据消息方向进行了布局，在展示前可以根据消息方向控制元素的显隐以及完成元素对象的赋值。
    
    - 以基础版皮肤中的文本消息为例，整个会话消息界面合并为 `ChatMessageTextCell`, 其继承链路为：`ChatMessageTextCell` -> `NormalChatMessageBaseCell` -> `NEBaseChatMessageCell` -> `NEChatBaseCell`
:::

会话界面的默认布局如下图所示：

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/7bad48d354a31a43a4a663a19406ab9d/消息布局新.png" />

该界面各视图的说明如下：


<div style="width:140px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`titleBarView` | UIView | 聊天界面标题，可通过`navigationView`来获取视图进行样式修改
`navigationView` |  TabNavigationView | 聊天界面的标题视图，可在子类直接获取视图进行样式修改，具体自定义示例请参见下文的[自定义标题栏按钮](#自定义标题栏按钮)
`bodyTopView` | UIView | 消息列表界面上方的小块视图，可在子类直接获取视图进行样式修改。用于在消息详情和顶部标题视图中间增加新的 UI 元素，具体自定义示例请参见下文的[会话消息标题栏下方扩展视图](#会话消息标题栏下方扩展视图)
`bodyView` | UIView | 消息列表的内容视图，可在子类直接获取视图进行样式修改。布局中包含`brokenNetworkView`错误提示视图和`contentView`列表视图。
`brokenNetworkView` | NEBrokenNetworkView | 聊天界面错误提示视图，可在子类直接获取视图进行样式修改
`contentView` | UIView | 消息列表的列表视图，可在子类直接获取视图进行样式修改。布局中包含`tableView`消息列表和`emptyView`空数据提示视图。
`tableView` | UITableView | 消息详情列表，可在子类直接获取视图进行样式修改
`emptyView` | NEEmptyDataView | 聊天界面空数据提示视图，可在子类直接获取视图进行样式修改
`bottomView` | UIView | 消息列表底部视图，可在子类直接获取视图进行样式修改，布局中包含`bodyBottomView`扩展视图和`chatInputView`输入框视图
`bodyBottomView` | UIView | 输入框视图上方的小块视图，可在子类直接获取视图进行样式修改，用于在消息详情和底部输入框中间增加新的 UI 元素，具体自定义示例请参见下文的[输入框上方区域扩展视图](#输入框上方区域扩展视图)
`chatInputView` | UIView | 聊天界面的底部输入框视图，可在子类中进行样式修改。具体自定义示例请参见下文的[自定义输入框左右间距](#自定义输入框左右间距)<br> `chatInputView.stackView` 为输入框底部工具栏视图，可添加或删除按钮。具体自定义示例请参见下文的[自定义底部工具条](#自定义底部工具条)和[自定义 “更多” 功能页](#自定义-更多-功能页) 


## 通过配置项自定义 UI 示例

::: note notice
会话消息的个性化 UI 样式需要在会话消息界面加载之前配置，例如您可以在 `IMKitEngine`的 `setupCoreKitIM` 方法中设置个性化定制属性。
:::

### 修改界面标题栏右侧图标

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```
    NEKitChatConfig.shared.ui.messageProperties.titleBarRightRes = UIImage(named: "image name")
    ```
    :::
    ::: tab Objective-C
    ```
    NEKitChatConfig.shared.ui.messageProperties.titleBarRightRes = [UIImage imageNamed:@"image name"];
    ```
    :::
    ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情右侧按钮.png](https://yx-web-nosdn.netease.im/common/ea31a022987bf9540cf27b79e5342471/消息详情右侧按钮.png)|



### 隐藏界面标题栏

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```
    NEKitChatConfig.shared.ui.messageProperties.showTitleBar = false
    ```
    :::
    ::: tab Objective-C
    ```
    NEKitChatConfig.shared.ui.messageProperties.showTitleBar = NO;
    ```
    :::
    ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情隐藏标题栏.png](https://yx-web-nosdn.netease.im/common/c40029028bbe94d2fb148827198c366e/消息详情隐藏标题栏.png)


### 修改会话界面背景色

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```
    NEKitChatConfig.shared.ui.messageProperties.chatViewBackground = UIColor.red
    ```
    :::
    ::: tab Objective-C
    ```
    NEKitChatConfig.shared.ui.messageProperties.chatViewBackground = [UIColor redColor];
    ```
    :::
    ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情背景色.png](https://yx-web-nosdn.netease.im/common/b2b708fc001fc2a2c06b4ce09a28099f/消息详情背景色.png)


### 修改消息体背景色

- 示例代码
    :::::: div custom-tabs
    ::: tab Swift
    ```
    //修改自己消息体背景色
    NEKitChatConfig.shared.ui.messageProperties.selfMessageBg = UIColor.green
    //修改对方消息体背景色
    NEKitChatConfig.shared.ui.messageProperties.receiveMessageBg = UIColor.gray
    NEKitChatConfig.shared.ui.messageProperties.rightBubbleBg = nil // 隐藏气泡
    ```
    :::
    ::: tab Objective-C
    ```
    //修改自己消息体背景色
    NEKitChatConfig.shared.ui.messageProperties.selfMessageBg = [UIColor blueColor];
    //修改对方消息体背景色
    NEKitChatConfig.shared.ui.messageProperties.receiveMessageBg = [UIColor blueColor];
    NEKitChatConfig.shared.ui.messageProperties.rightBubbleBg = nil; // 隐藏气泡
    ```
    :::
    ::::::

::: note notice
会话消息的消息体背景色与气泡共存，若只需要实现纯色背景色效果，请将默认气泡图片隐藏（置为nil）
:::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情消息背景色.png](https://yx-web-nosdn.netease.im/common/a0dc2119968ba46eac770f1b5594fb3f/消息详情消息背景色.png)



## 源码导读


### **会话消息**

`ChatViewController`为会话消息的基类，内部封装了 `UITableView`。

自V9.6.1，IM UIKit 按照消息类型合并界面左右两边的消息体，便于后期维护。
所有类型的消息都以 Cell 形式展示，需要在 `cellRegisterDic` 注册列表中声明不同消息体对应的 Cell 类，用于 `UITableView` 的 Cell 注册。利用面向对象语言的多态性，不同类型的 Cell 重写了父类的 `setModel` 方法，且每种类型的 Cell 都有与之对应的数据模型。

对应关系如下:


:::::: div custom-tabs
::: tab 基础版 UI Cell

基础版 UI Cell 类别 | 数据模型 | 说明
---- | -------------- | ---------
ChatMessageTextCell | MessageTextModel | 文本消息类型
ChatMessageAudioCell | MessageAudioModel | 语音消息类型
ChatMessageImageCell | MessageImageModel | 图片消息类型
ChatMessageVideoCell| MessageVideoModel | 视频消息类型
ChatMessageFileCell| MessageFileModel | 文件消息类型
ChatMessageLocationCell | MessageLocationModel | 地理位置消息类型
ChatMessageCallCell| MessageCallRecordModel |音视频消息类型
ChatMessageReplyCell | MessageReplyModel | 回复消息类型
ChatMessageRevokeCell | MessageRevokeModel | 撤回消息类型
ChatMessageTipCell|MessageTipsModel |提示消息类型
ChatMessageMergeCell|MessageCustomModel |合并转发消息类型
ChatMessageTitleTextCell|MessageTitleTextModel |换行消息类型



:::
::: tab 通用版 UI Cell

通用版 UI Cell 类别 | 数据模型 | 说明
---- | -------------- | ---------
FunChatMessageTextCell | MessageTextModel | 文本消息类型
FunChatMessageAudioCell | MessageAudioModel | 语音消息类型
FunChatMessageImageCell | MessageImageModel | 图片消息类型
FunChatMessageVideoCell| MessageVideoModel | 视频消息类型
FunChatMessageFileCell| MessageFileModel | 文件消息类型
FunChatMessageLocationCell | MessageLocationModel | 地理位置消息类型
FunChatMessageCallCell| MessageCallRecordModel | 音视频消息类型
FunChatMessageReplyCell | MessageReplyModel | 回复消息类型
FunChatMessageRevokeCell | MessageRevokeModel | 撤回消息类型
FunChatMessageTipCell|MessageTipsModel |提示消息类型
FunChatMessageMergeCell|MessageCustomModel |合并转发消息类型
FunChatMessageTitleTextCell|MessageTitleTextModel |换行消息类型

:::
::::::
  





### **赋值处理**

1. 根据 `NIMMessage` 的 `messageType `类型，判断消息类型。
2. 针对不同的消息类型，使用对应的数据模型进行解析。

    ```swift
    public class ChatMessageHelper: NSObject {
        public static func modelFromMessage(message: NIMMessage) -> MessageModel {
            var model: MessageModel
            switch message.messageType {
            
            case .video:
                model = MessageVideoModel(message: message)
            case .text:
                model = MessageTextModel(message: message)
            case .image:
                model = MessageImageModel(message: message)
            case .audio:
                model = MessageAudioModel(message: message)
            ...

            default:
                // 未识别的消息类型，默认为文本消息类型，text为未知消息体
                message.text = chatLocalizable("msg_unknown")
                model = MessageTextModel(message: message)
            }
            return model
        }
    }
    ```
3. 在 `ChatViewController` 的 Cell 展示数据源方法中进行赋值。
    ```
    open func tableView(_ tableView: UITableView,
                        cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let model = viewmodel.messages[indexPath.row]
        var reuseId = ""
        if model.replyedModel?.isReplay == true,
        model.isRevoked == false {
        reuseId = "\(MessageType.reply.rawValue)"
        } else {
        let key = "\(model.type.rawValue)"
        if model.type == .custom, let object = model.message?.messageObject as? NIMCustomObject, let custom = object.attachment as? NECustomAttachmentProtocol {
            if registerCellDic["\(custom.customType)"] != nil {
            reuseId = "\(custom.customType)"
            } else {
            reuseId = "\(NEBaseChatMessageCell.self)"
            }
        } else if model.type == .time || model.type == .notification || model.type == .tip {
            reuseId = "\(MessageType.time.rawValue)"
        } else if registerCellDic[key] != nil {
            reuseId = key
        } else {
            reuseId = "\(NEBaseChatMessageCell.self)"
        }
        }

        let cell = tableView.dequeueReusableCell(withIdentifier: reuseId, for: indexPath)
        if let c = cell as? NEBaseChatMessageTipCell {
        if let m = model as? MessageTipsModel {
            m.resetNotiText()
            c.setModel(m)
        }
        return c
        } 

        ...

        else {
        return NEBaseChatMessageCell()
        }
    }
    ```


### **子类继承**

`P2PChatViewController` 和 `GroupChatViewController` 均继承于 `ChatViewController`。

这里以 `P2PChatViewController` 为例，具体如下:
```swift
@objcMembers
open class P2PChatViewController: ChatViewController {

    open override func viewDidLoad() {
        super.viewDidLoad()

        // Do any additional setup after loading the view.
    }  
    override open func getSessionInfo(session: NIMSession) {
    let user = viewmodel.getUserInfo(userId: session.sessionId)
    let showName = user?.showName() ?? ""
    title = showName
    titleContent = showName
    let text = "\(chatLocalizable("send_to"))\(showName)"
    let attribute = NSMutableAttributedString(string: text)
    let style = NSMutableParagraphStyle()
    style.lineBreakMode = .byTruncatingTail
    style.alignment = .left
    attribute.addAttribute(.font, value: UIFont.systemFont(ofSize: 16), range: NSMakeRange(0, text.utf16.count))
    attribute.addAttribute(.foregroundColor, value: UIColor.gray, range: NSMakeRange(0, text.utf16.count))
    attribute.addAttribute(.paragraphStyle, value: style, range: NSMakeRange(0, text.utf16.count))
    menuView.textView.attributedPlaceholder = attribute
  }
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
        fatalError("init(coder:) has not been implemented")
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
        }
    }
}
```


### 自定义标题栏按钮

自V9.6.1 起，自定义导航栏需要使用 `customNavigationView` 来实现, V9.6.5更名为 `navigationView`。

`navigationView` 采用固定按钮，包括左侧的返回按钮（backButton）和右侧的更多按钮（moreButton），此外还包含中间的导航栏标题（navTitle）和底部分割线(titleBarBottomLine)，具体定义详见 `NENavigationView` 类，所有控件均可访问修改。

- 示例代码

    :::::: div custom-tabs
    ::: tab Swift
    ```
    // 修改标题
    navigationView.navTitle.text = "title"
    
    // 修改右侧按钮文案
    navigationView.setMoreButtonTitle("clear")
    
    // 修改右侧按钮文案颜色
    navigationView.moreButton.setTitleColor(.red, for: .normal)
    
    // 修改右侧按钮点击事件
    navigationView.moreButton.addTarget(self, action: #selector(clearMessage), for: .touchUpInside)
    ```
    ```
    :::
    ::: tab Objective-C
    ```
    // 修改标题
    navigationView.navTitle.text = @"title";
    
    // 修改右侧按钮文案
    [navigationView setMoreButtonTitle:@"clear"];
    
    // 修改右侧按钮文案颜色
    [navigationView.moreButton setTitleColor:[UIColor redColor] forState:UIControlStateNormal];
    
    // 修改右侧按钮点击事件
    [navigationView.moreButton addTarget:self action:@selector(clearMessage) forControlEvents:UIControlEventTouchUpInside];
    ```
    :::
    ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情自定义右侧图标.png](https://yx-web-nosdn.netease.im/common/746ede517ebaec0dd3a02935a1a3b13c/消息详情自定义右侧图标.png)


V9.6.1 之前版本实现自定义标题栏按钮的示例代码（Swfit）如下：

::: details 单击查看示例代码

```
class CustomP2PChatViewController: P2PChatViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        ...

    let backItem = UIBarButtonItem(
    image: UIImage(named: "arrow_right"),
    style: .plain,
    target: self,
    action: #selector(backEvent) // backEvent 为标题左侧返回按钮的默认点击事件
    )
    let settingItem = UIBarButtonItem(
    image: UIImage(named: "mine_setting"),
    style: .plain,
    target: self,
    action: #selector(toSetting) // toSetting 为标题右侧设置按钮的默认点击事件
    )
    navigationItem.leftBarButtonItems = [backItem]
    navigationItem.rightBarButtonItems = [settingItem]

        ...
    }
}
```

:::note note 
示例代码中可设置标题左右两侧的多个按钮，若只有单个按钮需求，也可使用内置方法 `addLeftAction` 和 `addRightAction` 分别设置标题左侧和右侧的按钮。
:::

      

### 自定义标题栏标题

- 示例代码（Swfit）
    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            super.viewDidLoad()

            // Do any additional setup after loading the view.
        }

        override func getSessionInfo(session: NIMSession) {
            super.getSessionInfo(session: session)
            title = "小易助手"
        }
    }
    ```
    ::: note note
    云信 IM 默认会在数据加载完成后设置会话消息页面标题，如需自定义标题，请重写 `getSessionInfo` 方法，并在父类方法调用之后设置其值。
    :::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情标题栏标题.png](https://yx-web-nosdn.netease.im/common/9df952e5a0ccc155a040540503e45e9d/消息详情标题栏标题.png)|



### 自定义单元格（TableviewCell）

用户可自定义单元格，实现自定义消息的自定义展示。

实现步骤与示例代码（Swift）：

1. 继承 NIMCustomAttach 类和 NECustomAttachmentProtocol 协议，实现自定义消息类和序列化方法。
   ```swift
    public class CustomAttachment: NECustomAttachment {
        public var goodsName = "name"

        public var goodsURL = "url"

        override public func encode() -> String {
            // 自定义序列化方法之前必须调用父类的序列化方法
            let neContent = super.encode()
            var info: [String: Any] = getDictionaryFromJSONString(neContent) as? [String: Any] ?? [:]
            info["goodsName"] = goodsName
            info["goodsURL"] = goodsURL

            let jsonData = try? JSONSerialization.data(withJSONObject: info, options: [])
            var content = ""
            if let data = jsonData {
            content = String(data: data, encoding: .utf8) ?? ""
            }
            return content
        }
    }
    ```

    ::: note notice
    NECustomAttachmentProtocol 协议中的 customType 和 cellHeight 必须实现，前者用于表明自定义消息对应的UI 类型，**在步骤4中注册单元格时需要和自定义 cell 进行绑定**；后者用于设置自定义 cell 的高度。
    :::


2. 继承 NIMCustomAttachmentCoding 类，对自定义消息进行反序列化。
   ```swift
   public class CustomAttachmentDecoder: NECustomAttachmentDecoder {
        override public func decodeCustomMessage(info: [String: Any]) -> CustomAttachment {
            // 自定义反序列化方法之前必须调用父类的反序列化方法
            let neCustomAttachment = super.decodeCustomMessage(info: info)
            let customAttachment = CustomAttachment(customType: neCustomAttachment.customType,
                                                    cellHeight: neCustomAttachment.cellHeight,
                                                    data: neCustomAttachment.data)
            if customAttachment.customType == 20 {
            customAttachment.cellHeight = 50
            }
            customAttachment.goodsName = info["goodsName"] as? String ?? ""
            customAttachment.goodsURL = info["goodsURL"] as? String ?? ""

            return customAttachment
        }
    }
   ```

    ::: note notice
    自定义消息类（CustomAttachment）中的 customType 和 cellHeight 需要重点关注，前者用于表明自定义 type 类型，**在步骤4中注册单元格时需要和自定义 cell 进行绑定**；后者用于设置自定义 cell 的高度。根据自身业务需求进行设置。
    :::


3. 继承 NEChatBaseCell 类，实现自定义单元格，对自定义消息进行展示。
   ```swift
    class CustomChatCell: NEChatBaseCell {
        public var testLabel = UILabel()

        ...

        override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
            super.init(style: style, reuseIdentifier: reuseIdentifier)
            selectionStyle = .none
            testLabel.translatesAutoresizingMaskIntoConstraints = false
            contentView.addSubview(testLabel)
            NSLayoutConstraint.activate([
                testLabel.centerXAnchor.constraint(equalTo: contentView.centerXAnchor),
                testLabel.centerYAnchor.constraint(equalTo: contentView.centerYAnchor),
            ])
            testLabel.font = UIFont.systemFont(ofSize: 14)
            testLabel.textColor = UIColor.black
        }

        override func setModel(_ model: MessageContentModel) {
            print("this is custom message")
            testLabel.text = "this is custom message"
        }
    }
   ```
4. 继承 P2PChatViewController 类，注册自定义消息的解析器。
   
   ```swift
    class CustomP2PChatViewController: P2PChatViewController {
        override func viewDidLoad() {
            // 自定义消息以及外部扩展 覆盖cell UI 样式示例
            // 注册自定义消息的解析器
            NIMCustomObject.registerCustomDecoder(CustomAttachmentDecoder())

            // 自定义消息类型的 customtype 与自定义 cell 需要绑定注册、一一对应
            // 自定义消息cell绑定需要放在 super.viewDidLoad() 之前
            NEChatUIKitClient.instance.regsiterCustomCell(["20": CustomChatCell.self])

            ...

            super.viewDidLoad()
        }
    }
   ```
    ::: note notice
    regsiterCustomCell 方法的入参类型为 [String: UITableViewCell.Type], **其中 key 对应步骤2中的 customType 的String值，需要在此处与其对应的自定义 cell 进行绑定**，从而实现不同类型的自定义消息的对应展示。
    :::

### 会话消息标题栏下方扩展视图

可在标题栏和消息详情中间插入扩展视图，例如插入**温馨提示**。

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
            customTopView.btn.setTitle("通过重写方式添加", for: .normal)
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

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情提示消息上.png](https://yx-web-nosdn.netease.im/common/2db94fd5ef69188f714bfc63b0ae2b88/消息详情提示消息上.png)


### 输入框上方区域扩展视图

用户可继承聊天界面详情页（P2PChatViewController/GroupChatViewController），在父类渲染页面之前更改输入框上方区域。

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

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情提示消息下.png](https://yx-web-nosdn.netease.im/common/538fde32fac1e3725b11ff1797f06ae3/消息详情提示消息下.png)

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

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情输入框间距.png](https://yx-web-nosdn.netease.im/common/7c56afb29900b5447839f1a56f7c402a/消息详情输入框间距.png)



### 自定义底部工具条

用户可自定义输入框底部工具条的按钮样式和点击事件。

- 示例代码（Swfit）
    // 通过配置项实现
```swift
    class CustomP2PChatViewController: P2PChatViewController {
    override func viewDidLoad() {
    NEKitChatConfig.shared.ui.chatInputBar = { [weak self] item in
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


    // 通过重写实现
    ```swift
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
                layoutInputView(offset: bottomExanpndHeight)
                chatInputView.addEmojiView()
            } else if btn.tag == 1 { // 语音
                layoutInputView(offset: bottomExanpndHeight)
                chatInputView.addRecordView()
            } else if btn.tag == 2 { // 照片
                goPhotoAlbumWithVideo(self)
            } else if btn.tag == 3 { // 更多
                layoutInputView(offset: bottomExanpndHeight)
                chatInputView.addMoreActionView()
            }
        }
    }
    ```
    :::note note 
    示例代码中，`chatInputView` 为输入框视图，`chatInputView.stackView` 为输入框底部工具栏视图，代码先将工具栏视图中的所有子视图（按钮）移除，然后依次添加自定义的子视图（按钮），并为按钮绑定点击事件buttonEvent。buttonEvent 中利用 tag 对按钮进行区分，实现具体的逻辑。
    :::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情底部工具条按钮.png](https://yx-web-nosdn.netease.im/common/6decd7562874d063cc48780fe6a19ba2/消息详情底部工具条按钮.png)



### 自定义 “更多” 功能页

用户可根据业务需求，自定义聊天输入区域的 “更多” 功能区。

- 示例代码（Swfit）
    // 通过配置项实现
    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
    NEKitChatConfig.shared.ui.chatInputMenu = { [weak self] menuList in
      // 新增未知类型
      let itemNew = NEMoreItemModel()
      itemNew.customImage = UIImage(named: "mine_collection")
      itemNew.customDelegate = self
      itemNew.action = #selector(self?.customClick)
      itemNew.title = "新增"
      menuList.append(itemNew)

      // 覆盖已有类型
      // 遍历 menuList， 根据type 覆盖已有类型
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
      // 遍历 menuList， 根据type 移除已有类型
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

    // 通过重写方式实现
    ```swift
    class CustomP2PChatViewController: P2PChatViewController {
    override func viewDidLoad() {
        // 新增未知类型
        let itemNew = NEMoreItemModel()
        itemNew.customImage = UIImage(named: "itemNew")
        itemNew.customDelegate = self
        itemNew.action = #selector(itemNewClicked)
        itemNew.title = "新增"
        NEChatUIKitClient.instance.moreAction.append(itemNew)

        // 覆盖已有类型
        // 遍历 NEChatUIKitClient.instance.moreAction， 根据type 覆盖已有类型
        for (i, item) in NEChatUIKitClient.instance.moreAction.enumerated() {
            if item.type == .rtc {
                let itemReplace = NEChatUIKitClient.instance.moreAction[i]
                itemReplace.customImage = UIImage(named: "itemReplace")
                // 覆盖默认的点击事件
                // itemReplace.customDelegate = self
                // itemReplace.action = #selector(itemReplaceClicked)
                itemReplace.type = .rtc
                itemReplace.title = "覆盖"
            }
        }

        // 移除已有类型
        // 遍历 NEChatUIKitClient.instance.moreAction， 根据type 移除已有类型
        for (i, item) in NEChatUIKitClient.instance.moreAction.enumerated() {
            if item.type == .file {
                NEChatUIKitClient.instance.moreAction.remove(at: i)
                break
            }
        }

        ...

        // 需要在父类视图加载之前完成自定义
        super.viewDidLoad() 
    }
    ```

    上述代码中的 `NEChatUIKitClient.instance.moreAction` 为全局 “更多” 功能列表，通过 `itemNew.customImage` 和 `itemNew.customDelegate` 共同组合来实现按钮的自定义点击事件。IM UIKit 默认实现的能力如下表所示，内部对这些类型的点击事件做了默认实现，可根据业务需要来决定是否覆盖。

    <div style="width:140px">标识Action</div>  | 说明 
    :---- | :---------
    `NEMoreActionType.takePicture` |  拍照
    `NEMoreActionType.file` |  发送文件
    `NEMoreActionType.rtc` |  音视频通话
    `NEMoreActionType.location`  | 地理位置

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![消息详情页默认.png](https://yx-web-nosdn.netease.im/common/1f92c687026734891bbb897355bda14e/消息详情页默认.png)|![消息详情更多功能页.png](https://yx-web-nosdn.netease.im/common/6ee4a3d3d23cbbccb822222fba349cf7/消息详情更多功能页.png)



### 消息长按菜单过滤部分能力

- 示例代码

```swift
class CustomP2PChatViewController: P2PChatViewController {
    override func viewDidLoad() {
        ...
    // 长按消息功能弹窗过滤列表（过滤列表中的能力会在整个页面中禁用）
    operationCellFilter = [.delete]
    }
}
```
- 代码解读

  示例代码中的 operationCellFilter 为长按菜单过滤列表, 其中的类型在整个会话详情页不会显示，示例代码最终的效果表现为：整个会话详情页的所有消息类型的长按菜单中均不显示【删除】功能

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![长按原.png](https://yx-web-nosdn.netease.im/common/4bdf574b176365ea64aed49d2361ebc9/长按原.png)|![长按新.png](https://yx-web-nosdn.netease.im/common/ee6e98fa344ddee6a90259e26be33d1f/长按新.png)


### 消息长按弹出菜单自定义

- 示例代码

```swift
class CustomP2PChatViewController: P2PChatViewController {
    override func viewDidLoad() {
        ...

        /// 消息长按弹出菜单自定义
        NEKitChatConfig.shared.ui.chatPopMenu = { menuList, model in
            // 遍历 menuList， 根据 type 覆盖已有类型
            // 将所有文本消息的【复制】替换成【粘贴】
            if model?.type == .text {
                for item in menuList {
                    if item.type == .copy {
                        item.text = "粘贴"
                    }
                }
            }
        }

        /// 消息长按弹出菜单点击事件回调，根据按钮类型进行区分
        NEKitChatConfig.shared.ui.popMenuClick = { [weak self] item in
        switch item.type {
            case .copy:
                // 更改【复制】类型按钮的点击事件
                self?.customClick()
            default:
                break
            }
        }
    }
}
```
- 代码解读

  示例代码中的 chatPopMenu 为消息长按弹出菜单回调、popMenuClick 为消息长按弹出菜单点击事件回调, 可以根据 type 类型进行区分进而实现自定义 

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![未弹出.png](https://yx-web-nosdn.netease.im/common/2be7edc71aa19b2a34983e36b8f9ff5e/未弹出.png)|![长按原.png](https://yx-web-nosdn.netease.im/common/4bdf574b176365ea64aed49d2361ebc9/长按原.png)
