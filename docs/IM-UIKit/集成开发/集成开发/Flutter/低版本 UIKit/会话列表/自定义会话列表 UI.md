IM UIKit 会话列表模块（`nim_conversationkit_ui`）的`ConversationUIConfig`提供会话列表界面的 UI 自定义配置项，助您快速修改会话列表界面的 UI 样式。




::: note notice
- 请确保在加载会话列表之前完成该界面的 UI 自定义。
- 会话列表界面自定义事件监听相关说明，请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/TY1NTM4NDM?platform=flutter" target="_blank">会话列表事件监听</a>。
:::
## 功能介绍


### **可自定义元素**

该界面可自定义的 UI 元素包括但不限于下图中的标注项。



![会话列表界面.PNG](https://yx-web-nosdn.netease.im/common/7b974bac3a427ca612fc79ace9eba724/会话列表.png)


### **自定义配置项**

`ConversationUIConfig`提供`titleBarConfig` 和`itemConfig`属性，分别用于自定义会话列表界面的标题栏和会话列表。

<div style="width:150px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`titleBarConfig` | `ConversationTitleBarConfig` | 会话列表界面标题栏配置，具体配置项请参见下文的**标题栏配置项**
`itemConfig` | `ConversationItemConfig` | 会话列表配置，具体配置项请参见下文的**会话列表配置配置**


- 标题栏配置项

<div style="width:150px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`showTitleBar` | `bool` | 是否展示 Title Bar
`showTitleBarLeftIcon` | `bool` | 是否展示 Title Bar 的最左侧图标 
`showTitleBarRightIcon` | `bool` | 是否展示 Title Bar 的最右侧图标
`showTitleBarRight2Icon` | `bool` | 是否展示 Title Bar 的次最右侧图标
`titleBarLeftIcon` | `Widget` | Title Bar 最左侧图标 
`titleBarRightIcon` | `Widget` | Title Bar 最右侧图标
`titleBarRight2Icon` | `Widget` | Title Bar 次最右侧图标
`title` | `String` | Title Bar 标题文案
`titleColor` | `Color` | Title Bar 标题颜色值


- 会话列表配置项（不包含点击事件）

<div style="width:150px">属性</div> | 类型 | 说明
:---- | :-------------- | :---------
`itemTitleColor` | `Color` | 会话项名称的字体颜色 
`itemTitleSize` | `double` | 会话项名称的字体大小 
`itemContentColor` | `Color` | 会话项消息缩略内容的字体颜色 
`itemContentSize` | `double` | 会话项消息缩略内容的字体大小 
`itemDateColor` | `Color` | 会话项时间的字体颜色 
`itemDateSize` | `double` | 会话项时间的字体大小 
`avatarCornerRadius` | `double` | 会话列表中会话头像的圆角成都，0 为方形，21 为圆形
`conversationComparator` | `Comparator<ConversationInfo>` | 会话列表排序自定义规则 
`customItemBuilder` | `ConversationItemBuilder` | 自定义会话 Item 组件，会替换掉默认的 Item 
`lastMessageContentBuilder` | `ConversationLastMessageContentBuilder` | 会话列表中最后一条消息的展示内容自定义回调
`clearMessageWhenDeleteSession` | `bool` | 删除会话时，是否同步删除会话的消息记录，默认为 false





## 自定义方式

您可通过两种方式自定义会话列表界面的 UI 样式，即单实例全局自定义和单界面自定义。


### **单实例全局自定义**


假设您的应用有多个会话列表界面，则通过`ConversationUIConfig`的配置项进行全局自定义后，自定义配置在单个实例全局生效，所有会话列表界面都将按自定义的 UI 样式进行展示。

示例代码如下：

```dart
// 设置ConversationKitClient的conversationUIConfig
ConversationKitClient.instance.conversationUIConfig = ConversationUIConfig(
  //会话列表标题栏配置
  titleBarConfig: ConversationTitleBarConfig(),
  // 会话列表项配置
  itemConfig: ConversationItemConfig()
);
```



### **单界面自定义**

通过 `ConversationUIConfig`的配置项，可对单个会话列表界面进行 UI 自定义。

::: note notice
该种方式优先级大于全局配置方式。换而言之，如果在单实例全局自定义后在进行单界面自定义，则后者的配置会覆盖前者的。
:::


<br>


示例代码如下：


  ```dart
  ConversationPage(
    // 设置ConversationPage页面的config参数
    config: ConversationUIConfig(
      //会话列表标题栏配置
      titleBarConfig: ConversationTitleBarConfig(),
      // 会话列表项配置
      itemConfig: ConversationItemConfig(),
    ),
  );
  ```

## 示例


### **设置标题样式**

标题使用的是`AppBar`系统组件，包含`title`与`actions`两块区域（图中的left icon, right icon2，right icon1 为`actions`区域），如下图所示：



![titlebar.drawio.png](https://yx-web-nosdn.netease.im/common/3186455df532d84432635a8d967eaecd/conversationTitle.drawio.png)


您可以通过设置`ConversationTitleBarConfig`的标题配置项来更改标题栏样式。

 

假设您需要：

- 修改标题文案和位置
- 隐藏左侧图标和次最右侧图标
- 自定义最右侧图标及其点击事件

则示例代码如下：

```dart
ConversationUIConfig(
  titleBarConfig: ConversationTitleBarConfig(
    centerTitle: true,
    titleBarTitle: '自定义标题',
    showTitleBarLeftIcon: false,
    showTitleBarRight2Icon: false,
    titleBarRightIcon: IconButton(
      onPressed: () {
        // 自定义点击
      },
      icon: Icon(Icons.more_horiz_outlined),
    )
  )
)
```


UI 效果对比如下：

|<div style="width:120px">默认样式</div> | <div style="width:120px">自定义样式</div>|
|-------- | ---------- |
|![列表默认.png](https://yx-web-nosdn.netease.im/common/bac81514a9e1944029a411e38bbd6b57/conversationtitledefaultnew.png) | ![列表配置.png](https://yx-web-nosdn.netease.im/common/b9f7224c65ec1a68b44ccdc82c62cefa/conversationtitleconfig.png) |








### **设置列表区域样式**

列表区域主要展示会话列表项内容。列表中 UI 属性设置，包括会话项名称的字体颜色及大小、会话项的消息缩略字体颜色及大小、会话项的时间字体颜色及大小、会话项左侧图标圆角大小等均由`ConversationItemConfig`配置实现。


#### **修改字体及头像圆角**


修改字体颜色、字体大小及头像圆角的示例代码如下：

  ```dart
  ConversationUIConfig(
    itemConfig: ConversationItemConfig(
      itemTitleColor: Colors.red,
      itemTitleSize: 20,
      avatarCornerRadius: 10
    )
  )
    
  ```

效果对比如下：


<div style="width:120px">默认样式</div> | <div style="width:120px">自定义样式</div>
-------- | ---------- 
![列表默认.png](https://yx-web-nosdn.netease.im/common/5a42c14b0da0124ba61a78528cd5aa74/conversationListSource.png) | ![列表配置.png](https://yx-web-nosdn.netease.im/common/48d4fdc4b7d383908b7f2585d67bf9d2/conversationItemConfig.png) 

#### **修改列表排序**

如果需要自定义列表的排序，可按照如下示例代码实现：

```dart
ConversationUIConfig(
  itemConfig: ConversationItemConfig(
    conversationComparator: (source, other) {
      // 按照名称字符串顺序排序
      return source.getName().compareTo(other.getName());
    })
)
```

UI 效果对比如下：

<div style="width:120px">默认顺序</div> | <div style="width:120px">自定义顺序</div> 
:-------- | :---------- |
![列表默认.png](https://yx-web-nosdn.netease.im/common/48d4fdc4b7d383908b7f2585d67bf9d2/conversationItemConfig.png) | ![列表配置.png](https://yx-web-nosdn.netease.im/common/1574950f8efb4458c89fcc924af9f3c6/conversationsortnew.png) 

#### **自实现自定义逻辑**

如果以上自定义仍无法满足您的自定义需求，您可自行实现相关逻辑来完成会话 Item 内容的自定义。

示例代码如下：


```dart
ConversationUIConfig(
  itemConfig: ConversationItemConfig(
    customItemBuilder: (data,position){
      return Expanded(
        child: Container(
          height: 62,
          padding: const EdgeInsets.symmetric(horizontal: 20),
          alignment: Alignment.center,
          child: Text(_getName(data)??'',
                      style: TextStyle(
                        fontSize: 16,
                        color: Colors.blue,
                        fontWeight: FontWeight.normal
                      ),
                     ),
        )
      );
    }
)
```

UI 效果对比如下：

|<div style="width:120px">默认样式</div> | <div style="width:120px">自定义样式</div> |
|:-------- | :---------- |
|![列表默认.png](https://yx-web-nosdn.netease.im/common/5a42c14b0da0124ba61a78528cd5aa74/conversationListSource.png) | ![列表配置.png](https://yx-web-nosdn.netease.im/common/9c5d8208416754f7a427e6c590b935c5/conversationitembuildernew.png) |






