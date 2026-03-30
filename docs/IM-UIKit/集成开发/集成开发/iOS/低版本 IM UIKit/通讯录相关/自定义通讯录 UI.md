
IM UIKit 通讯录模块（`NEContactUIKit`）提供通讯录界面的 UI 自定义配置项目配置项，助您快速实现该界面的 UI 个性化定制。

通讯录模块（`NEContactUIKit`）提供以下两种方式对通讯录的 UI 进行个性化定制。
- 通过接口配置的方式自定义 UI。
- 通过源码修改的方式自定义 UI。

:::note note
如果接口中的配置项满足您的界面个性化需求，请优先使用接口配置方式。
:::


## 自定义功能描述

### UI 元素自定义


通讯录界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/dcd0613a106dba5117da76fa1003b149/通讯录界面新.png" />


`NEKitContactConfig` 是整个通讯录的配置文件，其中 UI 实例化对象类型为 `ContactUIConfig`。

您可以通过 `ContactUIConfig` 类中的个性化配置项，对通讯录的 UI 样式进行修改，个性化配置项具体如下：


属性 | 类型 | 说明
---- | -------------- | ---------
`showTitleBar` | Bool | 是否展示标题栏
`showTitleBarRightIcon` | Bool | 是否展示标题栏的最右侧图标，具体自定义示例请参见下文的[隐藏标题栏搜索按钮和添加好友按钮](#隐藏标题栏搜索按钮和添加好友按钮)
`showTitleBarRight2Icon` | Bool | 是否展示标题栏的次最右侧图标，具体自定义示例请参见下文的[隐藏标题栏搜索按钮和添加好友按钮](#隐藏标题栏搜索按钮和添加好友按钮)
`titleBarRightRes` | UIImage | 标题栏的最右侧图标
`titleBarRight2Res` | UIImage | 标题栏的次最右侧图标
`titleBarRightClick` | () -> Void | 标题栏最右侧按钮点击事件
`titleBarRight2Click` | () -> Void | 标题栏次最右侧按钮点击事件
`title` | String | 标题栏文案
`titleColor` | UIColor | 标题栏字体颜色，具体自定义示例请参见下文的[自定义标题栏](#自定义标题栏navigationview)
`showHeader` | Bool | 是否在通讯录界面显示头部模块，具体自定义示例请参见下文的[隐藏头部模块](#隐藏头部模块)
`headerData` | ([ContactHeadItem]) -> Void | 头部模块的数据，如果不为空，则覆盖已有数据
`contactProperties` | ContactProperties | 通讯录好友列表中 UI 个性化定制属性设置，包括好友昵称的字体、好友头像、索引字体、颜色等
`friendItemClick` | (ContactInfo, IndexPath) -> Void | 好友列表的点击事件
`headerItemClick` | (ContactInfo, IndexPath) -> Void | 头部模块的点击事件
`customController` | (NEBaseContactsViewController) -> Void | 通讯录列表的视图控制器回调，回调中会返回通讯录列表的视图控制器

- **ContactProperties 个性化配置项**
属性 | 类型 | 说明
---- | -------------- | ---------
`avatarType` | NEContactAvatarType | 头像类型，NEContactAvatarType.rectangle = 1 为矩形，NEContactAvatarType.cycle 为圆形
`avatarCornerRadius` | CGFloat | 头像圆角大小，仅在 avatarType = NEContactAvatarType.rectangle 下有效
`itemTitleSize` | UIFont | 通讯录好友标题大小，具体自定义示例请参见下文的[修改通讯录好友标题字体颜色和大小](#修改通讯录好友标题字体颜色和大小)
`itemTitleColor` | UIColor | 通讯录好友标题颜色，具体自定义示例请参见下文的[修改通讯录好友标题字体颜色和大小](#修改通讯录好友标题字体颜色和大小)
`divideLineColor` | UIColor | 通讯录间隔线颜色，具体自定义示例请参见下文的[修改通讯录间隔线颜色](#修改通讯录间隔线颜色)
`indexTitleColor` | UIColor | 检索标题字体颜色

### 界面布局自定义

除了界面的 UI 元素，您也可对界面的布局进行自定义。在 `NEContactUIKit` 模块中，通讯录主界面是基于 `UITableview` 的封装，主要布局集中在 `NEBaseContactTableViewCell`中。

`NEBaseContactTableViewCell` 是一个子类，继承于 `NEBaseContactViewCell`，如果需要修改 Cell 样式可以在 `NEBaseContactTableViewCell` 中修改或者自定义 Cell 样式。

:::note notice
不建议直接修改 `NEBaseContactTableViewCell`，因为还存在其他类继承于 `NEBaseContactTableViewCell`。
:::

通讯录界面的默认布局如下图所示：

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/38653405f59787c81b84d99b59621362/通讯录布局新.png" />


该界面各视图的说明如下：

<div style="width:140px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`titleBarView` | UIView | 通讯录列表界面标题，可通过`navigationView`来获取视图进行样式修改
`navigationView` |  TabNavigationView | 通讯录列表界面标题视图，可在子类直接获取视图进行样式修改，具体自定义示例请参见下文的[自定义标题栏](#自定义标题栏navigationview)
`bodyTopView` | UIView | 好友列表上方的小块视图，可在子类直接获取视图进行样式修改。用于在通讯录列表和顶部标题中间增加新的 UI 元素，具体自定义示例请参见下文的[通讯录列表顶部添加扩展视图](#通讯录列表顶部添加扩展视图)
`bodyView` | UIView | 通讯录列表界面的内容视图，可在子类直接获取视图进行样式修改。布局中包含`brokenNetworkView`错误提示视图和`contentView`列表视图。
`brokenNetworkView` | NEBrokenNetworkView | 通讯录列表界面错误提示视图，可在子类直接获取视图进行样式修改
`contentView` | UIView | 通讯录列表界面的列表视图，可在子类直接获取视图进行样式修改。布局中包含`tableView`列表和`emptyView`空数据提示视图。
`tableView` | UITableView | 通讯录界面的列表，可自定义单元格，实现数据的自定义展示，具体自定义示例请参见下文的[自定义单元格](#自定义单元格contacttableviewcell)
`emptyView` | NEEmptyDataView | 通讯录列表界面空数据提示视图，可在子类直接获取视图进行样式修改
`bodyBottomView` | UIView | 好友列表底部的小块视图，可在子类直接获取视图进行样式修改，用于在好友列表底部增加新的 UI 元素，具体自定义示例请参见下文的[通讯录列表底部添加扩展视图](#通讯录列表底部添加扩展视图)

## 通过配置项自定义 UI 示例

::: note notice
通讯录的个性化 UI 样式需要在通讯录界面加载之前配置，例如您可以在 `IMKitEngine`的 `setupCoreKitIM` 方法中设置个性化定制属性。
:::

### 修改通讯录好友标题字体颜色和大小



- 示例代码
  :::::: div custom-tabs
  ::: tab Swift
  ```
  // 修改通讯录好友标题大小
  NEKitContactConfig.shared.ui.contactProperties.itemTitleSize = 28

  /// 修改通讯录好友标题颜色
  NEKitContactConfig.shared.ui.contactProperties.itemTitleColor = UIColor.red
  ```
  :::
  ::: tab Objective-C
  ```
  //修改通讯录好友标题大小
  NEKitContactConfig.shared.ui.contactProperties.itemTitleSize = 28;
  //修改通讯录好友标题颜色
  NEKitContactConfig.shared.ui.contactProperties.itemTitleColor = [UIColor redColor];
  ```
  :::
  ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![通讯录默认.png](https://yx-web-nosdn.netease.im/common/53437622dee7267b02739c4529e5e99f/通讯录默认.png)|![通讯录字体颜色.png](https://yx-web-nosdn.netease.im/common/a4b541222078e248934626cd2d092154/通讯录字体颜色.png)


### 隐藏标题栏搜索按钮和添加好友按钮

- 示例代码
  :::::: div custom-tabs
  ::: tab Swift
  ```
  //隐藏搜索按钮
  NEKitContactConfig.shared.ui.showTitleBarRight2Icon = false
  //隐藏添加好友按钮
  NEKitContactConfig.shared.ui.showTitleBarRightIcon = false
  ```
  :::
  ::: tab Objective-C
  ```
  //隐藏搜索按钮
  NEKitContactConfig.shared.ui.showTitleBarRight2Icon = NO;
  //隐藏添加好友按钮
  NEKitContactConfig.shared.ui.showTitleBarRightIcon = NO;
  ```
  :::
  ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![通讯录默认.png](https://yx-web-nosdn.netease.im/common/53437622dee7267b02739c4529e5e99f/通讯录默认.png)|![通讯录隐藏右侧按钮.png](https://yx-web-nosdn.netease.im/common/f5717ea90a2dc7a13cee5d3fe2f474ab/通讯录隐藏右侧按钮.png)



### 修改通讯录间隔线颜色

- 示例代码
  :::::: div custom-tabs
  ::: tab Swift
  ```
  NEKitContactConfig.shared.ui.contactProperties.divideLineColor = UIColor.red  
  ```
  :::
  ::: tab Objective-C
  ```
  NEKitContactConfig.shared.ui.contactProperties.divideLineColor = [UIColor redColor];
  ```
  :::
  ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![通讯录默认.png](https://yx-web-nosdn.netease.im/common/53437622dee7267b02739c4529e5e99f/通讯录默认.png)|![通讯录间隔线颜色.png](https://yx-web-nosdn.netease.im/common/e599887c6f70d76c8aea31dd5ed81175/通讯录间隔线颜色.png)


### 隐藏头部模块

- 示例代码
  :::::: div custom-tabs
  ::: tab Swift
  ```
  NEKitContactConfig.shared.ui.showHeader = false 

  ```
  :::
  ::: tab Objective-C
  ```
  NEKitContactConfig.shared.ui.showHeader = NO;
  ```
  :::
  ::::::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |<img style="width:100%" src="https://yx-web-nosdn.netease.im/common/4a8cd6a0b571962d5bad42230448e35e/原图.PNG" />|<img style="width:100%" src="https://yx-web-nosdn.netease.im/common/d09dfb526e22a4a9e906df8538c2f377/通讯录隐藏头部.PNG" />




## 通过源码自定义 UI

`NEBaseContactsViewController` 为通讯录的实现类。具体的方法如下:

方法 | 入参类型 | 说明
---- | -------------- | ---------
`loadData`|无|加载通讯录主界面数据
`goToFindFriend`|无 | 添加好友事件
`searchContact`| 无|搜索事件
`onFriendChanged`|User|好友状态发生变化的回调
`onBlackListChanged`|无|黑名单变化的回调
`onUserInfoChanged`|无|用户个人信息发生变化回调


### 自定义单元格（ContactTableViewCell）

用户可自定义单元格，实现数据的自定义展示。

实现步骤与示例代码（Swift），以通用皮肤为例：

1. 继承 ContactTableViewCell 类，实现自定义单元格，对数据进行展示。
  ```swift
  public class CustomContactTableViewCell: ContactTableViewCell {
    private lazy var onlineView: UIImageView = {
      let notify = UIImageView()
      notify.translatesAutoresizingMaskIntoConstraints = false
      notify.image = UIImage(named: "about_yunxin")
      notify.isHidden = true
      return notify
    }()

    override public init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
      super.init(style: style, reuseIdentifier: reuseIdentifier)
      contentView.addSubview(onlineView)
      NSLayoutConstraint.activate([
        onlineView.rightAnchor.constraint(equalTo: avatarImage.rightAnchor),
        onlineView.bottomAnchor.constraint(equalTo: avatarImage.bottomAnchor),
        onlineView.widthAnchor.constraint(equalToConstant: 12),
        onlineView.heightAnchor.constraint(equalToConstant: 12),
      ])
    }

    required init?(coder: NSCoder) {
      fatalError("init(coder:) has not been implemented")
    }

      // 根据数据模型设置 cell 内容
    override public func setModel(_ model: ContactInfo) {
      super.setModel(model)
      onlineView.isHidden = false
    }
  }
  ```
2. 继承 ContactsViewController 类，实现自定义表格。
  ```swift
  public class CustomContactsViewController: ContactsViewController, ContactsViewControllerDelegate {
    override public init(nibName nibNameOrNil: String?, bundle nibBundleOrNil: Bundle?) {
      super.init(nibName: nibNameOrNil, bundle: nibBundleOrNil)
      delegate = self
      // 自定义cell, [ContactCellType.ContactCutom.rawValue: 需要注册的自定义 UI 类型]
      // 自定义cell的注册字典需要在 viewDidLoad 之前完成初始化
      cellRegisterDic[ContactCellType.ContactCutom.rawValue] = CustomContactTableViewCell.self
    }

    required init?(coder: NSCoder) {
      fatalError("init(coder:) has not been implemented")
    }

    override public func viewDidLoad() {
      super.viewDidLoad()
      ...
    }

    //  父类加载完数据后会调用此方法，可在此对数据进行二次处理
    public func onDataLoaded() {
      viewModel.contacts[1].contacts.forEach { info in
        info.contactCellType = ContactCellType.ContactCutom.rawValue
      }
    }
  }
 ```
  
  **注意：**`onDataLoaded` 方法调用时，表明父类已完成数据的加载，数据存放在 viewModel.contacts（类型为 [ContactSection]） 列表中，数据模型定义为：

  ```swift
  /* 
      通讯录 section 数据模型
      // initial: tableView 对应 section 的标题
      // contacts: tableView 对应 section 的数据
  */
  public class ContactSection {
    public var initial: String
    public var contacts: Array = [ContactInfo]()
    init(initial: String, contacts: [ContactInfo]) {
      self.initial = initial
      self.contacts = contacts
    }
  }

  /* 
      通讯录 cell 数据模型
      // contactCellType: 自定义 UI 类型，其在注册会话列表 cell 时作为 key 与自定义 cell 进行绑定
      // localExtension: 本地扩展字段，可根据业务需求添加数据，与 contactCellType 结合可实现多种自定义 cell 的展示
  */
  public class ContactInfo {
    ...

    public var user: User?
    public var contactCellType = ContactCellType.ContactPerson.rawValue
    public var router = ContactPersonRouter
    public var isSelected = false
    public var headerBackColor: UIColor?
    public var localExtension: [String: Any]?
  }
  ```
  :::note notice
  需要在 viewDidLoad 之前完成会话列表 cell 注册字典（cellRegisterDic）的初始化，cellRegisterDic 的类型为 [Int : NEBaseContactTableViewCell.Type], **其中 key 对应通讯录 cell 数据模型中的 contactCellTypee，需要在此处与其对应的自定义 UI 类型进行绑定**，从而实现不同类型的自定义单元格的对应展示。
  :::

例如在用户头像下**添加小标**，如下图所示：

|默认|自定义后|
|:----|:----|
|![通讯录没小标默认.png](https://yx-web-nosdn.netease.im/common/50ab683403218a536403ee7c4def47df/通讯录没小标默认.png)|![通讯录头像小标.png](https://yx-web-nosdn.netease.im/common/edf533c19c7f00bdd1c5362a13615785/通讯录头像小标.png)




### 自定义标题栏（navigationView）

自V9.6.1 起，自定义导航栏需要使用 `customNavigationView` 来实现，V9.6.5 更名为 `navigationView`。

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
public class CustomContactsViewController: ContactsViewController, ContactsViewControllerDelegate {
  override public func viewDidLoad() {
    super.viewDidLoad()
    ...
  }

  // 自定义标题栏右侧按钮
  override public func addNavbarAction() {
    let addItem = UIBarButtonItem(
      image: UIImage(named: "mine_collection"),
      style: .plain,
      target: self,
      action: #selector(addItemAction)
    )
    addItem.tintColor = UIColor(hexString: "333333")
    let searchItem = UIBarButtonItem(
      image: UIImage(named: "mine_setting"),
      style: .plain,
      target: self,
      action: #selector(searchItemAction)
    )
    searchItem.imageInsets = UIEdgeInsets(top: 0, left: 35, bottom: 0, right: 0)
    searchItem.tintColor = UIColor(hexString: "333333")
    if NEKitContactConfig.shared.ui.hiddenRightBtns {
      return
    } else {
      if NEKitContactConfig.shared.ui.hiddenSearchBtn {
        navigationItem.rightBarButtonItems = [addItem]
      } else {
        navigationItem.rightBarButtonItems = [addItem, searchItem]
      }
    }
  }

  @objc private func addItemAction() {
    print("addItemAction")
  }

  @objc private func searchItemAction() {
    print("searchItemAction")
  }
}
```
:::note note 
示例代码中标题栏为通讯录页面的系统标题栏，用户可自定义其中的 UI 元素，包括但不限于标题、搜索按钮及其点击事件和添加按钮及其点击事件。
:::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![通讯录默认.png](https://yx-web-nosdn.netease.im/common/53437622dee7267b02739c4529e5e99f/通讯录默认.png)|![通讯录自定义右侧按钮.png](https://yx-web-nosdn.netease.im/common/035203374eab1d3a2ea3cf235d836ff4/通讯录自定义右侧按钮.png)




### 通讯录列表顶部添加扩展视图

- 示例代码（Swift）
  ```swift
  public class CustomContactsViewController: ContactsViewController, ContactsViewControllerDelegate {
    public lazy var customTopView: CustomView = {
      let view = CustomView(frame: CGRect(x: 0, y: 10, width: NEConstant.screenWidth, height: 40))
      view.backgroundColor = .blue
      return view
    }()

    override public func viewDidLoad() {
      super.viewDidLoad()
      ...

      // 顶部bodyTopView中添加自定义view（需要设置bodyTopView的高度）
      customTopView.btn.setTitle("通过重写方式添加", for: .normal)
      bodyTopView.addSubview(customTopView)
      bodyTopViewHeight = 80
    }
  }
  ```

  :::note  note 
  示例代码中 `bodyTopView` 为通讯录列表顶部预留的扩展视图，`bodyTopViewHeight` 为该扩展视图的高度，更改此变量会刷新页面布局。
  :::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |![通讯录默认.png](https://yx-web-nosdn.netease.im/common/53437622dee7267b02739c4529e5e99f/通讯录默认.png)|![通讯录提示消息.png](https://yx-web-nosdn.netease.im/common/9f52995f097e8d9a90c4a1338fa28e92/通讯录提示消息.png)


### 通讯录列表底部添加扩展视图

- 示例代码（Swift）
  ```swift
  public class CustomContactsViewController: ContactsViewController, ContactsViewControllerDelegate {
    override public func viewDidLoad() {
      super.viewDidLoad()
      ...

      // 底部bodyBottomView中添加自定义view（需要设置bodyBottomView的高度）
      customBottomView.btn.setTitle("通过重写方式添加", for: .normal)
      bodyBottomView.addSubview(customBottomView)
      bodyBottomViewHeight = 60
    }
  }
  ```

  :::note  note 
  示例代码中 `bodyBottomView` 为通讯录列表底部预留的扩展视图，`bodyBottomViewHeight` 为该扩展视图的高度，更改此变量会刷新页面布局。
  :::

- 效果对比

  |默认|自定义后|
  |:----|:----|
  |<img style="width:100%" src="https://yx-web-nosdn.netease.im/common/4a8cd6a0b571962d5bad42230448e35e/原图.PNG" />|<img style="width:100%" src="https://yx-web-nosdn.netease.im/common/6b02c859c30725b183246c8e677740f7/通讯录底层扩展视图.png" />
