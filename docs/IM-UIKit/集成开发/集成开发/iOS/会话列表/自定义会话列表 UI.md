网易云信 IM UIKit 支持本地会话组件（`NELocalConversationUIKit`）和云端会话组件（`NEConversationUIKit`），提供会话列表界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。

会话列表模块提供以下两种方式对会话列表的 UI 进行个性化定制。

- 通过接口配置的方式自定义 UI。 
- 通过源码修改的方式自定义 UI。

::: note note
如果接口中的配置项满足您的界面个性化需求，请优先使用接口配置方式。  
:::

## 自定义功能描述

### UI 元素自定义

会话列表界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/0ff0eb50754dce94e3a3eb644efb843b/会话列表界面新.png" />

`LocalConversationUIConfig` | `ConversationUIConfig` 是整个会话列表的配置文件，其中 UI 实例化对象类型为 `LocalConversationUIConfig` | `ConversationUIConfig`。

您可以通过 `LocalConversationUIConfig` | `ConversationUIConfig` 类中的个性化配置项，对会话列表的 UI 样式进行修改，个性化配置项具体如下：

属性 | 类型 | 说明
---- | ---- | ---- 
`showTitleBar` | Bool | 是否展示界面顶部的标题栏，具体自定义示例见下文的 [隐藏标题栏](#隐藏标题栏)。
`showTitleBarLeftIcon` | Bool | 是否展示标题栏左侧图标。
`showTitleBarRightIcon` | Bool | 是否展示标题栏最右侧图标。
`showTitleBarRight2Icon` | Bool | 是否展示标题栏次最右侧图标。
`titleBarLeftRes` | UIImage | 标题栏左侧图标。
`titleBarRightRes` | UIImage | 标题栏最右侧图标。
`titleBarRight2Res` | UIImage | 标题栏次最右侧图标。
`titleBarTitle` | String | 标题栏的文案。
`titleBarTitleColor` | UIColor | 标题栏的颜色值。
`titleBarRightClick` | () -> Void | 标题栏最右侧按钮点击事件。
`titleBarRight2Click` | () -> Void | 标题栏次最右侧按钮点击事件。
`titleBarLeftClick` | () -> Void | 标题栏左侧按钮点击事件。
`conversationProperties` | <li>LocalConversationProperties<li>ConversationProperties | 会话列表页面的 UI 个性化定制，具体配置见下文。
`stickTopButtonTitle` | String | 会话列表 cell 左划置顶按钮文案内容。
`stickTopButtonCancelTitle` | String | 会话列表 cell 左划取消置顶按钮文案内容。
`stickTopButtonBackgroundColor` | UIColor | 会话列表 cell 左划置顶按钮背景颜色。
`stickTopButtonClick` | <li>(NELocalConversationListModel?, IndexPath) -> Void<li>(NEConversationListModel?, IndexPath) -> Void | 会话列表 cell 左划置顶按钮点击事件。
`deleteButtonTitle` | String | 会话列表 cell 左划删除按钮文案内容。
`deleteButtonBackgroundColor` | UIColor | 会话列表 cell 左划删除按钮背景颜色。
`deleteButtonClick` | <li>(NELocalConversationListModel?, IndexPath) -> Void<li>(NEConversationListModel?, IndexPath) -> Void | 会话列表 cell 左划删除按钮点击事件。
`itemClick` | <li>(NELocalConversationListModel?, IndexPath) -> Void<li>(NEConversationListModel?, IndexPath) -> Void | 会话列表点击事件，包括单击和长按事件。
`customController` | <li>(NEBaseLocalConversationController) -> Void<li>(NEBaseConversationController) -> Void | 自定义界面 UI 接口，回调中会传入会话列表界面的UI布局，您可以进行UI元素调整。

<br>

`LocalConversationProperties` | `ConversationProperties` 类的个性化配置项具体如下：

属性 | 类型 | 说明
---- | ---- | ---- 
`itemTitleColor` | UIColor | 会话标题的字体颜色，具体示例见下文的 [修改会话名称字体颜色和大小](#修改会话名称字体颜色和大小)。
`itemTitleSize` | CGFloat | 会话标题的字体大小，具体示例见下文的 [修改会话名称字体颜色和大小](#修改会话名称字体颜色和大小)。
`itemBackground` | UIColor | 未被置顶的会话项的背景色。
`itemStickTopBackground` | UIColor | 置顶的会话项的背景色。
`itemContentColor` | UIColor | 会话消息缩略内容的字体颜色。
`itemContentSize` | CGFloat | 会话消息缩略内容的字体大小。
`itemDateColor` | UIColor | 会话时间的字体颜色。
`itemDateSize` | CGFloat | 会话时间的字体大小。
`avatarType` | <li>NELocalConversationAvatarType<li>NEConversationAvatarType | 头像类型，`rectangle = 1` 为矩形，`cycle` 为圆形。
`avatarCornerRadius` | CGFloat | 头像圆角大小，仅在 `avatarType = rectangle` 时有效。

### 界面布局自定义

除了界面的 UI 元素，您也可对界面的布局进行自定义，`NELocalConversationUIKit` | `NEConversationUIKit` 模块中的 `LocalConversationListCell` | `ConversationListCell` 支持对会话列表界面布局进行调整，包括界面元素调整和界面背景修改等。会话列表界面的默认视图布局如下图所示。

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/d755cffbdeee89778e5c0bb0a1e004e3/会话列表布局新.png" /> 

该界面各视图的说明如下：

属性 | 类型 | 说明
---- | ---- | ---- 
`titleBarView` | UIView | 会话列表界面标题视图，可通过 `navigationView` 来获取视图进行样式修改。
`navigationView` | TabNavigationView | 会话列表界面的标题视图，可在子类直接获取视图进行样式修改，具体自定义示例请参见下文的 [自定义标题栏](#自定义标题栏navigationview)。
`bodyTopView` | UIView | 会话列表上方的小块视图，可在子类直接获取视图进行样式修改。可用于在会话列表和顶部的界面标题中间增加新的 UI 元素。
`bodyView` | UIView | 会话列表界面的内容视图，可在子类直接获取视图进行样式修改。布局中包含 `brokenNetworkView` 错误提示视图和 `contentView` 列表视图。
`brokenNetworkView` | NEBrokenNetworkView | 会话列表界面错误提示视图，可在子类直接获取视图进行样式修改。
`contentView` | UIView | 会话列表界面的列表视图，可在子类直接获取视图进行样式修改。布局中包含 `tableView` 列表和 `emptyView` 空数据提示视图。
`tableView` | UITableView | 会话列表界面的列表，可在子类直接获取视图进行样式修改。
`emptyView` | NEEmptyDataView | 会话列表界面空数据提示视图，可在子类直接获取视图进行样式修改。
`bodyBottomView` | UIView | 会话列表底部的小块视图，可在子类直接获取视图进行样式修改，用于在会话列表底部增加新的 UI 元素。

## 通过配置项自定义 UI 示例

::: note notice
会话列表的个性化 UI 样式需要在会话列表界面加载之前配置，您可以在 `didFinishLaunchingWithOptions` 方法中设置个性化定制属性。
:::

### 隐藏标题栏

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    **Swift：**

    ```Swift
    LocalConversationUIConfig.shared.ui.showTitleBar = false
    ```

    **Objective-C:**

    ```Objective-C
    LocalConversationUIConfig.shared.ui.showTitleBar = NO;
    ```
    :::
    ::: code 云端会话
    **Swift：**

    ```Swift
    ConversationUIConfig.shared.ui.showTitleBar = false
    ```
    **Objective-C:**

    ```Objective-C
    ConversationUIConfig.shared.ui.showTitleBar = NO;
    ```
    :::
    ::::::

    :::note note
    除此之外，还可以隐藏标题栏中的新增图标和搜索图标。详见上文的个性化配置项列表。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/51ded5bb81d3d069bc062f591072586f/隐藏标题栏小.png" style="width:80%;border: 1px solid #BFBFBF;">

### 修改会话名称字体颜色和大小

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    **Swift：**

    ```Swift
    // 会话名称字体大小
    LocalConversationUIConfig.shared.ui.conversationProperties.itemTitleSize = 24
    // 会话名称字体颜色
    LocalConversationUIConfig.shared.ui.conversationProperties.itemTitleColor = UIColor.red
    ```

    **Objective-C:**

    ```Objective-C
    // 会话名称字体大小
    LocalConversationUIConfig.shared.ui.conversationProperties.itemTitleSize = 24;
    // 会话名称字体颜色
    LocalConversationUIConfig.shared.ui.conversationProperties.itemTitleColor = [UIColor redColor];
    ```
    :::
    ::: code 云端会话
    **Swift：**

    ```Swift
    // 会话名称字体大小
    ConversationUIConfig.shared.ui.conversationProperties.itemTitleSize = 24
    // 会话名称字体颜色
    ConversationUIConfig.shared.ui.conversationProperties.itemTitleColor = UIColor.red
    ```

    **Objective-C:**

    ```Objective-C
    // 会话名称字体大小
    ConversationUIConfig.shared.ui.conversationProperties.itemTitleSize = 24;
    // 会话名称字体颜色
    ConversationUIConfig.shared.ui.conversationProperties.itemTitleColor = [UIColor redColor];
    ```
    :::
    ::::::

    :::note note
    除此之外，还可以修改会话中的副标题和时间的字体颜色、字体大小，详见上文的个性化配置项列表。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/9bc6bc6b9bf7cb1ead0b857b9fb572eb/修改字体颜色和大小.png" style="width:80%;border: 1px solid #BFBFBF;">

## 通过源码自定义 UI 示例
 
:::::: div linked-codes
::: code 本地会话
`NEBaseLocalConversationController` 为本地会话列表的实现类，内部包含本地会话相关的回调，具体如下:

```Swift 
// MARK: ================= LocalConversationViewModelDelegate===================

extension NEBaseLocalConversationController: LocalConversationViewModelDelegate {
  open func reloadData() {
    delegate?.onDataLoaded()
  }
    
  /// 带排序的刷新
  open func reloadTableView() {
    if viewModel.stickTopConversations.count <= 0, viewModel.conversationListData.count <= 0 {
      emptyView.isHidden = false
    } else {
      emptyView.isHidden = true
    }
    viewModel.conversationListData.sort()
    viewModel.stickTopConversations.sort()
    tableView.reloadData()
  }

  /// 由于数据变更可能导致底部有更多数据，此方法重新使列表加载更多能力开启
  public func loadMoreStateChange(_ finish: Bool) {
    if finish {
      tableView.mj_footer = nil
    } else {
      tableView.mj_footer = MJRefreshBackNormalFooter(
        refreshingTarget: self,
        refreshingAction: #selector(loadMoreData)
      )
    }
  }
}
```
:::
::: code 云端会话
`NEBaseConversationController` 为云端会话列表的实现类，内部包含云端会话相关的回调，具体如下:

```Swift 
// MARK: ================= ConversationViewModelDelegate===================

extension NEBaseConversationController: ConversationViewModelDelegate {
  open func reloadData() {
    delegate?.onDataLoaded()
  }
    
  /// 带排序的刷新
  open func reloadTableView() {
    if viewModel.stickTopConversations.count <= 0, viewModel.conversationListData.count <= 0 {
      emptyView.isHidden = false
    } else {
      emptyView.isHidden = true
    }
    viewModel.conversationListData.sort()
    viewModel.stickTopConversations.sort()
    tableView.reloadData()
  }

  /// 由于数据变更可能导致底部有更多数据，此方法重新使列表加载更多能力开启
  public func loadMoreStateChange(_ finish: Bool) {
    if finish {
      tableView.mj_footer = nil
    } else {
      tableView.mj_footer = MJRefreshBackNormalFooter(
        refreshingTarget: self,
        refreshingAction: #selector(loadMoreData)
      )
    }
  }
}
```
:::
::::::

**其他**

自定义配置 | 说明
---- | ----
修改会话列表右侧按钮点击事件 | 通过 `TabNavigationViewDelegate` 协议中的 `searchAction` 和 `didClickAddBtn` 方法进行修改。
构造更多弹窗中的选项内容 | 通过 `NEBasePopListView` 视图类构造，当前默认设置为添加好友、创建讨论组、创建高级群。
实现长按置顶会话和删除会话弹窗 | 请参见 `NEBaseLocalConversationController`/`NEBaseConversationController` 中 `UITableview` 中的代理方法。

### 自定义单元格（TableviewCell）

用户可自定义云端会话列表单元格，实现数据的自定义展示。

实现步骤与示例代码（Swift）：

:::::: div linked-codes
::: code 本地会话
1. 继承 `LocalConversationListCell` 类，实现自定义单元格，对数据进行展示。

```Swift
open class CustomLocalConversationListCell: LocalConversationListCell {
  // 新增 UI 元素，用于展示在线状态
  private lazy var onlineView: UIImageView = {
    let notify = UIImageView()
    notify.translatesAutoresizingMaskIntoConstraints = false
    notify.image = UIImage(named: "about_yunxin")
    return notify
  }()

  override public init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
    super.init(style: style, reuseIdentifier: reuseIdentifier)

    // 头像右下角
    contentView.addSubview(onlineView)
    NSLayoutConstraint.activate([
      onlineView.rightAnchor.constraint(equalTo: headImge.rightAnchor),
      onlineView.bottomAnchor.constraint(equalTo: headImge.bottomAnchor),
      onlineView.widthAnchor.constraint(equalToConstant: 12),
      onlineView.heightAnchor.constraint(equalToConstant: 12),
    ])
  }

  public required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
  }

  // 此方法用于数据和 UI 的绑定，可在此处在数据展示前对数据进行处理
  open func configureData(_ sessionModel: NELocalConversationListModel?) {
    super.configureData(sessionModel)
//    subTitle.text = "[自定义类型文案]"
  }
}
```

2. 继承 `LocalConversationController` 类，实现自定义表格（以通用皮肤为例）。

```Swift
open class CustomLocalConversationController: LocalConversationController, NEBaseLocalConversationControllerDelegate {
  override public init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
    super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
    delegate = self

    // 自定义 cell, [NELocalConversationListModel.customType: 需要注册的自定义 UI 类型]
    // 自定义 cell 的注册字典需要在 viewDidLoad 之前完成初始化
    cellRegisterDic[1] = CustomLocalConversationListCell.self
  }

  public required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
  }

  override open func viewDidLoad() {
    super.viewDidLoad()
  }

  override open func deleteActionHandler(action: UITableViewRowAction, indexPath: IndexPath) {
    showSingleAlert(message: "override deleteActionHandler") {}
  }

  override open func topActionHandler(action: UITableViewRowAction, indexPath: IndexPath, isTop: Bool) {
    showSingleAlert(message: "override topActionHandler") {
      super.topActionHandler(action: action, indexPath: indexPath, isTop: isTop)
    }
  }

  //  父类加载完数据后会调用此方法，可在此对数据进行二次处理
  public func onDataLoaded() {
    guard let conversationList = viewModel.conversationListArray else { return
    }
    conversationList.forEach { model in
      model.customType = 1
    }
    tableView.reloadData()
  }
}
```

**注意：** `onDataLoaded` 方法调用时，表明父类已完成数据的加载，数据存放在 `viewModel.conversationListArray` 列表中，数据模型定义如下：

```Swift
/* 
    本地会话列表数据模型 NELocalConversationListModel
    // customType: 自定义 UI 类型，其在注册本地会话列表 cell 时作为 key 与自定义 cell 进行绑定
    // localExtension: 本地扩展字段，可根据业务需求添加数据，与 customType 结合可实现多种自定义 cell 的展示
*/
@objcMembers
public class NELocalConversationListModel: NSObject, Comparable {
/// 会话
public var conversation: V2NIMLocalConversation?
/// 自定义类型
public var customType = 0
}
```

::: note notice
需要在 `viewDidLoad` 之前完成本地会话列表 cell 注册字典（`cellRegisterDic`）的初始化，`cellRegisterDic` 的类型为 [Int : NEBaseLocalConversationListCell.Type]，**其中 key 对应本地会话列表数据模型中的 customType，需要在此处与其对应的自定义 UI 类型进行绑定**，从而实现不同类型的自定义单元格的对应展示。
:::

例如在用户头像下 **添加小标**，如下图所示：

默认 | 自定义后 |
---- | ---- |
<img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/fe027bf10233308fbbe254d525fff66c/小标.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::: code 云端会话
1. 继承 `ConversationListCell` 类，实现自定义单元格，对数据进行展示。

```Swift
open class CustomConversationListCell: ConversationListCell {
  // 新增 UI 元素，用于展示在线状态
  private lazy var onlineView: UIImageView = {
    let notify = UIImageView()
    notify.translatesAutoresizingMaskIntoConstraints = false
    notify.image = UIImage(named: "about_yunxin")
    return notify
  }()

  override public init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
    super.init(style: style, reuseIdentifier: reuseIdentifier)

    // 头像右下角
    contentView.addSubview(onlineView)
    NSLayoutConstraint.activate([
      onlineView.rightAnchor.constraint(equalTo: headImge.rightAnchor),
      onlineView.bottomAnchor.constraint(equalTo: headImge.bottomAnchor),
      onlineView.widthAnchor.constraint(equalToConstant: 12),
      onlineView.heightAnchor.constraint(equalToConstant: 12),
    ])
  }

  public required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
  }

  // 此方法用于数据和 UI 的绑定，可在此处在数据展示前对数据进行处理
  open func configureData(_ sessionModel: NEConversationListModel?) {
    super.configureData(sessionModel)
//    subTitle.text = "[自定义类型文案]"
  }
}
```

2. 继承 `ConversationController` 类，实现自定义表格（以通用皮肤为例）。

```Swift
open class CustomConversationController: ConversationController, NEBaseConversationControllerDelegate {
  override public init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
    super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
    delegate = self

    // 自定义 cell, [NEConversationListModel.customType: 需要注册的自定义 UI 类型]
    // 自定义 cell 的注册字典需要在 viewDidLoad 之前完成初始化
    cellRegisterDic[1] = CustomConversationListCell.self
  }

  public required init?(coder: NSCoder) {
    fatalError("init(coder:) has not been implemented")
  }

  override open func viewDidLoad() {
    super.viewDidLoad()
  }

  override open func deleteActionHandler(action: UITableViewRowAction, indexPath: IndexPath) {
    showSingleAlert(message: "override deleteActionHandler") {}
  }

  override open func topActionHandler(action: UITableViewRowAction, indexPath: IndexPath, isTop: Bool) {
    showSingleAlert(message: "override topActionHandler") {
      super.topActionHandler(action: action, indexPath: indexPath, isTop: isTop)
    }
  }

  //  父类加载完数据后会调用此方法，可在此对数据进行二次处理
  public func onDataLoaded() {
    guard let conversationList = viewModel.conversationListArray else { return
    }
    conversationList.forEach { model in
      model.customType = 1
    }
    tableView.reloadData()
  }
}
```
  
**注意：** `onDataLoaded` 方法调用时，表明父类已完成数据的加载，数据存放在 `viewModel.conversationListArray` 列表中，数据模型定义如下：

```swift
/* 
    云端会话列表数据模型 NEConversationListModel
    // customType: 自定义 UI 类型，其在注册云端会话列表 cell 时作为 key 与自定义 cell 进行绑定
    // localExtension: 本地扩展字段，可根据业务需求添加数据，与 customType 结合可实现多种自定义 cell 的展示
*/
@objcMembers
public class NEConversationListModel: NSObject, Comparable {
/// 会话
public var conversation: V2NIMConversation?
/// 自定义类型
public var customType = 0
}
```

::: note notice
需要在 `viewDidLoad` 之前完成云端会话列表 cell 注册字典（`cellRegisterDic`）的初始化，`cellRegisterDic` 的类型为 [Int : NEBaseConversationListCell.Type]，**其中 key 对应云端会话列表数据模型中的 customType，需要在此处与其对应的自定义 UI 类型进行绑定**，从而实现不同类型的自定义单元格的对应展示。
:::

例如在用户头像下 **添加小标**，如下图所示：

默认 | 自定义后 |
---- | ---- |
<img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/fe027bf10233308fbbe254d525fff66c/小标.png" style="width:80%;border: 1px solid #BFBFBF;">
:::
::::::

### 自定义标题栏（navigationView）

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    **Swift：**

    ```Swift
    open class CustomLocalConversationController: LocalConversationController {
      override public func viewDidLoad() {
        // 实现协议（重写 tabbar 点击事件）
        navigationView.delegate = self

        // 自定义本地会话列表标题、图标、间距
        navigationView.brandBtn.setTitle("消息", for: .normal)
        navigationView.brandBtn.setImage(nil, for: .normal)
        navigationView.brandBtn.layoutButtonImage(style: .left, space: 0)

        // 自定义添加按钮图标
        navigationView.addBtn.setImage(UIImage.ne_imageNamed(name: "noNeed_notify"), for: .normal)

        ...

        super.viewDidLoad()
      }

      // 通过继承方式重写次最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
      override open func searchAction() {
        // searchAction
      }

      // 通过继承方式重写最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
      override open func didClickAddBtn() {
        showSingleAlert(message: "override didClickAddBtn") {
          // didClickAddBtn
        }
      }
    }
    ```
    :::
    ::: code 云端会话
    **Swift：**

    ```Swift
    open class CustomConversationController: ConversationController {
      override public func viewDidLoad() {
        // 实现协议（重写 tabbar 点击事件）
        navigationView.delegate = self

        // 自定义云端会话列表标题、图标、间距
        navigationView.brandBtn.setTitle("消息", for: .normal)
        navigationView.brandBtn.setImage(nil, for: .normal)
        navigationView.brandBtn.layoutButtonImage(style: .left, space: 0)

        // 自定义添加按钮图标
        navigationView.addBtn.setImage(UIImage.ne_imageNamed(name: "noNeed_notify"), for: .normal)

        ...

        super.viewDidLoad()
      }

      // 通过继承方式重写次最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
      override open func searchAction() {
        // searchAction
      }

      // 通过继承方式重写最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
      override open func didClickAddBtn() {
        showSingleAlert(message: "override didClickAddBtn") {
          // didClickAddBtn
        }
      }
    }
    ```
    :::
    ::::::
      
    ::: note note 
    上述示例代码中 `navigationView` 为会话列表页面的标题栏视图，用户可自定义其中的 UI 元素，包括但不限于标题、标题图标、搜索按钮及其点击事件和添加按钮及其点击事件。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/f991d1e5381c6e2f71174c69b651190e/按钮.png" style="width:80%;border: 1px solid #BFBFBF;">

### 会话列表页顶部扩展视图

例如，可以在会话列表顶部增加提示条。

- 示例代码

    :::::: div linked-codes
    ::: code 本地会话
    **Swift：**

    ```Swift
    public class CustomView: UIView {
      public let btn = UIButton()

      override public init(frame: CGRect) {
        super.init(frame: frame)
        btn.translatesAutoresizingMaskIntoConstraints = false
        btn.addTarget(self, action: #selector(tapView), for: .touchUpInside)
        btn.setTitle("按钮", for: .normal)
        btn.backgroundColor = .red
        addSubview(btn)
        NSLayoutConstraint.activate([
          btn.topAnchor.constraint(equalTo: topAnchor),
          btn.bottomAnchor.constraint(equalTo: bottomAnchor),
          btn.widthAnchor.constraint(equalToConstant: 200),
          btn.centerXAnchor.constraint(equalTo: centerXAnchor),
        ])
      }

      required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
      }

      @objc func tapView() {
        print("点击了自定义按钮")
      }
    }

    open class CustomLocalConversationController: LocalConversationController {
      public lazy var customTopView: CustomView = {
        let view = CustomView(frame: CGRect(x: 0, y: 10, width: NEConstant.screenWidth, height: 40))
        view.backgroundColor = .blue
        return view
      }()

      override public init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
        super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
      }

      public required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
      }

      override public func viewDidLoad() {
        // 顶部 bodyTopView 中添加自定义 view（需要设置 bodyTopView 的高度）
        customTopView.btn.setTitle("通过重写方式添加", for: .normal)
        bodyTopView.addSubview(customTopView)
        bodyTopViewHeight = 80

        // 自定义占位图文案、背景图片
        emptyView.setEmptyImage(image: UIImage())
        emptyView.settingContent(content: "")
        ...
        super.viewDidLoad()
      }

      // 通过继承方式重写次最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
    override open func searchAction() {
      bodyTopViewHeight = 80
      bodyBottomViewHeight = 80
    }

    // 通过继承方式重写最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
    override open func didClickAddBtn() {
      bodyTopViewHeight = 0
      bodyBottomViewHeight = 0
    }
    }
    ```
    ::: 
    ::: code 云端会话
    **Swift：**
    ```Swift
    public class CustomView: UIView {
      public let btn = UIButton()

      override public init(frame: CGRect) {
        super.init(frame: frame)
        btn.translatesAutoresizingMaskIntoConstraints = false
        btn.addTarget(self, action: #selector(tapView), for: .touchUpInside)
        btn.setTitle("按钮", for: .normal)
        btn.backgroundColor = .red
        addSubview(btn)
        NSLayoutConstraint.activate([
          btn.topAnchor.constraint(equalTo: topAnchor),
          btn.bottomAnchor.constraint(equalTo: bottomAnchor),
          btn.widthAnchor.constraint(equalToConstant: 200),
          btn.centerXAnchor.constraint(equalTo: centerXAnchor),
        ])
      }

      required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
      }

      @objc func tapView() {
        print("点击了自定义按钮")
      }
    }

    open class CustomConversationController: ConversationController {
      public lazy var customTopView: CustomView = {
        let view = CustomView(frame: CGRect(x: 0, y: 10, width: NEConstant.screenWidth, height: 40))
        view.backgroundColor = .blue
        return view
      }()

      override public init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
        super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
      }

      public required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
      }

      override public func viewDidLoad() {
        // 顶部 bodyTopView 中添加自定义 view（需要设置 bodyTopView 的高度）
        customTopView.btn.setTitle("通过重写方式添加", for: .normal)
        bodyTopView.addSubview(customTopView)
        bodyTopViewHeight = 80

        // 自定义占位图文案、背景图片
        emptyView.setEmptyImage(image: UIImage())
        emptyView.settingContent(content: "")
        ...
        super.viewDidLoad()
      }

      // 通过继承方式重写次最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
    override open func searchAction() {
      bodyTopViewHeight = 80
      bodyBottomViewHeight = 80
    }

    // 通过继承方式重写最右侧按钮点击事件, 这种方式会覆盖配置项中的点击事件
    override open func didClickAddBtn() {
      bodyTopViewHeight = 0
      bodyBottomViewHeight = 0
    }
    }
    ```
    :::
    ::::::

    ::: note note
    示例代码中 `bodyTopView` 为会话列表页顶部预留的扩展视图，`bodyTopViewHeight` 为该扩展视图的高度，更改此变量会刷新页面布局。
    :::

- 效果对比

    默认 | 自定义后 |
    ---- | ---- |
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/cf516485978b14f8e0f20c68edee4188/未隐藏标题栏.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/7a9a4dc1dad1008141713f88745ceaf7/顶部扩展.png" style="width:80%;border: 1px solid #BFBFBF;">