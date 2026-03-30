IM UIKit 的会话模块（`nim_chatkit_ui`）的 `ChatUIConfig` 提供会话界面 UI 的自定义配置项，助您快速实现该界面的 UI 个性化定制。

::: note notice
请确保在会话界面加载之前完成该界面的 UI 自定义。
:::

## 功能介绍

### 可自定义元素

会话界面可自定义的 UI 元素包括但不限于下图中的标注项。

![会话消息界面.png](https://yx-web-nosdn.netease.im/common/d822b5dabd2830bf368f9e0b1107c1f2/会话消息界面.png)

### 自定义配置项

`ChatUIConfig` 配置项具体说明如下：

属性 | 类型 | 说明
---- | ---- | ----
`receiveMessageBg` | BoxDecoration | 他人发送消息内容的背景装饰器。
`selfMessageBg` | BoxDecoration | 自己发送消息内容的背景装饰器。
`userNickColor` | Color | 不设置头像的用户所展示的文字头像中的文字颜色。
`userNickTextSize` | double | 不设置头像的用户所展示的文字头像中的文字字体大小。
`messageTextColor` | Color | 文本消息字体颜色。
`messageTextSize` | double | 文本消息字体大小。
`avatarCornerRadius` | double | 头像的圆角，0 代表方形，16 为圆形。
`timeTextSize` | double | 消息列表中，时间字体大小。
`timeTextColor` | Color | 消息列表中，时间字体颜色。
`signalBgColor` | Color | 被标记消息的背景色。
`showP2pMessageStatus` | bool | 单聊中是否展示已读未读状态。
`showTeamMessageStatus` | bool | 群聊中是否展示已读未读状态。
`enableMessageLongPress` | bool | 长按弹框功能开关。
`popMenuConfig` | PopMenuConfig | 长按弹框配置，详见下文的 **PopMenuConfig 弹框配置项说明**。
`keepDefaultMoreAction` | bool | 保留默认的更多面板按钮。
`moreActions` | List\<ActionItem> | 更多面板自定义按钮，详见下文的 **ActionItem 更多按钮配置项说明**。 
`keepDefaultInputAction` | bool | 保留默认的输入框功能按钮，默认为 true。
`inputActions` | List\<ActionItem> | 自定义输入框功能按钮，详见下文的 **ActionItem 更多按钮配置项说明**。
`messageBuilder` | ChatKitMessageBuilder | 自定义消息构建，详见下文的 **ChatKitMessageBuilder 自定义消息构建配置项说明**。 
`messageClickListener` | MessageClickListener | 消息点击事件，详见 [会话消息事件监听](https://doc.yunxin.163.com/messaging-uikit/guide/Dk3OTA4OTA?platform=flutter)。
`getPushPayload` | Map\<String, dynamic> Function(NIMMessage message) | 设置推送 payload 的回调方法，会在消息发送前调用。
`imagePlaceHolder` | Widget Function(double aspectRatio, {double? width})?  | 设置图片消息显示的预占位图。
`maxVideoSize` | int | 视频消息最大 size 单位 M，不设置默认为 200。
`maxFileSize` | int | 文件消息最大 size 单位 M，不设置默认为 200。
`locationProvider` | ChatKitLocationProvider | 定位消息提供者，接入地理位置消息时使用。
`onTapAitLink` |  Function(String account, String text) | 被@的消息点击回调。

- `PopMenuConfig` 弹框配置项说明

属性 | 类型 | 说明
---- | ---- | ----
`enableForward` | bool | 转发。
`enableCopy` | bool | 复制。
`enableReply` | bool | 回复。
`enablePin` | bool | Pin。
`enableDelete` | bool | 删除。
`enableRevoke` | bool | 撤回。

- `ActionItem` 更多按钮配置项说明

属性 | 类型 | 说明
---- | ---- | ----
`type` | String | 按钮类型。
`icon` | Widget | 按钮图标。
`title` | String | 按钮标题。
`onTap` | Function(BuildContext context) | 按钮点击事件。
`permissions` | List\<Permission> | 按钮点击需要请求的权限。
`deniedTip` | String | 权限拒绝后的提示。

- `ChatKitMessageBuilder` 自定义消息构建配置项说明

属性 | 类型 | 说明
---- | ---- | ----
`textMessageBuilder` | ChatMessageItemBuilder | 文案类型消息构建。
`audioMessageBuilder` | ChatMessageItemBuilder |  音频类型消息构建。
`imageMessageBuilder` | ChatMessageItemBuilder |  图片类型消息构建。
`videoMessageBuilder` | ChatMessageItemBuilder |  视频类型消息构建。
`tipsMessageBuilder` | ChatMessageItemBuilder |  提醒类型消息构建。
`fileMessageBuilder` | ChatMessageItemBuilder |  文件类型消息构建。
`locationMessageBuilder` | ChatMessageItemBuilder |  位置类型消息构建。
`extendBuilder` | Map\<NIMMessageType, ChatMessageItemBuilder?> |  自定义类型消息构建。

::: note notice
所有类型的消息构建都会覆盖掉对应类型的默认消息组件。
:::

<br>

::: note note
关于自定义消息的详细内容，请参见 [实现自定义消息收发](https://doc.yunxin.163.com/messaging-uikit/guide/TE0MjMwMTI?platform=flutter)。
:::
  
## 自定义方式

您可通过两种方式自定义会话界面的 UI 样式，即单实例全局自定义和单界面自定义。

### 单实例全局自定义

假设您的应用有多个会话界面，则通过 `ChatUIConfig` 的配置项进行全局自定义后，自定义配置在单个实例全局生效，所有会话界面都将按自定义的 UI 样式进行展示。

示例代码如下：

```dart
// 设置ChatKitClient的chatUIConfig
ChatKitClient.instance.chatUIConfig = ChatUIConfig(
  // 设置接收消息的背景
  receiveMessageBg: BoxDecoration(
    color: Colors.amberAccent,
  ),
  // 头像的圆角
  avatarCornerRadius: 5,
);
```

### 单界面自定义

通过 `ChatUIConfig` 的配置项，可对单个会话界面进行 UI 样式自定义。 

::: note notice
该种方式优先级大于全局配置方式。换而言之，如果在单实例全局自定义后在进行单界面自定义，则后者的配置会覆盖前者的。
:::

示例代码如下：

```dart
ChatPage(
  conversationId: 'conversationId',
  conversationType: NIMConversationType.p2p,
  // 设置ChatPage页面的config参数
  chatUIConfig: ChatUIConfig(
    // 设置接收消息的背景
    receiveMessageBg: BoxDecoration(
      color: Colors.amberAccent,
    ),
    // 头像的圆角
    avatarCornerRadius: 5,
  ),
)
```

## 示例

### 设置消息 Item

- 假设您需要标记消息背景色、已读未读状态等。

  - 示例代码

    ```dart
    ChatUIConfig(
      // 设置标记消息背景色，见图一
      signalBgColor: Colors.yellowAccent,
      // 消息已读未读状态，见图二
      showP2pMessageStatus: true,
      showTeamMessageStatus: true,
    );
    ```

  - UI 效果

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/e8f5710e0f8fb7ff1b15677d709446ba/被标记消息的背景色.PNG" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/fc1e9ba530605e407b15324e200b6c18/Flutter已读未读状态.png" style="width:80%;border: 1px solid #BFBFBF;">

- 假设您需要修改消息背景色，头像圆角，消息字体，时间字体等。

  - 示例代码

    ```dart
    ChatUIConfig(
      // 设置接收消息的背景
      receiveMessageBg: BoxDecoration(
        color: Colors.amberAccent,
        borderRadius: const BorderRadius.only(
          topRight: Radius.circular(12),
          bottomLeft: Radius.circular(12),
          bottomRight: Radius.circular(12)),
      ),
      // 头像圆角
      avatarCornerRadius: 16,
      // 消息字体颜色和大小
      messageTextColor: Colors.green,
      messageTextSize: 20,
      // 时间字体颜色和大小
      timeTextColor: Colors.black,
      timeTextSize: 16,
    );
    ```

  - UI 效果

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/9bea758f4f6dd6f957c1fb14ea8c1e79/消息默认.jpg" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/1e29a1b83eb50669a3c2079cb8c89b04/消息自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

### 设置长按弹窗

通过对 `PopMenuConfig` 的配置，可以控制消息长按弹窗中的显示项。

假设您需要隐藏转发按钮。

- 示例代码

  ```dart
  ChatUIConfig(
    popMenuConfig: PopMenuConfig(
      // 不显示转发
      enableForward: false,
    ),
  );
  ```

- UI 效果

    默认 | 自定义后
    ---- | ----
    <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/f1698fcd81d2e73d6e9add455cdca8b6/消息弹窗默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="conversation_01_resized.png" src="https://yx-web-nosdn.netease.im/common/de7ba135b52b83cc3069496119f21309/消息弹窗.png" style="width:80%;border: 1px solid #BFBFBF;">

### 设置更多面板的自定义按钮

通过配置 `moreActions` 来给更多面板添加自定义按钮，同时，如果您不需要展示原本的默认按钮，那可以将 `keepDefaultMoreAction` 设置为 false。

例如，添加一个发送自定义消息的按钮，示例代码如下：

```dart
ChatKitClient.instance.chatUIConfig.moreActions = [
      ActionItem(
          type: 'custom',
          icon: Icon(Icons.android_outlined),
          title: "自定义",
          onTap: (BuildContext context, String conversationId,
              NIMConversationType sessionType,
              {NIMMessageSender? messageSender}) async {
            var msg = await MessageCreator.createCustomMessage('自定义消息', '');
            if (msg.isSuccess && msg.data != null) {
              Fluttertoast.showToast(msg: '发送自定义消息！ ');
              messageSender?.call(msg.data!);
            }
          }),
    ];
```

效果如下图所示：

<img style="width:50%" src="https://yx-web-nosdn.netease.im/common/63bd0964ac2a99be56fb64ea1099db4f/更多面板按钮.png"/>