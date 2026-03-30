
IM UIKit 提供一套包含 UI 的 IM 接入方式。在 UIKit 中我们对业务场景使用到 IM SDK 的接口封装成业务数据能力层，将复杂的数据关联调用精简成一次接口调用，减少上层业务的复杂性。本文概要性介绍业务数据能力层的接口。

## UIKit API 概览

### 核心类

* `IMKitClient` 提供初始化，登录登出以及单例相关的能力接口。
* `ContactRepo` 提供通讯录模块使用的数据能力接口，包括查询好友列表、黑名单等。
* `ConversationRepo` 提供会话列表模块使用的数据能力接口，包括查询会话列表、置顶、删除等接口。
* `ChatRepo` 提供会话详情页模块使用的数据能力接口，包括发送消息、删除消息等接口。
* `SettingRepo` 提供“我的页面”设置模块能力接口。
* `TeamRepo` 提供群组模块相关的数据能力接口，包括更新群名，退群，创建高级群等接口。


### Provider 核心类
* `ChatExtendProvider` 聊天拓展类，包含置顶，收藏，pin等操作。
* `ChatProvider` 聊天管理类，负责消息的收发，撤回，发送已读回执等。
* `ConversationProvider` 会话管理类，负责消息，最近会话的读写和管理，包含删除增加会话，获取会话列表，设置会话已读等功能。
* `FriendProvider` 好友管理类，包含添加，删除好友，将好友添加，移除黑名单，获取好友资料，查找成员等功能。
* `UserInfoProvider` 获取用户资料，修改自己资料。
* `TeamProvider` 群组管理类，负责群组的操作：创建，拉人，踢人，同步等。
* `SystemMessageProvider` 系统通知管理类，包含获取系统通知，删除系统消息，标记系统消息已读，发送自定义通知等。
* `SettingProvider` 设置获取推送状态等。
* `ResourceProvider` 设置使用短链换源链。


### IMKitClient 核心方法

<div style="width:240px">方法/属性</div> | 功能 | 描述
---- | -------------- | ---------
setupCoreKitIM(_:) | 初始化接口 | 需要在功能使用之前，进行初始化。<br/>不需要额外调用SDK的初始化方法
appKey() | 获取appkey | 返回当前注册的AppKey
isUsingDemoAppKey() | 是否正在使用Demo AppKey | 返回是否正在使用Demo AppKey
loginIM(_:_:_:) | 登录 IM | 登录 IM
logout(_:) | 登出 IM | 登出 IM
autoLogin(account:token:) | 自动登录 IM |自动登录
updateApnsToken(token:) | 更新APNS Token | token APNS Token
updatePushKitToken(token:) | 更新 PushKit Token | 目前仅支持 PKPushTypeVoIP
addDelegate(_:)|设置用户信息代理|支持同步获取用户信息、异步获取用户信息和更新用户信息
removeDelegate(_:)|移除用户信息代理|移除用户信息代理




### 代理相关方法

<div style="width:260px">方法/属性</div> | 功能 
---- | -------------- 
addChatDelegate(delegate: NIMChatManagerDelegate) | 添加聊天代理
removeChatDelegate(delegate: NIMChatManagerDelegate) | 移除聊天代理
addChatExtendDelegate(delegate: ChatExtendProviderDelegate) | 添加聊天扩展代理
removeChatExtendDelegate(delegate: ChatExtendProviderDelegate) | 移除聊天扩展代理
addContactDelegate(delegate: FriendProviderDelegate) | 添加通讯录代理
removeContactDelegate(delegate: FriendProviderDelegate) | 移除通讯录代理
addTeamDelegate(delegate: NIMTeamManagerDelegate) | 添加群组代理
removeTeamDelegate(delegate: NIMTeamManagerDelegate) | 移除群组代理
addSessionDelegate(delegate: NIMConversationManagerDelegate) | 添加会话代理
removeSessionDelegate(delegate: NIMConversationManagerDelegate) | 移除会话代理
addSystemNotificationDelegate(delegate: NIMSystemNotificationManagerDelegate) | 添加系统通知代理
removeSystemNotificationDelegate(delegate: NIMSystemNotificationManagerDelegate) | 移除系统通知代理



## 会话列表 API

会话列表模块分为`NEConversationUIKit` 和 `NEChatKit`两层设计，其中`NEConversationUIKit`提供会话列表界面相关的 UI 和交互逻辑，`NEChatKit`包含对会话相关业务能力的封装，向 UI 层提供业务数据聚合接口和 IM SDK 接口的封装。

相较于 IM SDK，`NEChatKit` 提供的接口拥有更好的业务聚合性，更方便您在 UI 层的展示和操作。以会话列表查询接口为例，IM SDK 的会话列表查询接口，调用成功后仅返回会话信息；而 `NEChatKit` 提供的会话列表查询接口，调用成功后的返回结果不仅包含会话信息，也包含该会话对应的用户信息或群组信息。 

### 获取 UIKit 会话列表

`ConversationRepo` 提供操作/配置会话列表的相关方法和属性。其中调用会话列表查询接口的示例代码如下：
:::::: div custom-tabs
::: tab Swift
```
//查询会话列表接口
let repo = ConversationRepo()
repo.getSessionList(...) 
```
:::
::: tab Objective-C
```
//查询会话列表接口
ConversationRepo *repo = [[ConversationRepo alloc] init];
[repo getSessionList:^(NSError * _Nullable, NSArray<ConversationListModel *> * _Nullable) {
    // code
}];
```
:::
::::::

### ConversationRepo 说明

`ConversationRepo` 的其他方法/属性说明见下表：

<div style="width:240px">方法/属性</div> | 功能描述 | 参数
---- | -------------- | ---------
getSessionList(_:) | 获取会话列表 |`option`：获取服务端会话列表可选参数
addStickTop(params:_:) | 增加一条置顶记录 | `params`：添加置顶的参数
removeStickTop(params:_:) | 移除一条置顶记录| `params`：添加置顶的参数
getMsgUnreadCount(notify:) | 获取所有未读数| `notify`：是否是通知
getStickTopSessionList(_:) | 查找所有的置顶记录 | 返回查找到的记录
getStickTopSessionInfo(session:) | 查询某个会话的置顶信息 | `session`：需要查询的会话
createTeamSession(_:) | 增加某个最近会话(Team类型)| `teamid`：群组id
deleteSession(sessions:_:) | 删除服务器端最近会话| `sessions`：会话参数数组
deleteLocalSession(recentSession:) | 删除某个最近会话| `recentSession`：待删除的最近会话
getUserInfo(userId:_:) | 从本地获取用户资料| `userId`：用户id
isNeedNotify(userId:) | 是否需要通知| `userId`：用户id
searchUserInfo(_:_:) | 查找成员| `option`：查找条件
searchContact(searchStr:_:) | 通讯录搜索|`searchStr`：搜索关键字
getTeamInfoList(teamsIds:_:) | 获取指定群ID的群信息| `teamsIds`：群id列表,数组元素超过10个只取前10个
getTeamInfo(teamId:_:) | 获取群信息|`teamId`：群组id
isNeedNotifyForTeam(teamId:) | 群通知状态| `teamId`：群组id
searchTeam(_:_:) | 查询群信息| `option`：查询选项


## 会话消息 API



会话消息模块分为 `NEChatUIKit` 和 `NEChatKit` 两层设计，其中 `NEChatUIKit` 包含会话消息界面相关的 UI 和交互逻辑，`NEChatKit` 是对会话消息相关业务能力的封装，向 UI 层提供业务数据聚合接口和 IM SDK 接口的封装。

相较于 IM SDK，`NEChatKit` 提供的接口拥有更好的业务聚合性，更方便您在 UI 层的展示和操作。

### 获取 UIKit 会话消息

`ChatRepo` 提供操作/配置会话消息的相关方法和属性。其中调用会话消息查询接口的示例代码如下：
:::::: div custom-tabs
::: tab Swift
```
//查询会话消息接口
let repo = ChatRepo()
repo.getHistoryMessage(...) 
```
:::
::: tab Objective-C
```
//查询会话消息接口
ChatRepo *repo = [[ChatRepo alloc] init];
    NIMSession *session = [[NIMSession alloc] init];
    NIMHistoryMessageSearchOption *option = [[NIMHistoryMessageSearchOption alloc] init];
    [repo getHistoryMessageWithSession:session option:option :^(NSError * _Nullable error, NSArray<NIMMessage *> * _Nullable messages) {
        ...
    }];
```
:::
::::::


### ChatRepo 说明

`ChatRepo` 提供操作/配置会话消息的相关方法和属性，具体说明见下表：

<div style="width:260px">方法/属性</div> | 功能描述 | 参数
---- | -------------- | ---------
sendMessage(message:session:_:) | 发送消息 |<div><ul><li>`message`消息对象</li><li>`session`接收方</li></ul></div>
getHistoryMessage(session:message:limit:_:) | 从本地数据库读取一个会话里某条消息之前的若干条的消息 |<div><ul><li>`session`：消息所属的会话</li><li>`message`：当前最早的消息,没有则传入nil</li><li>`limit`：个数限制</li></ul></div>
getHistoryMessage(session:option:_:) | 从服务器上获取一个会话里某条消息之前的若干条的消息(此接口不支持查询聊天室消息)| <div><ul><li>`session`：用户id</li><li>`option`：搜索选项</li></ul></div>
markP2pMessageRead(param:_:) | 发送已读回执(p2p)|`param`：已读回执
markTeamMessageRead(param:_:) | 发送已读回执 (Team)|`param`：已读回执
resendMessage(message:) | 重新发送消息 |`message`：消息
deleteMessage(message:) | 删除消息 |`message`：待删除的聊天消息
replyMessage(_:_:_:) | 回复消息|<div><ul><li>`message`：新生成的消息</li><li>`target`：被回复的消息</li></ul></div>
revokeMessage(message:_:) | 撤回消息，不包含推送信息|`message`：需要被撤回的消息
markMessageRead(_:_:) | 设置一个会话里所有消息置为已读|`session`：需设置的会话
getUserInfo(userId:) | 从本地获取用户资料| `userId`：用户id
getUserInfo(_:_:) | 批量获取用户信息| <div><ul><li>`remainUserIds`：用户模型类型为[[NIMTeamMember]]</li><li>`model`：群信息模型</li></ul></div>
getTeamMemberList(userId:teamId:) | 获取单个群成员信息| <div><ul><li>`userId`：用户id</li><li>`teamId`：群组id</li></ul></div>
getTeamInfo(teamId:_:) | 获取群信息| `teamId`：群组id
isTopStick(_:) | 是否是置顶会话| `uid`：会话id (P2P为userId，team时为teamId)
removeBlackList(account:_:) | 将用户从黑名单移除| `account`：用户id
addBlack(account:_:) | 添加用户到黑名单| `account`：用户id
isNeedNotify(userId:) | 是否需要消息通知| `userId`：用户id
setNotify(_:_:_:) | 设置消息提醒| <div><ul><li>`userId`：用户id</li><li>`notify`：是否提醒</li></ul></div>
getIncompleteSessionInfo(session:_:) | 查询漫游消息未完整会话信息|`session`：目标会话
updateIncompleteSessions(messages:_:) | 更新未漫游完整会话列表| `messages`：消息对象数组
searchMessages(_:option:_:) | 搜索本地会话内消息| <div><ul><li>`session`：消息所属的会话</li><li>`option`搜索选项：</li></ul></div>
createAdvanceTeam(_:_:_:_:) | 创建高级群|<div><ul><li>`accids`：用户accid列表</li><li>`iconUrl`：群头像</li><li>`teamName`：群名称</li></ul></div>
getTeamInfo(_:_:) | 获取群信息及群成员| `teamid`：群组id
collectMessage(_:_:) | 添加一个收藏| `info`：添加收藏的参数
addMessagePin(_:_:) | 添加一条PIN记录| `pinItem`：需要添加的PIN记录
removeMessagePin(_:_:) | 删除一条PIN记录| `pinItem`：需要删除的PIN记录
searchMessagePinHistory(_:) | 查询某条消息的PIN记录|`message`：消息
downloadMessageAttachment(_:_:) | 收取消息附件| `message`：群组需要收取附件的消息id
downloadSource(_:_:_:_:) | 下载文件| <div><ul><li>`urlString`：下载的Url</li><li>`filePath`：下载路径</li><li>`progress`：进度</li></ul></div>
makeForwardMessage(message:session:) | 生成转发消息| <div><ul><li>`message`：消息</li><li>`session`：接收方</li></ul></div>
sendCustomNotification(_:_:_:) | 发送自定义系统通知| <div><ul><li>`noti`：NIMSDK系统通知</li><li>`session`：接收方</li></ul></div>
getHandsetMode() | 听筒是否外放| 返回是否外放
getMessageRead() | 消息是否已读| 返回是否已读

## 通讯录 API



通讯录模块分为 `NEContactUIKit` 和 `NEChatKit`两层设计，其中`NEContactUIKit`提供通讯录界面相关的 UI 和交互逻辑，`NEChatKit`包含对通讯录相关业务能力的封装，向 UI 层提供业务数据聚合接口和 IM SDK 接口的封装。

相较于 IM SDK，`NEChatKit` 提供的接口拥有更好的业务聚合性，更方便您在 UI 层的展示和操作。以通讯录列表查询接口为例，IM SDK 的通讯录列表查询接口，调用成功后返回结果是您所有的好友信息，包含了黑名单中的好友；而 `NEChatKit` 提供的 `getFriendList(_:local:_:)` 接口，调用成功后返回的是除黑名单外的好友信息，自动过滤了黑名单中的好友。


### 获取 UIKit 通讯录列表

`ContactRepo` 提供操作/配置通讯录的相关方法和属性。其中调用通讯录列表查询接口的示例代码如下：

```swift
//查询通讯录列表接口
let repo = ContactRepo()
repo.getFriendList(...) 
```


### ContactRepo 说明

`ContactRepo` 的其他方法/属性说明见下表：

<div style="width:240px">方法/属性</div> | 功能描述 | 参数
---- | -------------- | ---------
getFriendList(_:local:_:) | 获取好友列表不包含黑名单好友 | 返回我的好友列表
getUserInfo(_:_:) | 从本地获取用户资料，本地获取不到，会返回远端数据| `userId`：用户id
fetchUserInfo(accountList:_:) | 从云信服务器批量获取用户资料| `accountList`：用户id列表
addFriend(request:_:) | 添加好友| `request`：添加好友参数
deleteFriend(account:deleteAlias:_:) | 删除好友| <div><ul><li>`account`：账号id</li><li>`deleteAlias`： 是否同时删除备注</li></ul></div>
isFriend(account:) | 是否是好友| `account`：账号id
getBlackList() | 获取黑名单列表| 返回黑名单列表信息
removeBlackList(account:_:) | 从黑名单中移除| `account`：账号id
addBlackList(account:_:) | 加入黑名单| `account`：账号id
isBlackList(account:) | 判断用户是否已被拉黑| `account`：账号id
getNotificationList(limit:) | 是否需要消息通知| <div><ul><li>`notification`：当前最早系统消息</li><li>`limit`：最大获取数</li></ul></div>
clearNotification() | 删除所有系统消息| 无
updateUser(_:_:) | 修改自己与目标用户的关系| `user`：目标用户
getNotificationUnreadCount() |  未读系统消息数| 返回未读数
clearNotificationUnreadCount() | 标记所有系统消息为已读| 无
getTeamList() |  获取所有群组| 返回获取到的所有群组
getUserName() | 添加好友| `option`：查询选项
acceptTeamInvite(_:_:_:) | 接受群邀请| <div><ul><li>`teamId`：群id</li><li>`invitorId`：邀请者id</li></ul></div>
rejectTeamInvite(_:_:_:) | 拒绝群邀请| <div><ul><li>`teamId`：群id</li><li>`invitorId`：邀请者id</li></ul></div>




