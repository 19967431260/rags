网易云信 IM UIKit 是基于 [NIM SDK（网易云信 IM SDK）](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client) 开发的一款即时通讯 UI 组件库，包括聊天、会话、圈组、搜索、通讯录、群管理等组件。

本文主要针对通过 UIKit 直接使用了 IM SDK 底层能力的用户，介绍在 [IM UIKit](https://doc.yunxin.163.com/messaging-uikit/concept/jkyNDc2Mjg?platform=client) 升级过程中需要关注的底层 [IM SDK](https://doc.yunxin.163.com/messaging2/concept/DI0Nzc2NzA?platform=client) 9.x.x 系列和 10.x.x 系列版本之间的区别。

::: note note
若您直接使用 UIKit 的接口，不直接使用底层 SDK 的能力，可以忽略该文档，直接参考 [UIKit 版本区分](https://doc.yunxin.163.com/messaging-uikit/concept/TA1OTcwOTc?platform=client) 进行升级。
:::

<!--
即时通讯 NIM SDK 10.x.x 系列是基于 NIM SDK 9.x.x 系列稳定版的升级版本，于 2024-01-26 发布。它不仅兼容 NIM SDK 9.x.x 系列稳定的接口和功能，提供了一整套即时通讯技术解决方案，包括客户端 IM 组件、客户端 IM 基础库、全平台 SDK 以及服务端 API 等，还支持云端会话、会话分组、IM 圈组融合登录、聊天室独立登录等功能。同时，提供全新的适配鸿蒙系统的 NIM SDK。
-->

## 版本说明

IM SDK 版本号为 1.0.0～9.x.x 都概指 V9 系列版本；版本号为 10.x.x 都代表 V10 系列版本。

两个系列的最新版本号，请参考对应开发平台的更新日志（[V10](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) | [V9](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client)）。

各平台 UIKit 与 SDK 的版本对应关系，请参考 [UIKit 更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/zMzNDI4MDI?platform=client) 中的兼容版本信息。

## 变更说明

IM V9 系列版本和 V10 系列版本的主要变更涉及服务变更和监听变更。

- [服务变更](#服务变更)：各模块服务名称变更。以消息服务的使用为例展开使用说明。
- [监听变更](#监听变更)：将 Observer/Delegate 监听改为设置 Listener 监听。

## 服务变更

**IM SDK 对应版本的核心类服务：**

| 服务名称 | V9 | V10 | 服务说明 |
| --- | --- | --- | --- |
| 消息服务 | NIMMessageService | [V2NIMMessageService](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client) | 云信消息服务接口类，提供消息发送、消息查询、历史消息、消息扩展功能、获取未读数、已读回执、会话列表等相关接口。|
| 好友服务 | FriendService | [V2NIMFriendService](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client) | 好友服务接口类，提供好友管理/好友关系/黑名单关系/消息提醒相关接口。 |
| 用户服务 | UserService | [V2NIMUserService](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client) | 用户资料接口类，提供用户资料相关接口。 |
| 会话服务 | NIMMessageService | [V2NIMConversationService](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client) | 会话服务接口类，提供会话管理，查询、置顶、删除会话等相关接口。 | 
| 群服务 | TeamService | [V2NIMTeamService](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client) | 群组服务接口类，提供群组操作相关接口。 |
| 用户认证服务 | AuthService | [V2NIMLoginService](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client) | 用户认证服务接口类，提供用户登录登出等业务接口。 | 
| 三方推送服务 | MixPushService | MixPushService | 推送服务接口类，三方推送服务目前接入的第三方推送有：小米、华为、魅族、fcm。|
| 系统通知消息服务 | SystemMessageService | - | 通知消息接口类，处理系统通知消息，如好友申请、入群申请、入群邀请等。V10 系列接口对应为 [V2NIMFriendService（好友相关）](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client) 和 [V2NIMTeamService（群相关）](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client)。 | 

**IM SDK 对应版本的辅助类服务：**

| 服务名称 | V9 | V10 | 服务说明 |
| --- | --- | --- | --- |
| 数字人 AI 服务 | - | [V2NIMAIService](https://doc.yunxin.163.com/messaging2/client-apis/TA0NjQ0ODE?platform=client) | 数字 AI 服务接口类。|
| 配置服务 | SettingsService | [V2NIMSettingService](https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client) | 配置服务接口类，提供多端推送、免打扰配置接口。
| 云存储服务 | NosService | [V2NIMStorageService](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client) | 网易云存储服务接口类。|
| 自定义通知服务 | NIMMessageService | [V2NIMNotificationService](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client) | 自定义通知服务接口类。|
| 订阅服务 | EventSubscribeService |  EventSubscribeService | 事件订阅服务接口类。|
| 其他接口服务 | MiscService | MiscService | 其他接口类，提供日志文件上传、SDK 本地缓存、获取云信服务端时间等接口。|

**获取 IM SDK 服务示例代码：**

- Android

:::::: div linked-codes
::: code V10 
```java
NIMClient.getService(V2NIMMessageService::class.java)
```
:::
::: code V9
```java
NIMClient.getService(NIMMessageService::class.java)
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
[NIMSDK.sharedSDK.v2MessageService]
```

**Swift：**

```Swift
NIMSDK.shared().v2MessageService
```
:::
::: code V9
**Objective-C：**

```Objective-C
NIMSDK.sharedSDK.chatManager
NIMSDK.sharedSDK.chatExtendManager
```

**Swift：**

```Swift
NIMSDK.shared().chatManager
NIMSDK.shared().chatExtendManager
```
:::
::::::

## 监听变更

IM V9 系列中：

- Android 通过 Observer 实现监听，每个服务都提供对应的 Observer；
- iOS 通过 Delegate 实现监听。

在 V10 系列中：通过设置 Listener 实现监听，监听接口在对应的服务中。

以常见事件的监听为例：

| 监听事件 | V9 Android | V9 iOS | V10（Android&iOS） 
| --- | --- | --- |
| 消息接收 | [`MsgServiceObserve.observeReceiveMessage`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service_observe.html#a9001f2ba497fd73b076328fc52a40532) | [`NIMChatManagerDelegate.onRecvMessages:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/da7/protocol_n_i_m_chat_manager_delegate-p.html#ad7e5965ba2af93a24e6814a004866965) | [`V2NIMMessageListener.onReceiveMessages`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addmessagelistener) 
| 会话变更 | [`MsgServiceObserve.observeUpdateMySession`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service_observe.html#aad17d90cedaeeae10a2687e2ec5d5a42) | [`NIMConversationManagerDelegate.didUpdateRecentSession`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/dfa/protocol_n_i_m_conversation_manager_delegate-p.html#a75080600489446d539a00ddcc7b4f6a2) | [`V2NIMConversationListener.onConversationChanged`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimconversationlistener) 
| 通讯录好友变更 | [`FriendServiceObserve.observeFriendChangedNotify`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service_observe.html#abe133a60ec2bb5822f9ea14248964a9e) | [`NIMUserManagerDelegate.onFriendChanged:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d1/deb/protocol_n_i_m_user_manager_delegate-p.html#addc2e22868d0ec51410076d6530ef7f2) | [`V2NIMFriendListener.onFriendAdded`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimfriendlistener) 
| 群信息变更 | [`TeamServiceObserver.observeTeamUpdate`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service_observer.html#a48326669f9c3f3161ad29ce8f0ef9a1c) | [`NIMTeamManagerDelegate.onTeamAdded:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/df3/protocol_n_i_m_team_manager_delegate-p.html#a1cf7904ac10714a86a0cbfeb0781daa7) | [`V2NIMTeamListener.onTeamCreated`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimteamlistener) 

**消息接收&标记消息监听示例：**

- Android

:::::: div linked-codes
::: code V10
```java
NIMClient.getService(V2NIMMessageService.class).addMessageListener(new V2NIMMessageListener(){
    // 接收新消息    
    public void onReceiveMessages(List<V2NIMMessage> messages){
    }
    // 标记消息    
    public void onMessagePinNotification(V2NIMMessagePinNotification pinNotification){
    }
});
```
:::
::: code V9
```java
// 接收新消息
NIMClient.getService(MsgServiceObserve.class).observeReceiveMessage(new Observer<List<IMMessage>>() {
  @Override  public void onEvent(List<IMMessage> imMessages) {
  }
},true);

// 消息PIN通知
NIMClient.getService(MsgServiceObserve.class).observeAddMsgPin(new Observer<MsgPinSyncResponseOption>() {
  @Override  public void onEvent(MsgPinSyncResponseOption pinOption) {
  }
},true);
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<V2NIMMessageListener>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.v2MessageService addMessageListener:self];
    }
    return self;
}
// 接收新消息
- (void)onReceiveMessages:(NSArray<V2NIMMessage *> *)messages {    
}
// 标记消息
- (void)onMessagePinNotification:(V2NIMMessagePinNotification *)pinNotification { 
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, V2NIMMessageListener {
    override init() {
        super.init()
        NIMSDK.shared().v2MessageService.add(self)
    }
    // 接收新消息
    func onReceive(_ messages: [V2NIMMessage]) {
        <#code#>
    }
    // 标记消息
    func onMessagePinNotification(_ pinNotification: V2NIMMessagePinNotification) {
        <#code#>
    }
    ...
}
```
:::
::: code V9
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<NIMChatManagerDelegate, NIMChatExtendManagerDelegate>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.chatManager addDelegate:self];
        [NIMSDK.sharedSDK.chatExtendManager addDelegate:self];
    }
    return self;
}
// 接收新消息
- (void)onRecvMessages:(NSArray<NIMMessage *> *)messages {
    
}
// 标记消息
- (void)onNotifyAddMessagePin:(NIMMessagePinItem *)item {
    
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, NIMChatManagerDelegate, NIMChatExtendManagerDelegate {
    override init() {
        super.init()
        NIMSDK.shared().chatManager.add(self)
        NIMSDK.shared().chatExtendManager.add(self)
    }
    // 接收新消息
    func onRecvMessages(_ messages: [NIMMessage]) {
        <#code#>
    }
    // 标记消息
    func onNotifyAddMessagePin(_ item: NIMMessagePinItem) {
        <#code#>
    }
    ...
}
```
:::
::::::

**会话变更监听示例：**

- Android

:::::: div linked-codes
::: code V10
```java
 NIMClient.getService(V2NIMConversationService.class).addConversationListener(new V2NIMConversationListener(){
     // 创建新会话     
     public void onConversationCreated(V2NIMConversation conversation){
     }
     // 会话信息变更     
     public void onConversationChanged(List<V2NIMConversation> conversationList){
     }
    ......
 });
```
:::
::: code V9
```java
// 监听会话创建和变更
NIMClient.getService(MsgServiceObserve.class).observeRecentContact(new Observer<List<RecentContact>>() {
  @Override  public void onEvent(List<RecentContact> recentContacts) {
  }
},true);
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<V2NIMConversationListener>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.v2ConversationService addConversationListener:self];
    }
    return self;
}
// 创建新会话
- (void)onConversationCreated:(V2NIMConversation *)conversation {
}
// 会话信息变更
- (void)onConversationChanged:(NSArray<V2NIMConversation *> *)conversations {
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, V2NIMConversationListener {
    override init() {
        super.init()
        NIMSDK.shared().v2ConversationService.add(self)
    }
    // 创建新会话
    func onConversationCreated(_ conversation: V2NIMConversation) {
        <#code#>
    }
    // 会话信息变更
    func onConversationChanged(_ conversations: [V2NIMConversation]) {
        <#code#>
    }
    ...
}
```
:::
::: code V9
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<NIMConversationManagerDelegate>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.conversationManager addDelegate:self];
    }
    return self;
}
// 创建新会话
- (void)didAddRecentSession:(NIMRecentSession *)recentSession totalUnreadCount:(NSInteger)totalUnreadCount {
    
}
// 会话信息变更
- (void)didUpdateRecentSession:(NIMRecentSession *)recentSession totalUnreadCount:(NSInteger)totalUnreadCount {
    
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, NIMConversationManagerDelegate {
    override init() {
        super.init()
        NIMSDK.shared().conversationManager.add(self)
    }
    // 创建新会话
    func didAdd(_ recentSession: NIMRecentSession, totalUnreadCount: Int) {
        <#code#>
    }
    // 会话信息变更
    func didUpdate(_ recentSession: NIMRecentSession, totalUnreadCount: Int) {
        <#code#>
    }
    ...
}
```
:::
::::::

**好友变更监听示例：**

- Android

:::::: div linked-codes
::: code V10
```java
NIMClient.getService(V2NIMFriendService.class).addFriendListener(new V2NIMFriendListener(){
    // 添加好友通知
    public void onFriendAdded(V2NIMFriend friendInfo){      
     } 
     // 好友信息变更通知
     public void onFriendInfoChanged(V2NIMFriend friendInfo){      
     }
     .....
 });
```
:::
::: code V9
```java
// 好友添加和变更
NIMClient.getService(FriendServiceObserve.class).observeFriendChangedNotify(new Observer<FriendChangedNotify>() {
  @Override  public void onEvent(FriendChangedNotify friendChangedNotify) {
  }
},true);
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<V2NIMFriendListener>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.v2FriendService addFriendListener:self];
    }
    return self;
}
// 添加好友通知
- (void)onFriendAdded:(V2NIMFriend *)friendInfo {
}
// 好友信息变更通知
- (void)onFriendInfoChanged:(V2NIMFriend *)friendInfo {
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, V2NIMFriendListener {
    override init() {
        super.init()
        NIMSDK.shared().v2FriendService.add(self)
    }
    // 添加好友通知
    func onFriendAdded(_ friendInfo: V2NIMFriend) {
        <#code#>
    }
    // 好友信息变更通知
    func onFriendInfoChanged(_ friendInfo: V2NIMFriend) {
        <#code#>
    }
    ...
}
```
:::
::: code V9
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<NIMUserManagerDelegate>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.userManager addDelegate:self];
    }
    return self;
}

// 好友信息变更通知
- (void)onFriendChanged:(NIMUser *)user {
    
}

// 黑名单列表发生变化 (在线)
- (void)onBlackListChanged {
    
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, NIMUserManagerDelegate {
    override init() {
        super.init()
        NIMSDK.shared().userManager.add(self)
    }
    // 好友信息变更通知
    func onFriendChanged(_ user: NIMUser) {
        <#code#>
    }
    // 黑名单列表发生变化 (在线)
    func onBlackListChanged() {
        <#code#>
    }
    ...
}
```
:::
::::::

**群信息变更监听示例：**

- Android

:::::: div linked-codes
::: code V10
```java
 NIMClient.getService(V2NIMTeamService.class).addTeamListener(new V2NIMTeamListener(){
    // 群创建通知
    public void onTeamCreated(V2NIMTeam team){     
     } 
     // 群信息变更
     public void onTeamInfoUpdated(V2NIMTeam team){      
     }
     .....
 });
```
:::
::: code V9
```java
// 群创建和更新
NIMClient.getService(TeamServiceObserver.class).observeTeamUpdate(new Observer<List<Team>>() {
  @Override  public void onEvent(List<Team> teams) {
  }
},true);
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<V2NIMTeamListener>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.v2TeamService addTeamListener:self];
    }
    return self;
}
// 群创建通知
- (void)onTeamCreated:(V2NIMTeam *)team {
    
}
 // 群信息变更
- (void)onTeamInfoUpdated:(V2NIMTeam *)team { 
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, V2NIMTeamListener {
    override init() {
        super.init()
        NIMSDK.shared().v2TeamService.add(self)
    }
    // 群创建通知
    func onTeamCreated(_ team: V2NIMTeam) {
        <#code#>
    }
    // 群信息变更
    func onTeamInfoUpdated(_ team: V2NIMTeam) {
        <#code#>
    }
}
```
:::
::: code V9
**Objective-C：**

```Objective-C
@interface SampleClass : NSObject<NIMTeamManagerDelegate>
@end

@implementation SampleClass
- (instancetype)init
{
    self = [super init];
    if (self) {
        [NIMSDK.sharedSDK.teamManager addDelegate:self];
    }
    return self;
}
// 群创建通知
- (void)onTeamAdded:(NIMTeam *)team {
    
}
 // 群信息变更
- (void)onTeamUpdated:(NIMTeam *)team {
    
}
@end
```

**Swift：**

```Swift
class SampleClass: NSObject, NIMTeamManagerDelegate {
    override init() {
        super.init()
        NIMSDK.shared().teamManager.add(self)
    }
    // 添加好友通知
    func onTeamAdded(_ team: NIMTeam) {
        <#code#>
    }
        // 好友信息变更通知
    func onTeamMemberChanged(_ team: NIMTeam) {
        <#code#>
    }
    ...
}
```
:::
::::::

**注销监听示例：**

- Android

:::::: div linked-codes
::: code V10
```java
NIMClient.getService(MsgServiceObserve::class.java).removeMessageListener(msgListener)
```
:::
::: code V9
```java
NIMClient.getService(MsgServiceObserve.class).observeReceiveMessage(receiveObserver,false);
```
:::
::::::

- iOS

:::::: div linked-codes
::: code V10
**Objective-C：**

```Objective-C
[NIMSDK.sharedSDK.v2MessageService removeMessageListener:msgListener];
```

**Swift：**

```Swift
NIMSDK.shared().v2MessageService.remove(msgListener)
```
:::
::: code V9
**Objective-C：**

```Objective-C
[NIMSDK.sharedSDK.chatManager removeDelegate:self];
[NIMSDK.sharedSDK.chatExtendManager removeDelegate:self];
```

**Swift：**

```Swift
NIMSDK.shared().chatManager.remove(self)
NIMSDK.shared().chatExtendManager.remove(self)
```
:::
::::::

## V10 IM SDK 使用指导

### V10 初始化登录

:::::: div linked-codes
::: code Android
1. 初始化配置 [`SDKOptions`](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_s_d_k_options.html) 中新增 `disableV2Login` 参数，表示是否在开启 V10 API 后，仍使用 V9 的登录 API 登录 IM。

    - 默认 false，即开启 V10 API 后使用 V10 的登录 API 登录 IM。
    - 设置为 true，则开启 V10 API 后仍需要使用 V9 的登录 API 登录 IM。

    ::: note note
    V9 和 V10 版本的登录 API 无法同时使用，只能选择其一。
    :::

    ```java
    // 激活 V10 API 后，可以根据该字段选项选择是否禁用 V10 API 登录，默认 false，即使用 V10 API 登录
    // sdkOptions.disableV2Login = true;
    ...
    // 按需设置其它 SDKOptions 设置项
    NIMClient.initV2(context, sdkOptions);
    ```

2. 使用新的初始化接口 [`NIMClient#initV2`](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#aa8e0e524f223d29e8f2499557a2ae2e5) 进行初始化。

    ```java
    V2NIMLoginOption option = new V2NIMLoginOption();
    //set auth type
    option.setAuthType(V2NIMLoginAuthType.V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN);
    //set auth token provider
    option.setTokenProvider(new V2NIMTokenProvider() {
        @Override
        public String getToken(String accountId) {
            return "return your token with accountId";
        }
    });
    NIMClient.getService(V2NIMLoginService.class).login("accountId",null,option,new V2NIMSuccessCallback<Void>() {
            @Override
            public void onSuccess(Void unused) {
                // TODO
            }
    ```

3. 监听 IM 登录状态。

    登录 IM 成功后，SDK 会自动同步离线消息、漫游消息、用户信息、群信息、系统通知等数据。数据同步完成时，整个登录过程才算真正完成。
    
    调用 [`addLoginDetailListener`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#addLoginDetailListener) 方法注册登录连接状态监听器，包括登录连接状态变化（onConnectStatus）、断开连接（onDisconnected）、连接失败（onConnectFailed）、数据同步状态（onDataSync）。

    ```java
    NIMClient.getService(V2NIMLoginService.class).addLoginDetailListener(new V2NIMLoginDetailListener() {

        @Override
        public void onConnectStatus(V2NIMConnectStatus status) {
            // 链接状态变更
        }
        @Override
        public void onDisconnected(V2NIMError error) {
            // 断开连接
        }
        @Override
        public void onConnectFailed(V2NIMError error) {
            // 链接失败
        }
        @Override
        public void onDataSync(V2NIMDataSyncType type, V2NIMDataSyncState state, V2NIMError error) {
            // 数据同步
        }
    });
    ```

    若需要移除登录监听，可以调用 [`removeLoginListener`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#removeloginlistener) 方法。

    ```java
    NIMClient.getService(V2NIMLoginService.class).removeLoginListener(listener);
    ```

4. 登出 IM。

    一般情况下，如果您的应用生命周期跟 NIM SDK 生命周期一致，用户在退出应用前可以不登出，直接退出即可。
    
    但某些特殊场景，例如用户仅在进入特定界面后才调用 NIM SDK 的能力，退出界面后不再调用，此时需要调用 NIM SDK 的登出接口注销 IM 登录。登出后，用户将不再接收 IM 的消息。用户在登出应用/注销自己的账号时需要调用 [`logout`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout) 方法登出 IM，该方法没有回调。

    ```java
    // 请勿在 Activity 的 `onDestroy` 中调用 `logout` 方法
    NIMClient.getService(V2NIMLoginService.class).logout(new V2NIMSuccessCallback(){
        @Override
        public void onSuccess(){
            // TODO
        }
    }, new V2NIMFailueCallback<V2NIMError>(){
        @Override
        public void onFailure(V2NIMError error){
            int code = error.code;
            String desc = error.desc;
            // TODO
        }
    });
    ```
:::
::: code iOS
1. 初始化配置新增 [`V2NIMSDKOption.useV1Login`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#V2NIMSDKOption) 参数，表示是否在开启 V10 API 后，仍使用 V9 的登录 API 登录 IM。

    - 默认 NO，即开启 V10 API 后需要使用 V10 的登录 API 登录 IM。
    - 设置为 YES，则开启 V10 API 后仍需要使用 V9 的登录 API 登录 IM。

    ::: note note
    V9 和 V10 版本的登录 API 无法同时使用，只能选择其一。
    :::

2. 使用新的初始化接口 [`registerWithOptionV2`](https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a4140971377bec8212dabd66fdea0bbb3) 进行初始化。

    **Objective-C：**

    ```Objective-C
    @interface YourTokenProvider : NSObject <V2NIMTokenProvider>
    @end
    @implementation YourTokenProvider
    - (NSString *)getToken:(NSString *)accountId
    {
        return @"return your token with accountId";
    }
    @end
    - (void)loginWithDynamicToken
    {
        NSString *accountId = @"accountId";
        V2NIMLoginOption *option = [[V2NIMLoginOption alloc] init];
        option.authType = V2NIM_LOGIN_AUTH_TYPE_DYNAMIC_TOKEN; // setup type
        option.tokenProvider = [[YourTokenProvider alloc] init]; // setup provider
        [[NIMSDK sharedSDK].v2LoginService login:accountId token:nil
                option:option
                success:^{
            NSLog(@"login succ");
        }
                failure:^(V2NIMError * _Nonnull error) {
            NSLog(@"login fail: error = %@", error);
        }];
    }
    ```

    **Swift：**

    ```Swift
    class YourTokenProvider: NSObject, V2NIMTokenProvider {
        func getToken(_ accountId: String) -> String? {
            return "return your token with accountId"
        }
    }
    func loginWithDynamicToken() {
        let accountId = "accountId"
        let option = V2NIMLoginOption()
        option.authType = .LOGIN_AUTH_TYPE_DYNAMIC_TOKEN
        option.tokenProvider = YourTokenProvider()
        NIMSDK.shared().v2LoginService.login(accountId, token: nil, option: option) {
            print("login succ")
        } failure: { error in
            print("login fail: error = \(error)")
        }
    }
    ```

3. 监听 IM 登录状态。

    登录 IM 成功后，SDK 会自动同步离线消息、漫游消息、用户信息、群信息、系统通知等数据。数据同步完成时，整个登录过程才算真正完成。
    
    调用 [`addLoginDetailListener`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#addLoginDetailListener) 方法注册登录连接状态监听器，包括登录连接状态变化（onConnectStatus）、断开连接（onDisconnected）、连接失败（onConnectFailed）、数据同步状态（onDataSync）。

    **Objective-C：**

    ```Objective-C
    interface V2NIMLoginServiceSample : NSObject <V2NIMLoginDetailListener>
    @end
    @implementation V2NIMLoginServiceSample
    - (void)listen {
        [[[NIMSDK sharedSDK] v2LoginService] addLoginDetailListener:self];
    }
    - (void)onConnectStatus:(V2NIMConnectStatus)status {
        // Handle connect status
    }
    - (void)onDisconnected:(nullable V2NIMError *)error {
        // Handle disconnected error
    }
    - (void)onConnectFailed:(nullable V2NIMError *)error {
        // Handle connect failed error
    }
    - (void)onDataSync:(V2NIMDataSyncType)type
                state:(V2NIMDataSyncState)state
                error:(nullable V2NIMError *)error {
        // Handle data sync
    }
    @end
    ```

    **Swift：**

    ```Swift
    class V2NIMLoginServiceSample: NSObject, V2NIMLoginDetailListener {
        func listen() {
            NIMSDK.shared().v2LoginService.add(self)
        }
        func onConnectStatus(_ status: V2NIMConnectStatus) {
            // Handle connect status
        }
        func onDisconnected(_ error: V2NIMError?) {
            // Handle disconnected error
        }
        func onConnectFailed(_ error: V2NIMError?) {
            // Handle connect failed error
        }
        func onDataSync(_ type: V2NIMDataSyncType, state: V2NIMDataSyncState, error: V2NIMError?) {
            // Handle data sync
        }
    }
    ```

    若需要移除登录监听，可以调用 [`removeLoginListener`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#removeloginlistener) 方法。

    **Objective-C：**

    ```Objective-C
    [NIMSDK.sharedSDK.v2LoginService removeLoginDetailListener:self];
    ```

    **Swift：**

    ```Swift
    NIMSDK.shared().v2LoginService.remove(self)
    ```

4. 登出 IM 。

    一般情况下，如果您的应用生命周期跟 NIM SDK 生命周期一致，用户在退出应用前可以不登出，直接退出即可。
    
    但某些特殊场景，例如用户仅在进入特定界面后才调用 NIM SDK 的能力，退出界面后不再调用，此时需要调用 NIM SDK 的登出接口注销 IM 登录。登出后，用户将不再接收 IM 的消息。用户在登出应用/注销自己的账号时需要调用 [`logout`]() 方法登出 IM，该方法没有回调。

    **Objective-C：**

    ```Objective-C
    - (void)logout
    {
        [[NIMSDK sharedSDK].v2LoginService logout:^{
            NSLog(@"logout succ");
        } failure:^(V2NIMError * _Nonnull error) {
            NSLog(@"logout fail: error = %@", error);
        }];
    }
    ```
    
    **Swift：**

    ```Swift
    func logout() {
        NIMSDK.shared().v2LoginService.logout {
            print("login succ")
        } failure: { error in
            print("login fail: error = \(error)")
        }
    }
    ```
:::
::::::

### V10 消息服务使用

以消息服务为例，介绍 IM V10 系列如何使用核心服务，实现消息收发。有关其他消息发送实现方式，请参考 [消息收发](https://doc.yunxin.163.com/messaging2/guide/DYzMjA0Njc?platform=client)。

:::::: div linked-codes
::: code Android
1. 设置消息监听，在监听中接收消息。

    ```java
    V2NIMMessageService v2MessageService = NIMClient.getService(V2NIMMessageService.class);
    V2NIMMessageListener messageListener = new V2NIMMessageListener() {
        @Override
        public void onSendMessage(V2NIMMessage message) {
            // 消息发送状态回调，消息发送中，发送失败或者成功都在这里回调
        }
        @Override
        public void onReceiveMessages(List<V2NIMMessage> messages) {
            // 接受消息
            //messages.get(0).getConversationId() 消息所在的会话ID，所有接受的消息都在这里回调
            // messages.get(0).getAttachment() 消息附件，自定义内容自行解析，SDK支持的消息自动转换
        }
        @Override
        public void onReceiveP2PMessageReadReceipts(List<V2NIMP2PMessageReadReceipt> readReceipts) {
        }
        @Override
        public void onReceiveTeamMessageReadReceipts(List<V2NIMTeamMessageReadReceipt> readReceipts) {
        }
        @Override
        public void onMessageRevokeNotifications(List<V2NIMMessageRevokeNotification> revokeNotifications) {
        }
        @Override
        public void onMessagePinNotification(V2NIMMessagePinNotification pinNotification) {
        }
        @Override
        public void onMessageQuickCommentNotification(V2NIMMessageQuickCommentNotification quickCommentNotification) {
        }
        @Override
        public void onMessageDeletedNotifications(List<V2NIMMessageDeletedNotification> messageDeletedNotifications) {
        }
        @Override
        public void onClearHistoryNotifications(List<V2NIMClearHistoryNotification> clearHistoryNotifications) {
        }
    };
    v2MessageService.addMessageListener(messageListener);
    ```

2. 构建消息。

    发送消息之前，需要先构建需要发送的消息对象，包括文本消息、图片消息、视频消息、自定义消息等。

    ```java
    // 创建文本消息
    V2NIMMessage v2TextMessage = V2NIMMessageCreator.createTextMessage("text content");
    // 创建一条图片消息
    V2NIMMessage v2ImageMessage = V2NIMMessageCreator.createImageMessage(imagePath, name, sceneName, width, height);
    // 创建一条文件消息
    V2NIMMessage v2FileMessage = V2NIMMessageCreator.createFileMessage(filePath, name, sceneName);
    // 创建一条自定义消息
    V2NIMMessage v2CustomMessage = V2NIMMessageCreator.createCustomMessage(text, rawAttachment);
    ```
3. 发送一条消息，以文本消息为例。

    ```java
    // 获取消息Service
    V2NIMMessageService v2MessageService = NIMClient.getService(V2NIMMessageService.class);
    // 创建一条文本消息
    V2NIMMessage v2Message = V2NIMMessageCreator.createTextMessage("xxx");
    // 要发送消息的会话ID
    String conversationId = ""；
    // 发送消息
    v2MessageService.sendMessage(v2Message, conversationId, null,
            new V2NIMSuccessCallback<V2NIMSendMessageResult>() {
                @Override
                public void onSuccess(V2NIMSendMessageResult v2NIMSendMessageResult) {
                    // TODO: 发送成功
                }
            },
            new V2NIMFailureCallback() {
                @Override
                public void onFailure(V2NIMError error) {
                    // TODO: 发送失败
                }
            },
            new V2NIMProgressCallback() {
                @Override
                public void onProgress(int progress) {
                    // TODO: 发送进度
                }
            });
    ```
:::
::: code iOS
1. 设置消息监听，在监听中接收消息。

    **Objective-C:**

    ```Objective-C
    @interface SampleClass : NSObject<V2NIMMessageListener>
    @end

    @implementation SampleClass
    - (instancetype)init
    {
        self = [super init];
        if (self) {
            [NIMSDK.sharedSDK.v2MessageService addMessageListener:self];
        }
        return self;
    }
    - (void)onSendMessage:(nonnull V2NIMMessage *)message {
        // 消息发送状态回调，消息发送中，发送失败或者成功都在这里回调
    }
    - (void)onReceiveMessages:(nonnull NSArray<V2NIMMessage *> *)messages {
        // 接受消息
        [[messages firstObject] conversationId];    // 消息所在的会话ID，所有接受的消息都在这里回调
        [[messages firstObject] attachment ];   //消息附件，自定义内容自行解析，SDK支持的消息自动转换
    }
    - (void)onReceiveMessagesModified:(nonnull NSArray<V2NIMMessage *> *)messages { 
        <#code#>
    }
    - (void)onReceiveP2PMessageReadReceipts:(nonnull NSArray<V2NIMP2PMessageReadReceipt *> *)readReceipts { 
        <#code#>
    }
    - (void)onReceiveTeamMessageReadReceipts:(nonnull NSArray<V2NIMTeamMessageReadReceipt *> *)readReceipts { 
        <#code#>
    }
    - (void)onClearHistoryNotifications:(nonnull NSArray<V2NIMClearHistoryNotification *> *)clearHistoryNotification {
        <#code#>
    }
    - (void)onMessageDeletedNotifications:(nonnull NSArray<V2NIMMessageDeletedNotification *> *)messageDeletedNotification {
        <#code#>
    }
    - (void)onMessagePinNotification:(nonnull V2NIMMessagePinNotification *)pinNotification {
        <#code#>
    }
    - (void)onMessageQuickCommentNotification:(nonnull V2NIMMessageQuickCommentNotification *)notification {
        <#code#>
    }
    - (void)onMessageRevokeNotifications:(nonnull NSArray<V2NIMMessageRevokeNotification *> *)revokeNotifications {
        <#code#>
    }
    @end
    ```
    
    **Swift:**

    ```Swift
    class SampleClass: NSObject, V2NIMMessageListener {
        override init() {
            super.init()
            NIMSDK.shared().v2MessageService.add(self)
        }
        func onSend(_ message: V2NIMMessage) {
            // 消息发送状态回调，消息发送中，发送失败或者成功都在这里回调
        }
        func onReceive(_ messages: [V2NIMMessage]) {
            // 接受消息
            let message = messages.first
            message?.conversationId // 消息所在的会话ID，所有接受的消息都在这里回调
            message?.attachment //消息附件，自定义内容自行解析，SDK支持的消息自动转换
        }
        func onReceive(_ readReceipts: [V2NIMP2PMessageReadReceipt]) {
            <#code#>
        }
        func onReceive(_ readReceipts: [V2NIMTeamMessageReadReceipt]) {
            <#code#>
        }
        func onReceiveMessagesModified(_ messages: [V2NIMMessage]) {
            <#code#>
        }
        func onMessageRevokeNotifications(_ revokeNotifications: [V2NIMMessageRevokeNotification]) {
            <#code#>
        }
        func onMessagePinNotification(_ pinNotification: V2NIMMessagePinNotification) {
            <#code#>
        }
        func onMessageQuickCommentNotification(_ notification: V2NIMMessageQuickCommentNotification) {
            <#code#>
        }
        func onMessageDeletedNotifications(_ messageDeletedNotification: [V2NIMMessageDeletedNotification]) {
            <#code#>
        }
        func onClearHistoryNotifications(_ clearHistoryNotification: [V2NIMClearHistoryNotification]) {
            <#code#>
        }
    }
    ```

2. 构建消息。

    发送消息之前，需要先构建需要发送的消息对象，包括文本消息、图片消息、视频消息、自定义消息等。

    **Objective-C:**

    ```Objective-C
    // 创建文本消息
    V2NIMMessage *v2Message = [V2NIMMessageCreator createTextMessage：@"hello world"];
    // 创建一条图片消息。
    NSString *imagePath = @ "文件沙盒路径";
    V2NIMMessage *message = [V2NIMMessageCreator createImageMessage:imagePath
                                                            name:@"imageName"
                                                        sceneName:@"nim_default_im"
                                                            width:200
                                                            height:200];                                                             
    // 创建一条文件消息。
    NSString *filePath = @"文件沙盒路径";
    V2NIMMessage *message = [V2NIMMessageCreator createFileMessage:filePath
                                                            name:@"name"
                                                        sceneName:@"nim_default_im"];
    // 创建一条自定义消息
    V2NIMessage *message = [V2NIMMessageCreator createCustomMessage:@"text"
                                                    rawAttachment:@"custoom JSON String"];
    ```
    
    **Swift:**

    ```Swift
    // 创建文本消息
    let v2Message = V2NIMMessageCreator.createTextMessage("hello world")
    // 创建一条图片消息。
    let imagePath = "文件沙盒路径"
    let message = V2NIMMessageCreator.createImageMessage(imagePath, name: "imageName", sceneName: "nim_default_im", width: 200, height: 200)
    // 创建一条文件消息。
    let filePath = "文件沙盒路径"
    let message = V2NIMMessageCreator.createFileMessage(filePath, name: "name", sceneName: "nim_default_im")
    // 创建一条自定义消息
    let message = V2NIMMessageCreator.createCustomMessage("text", rawAttachment: "custoom JSON String")
    ```

3. 发送一条消息，以文本消息为例。

    **Objective-C:**

    ```Objective-C
    V2NIMMessage *v2Message = [[V2NIMMessage alloc] init];
    V2NIMSendMessageParams *sendParams = [[V2NIMSendMessageParams alloc] init];
        [NIMSDK.sharedSDK.v2MessageService sendMessage:v2Message conversationId:@"conversationId" params:sendParams success:^(V2NIMSendMessageResult * _Nonnull result) {
            // 成功回调
        } failure:^(V2NIMError * _Nonnull error) {
            // 失败回调
        } progress:^(NSUInteger) {
            // 进度
        }];
    }];
    ```
    
    **Swift:**

    ```Swift
    let v2Message = V2NIMMessageCreator.createTextMessage("hello world")
    let sendParams = V2NIMSendMessageParams()
    NIMSDK.shared().v2MessageService.send(v2Message, conversationId: "conversationId", params: sendParams) { <#V2NIMSendMessageResult#> in
        // 成功回调
    } failure: { error in
        // 失败回调
    } progress: { progress in
        // 进度
    }
    ```
:::
::::::