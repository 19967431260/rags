IM UIKit 通讯录模块（`nim_contactkit_ui`）的 `ContactUIConfig` 提供通讯录界面的 UI 自定义配置项目，助您快速实现该界面的 UI 个性化定制。该界面可自定义的 UI 元素包括但不限于下图中的标注项。

::: note notice 
- 请确保在加载通讯录界面之前完成该界面的 UI 自定义。
- 讯录界面自定义事件监听相关说明，请参见 [通讯录事件监听](https://doc.yunxin.163.com/messaging-uikit/guide/jEzMDY4Mjc?platform=flutter)。
:::

## 功能介绍

### 可自定义元素

![通讯录界面.PNG](https://yx-web-nosdn.netease.im/common/708029e4de9b208b04c96ade8b30af84/通讯录界面.PNG)

### 自定义配置项

`ContactUIConfig` 配置项如下：

属性 | 类型 | 说明
---- | ---- | ----
`ContactTitleBarConfig` | ContactTitleBarConfig | 通讯录标题栏配置信息，详见 **ContactTitleBarConfig 标题栏配置项说明**.
`contactListConfig` | ContactListConfig | 通讯录列表配置，详见 **ContactListConfig 列表配置项说明**。
`showHeader` | bool | 是否在通讯录界面显示相关功能模块。
`headerData` | List\<TopListItem> | 相关功能模块的数据，如果不为空，则覆盖已有数据。
`topListItemBuilder` | TopListItemBuilder | 自定义相关功能模块组件构建，会替换掉默认的 Item。
`topEntranceClick` | TopEntranceClick |相关功能模块的点击。
`contactItemBuilder` | ContactItemBuilder | 自定义通讯录好友组件构建，会替换掉默认的 Item。
`contactItemClick` | ContactItemClick | 通讯录好友的点击。
`contactItemSelect` | ContactItemSelect | 通讯录好友的选择（通讯录列表 isCanSelectMemberItem 字段为 true 时有效，默认false）。

- `ContactTitleBarConfig` 标题栏配置项说明

属性 | 类型 | 说明
---- | ---- | ----
`showTitleBar` | bool | 是否展示 Title Bar。
`showTitleBarRightIcon` | bool | 是否展示 Title Bar 的最右侧图标。
`showTitleBarRight2Icon` | bool | 是否展示 Title Bar 的次最右侧图标。
`titleBarRightIcon` | Widget | Title Bar 最右侧图标。
`titleBarRight2Icon` | Widget | Title Bar 次最右侧图标。
`title` | String | Title Bar 标题文案。
`titleColor` | int | Title Bar 标题颜色值。

- `ContactListConfig` 列表配置项说明

属性 | 类型 | 说明
---- | ---- | ----
`nameTextColor` | Color | 通讯录好友列表中名称颜色设置。
`nameTextSize` | double | 通讯录好友列表中名称字体大小设置。
`indexTextColor` | Color | 通讯录好友列表中索引颜色属性设置。
`indexTextSize` | double | 通讯录好友列表中索引字体大小属性设置。
`showIndexBar` | bool | 通讯录好友列表设置是否展示索引条。
`showSelector` | bool | 通讯录好友列表设置是否展示选择框。
`avatarCornerRadius` | double | 通讯录好友列表头像的圆角，0 代表方形，18 为圆形。
`divideLineColor` | Color | 通讯录好友列表索引分割线颜色设置。

## 自定义方式

您可通过两种方式自定义会话列表界面的 UI 样式，即单实例全局自定义和单界面自定义。

### 单实例全局自定义

假设您的应用有多个通讯录界面，则通过 `ContactUIConfig` 的配置项进行全局自定义后，自定义配置在单个实例全局生效，所有通讯录界面都将按自定义的 UI 样式进行展示。

示例代码如下：

```dart
// 设置ContactKitClient的contactUIConfig
ContactKitClient.instance.contactUIConfig = ContactUIConfig(
  // 通讯录标题栏配置信息
  contactTitleBarConfig: ContactTitleBarConfig(
    // 设置不展示头部功能入口
    showTitleBar: false,
  ),
  // 通讯录列表配置
  contactListConfig: ContactListConfig(),
);
```

### 单界面自定义

通过 `ContactUIConfig` 的配置项，可对单个通讯录界面进行 UI 自定义。

```dart
ContactPage(
  // 设置ContactPage页面的config参数
  config: ContactUIConfig(
    contactTitleBarConfig: ContactTitleBarConfig(
      showTitleBar: false,
    ),
    contactListConfig: ContactListConfig(),
  ),
)
```

## 示例

### 设置标题样式

标题使用的是 `AppBar` 系统组件，包含 `title`（标题区域）与 `actions`（icon1 和 icon2 区域）两块区域，如下图所示：

![titlebar.drawio.png](https://yx-web-nosdn.netease.im/common/31850a8589cc959bc39222eae0e91f3b/titlebar.drawio.png)

您可以使用 `ContactTitleBarConfig` 来更改标题栏样式。

假设您需要：
- 修改标题文案和位置
- 隐藏次最右侧图标
- 自定义最右侧图标与事件

则示例代码如下：

```dart
ContactPage(
  config: ContactUIConfig(
    contactTitleBarConfig: ContactTitleBarConfig(
      title: "自定义标题",
      centerTitle: true,
      // 不展示右边第二图标
      showTitleBarRight2Icon: false,
      titleBarRightIcon: IconButton(
        onPressed: () {
          // 自定义点击
        },
        icon: Icon(Icons.more_horiz_outlined),
      ),
    ),
  ),
)
```

UI 效果如下：

![自定义标题.png](https://yx-web-nosdn.netease.im/common/188e364a5f83acef994a225e9bf01fb8/自定义标题.png)

### 设置列表区域样式

列表区域主要分为 **相关功能模块** 和 **好友列表模块**，列表中 UI 属性设置，包括好友昵称的字体、好友头像、索引字体、颜色等均由 `ContactListConfig` 配置实现。

假设您需要自定义昵称颜色、字体大小和头像圆角等，示例代码如下：

```dart
ContactPage(
  // 通过方式二配置
  config: ContactUIConfig(
    contactListConfig: ContactListConfig(
      // 昵称颜色
      nameTextColor: Colors.black45,
      // 昵称字体大小
      nameTextSize: 10,
      // 头像圆角
      avatarCornerRadius: 10,
    ),
  ),
)
```

UI 效果比对如下：

默认 | 自定义后
---- | ----
<img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/67c12f6911731349ad0f1a9a937ad40f/列表默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/766e55bc1e0a3c63536c6e8ad01c3897/列表配置.png" style="width:80%;border: 1px solid #BFBFBF;">