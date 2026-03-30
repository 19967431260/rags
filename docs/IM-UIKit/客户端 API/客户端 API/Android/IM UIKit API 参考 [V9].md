<!--keywords: 接口,API,UIKit,demo,IM UIKit,IMUIKit,Kit -->



IM UIKit 提供一套包含 UI 的IM 接入方式。在 UIKit 中我们对业务场景使用到的 IM SDK 的接口封装成业务数据能力层，将复杂的数据关联调用精简成一次接口调用，减少上层业务的复杂性。本文概要性介绍业务数据能力层的接口。

本文提供 IM UIKit API 的概览性介绍。

## 核心类

* `IMKitClient` 提供初始化、登录等功能能力接口。
* `ContactRepo` 提供通讯录模块使用的数据能力接口，包括查询好友列表、黑名单等。
* `ConversationRepo` 提供会话列表模块使用的数据能力接口，包括查询会话列表、置顶、删除等接口。
* `ChatMessageRepo` 提供会话详情页模块使用的数据能力接口，包括发送消息、删除消息等接口。
* `SearchRepo` 提供搜索模块使用的数据能力接口。
* `TeamRepo` 提供群组模块相关的数据能力接口。
* `SettingRepo` 提供全局设置接口。


<div hidden="hidden">## Provider   这部分后面需要补充</div>


## 核心方法


方法/属性 | 功能 | 描述
:---- | :-------------- | :---------
init | 初始化接口 | 需要在功能使用之前，进行初始化。不需要额外调用SDK的初始化方法
config | 配置接口 | 一般用于隐私合规的时候，分步初始化，与`initSDk`配合使用
initSDK | 初始化接口 | 一般用于隐私合规的时候，分步初始化，与`config`配合使用
getSDKLifecycleObserver | 获取SDK生命周期观察者 | 获取之后可以注册SDK生命周期的监听器
getAuthServiceObserver | 获取用户认证服务观察者 | 获取之后可以注册客户认证的监听器
getApplicationContext | 获取`ApplicationContext` | 初始化之后可使用
getStatus | 获取登录状态 | 用于判断当前账号的状态信息，包括是否登录、被其他端踢掉等
getLoginMode | 获取当前登录模式 | 返回登录模式状态码，包括初始化状态、IM登录状态等
toggleNotification | 通知栏提醒开关控制 | 只有`StatusBarNotificationConfig`配置不为空时才有效
toggleRevokeMessageNotification | 设置撤回消息是否需要提醒 | 只有`StatusBarNotificationConfig`配置不为空，并且通知栏提醒开关是打开的才有效。 默认打开
updateStatusBarNotificationConfig | 更新状态栏通知提醒设置 | 消息通知样式等
getSDKVersion | 运行时获取当前 SDK 版本号 | 返回例如 "9.2.0"
registerMixPushMessageHandler | 注册第三方推送消息接收handler | 在初始化`init`接口前调用
loginIM | 登录IM账号 | 如果在`init`接口中传入账号信息，则不需要再进行单独登录
logoutIM | 登出IM账号 | 登出接口
setUserInfoDelegate | 设置用户数据代理 | 设置IM用户数据获取代理，如果您需要自己实现用户数据信息，那边可以使用该代理，IMUIKit里面所有的用户数据都会通过代理来获取。相关文档请参见[自定义用户信息](https://doc.yunxin.163.com/messaging-uikit/docs/jEzNjIxODM?platform=android)

<!--keywords: 会话, 消息, 会话消息， API，UIKit,demo,IM UIKit,IMUIKit,Kit -->



会话消息模块分为`ChatKit-ui`和`ChatKit`两层设计，其中`ChatKit-ui`提供会话消息页面相关的 UI 和交互逻辑，`ChatKit`是对会话相关业务能力的封装，向 UI 层提供业务数据聚合接口和 NIM SDK 接口的封装。相较于 NIM SDK 的接口，`ChatKit` 的接口拥有更好的业务聚合性，更方便您实现 UI 层的展示和操作。 



## 会话消息相关


`ChatKit` 模块下的`ChatMessageRepo`类，提供操作/配置会话消息相关的接口和属性。其中获取会话消息的方法和示例代码如下：

```java
//获取会话消息的接口
ChatMessageRepo.getHistoryMessage(...);
```

### ChatMessageRepo 说明

`ChatMessageRepo`类的方法/属性说明如下：

<div style="width:150px">方法/属性</div> | <div style="width:180px">功能</div> | <div style="width:180px">描述</div>
:---- | :-------------- | :---------
getHistoryMessage | 从本地数据库获取一个会话里某条消息之前的若干条的消息 |参数如下<br><div><ul><li>`anchor`：消息查询的锚点</li><li>`direction`：消息查询的方向，类型`QueryDirectionEnum`</li><li>`limit`：个数限制</li><li>`callback`：查询结果回调，类型`FetchCallback<List<IMMessageInfo>>`</li></ul></div>
fetchHistoryMessage | 从服务端获取一个会话里某条消息之前的若干条的消息 |参数如下<br><div><ul><li>`anchor`：消息查询的锚点</li><li>`toTime`：消息查询的截止时间，类型 Long</li><li>`limit`：个数限制</li><li>`direction`：消息查询的方向，类型`QueryDirectionEnum`</li><li>`callback`：查询结果回调，类型`FetchCallback<List<IMMessageInfo>>`</li></ul></div>
fetchTeamMessageReceiptDetail | (群消息发送方)查询单条群组消息已读、未读账号列表 |参数如下<br><div><ul><li>`message`：要查询账号列表对应的消息</li><li>`callback`：查询结果回调，类型`FetchCallback<TeamMsgAckInfo>`</li></ul></div>
setChattingAccount | 设置当前聊天的账号 |参数如下<br><div><ul><li>`account`：当前聊天的账号ID（`accid`）或者群组ID</li><li>`sessionType`：会话类型`SessionTypeEnum`</li></ul></div>
clearChattingAccount | 清除设置的当前聊天账号信息 |无
setCustomAttachParser | 注册自定义消息数据解析器 |参数如下<br><div><ul><li>`parser`：需自实现的消息解析器，类型为`MsgAttachmentParser`</li></ul></div>
sendMessage | 发送消息 |参数如下<br><div><ul><li>`message`消息对象</li><li>`resend`：发送失败后是否重发，true：重发，false：不重发</li><li>`callback`：发送结果回调，类型`FetchCallback`</li></ul></div>
replyMessage | 回复消息 |参数如下<br><div><ul><li>`msg`：消息对象，类型`IMMessage`</li><li>`replyMsg`：被回复的消息对象</li><li>`resend`：发送失败后是否重发，true：重发，false：不重发</li><li>`callback`:发送结果回调，类型`FetchCallback`</li></ul></div>
sendCustomNotification | 发送自定义通知 |参数如下<br><div><ul><li>`notification`自定义通知，类型为`CustomNotification`</li></ul></div>
sendTeamTipWithoutUnread | 发送群组提示消息，该消息不包含未读状态信息 |参数如下<br><div><ul><li>`sessionId`：会话 ID (如会话为单聊类型，则为聊天对象的`accid`，如为群聊类型，则为群 ID，即`teamId`)，类型为`String`</li><li>`map`扩展参数，可用于传递信息内容，类型为`Map<String, Object>`</li><li>`notify`是否需要通知，类型为`Boolean`,默认为true</li><li>`callback`:下载结果回调，类型`FetchCallback`</li></ul></div>
markP2PMessageRead | 设置单聊中消息为已读状态 |参数如下<br><div><ul><li>`sessionId`：会话ID</li><li>`message`：设置已读状态的消息对象</li></ul></div>
markTeamMessageRead | 设置群组消息为已读状态 |参数如下<br><div><ul><li>`messages`：需要刷新的消息对象列表，类型为`List<IMMessage>`</li></ul></div>
refreshTeamMessageReceipt | (群消息发送方)批量刷新群组消息已读、未读的数量信息 |参数如下<br><div><ul><li>`message`：消息对象，类型`IMMessage`</li></ul></div>
deleteMessage | 删除消息 |参数如下<br><div><ul><li>`message`：消息对象，类型`IMMessage`</li></ul></div>
revokeMessage | 撤回消息 |参数如下<br><div><ul><li>`message`：消息对象，类型`IMMessage`</li></ul></div>
downloadAttachment | 下载消息附件 |参数如下<br><div><ul><li>`message`：消息对象，类型`IMMessage`</li><li>`thumb`：下载缩略图还是原文件。`Boolean`类型为true时，仅下载缩略图</li><li>`callback`:下载结果回调，类型`FetchCallback`</li></ul></div>
queryRoamMsgTimestamps | 查询漫游消息时间戳，离线状态下收到消息有数量限制，如果超过限制，则需要根据该方法判断是否需要从远端拉取消息 | 参数如下<br><div><ul><li>`sessionId`：当前会话ID</li><li>`sessionType`：会话类型，类型为`SessionTypeEnum`</li><li>`callback`：下载结果回调，类型`FetchCallback`</li></ul></div>
updateRoamMsgTimestamps | 更新漫游消息时间戳，具体用法参考后续补充漫游消息拉取逻辑文档 | 参数如下<br><div><ul><li>`newTag`：消息对象，类型`IMMessage`</li></ul></div>
addStickTop | 添加置顶会话| 参数如下<br><div><ul><li>`accId`：会话ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li><li>`ext`：操作扩展参数，类型String</li><li>`callback`：操作结果回调，类型`FetchCallback`</li></ul></div>
removeStickTop | 移除置顶会话| 参数如下<br><div><ul><li>`accId`：会话ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li><li>`ext`:操作扩展参数，类型String</li><li>`callback`:操作结果回调，类型`FetchCallback`</li></ul></div>
isTopStick | 是否是置顶会话| 参数如下<br><div><ul><li>`accId`：会话ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li></ul></div>
isNeedNotify | 是否打开消息提醒| 参数如下<br><div><ul><li>`accId`：会话ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li></ul></div>
setNotify | 打开或关闭消息提醒| 参数如下<br><div><ul><li>`accId`：会话 ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li><li>`notify`：是否需要通知。Boolean类型，为 true 时，打开通知</li><li>`callback`：操作结果回调，类型`FetchCallback`</li></ul></div>
getFriendInfo | 从本地获取好友的用户资料| 参数如下<br><div><ul><li>`accId`：用户id</li></ul></div>
queryTeamMemberList | 获取单个群成员信息| 参数如下<br><div><ul><li>`teamId`：群组 ID</li><li>`callback`：查询结果回调，类型`FetchCallback<List<UserInfoWithTeam>>`</li></ul></div>
searchMessage | 搜索本地会话内消息| 参数如下<br><div><ul><li>`keyword`：搜索关键字，类型 String </li><li>`sessionType`：会话类型，类型为`SessionTypeEnum`</li><li>`sessionId`：会话ID。如会话为单聊类型，则为聊天对象的`accid`。如为群聊类型，则为群 ID，即`teamId`</li><li>`callback`：搜索结果回调，类型`FetchCallback<List<IMMessageRecord>>`</li></ul></div>

collectMessage | 添加一个收藏| 参数如下<br><div><ul><li>`message`：需添加收藏的消息，类型`IMMessage`</li><li>`callback`：收藏结果回调，类型`FetchCallback<CollectInfo>`</li></ul></div>
addMessagePin | 添加一条PIN记录| 参数如下 <br><div><ul><li>`message`：需要 PIN 的消息，类型`IMMessage`</li><li>`ext`：操作扩展参数，类型 String</li><li>`callback`收藏结果回调，类型`FetchCallback<Long>`</li></ul></div>
removePin | 删除一条PIN记录| 参数如下 <br><div><ul><li>`message`：需要 PIN 的消息，类型`IMMessage`</li><li>`ext`：操作扩展参数，类型 String</li><li>`callback`：收藏结果回调，类型`FetchCallback<Long>`</li></ul></div>
registerShowNotificationWhenRevokeFilter | 注册是否在撤回消息时展示通知的过滤器 | 参数如下 <br><div><ul><li>`filter`：通知消息过滤器，类型`ShowNotificationWhenRevokeFilter`</li></ul></div>

<!--keywords: 通讯录, API，UIKit,demo,IM UIKit,IMUIKit,Kit -->



通讯录模块分为`ContactKit-ui` 和 `ContactKit`两层设计，其中`ContactKit-ui`提供通讯录界面相关的 UI 和交互逻辑，`ContactKit`是对通讯录相关业务能力的封装，向 UI 层提供业务数据聚合接口和 NIM SDK 接口的封装。



## 通讯录相关

`ContactKit`模块的`ContactRepo`类提供操作/配置通讯录列表的相关方法和属性。其中调用通讯录列表查询接口的示例代码如下：

```java
//查询通讯录接口
ContactRepo.getContactList(...);
```
### ContactRepo 说明

`ContactRepo`类所提供的其他方法/属性的说明如下：

<div style="width:140px">方法/属性</div> | <div style="width:180px">功能描述</div> | 参数
:---- | :-------------- |:---------
getContactList | 获取通讯录列表数据 | 参数如下<br><div><ul><li>`callback`：查询结果回调，类型`FetchCallback<List<FriendInfo>>`</li></ul></div>
getFriendList | 获取我的好友列表信息 | 无
getFriend | 根据账号ID （`accid`）查询对应的好友信息 | 参数如下<br><div><ul><li>`account`：待查询好友的账号ID （`accid`），类型`String`</li></ul></div>
getBlackList | 获取黑名单列表 | 参数如下<br><div><ul><li>`callback`：查询结果回调，类型`FetchCallback<List<UserInfo>>`</li></ul></div>
updateAlias | 更新好友昵称 | 参数如下<br><div><ul><li>`account`:需修改昵称的好友的账号ID （`accid`），类型`String`, alias: String</li><li>`alias`要修改的昵称，类型`String`</li></ul></div>
addFriend | 添加好友 | 参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li><li>`type`：添加方式，直接添加、验证添加等，类型为`FriendVerifyType`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
acceptAddFriend | 同意添加好友申请 |参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li><li>`agree`：是否同意添加为好友，类型为`Boolean`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
isFriend | 是否为好友关系，返回boolean，true 代表是好友关系|参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li></ul></div>
deleteFriend | 删除好友 | 参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
removeBlacklist | 将该用户从黑名单中移除 | 参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
addBlacklist | 添加用户到黑名单 | 参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
isBlackList | 是否在黑名单中，返回`Boolean`，true 代表在黑名单|参数如下<br><div><ul><li>`account`：账号ID （`accid`），类型`String`</li></ul></div>
getUserInfo | 获取用户信息，根据accountId（accid），从应用服务端拉取用户信息|参数如下<br><div><ul><li>`accountList`：账号ID （`accid`）列表，类型` List<String>`</li><li>`callback`：结果回调，类型`FetchCallback<List<UserInfo>>`</li></ul></div>
updateNickName | 修改自己的昵称 | 参数如下<br><div><ul><li>`name`：昵称，类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
getTeamList | 获取我的群组列表 |  参数如下<br><div><ul><li>`callback`：结果回调，类型`FetchCallback<List<Team>>`</li></ul></div>
queryTeamList | 查询群组信息 | 参数如下<br><div><ul><li>`teamIdList`：群ID列表，类型` List<String>`</li><li>`callback`：结果回调，类型`FetchCallback<List<Team>>`</li></ul></div>
agreeTeamApply | 同意入群申请 | 参数如下<br><div><ul><li>`teamId`：群ID，类型`String`</li><li>`account`：申请入群的账号ID （`accid`），类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
rejectTeamApply | 拒绝入群申请 |  参数如下<br><div><ul><li>`teamId`：群ID，类型`String`</li><li>`account`：申请入群的账号ID （`accid`），类型`String`</li><li>`reason`：拒绝入群的理由，类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
acceptTeamInvite | 接受入群邀请 | 参数如下<br><div><ul><li>`teamId`：群ID，类型`String`</li><li>`inviter`：邀请人的账号ID （`accid`），类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
rejectTeamInvite | 拒绝入群邀请 | 参数如下<br><div><ul><li>`teamId`：群ID，类型`String`</li><li>`inviter`：邀请人的账号ID （`accid`），类型`String`</li><li>`reason`：拒绝入群的理由，类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
applyJoinTeam | 当前用户申请加入群 |参数如下<br><div><ul><li>`teamId`：申请加入的群ID，类型`String`</li><li>`postscript`：申请附言，类型`String`</li><li>`callback`：结果回调，类型`FetchCallback<Void>`</li></ul></div>
getNotificationUnreadCount | 查询系统通知的未读数 | 参数如下<br><div><ul><li>`callback`：结果回调，类型`FetchCallback<int>`</li></ul></div>
getNotificationList | 查询系统通知列表| 参数如下<br><div><ul><li>`offset`：数据库查询offset，类型`int`</li><li>`limit`：数据库查询limit，类型`int`</li><li>`callback`：结果回调，类型`FetchCallback<List<SystemMessageInfo>>`</li></ul></div>
setNotificationStatus | 设置系统通知状态 | 参数如下<br><div><ul><li>`id`：系统通知的ID，类型`Long`</li><li>`infoStatus`：修改的状态值，类型`SystemMessageInfoStatus`</li></ul></div>
clearNotification | 清空系统通知 | 无
clearNotificationUnreadCount | 清除系统通知未读数量 | 无
registerFriendObserver  | 注册好友变化的监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`FriendObserver`</li></ul></div>
unregisterFriendObserver | 取消注册好友变化监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`FriendObserver`</li></ul></div>
registerTeamUpdateObserver | 注册群组信息更新监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`Observer<List<Team>>`</li></ul></div>
unregisterTeamUpdateObserver | 取消群组信息更新监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`Observer<List<Team>>`</li></ul></div>
registerTeamRemoveObserver | 注册群组移除监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`Observer<Team>`</li></ul></div>
unregisterTeamRemoveObserver | 取消注册群组移除监听器 | 参数如下<br><div><ul><li>`observer`：监听器，类型为`Observer<Team>`</li></ul></div>
registerNotificationUnreadCountObserver | 注册系统消息未读数字变化监听器 | 参数如下<br><div><ul><li>`unreadCountObserver`：监听器，类型为` SystemUnreadCountObserver`</li></ul></div>
unregisterNotificationUnreadCountObserver | 取消注册系统消息未读数字变化监听器 | 参数如下<br><div><ul><li>`unreadCountObserver`：监听器，类型为` SystemUnreadCountObserver`</li></ul></div>
registerNotificationObserver | 注册系统通知监听器 |参数如下<br><div><ul><li>`messageObserver`：监听器，类型为`SystemMessageInfoObserver`</li></ul></div>
unregisterNotificationObserver | 取消注册系统通知监听器 | 参数如下<br><div><ul><li>`messageObserver`：监听器，类型为`SystemMessageInfoObserver`</li></ul></div>
registerLoginSyncObserver | 注册登录同步数据监听器 | 参数如下<br><div><ul><li>`loginSyncObserver`：监听器，类型为`LoginSyncObserver`</li></ul></div>
unregisterLoginSyncObserver | 取消注册登录监听器 | 参数如下<br><div><ul><li>`loginSyncObserver`：监听器，类型为`LoginSyncObserver`</li></ul></div>