IM UIKit 的消息模块（`chatkit-ui`）提供消息界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。您也可以直接修改布局文件（`chat_layout_fragment.xml`）的源码自定义 UI。

::: note notice
请确保在消息界面加载之前完成该界面的 UI 自定义，具体加载的对象包括 `ChatP2PFragment`（单聊 Fragment）的 Activity、`ChatTeamFragment`（群聊 Fragment）的 `Activity` 和您的 Application。
:::

<div id="main-content">

## 功能概述

### UI 元素自定义

<div id="examples">

消息界面可自定义的 UI 元素包括但不限于下图中的标注项。

<img src="https://yx-web-nosdn.netease.im/common/5e410edf8bd72d095c958f6873c9d7cc/会话消息界面.png" style="width:60%;border: 1px solid #BFBFBF;" />

</div>

您可通过 `ChatUIConfig` 中的个性化配置项修改消息界面 UI 元素，如消息体、输入按钮和消息长按菜单等，具体如下：
<div style="width:140px">属性</div> | 类型 | 说明
:---- | :---- | :----
`messageItemClickListener` | IMessageItemClickListener | 用于设置消息体中的单击事件处理
`messageProperties` | MessageProperties | 消息页面的 UI 个性化定制，包括常用的字体颜色、大小、是否可见、背景色等属性等，具体见下文的 **MessageProperties 个性化配置项**
`permissionListener` | IPermissionListener | 系统权限申请监听器，可用于修改系统权限申请的默认实现
`chatFactory` | IChatFactory | 消息页面中，消息体的 ViewHolder 的构建器，可用于修改默认消息体 UI 的创建。
`chatViewCustom` | IChatViewCustom | 消息页面中，获取页面的整个视图。可用于在页面中添加、移除或者修改布局元素。
`chatInputMenu` | IChatInputMenu | 消息页面中，输入框按钮定制。可用于修改输入框按钮以及更多中按钮的增加、修改和删除。
`chatPopMenu` | IChatPopMenu | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单的增加、删除和修改。
`popMenuClickListener` | IChatPopMenuClickListener | 消息页面中，长按消息体弹出菜单定制。用于对长按菜单单击事件的修改，可修改默认实现和自定义菜单的单击。

- **MessageProperties 个性化配置项**

  <div style="width:140px">属性</div> | 类型 | 说明
  :---- | :---- | :----
  `selfMessageBg` | Drawable | 自己发送的消息体的背景色，具体自定义示例见下文的 [修改消息体背景色](#修改消息体背景色)
  `receiveMessageBg` | Drawable | 接收到的消息体的背景色，具体自定义示例见下文的 [修改消息体背景色](#修改消息体背景色)
  `receiveMessageRes` | int | 他人发送消息内容的背景资源 ID，支持 drawable/color
  `selfMessageRes` | int | 自己发送消息内容的背景资源 ID，支持 drawable/color
  `userNickColor` | int | 不设置头像的用户所展示的文字头像中的文字颜色
  `userNickTextSize` | int | 不设置头像的用户所展示的文字头像中的文字字体大小
  `messageTextColor` | int | 文本消息字体颜色
  `messageTextSize` | int | 文本消息字体大小
  `avatarCornerRadius` | float | 头像的圆角，0 代表方形，30dp 代表圆形。这里您需要自行将 dp（density-independent pixels）单位转换为像素（px）单位。
  `timeTextSize` | int | 消息列表中，时间字体大小
  `timeTextColor` | int | 消息列表中，时间字体颜色
  `signalBgColor` | int | 被标记消息的背景色（见下图一）
  `showP2pMessageStatus` | boolean | 单聊中是否展示已读未读状态（见下图二）
  `showTeamMessageStatus` | boolean | 群聊中是否展示已读未读状态（见下图二）
  `showTitleBar` | boolean | 是否展示标题栏，具体自定义示例见下文的 [隐藏界面标题栏](#隐藏界面标题栏)
  `showTitleBarRightIcon` | boolean | 是否展示标题栏右侧图标按钮
  `titleBarRightRes` | int | 设置标题栏右侧图标按钮展示图标，具体自定义示例见下文的 [修改界面标题右侧图标](#修改界面标题栏右侧图标)
  `titleBarRightClick` | View.OnClickListener | 标题栏右侧图标的单击事件，具体配置示例见下文的 [修改界面标题右侧图标](#修改界面标题栏右侧图标)
  `chatViewBackground` | Drawable | 设置界面背景色，具体自定义示例见下文的 [修改界面背景色](#修改界面背景色)

<div id="examples">

<div style="width:120px">图一</div> | <div style="width:120px">图二</div>
:---- | :----
<img alt="标记消息背景色示意图.png" src="https://yx-web-nosdn.netease.im/common/1658e8c192fad445aba1cdc302680e13/标记消息背景色示意图.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="已读未读状态.png" src="https://yx-web-nosdn.netease.im/common/8106e3b9a381b1194e167679270b26fa/已读未读状态.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### 界面布局自定义

<div id="examples">

除了界面的 UI 元素，您也可对界面的布局进行自定义，消息界面的默认布局如下图所示。

<img style="width:60%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/1c5b88984d0a06ac47240f5016f4b03a/会话界面布局图2.png" />

</div>

该界面各视图的说明如下：

<div style="width:140px">属性</div> | 类型 | 说明
:---- | :---- | :----
`ChatViewTitle` | BackTitleBar | 消息界面的标题视图，可通过 `ChatView` 的 `getTitleBar()` 来获取视图进行样式修改
`ChatViewBodyTop` | FrameLayout | 消息列表上方的小块视图，可通过 `ChatView` 的 `getChatBodyTopLayout()` 来获取视图进行样式修改。该视图可用于在消息列表和顶部界面标题中间增加新的 UI 元素
`ChatViewBody` | FrameLayout | 消息列表视图，可通过 `ChatView` 的 `getChatBodyLayout()` 来获取视图进行样式修改。布局中包含 `ChatMessageListView` 消息列表和通知文本视图。文本视图 ID 为 `tvNotification`，用于断网提示
`ChatViewBodyBottom` | FrameLayout | 消息列表下视图，可通过 `ChatView` 的 `getChatBodyBottomLayout()` 来获取视图进行样式修改。用于在消息列表和底部输入框中间增加新的 UI 元素，具体自定义示例请参考下文的 [在输入框上方增加按钮](#在输入框上方增加按钮)
`ChatViewBottom` | FrameLayout | 底部输入框视图，可通过 `ChatView` 的 `getChatBottomLayout()` 来获取视图进行样式修改。布局中包含底部输入框视图 `MessageBottomLayout`
`ChatMessageListView` | ChatMessageListView | 消息列表，可通过 `ChatView` 的 `getMessageListView()` 来获取视图进行样式修改
`MessageBottomLayout` | MessageBottomLayout | 底部输入框视图，可通过 `ChatView` 的 `getInputView()` 来获取视图进行样式修改

::: note note
上述元素都可以通过 `ChatView` 提供的相应接口获取。`ChatView` 的获取可参考上述的 `ChatUIConfig:chatViewCustom` 来获取整个界面视图。
:::

## 自定义示例

### **修改界面标题栏右侧图标**

消息界面标题采用的是 IM UIKit 内部封装的标题视图 `BackTitleBar`，包含左侧返回按钮、中间标题区域、右侧按钮区域。

- 示例代码
    ```Java
        ChatUIConfig chatUIConfig = new ChatUIConfig();
          chatUIConfig.messageProperties = new MessageProperties();
          //设置右侧按钮图标
          chatUIConfig.messageProperties.titleBarRightRes = R.drawable.ic_user_setting;
          //设置右侧按钮单击事件
          chatUIConfig.messageProperties.titleBarRightClick = new View.OnClickListener() {
              @Override
              public void onClick(View v) {
                  //todo 右侧按钮的单击事件
              }
          };
          ChatKitClient.setChatUIConfig(chatUIConfig);
    ```
  
<div id="examples">

- 效果对比

    <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
    :---- | :----
    <img alt="Screenshot_20221018_154951.png" src="https://yx-web-nosdn.netease.im/common/5385ba879fcd9fb40033475cd6c1ba1f/Screenshot_20221018_154951.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img style="width:80%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/e3b1d8c6ce11d66f075df37180b741b0/修改会话界面标题栏右侧图标.png" />

</div>

### **隐藏界面标题栏**

- 示例代码
  ```Java
      ChatUIConfig chatUIConfig = new ChatUIConfig();
      chatUIConfig.messageProperties = new MessageProperties();
        //设置标题不可见
      chatUIConfig.messageProperties.showTitleBar = false;
      ChatKitClient.setChatUIConfig(chatUIConfig);
  ```

<div id="examples">

- 效果对比

  <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
  --- | ----
  <img alt="不隐藏会话界面标题.png" src="https://yx-web-nosdn.netease.im/common/86ce81132c56b24cd427960df3362ca3/不隐藏会话界面标题.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="隐藏会话界面标题.png" src="https://yx-web-nosdn.netease.im/common/bf0ff6fa7117446f130fb8cb49891cfa/隐藏会话界面标题.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### **修改界面背景色**

- 示例代码
  ```Java
  ChatUIConfig chatUIConfig = new ChatUIConfig();
  chatUIConfig.messageProperties = new MessageProperties();
  //页面背景色
  chatUIConfig.messageProperties.chatViewBackground =
      new ColorDrawable(context.getResources().getColor(R.color.color_blue_3a9efb));
  ChatKitClient.setChatUIConfig(chatUIConfig);
  ```

<div id="examples">

- 效果对比
  <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
  ---- | ----
  <img alt="会话背景色默认.png" src="https://yx-web-nosdn.netease.im/common/5385ba879fcd9fb40033475cd6c1ba1f/会话背景色默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="会话背景色自定义.png" src="https://yx-web-nosdn.netease.im/common/ebf998044a5974e05f3a2cdf649b664d/会话背景色自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### **修改消息体背景色**

- 示例代码
  ```Java
  ChatUIConfig chatUIConfig = new ChatUIConfig();
  chatUIConfig.messageProperties = new MessageProperties();
  //发送消息背景色
  chatUIConfig.messageProperties.selfMessageBg =new ColorDrawable(context.getResources().getColor(R.color.color_blue_3a9efb));
  //接受消息背景色
  chatUIConfig.messageProperties.receiveMessageBg =new ColorDrawable(context.getResources().getColor(R.color.color_666666));;
  ChatKitClient.setChatUIConfig(chatUIConfig);
  ```

<div id="examples">

- 效果对比

  <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
  --- | ----
  <img alt="消息体背景色默认.png" src="https://yx-web-nosdn.netease.im/common/b28eb38ebcb01b1251b2524e1e53203c/消息体背景色默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="消息提背景色自定义.png" src="https://yx-web-nosdn.netease.im/common/43735ebc20303551e9e5d65d15cf8098/消息提背景色自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### **不展示消息长按菜单**

长按消息默认会弹出操作菜单，该菜单可设置为长按消息时不展示。

<div id="examples">

- 默认展示该菜单

  <img style="width:400px" src="https://yx-web-nosdn.netease.im/common/3fbe564f917dc662afce069d71748ce8/操作菜单未去除标记.jpg"/>

</div>

- 示例代码

  以下为不展示消息长按菜单的示例代码：

  ```Java
  ChatUIConfig chatUIConfig = new ChatUIConfig();
    chatUIConfig.chatPopMenu =
          new IChatPopMenu() {
            @Override
            public boolean showDefaultPopMenu() {
              return false;
            }
          };
      ChatKitClient.setChatUIConfig(chatUIConfig);

  ```

### **去除消息长按菜单的标记按钮**

- 示例代码
  ```Java
  ChatUIConfig chatUIConfig = new ChatUIConfig();
  chatUIConfig.chatPopMenu = new IChatPopMenu() {
            @NonNull
            @Override
            public List<PluginAction> customizePopMenu(
                List<PluginAction> menuList, ChatMessageBean messageBean) {
                if(menuList != null){
                    for (int index = menuList.size() - 1;index >=0;index--){
                        if (TextUtils.equals(menuList.get(index).getAction(),ActionConstants.POP_ACTION_PIN)){
                            menuList.remove(index);
                            break;
                        }
                    }
                }
                return menuList;
            }
          };
    ChatKitClient.setChatUIConfig(chatUIConfig);

  ```

<div id="examples">

- 效果对比

  <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
  --- | ----
  <img alt="操作菜单未去除标记.jpg" src="https://yx-web-nosdn.netease.im/common/3fbe564f917dc662afce069d71748ce8/操作菜单未去除标记.jpg" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="操作菜单去除标记.jpg" src="https://yx-web-nosdn.netease.im/common/945a6c85fdefd6064170abdadf180b85/操作菜单去除标记.jpg" style="width:80%;border: 1px solid #BFBFBF;">

</div>

上述代码的 `public List<PluginAction> customizePopMenu(List<PluginAction> menuList, ChatMessageBean messageBean)` 方法中，`menuList` 参数会把当前 IM UIKit 的默认实现的能力传递过来。如果不需要默认实现的能力，在该方法中将 `menuList` 清空即可。同时也可对 `menuList` 进行操作来调整菜单顺序。`messageBean` 代表当前长按消息的消息实体类。IM UIKit 默认实现的能力如下表示所示：
<div style="width:140px">标识 Action</div> | 说明
:---- | :----
`ActionConstants.POP_ACTION_REPLY` | 回复消息
`ActionConstants.POP_ACTION_COPY` | 复制消息
`ActionConstants.POP_ACTION_RECALL` | 撤回消息
`ActionConstants.POP_ACTION_PIN` | 标记消息
`ActionConstants.POP_ACTION_MULTI_SELECT` | 多选消息
`ActionConstants.POP_ACTION_DELETE` | 删除消息
`ActionConstants.POP_ACTION_TRANSMIT` | 转发消息
`ActionConstants.POP_ACTION_TOP_STICK` | 置顶消息

### **在界面底部菜单栏增加按钮**

- 示例打码
  ```Java
      ChatUIConfig chatUIConfig = new ChatUIConfig();
      chatUIConfig.chatInputMenu =
          new IChatInputMenu() {
            @Override
            public List<ActionItem> customizeInputBar(List<ActionItem> actionItemList) {
              //向输入区域的菜单中增加一个按钮，其中 ActionItem，第一个参数 action 为该菜单项的唯一 KEY，在下面单击事件中进行区分。第二个参数为图片资源
              actionItemList.add(new ActionItem("custom_action",R.drawable.ic_user_setting));
              return actionItemList;
            }
            //新增加的菜单的单击事件，action 为添加时候填写的唯一值
            @Override
            public boolean onCustomInputClick(Context context, View view, String action) {
              ToastX.showShortToast(action);
              return true;
            }
          };
      ChatKitClient.setChatUIConfig(chatUIConfig);

  ```

<div id="examples">

- 效果对比

  <div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
  --- | ----
  <img alt="默认底部输入区域.png" src="https://yx-web-nosdn.netease.im/common/43d7b1365be3a8b91c4d6a4f0ff47d48/默认底部输入区域.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="底部输入区域增加按钮.png" src="https://yx-web-nosdn.netease.im/common/9bec61ba3e92a6e35cdace9d4dde233b/底部输入区域增加按钮.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### **在更多区域增加按钮**

您可根据业务需求在聊天输入区域的<img alt="更多按钮.png" src="https://yx-web-nosdn.netease.im/common/b8cc1ffb306abdcb505c48708b1de09d/更多按钮.png" style="width:5%;border: 1px solid #BFBFBF;">下增加自定义按钮。

**示例代码**

```Java
    ChatUIConfig chatUIConfig = new ChatUIConfig();
    chatUIConfig.chatInputMenu =
        new IChatInputMenu() {
          @Override
          public List<ActionItem> customizeInputMore(List<ActionItem> actionItemList) {
            //向输入区域的菜单中增加一个按钮，其中 ActionItem，第一个参数 action 为该菜单项的唯一 KEY，在下面单击事件中进行区分。第二个参数为图片资源，第三个参数为展示文案
            actionItemList.add(new ActionItem("custom_more_1",R.drawable.ic_user_setting,R.string.chat));
            return actionItemList;
          }
          //新增加的菜单的单击事件，action 为添加时候填写的唯一值
          @Override
          public boolean onCustomInputClick(Context context, View view, String action) {
            ToastX.showShortToast(action);
            return true;
          }
        };
    ChatKitClient.setChatUIConfig(chatUIConfig);

```
::: note note
更多区域中，IM UIKit 默认实现的按钮只有拍摄按钮，其对应的 Action 为 `ActionConstants.ACTION_TYPE_CAMERA`。
:::

**示例代码解读**

上述代码的 `public boolean customizeInputBar(List<ActionItem> actionItemList)` 方法中，`actionItemList` 参数会把当前 IM UIKit 的默认实现的能力传递过来。如果不需要默认实现的能力，在该方法中将 `actionItemList` 清空即可。同时也可对 `actionItemList` 进行操作来调整菜单顺序。IM UIKit 默认实现的能力如下表示所示：

<div style="width:140px">标识 Action</div> | 说明
:---- | :----
`ActionConstants.ACTION_TYPE_RECORD` | 录音功能
`ActionConstants.ACTION_TYPE_EMOJI` | 表情功能
`ActionConstants.ACTION_TYPE_ALBUM` | 发送图片
`ActionConstants.ACTION_TYPE_MORE` | 展开更多菜单
`ActionConstants.ACTION_TYPE_CAMERA` | 弹出拍照和录像弹窗
`ActionConstants.ACTION_TYPE_TAKE_PHOTO` | 拍照
`ActionConstants.ACTION_TYPE_TAKE_VIDEO` | 录像
`ActionConstants.ACTION_TYPE_LOCATION` | 地理位置

<div id="examples">

**效果对比**

<div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
--- | ----
<img alt="底部输入区域更多默认样式.png" src="https://yx-web-nosdn.netease.im/common/d73b27f27118339e7034e9fb04628971/底部输入区域更多默认样式.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="底部输入区域更多自定义.png" src="https://yx-web-nosdn.netease.im/common/4c0ee8e1742e1b1d03a4eeb1012365fe/底部输入区域更多自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### **在更多区域移除按钮**

您可根据业务需求在聊天输入区域的<img alt="更多按钮.png" src="https://yx-web-nosdn.netease.im/common/b8cc1ffb306abdcb505c48708b1de09d/更多按钮.png" style="width:5%;border: 1px solid #BFBFBF;">下删除 IM UIKit 的内置按钮。以下以**移除发送地理位置消息的按钮**为例进行说明。

**示例代码**

```
ChatUIConfig chatUIConfig = new ChatUIConfig();
chatUIConfig.chatInputMenu =
            new IChatInputMenu() {
              @Override
              public List<ActionItem> customizeInputBar(List<ActionItem> actionItemList) {
                //个性化配置输入框下方按钮，actionItemList 传递默认配置的四个按钮：语音、表情、图片和更多。
                //您可以根据自己的需求修改 actionItemList 的数量和顺序，ChatKit-UI 会按照您的返回结果展示。
                return actionItemList;
              }

              @Override
              public List<ActionItem> customizeInputMore(List<ActionItem> actionItemList) {
              //个性化配置更多面板中按钮，actionItemList 传递默认配置的四个按钮：拍摄、文件、位置和音视频通话。
                  for (int index = 0;index < actionItemList.size();index++){
                  //根据 Action 判断按钮是否删除
                      if (TextUtils.equals(actionItemList.get(index).getAction(),
                              ActionConstants.ACTION_TYPE_LOCATION)){
                          actionItemList.remove(index);
                          break;
                      }
                  }
                  return actionItemList;
              }

              @Override
              public boolean onCustomInputClick(Context context, View view, String action) {
                return false;
              }
            };
ChatKitClient.setChatUIConfig(chatUIConfig);
```

<div id="examples">

**效果对比**

<div style="width:120px">默认</div> | <div style="width:120px">移除后</div>
--- | ----
<img alt="地理位置按钮默认.png" src="https://yx-web-nosdn.netease.im/common/c9a44795bfc644b3f41e754c7cefb8bc/地理位置按钮默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="去除地图功能后的界面 resized.png" src="https://yx-web-nosdn.netease.im/common/889bcbd03158e0306c79038d56c9850f/去除地图功能后的界面resized.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

### 在输入框上方增加按钮

**示例代码**

```Java
ChatUIConfig chatUIConfig = new ChatUIConfig();
chatUIConfig.chatViewCustom = layout -> {
    // 从 ChatView 中获取底部消息类型布局自定义
    FrameLayout frameLayout = null;
    
    // 根据您当前使用的皮肤去获取，基础版皮肤使用(layout instanceof ChatView)，通用皮肤采用(layout instanceof FunChatView)
    if (layout instanceof ChatView) {
        frameLayout = ((ChatView) layout).getChatBodyBottomLayout();
    } else if (layout instanceof FunChatView) {
        frameLayout = layout.getChatBodyBottomLayout();
    }
    
    // 效果截图中红色框中的布局视图 View
    IMBottomView imBottomView = new IMBottomView(context);
    FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams(
        ViewGroup.LayoutParams.WRAP_CONTENT, 
        ViewGroup.LayoutParams.WRAP_CONTENT
    );
    layoutParams.leftMargin = context.getResources().getDimensionPixelSize(R.dimen.dp_16);
    
    // 把自定义 View 添加到聊天页面中
    frameLayout.addView(imBottomView, layoutParams);
};

ChatKitClient.setChatUIConfig(chatUIConfig);
```

**示例代码解读**

示例代码中 `chatUIConfig.chatViewCustom` 的接口源码如下：

```Java
public interface IChatViewCustom {
  void customizeChatLayout(final ChatView layout);
}
```
`ChatView` 作为消息界面的整体 View 提供了获取该界面中所有 View 的获取方法，具体如下：
<div style="width:140px">方法</div> | 返回值 | 说明
:---- | :---- | :----
`getTitleBar` | BackTitleBar | 获取聊天页面头部 TitleBar 视图
`getChatBodyTopLayout` | FrameLayout | 获取消息列表和头部 TitleBar 中间的视图布局，默认里面为空
`getChatBodyLayout` | FrameLayout | 获取消息列表区块布局，其中该布局内部包含 `ChatMessageListView` 消息列表视图
`getChatBodyBottomLayout` | FrameLayout | 获取消息列表和底部输入框中间的视图布局，默认为空。可用于上述示例中的场景。
`getChatBottomLayout` | FrameLayout | 获取底部视图布局，其中包含输入框视图 `MessageBottomLayout`
`getChatViewLayoutBinding` | ChatViewLayoutBinding | 获取整个聊天页面的布局 viewBinding
`getInputView` | MessageBottomLayout | 获取底部输入框区域的视图
`setMessageBackground` | void | 设置聊天列表的背景

<div id="examples">

**效果对比**

<div style="width:120px">默认</div> | <div style="width:120px">自定义后</div>
--- | ----
<img alt="会话界面布局原图_resized.png" src="https://yx-web-nosdn.netease.im/common/734e875c4df8f1ab42f1b94222b68c8c/会话界面布局原图_resized.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="输入框上方增加按钮.png" src="https://yx-web-nosdn.netease.im/common/6858e9f8f985c6dcccb467b8025fc99d/输入框上方增加按钮.png" style="width:80%;border: 1px solid #BFBFBF;">

</div>

## 源码导读

### **界面布局**

`ChatKit-ui` 模块的 `chat_layout_fragment.xml` 文件包含了整个消息列表的布局配置。通过修改该文件的源码可实现界面元素调整和界面背景修改等自定义操作。该文件的源码概略如下：

```XML
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    //消息界面的 UI 都封装在 ChatView 中
    <com.netease.yunxin.kit.chatkit.ui.view.ChatView
        android:id="@+id/chatView"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</LinearLayout>
```

### **消息**

`ChatView` 为消息 UI 的实现类，`ChatView` 是对 `RecyclerView` 的封装，同时提供数据更新接口，具体如下:
<div style="width:200px">方法</div> | <div style="width:180px">入参类型</div> | 说明
:---- | :---- | :----
`setItemClickListener` | `IMessageItemClickListener` | 设置消息的单击事件
`setMessageProperties` | `MessageProperties` | 设置列表单击事件，分为单击和长按
`clearMessageList` | 无 | 清理消息列表
`addMessageListForward` | List<ChatMessageBean> | 在列表头部添加消息
`appendMessageList` | List<ChatMessageBean> | 在消息列表添加数据
`updateMessage` | `ChatMessageBean`, `Object` | 更新消息数据，消息发送状态、已读状态更新使用,第二个参数为 payload，表示更新类型，如果传 null,会全量刷新 item
`setMessageProxy` | `IMessageProxy` | 设置消息行为的实现，包括发送文本消息、图片消息等
`setMessageViewHolderFactory` | `IChatFactory` | 消息构造工程类，具体实现可参考 `ChatDefaultFactory`
`getInputView` | 无 | 获取消息界面底部输入视图，可以自行设置底部视图

### **消息 UI**

在消息界面中存在多种类型的 ViewHolder，分别代表不同的消息类型。

<div style="width:200px">ViewHolder</div> | <div style="width:90px">消息类型</div> | 说明
:---- | :---- | :----
`ChatTextMessageViewHolder` | 文本消息 | 布局文件为 `chat_message_text_view_holder.xml`(多个类型公用)，可以在该文件中调整其布局结构
`ChatAudioMessageViewHolder` | 语音消息 | 布局文件为 `chat_message_audio_view_holder.xml`，可以在该文件中调整其布局结构
`ChatImageMessageViewHolder` | 图片消息 | 继承 `ChatThumbBaseViewHolder`，其布局文件为 `chat_message_thumbnail_view_holder.xml`，可以在该文件中调整其布局结构
`ChatVideoMessageViewHolder` | 视频消息 | 继承 `ChatThumbBaseViewHolder`，其布局文件为 `chat_message_thumbnail_view_holder.xml`，可以在该文件中调整其布局结构
`ChatNotificationMessageViewHolder` | 系统通知 | 布局文件为 `chat_message_text_view_holder.xml`，可以在该文件中调整其布局结构
`ChatTipsMessageViewHolder` | 提示消息 | 布局文件为 `chat_message_text_view_holder.xml`(多个类型公用)`，可以在该文件中调整其布局结构

### **其他**

* 消息发送逻辑，在 `ChatBaseFragment` 中的 `IMessageProxy.messageProxy` 实现。

* 消息的单击事件，在 `ChatBaseFragment` 中的 `IMessageItemClickListener.itemClickListener` 实现。

* 长按消息弹出菜单的事件处理，在 `ChatBaseFragment` 中 `ChatPopMenuActionListener.actionListener` 实现。

* 消息界面中消息的构造工程，在 `ChatDefaultFactory` 实现。

</div>