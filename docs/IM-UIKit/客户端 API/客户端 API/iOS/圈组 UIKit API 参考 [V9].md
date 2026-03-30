
QChatKit 模块中提供了圈组 QChatKit-UI 中使用到的接口封装，提供的接口都是基于 NIM SDK 的接口进行封装，并根据业务进行逻辑处理形成业务型接口。

在开发过程中，如果有满足您需求的接口可以直接使用，如果没有则可以使用 NIM SDK提供的接口来实现。

## 核心类

QChatRepo 提供圈组能力的接口类。

``` swift
@objcMembers
public class QChatRepo: NSObject, QChatMessageProviderDelegate 
```

## Provider 核心类

- `roleProvider` 身份组权限管理类，包含身份组权限设置等功能。

    ``` swift
    public let roleProvider = QChatRoleProvider.shared
    ```
- `serverProvider` 社区管理类，包含社区操作管理，设置等功能。

    ``` swift
    public let serverProvider = QChatServerProvider.shared
    ```
-  `channelProvider` 话题管理类，包含话题操作管理，设置等功能。

    ``` swift
    public let channelProvider = QChatChannelProvider.shared
    ```
-  `contactProvider` 通讯录管理类，包含成员列表，订阅者展示等功能。

    ``` swift
    public let contactProvider = FriendProvider.shared
    ```
- `userProvider` 用户资料管理类，包含用户资料修改等功能。

    ``` swift
    public let userProvider = UserInfoProvider.shared
    ```
- `messageProvider` 消息管理类，包含消息的收发、撤回、点赞等功能。

    ``` swift
    public let messageProvider = QChatMessageProvider.shared
    ```
- `settingProvider` 系统设置类，包含系统配置等功能。

    ``` swift
    public let settingProvider = SettingProvider.shared
    ```
- `apnsProvider` 推送管理类，包含推送设置等功能。

    ``` swift
    public let apnsProvider = QChatApnsProvider.shared
    ```

## 核心方法

### shared

单例初始化

``` swift
public static let shared 
```

### delegate

事件监听

``` swift
public weak var delegate: QChatRepoMessageDelegate? 
```


### onReceive

消息接收回调

``` swift
public func onReceive(_ messages: [NIMQChatMessage]) 
```

### onUnReadChange

未读数变更回调

``` swift
public func onUnReadChange(_ unreads: [NIMQChatUnreadInfo]?,
                             _ lastUnreads: [NIMQChatUnreadInfo]?) 
```

### serverUnreadInfoChanged

社区未读数变更回调

``` swift
public func serverUnreadInfoChanged(_ serverUnreadInfoDic: [NSNumber: NIMQChatServerUnreadInfo]) 
```

### createRole

创建身份组

``` swift
public func createRole(_ param: ServerRoleParam,
                         _ completion: @escaping (Error?, ServerRole) -> Void) 
```

### getRoles

获取社区身份组

``` swift
public func getRoles(_ param: GetServerRoleParam,
                       _ completion: @escaping (Error?, [ServerRole]?, Set<NSNumber>?) -> Void) 
```

### updateServerRolePriorities

批量更新社区身份组的权限优先级

``` swift
public func updateServerRolePriorities(_ param: UpdateServerRolePrioritiesParam,
                                         _ completion: @escaping (Error?) -> Void) 
```

### getChannelRoles

查询主题下身份组列表

``` swift
public func getChannelRoles(_ param: ChannelRoleParam,
                              _ completion: @escaping (Error?, [ChannelRole]?) -> Void) 
```

### getServerRoleMembers

查询某社区下某身份组下的成员列表

``` swift
public func getServerRoleMembers(_ param: GetServerRoleMembersParam,
                                   _ completion: @escaping (Error?, [RoleMember]) -> Void) 
```

### updateRole

更新社区身份组

``` swift
public func updateRole(_ param: UpdateServerRoleParam,
                         _ completion: @escaping (Error?, ServerRole) -> Void) 
```

### deleteRoles

删除社区身份组

``` swift
public func deleteRoles(_ param: DeleteServerRoleParam,
                          _ completion: @escaping (Error?) -> Void) 
```

### getServerMembers

分页查询社区成员信息

``` swift
public func getServerMembers(_ param: GetServerMembersByPageParam,
                               _ completion: @escaping (Error?, [ServerMemeber]) -> Void) 
```

### updateMyServerMember

修改社区成员信息

``` swift
public func updateMyServerMember(_ param: UpdateMyMemberInfoParam,
                                   _ completion: @escaping (Error?, ServerMemeber) -> Void) 
```

### updateServerMember

修改他人社区成员信息

``` swift
public func updateServerMember(_ param: UpdateServerMemberInfoParam,
                                 _ completion: @escaping (Error?, ServerMemeber) -> Void) 
```

### addRoleMember

将某些人加入某社区身份组

``` swift
public func addRoleMember(_ param: AddServerRoleMemberParam,
                            _ completion: @escaping (Error?, [String], [String]) -> Void) 
```

### updateChannelRole

设置话题下身份组权限

``` swift
public func updateChannelRole(param: UpdateChannelRoleParam,
                                _ completion: @escaping (NSError?, ChannelRole?) -> Void) 
```

### removeChannelRole

删除话题下的身份组

``` swift
public func removeChannelRole(param: RemoveChannelRoleParam,
                                _ completion: @escaping (NSError?) -> Void) 
```

### getServerRolesByAccId

通过accid查询自定义身份组列表

``` swift
public func getServerRolesByAccId(param: GetServerRolesByAccIdParam,
                                    _ completion: @escaping (Error?, [ServerRole]?) -> Void) 
```

### deleateRoleMember

删除

``` swift
public func deleateRoleMember(_ param: RemoveServerRoleMemberParam,
                                _ completion: @escaping (Error?, [String], [String]) -> Void) 
```

### addMemberRole

添加成员到话题

``` swift
public func addMemberRole(param: AddMemberRoleParam,
                            _ completion: @escaping (NSError?, MemberRole?) -> Void) 
```

### getMemberRoles

查询话题下成员的权限

``` swift
public func getMemberRoles(param: GetMemberRolesParam,
                             _ completion: @escaping (NSError?, [MemberRole]?) -> Void) 
```

### updateMemberRole

设置某个话题下的成员的权限

``` swift
public func updateMemberRole(param: UpdateMemberRoleParam,
                               _ completion: @escaping (NSError?, MemberRole?) -> Void) 
```

### removeMemberRole

移除某个话题下的成员

``` swift
public func removeMemberRole(param: RemoveMemberRoleParam,
                               _ completion: @escaping (NSError?) -> Void) 
```

### removeServerRoleMember

将某些人移除某社区身份组

``` swift
public func removeServerRoleMember(param: NIMQChatRemoveServerRoleMemberParam,
                                     _ completion: @escaping (Error?, NIMQChatRemoveServerRoleMembersResult?) -> Void) 
```

### revokeMessage

撤回圈组消息

``` swift
public func revokeMessage(param: NIMQChatRevokeMessageParam, completion: NIMQChatUpdateMessageHandler?) 
```

### deleteMessage

删除圈组消息

``` swift
public func deleteMessage(param: NIMQChatDeleteMessageParam, completion: NIMQChatUpdateMessageHandler?) 
```

### addQuickComment

发送快捷评论

``` swift
public func addQuickComment(type: Int64, to message: NIMQChatMessage, completion: NIMQChatHandler?) 
```

### deleteQuickComment

删除快捷评论

``` swift
public func deleteQuickComment(type: Int64, to message: NIMQChatMessage, completion: NIMQChatHandler?) 
```

### fetchQuickComments

批量获取快捷评论

``` swift
public func fetchQuickComments(messages: [NIMQChatMessage], completion: @escaping NIMQChatFetchQuickCommentsByMsgsHandler) 
```

### updateChannelInfo

修改圈组主题信息

``` swift
public func updateChannelInfo(_ param: UpdateChannelParam,
                                _ completion: @escaping (NSError?, ChatChannel?) -> Void) 
```

### getChannelMembers

查询话题成员信息列表

``` swift
public func getChannelMembers(param: ChannelMembersParam,
                                _ completion: @escaping (NSError?, ChannelMembersResult?)
                                  -> Void) 
```

### getExistingChannelBlackWhiteMembers

查询成员是否在该话题的黑白名单中

``` swift
public func getExistingChannelBlackWhiteMembers(param: GetExistingChannelBlackWhiteMembersParam,
                                                  _ completion: @escaping (NSError?,
                                                                           BlackWhiteMembersResult?)
                                                    -> Void) 
```

### fetchUserInfo

从云信服务器批量获取用户资料

``` swift
public func fetchUserInfo(accountList: [String],
                            _ completion: @escaping (NSError?, [User]?) -> Void) 
```

### kickoutServerMembers

踢除社区成员

``` swift
public func kickoutServerMembers(_ param: KickServerMembersParam,
                                   _ completion: @escaping (Error?) -> Void) 
```

### getServers

查询社区信息

``` swift
public func getServers(_ parameter: QChatGetServersParam,
                         _ completion: @escaping (NSError?, QChatGetServersResult?) -> Void) 
```

### updateServer

修改社区信息

``` swift
public func updateServer(_ param: UpdateServerParam, _ completion: @escaping (Error?, QChatServer) -> Void) 
```

### getServerMembersByPage

分页查询社区成员信息

``` swift
public func getServerMembersByPage(_ parameter: QChatGetServerMembersByPageParam,
                                     _ completion: @escaping (NSError?,
                                                              QChatGetServerMembersResult?)
                                       -> Void) 
```

### inviteMembersToServer

邀请社区成员

``` swift
public func inviteMembersToServer(_ parameter: QChatInviteServerMembersParam,
                                    _ completion: @escaping (NSError?) -> Void) 
```

### inviteMembersToServerWithResult

邀请社区成员(携带成功失败列表)

``` swift
public func inviteMembersToServerWithResult(param: QChatInviteServerMembersParam,
                                              _ completion: @escaping (NSError?, [String]?, [String]?) -> Void) 
```

### getExistingServerRolesByAccids

查询一批accids的自定义身份组列表

``` swift
public func getExistingServerRolesByAccids(_ parameter: QChatGetExistingAccidsInServerRoleParam,
                                             _ completion: @escaping (NSError?,
                                                                      [String: [ServerRole]]?)
                                               -> Void) 
```

### checkPermission

查询自己是否有某个权限

``` swift
public func checkPermission(serverId: UInt64, channelId: UInt64?, permissionType: NIMQChatPermissionType, complete: @escaping (NSError?, Bool) -> Void) 
```

### getExistingServerRoleMembersByAccids

查询一批accids是否在某个社区身份组,返回在的成员信息

``` swift
public func getExistingServerRoleMembersByAccids(_ param: GetExistingServerRoleMembersByAccidsParam,
                                                   _ completion: @escaping (Error?, [String])
                                                     -> Void) 
```

### getChannelUnReadInfo

查询话题未读信息

``` swift
public func getChannelUnReadInfo(_ param: GetChannelUnreadInfosParam,
                                   _ completion: @escaping (Error?, [NIMQChatUnreadInfo]?)
                                     -> Void) 
```

### getChannelsByPage

分页查询圈组主题信息

``` swift
public func getChannelsByPage(param: QChatGetChannelsByPageParam,
                                _ completion: @escaping (NSError?, QChatGetChannelsByPageResult?)
                                  -> Void) 
```

### leaveServer

主动离开社区

``` swift
public func leaveServer(_ serverId: UInt64?, _ completion: @escaping (Error?) -> Void) 
```

### getLastMessage

批量获取话题最后一条消息

``` swift
public func getLastMessage(_ serverId: UInt64, _ channelIds: [NSNumber], _ completion: @escaping (Error?, [NSNumber: NIMQChatMessage]?) -> Void) 
```

### enterAsVisitor

游客模式加入

``` swift
public func enterAsVisitor(_ param: NIMQChatEnterServerAsVisitorParam, _ completion: @escaping (Error?, NIMQChatEnterServerAsVisitorResult?) -> Void) 
```

### leaveAsVisitor

退出游客模式

``` swift
public func leaveAsVisitor(_ param: NIMQChatLeaveServerAsVisitorParam, _ completion: @escaping (Error?, NIMQChatLeaveServerAsVisitorResult?) -> Void) 
```

### subscribeChannel

游客模式订阅channel

``` swift
public func subscribeChannel(_ param: NIMQChatSubscribeChannelAsVisitorParam, _ completion: @escaping (Error?, NIMQChatSubscribeChannelAsVisitorResult?) -> Void) 
```

### subscribeAsVisitor

游客模式订阅Server

``` swift
public func subscribeAsVisitor(_ param: NIMQChatSubscribeServerAsVisitorParam, _ completion: @escaping (Error?, NIMQChatSubscribeServerAsVisitorResult?) -> Void) 
```

### fetchChannelsByServerIdWithLastMessage

分页获取话题信息，回调中携带last message

``` swift
public func fetchChannelsByServerIdWithLastMessage(_ serverId: UInt64, _ timeTag: TimeInterval, _ limit: Int, _ completion: @escaping (NSError?, QChatGetChannelsByPageResult?, [NSNumber: NIMQChatMessage]?) -> Void) 
```

### applyServerJoin

申请加入社区

``` swift
public func applyServerJoin(param: QChatApplyServerJoinParam,
                              _ completion: @escaping (NSError?) -> Void) 
```

### getServerMembers

批量查询社区成员信息

``` swift
public func getServerMembers(param: QChatGetServerMembersParam, _ completion: @escaping (Error?, [ServerMemeber]?) -> Void) 
```

### getServerList

批量拉取社区

``` swift
public func getServerList(param: GetServersByPageParam,
                            _ completion: @escaping (NSError?, GetServersByPageResult?)
                              -> Void) 
```

### createServer

创建社区

``` swift
public func createServer(param: CreateServerParam,
                           _ completion: @escaping (NSError?, CreateServerResult?) -> Void) 
```

### deleteServer

删除社区

``` swift
public func deleteServer(_ serverid: UInt64, _ completion: @escaping (Error?) -> Void) 
```

### applyServerJoin

申请加入社区

``` swift
public func applyServerJoin(parameter: QChatApplyServerJoinParam,
                              _ completion: @escaping (NSError?) -> Void) 
```

### getServerMemberList

查询社区内成员信息

``` swift
public func getServerMemberList(parameter: QChatGetServerMembersParam,
                                  _ completion: @escaping (NSError?,
                                                           QChatGetServerMembersResult?) -> Void) 
```

### createAnncServer

创建公告主题

``` swift
public func createAnncServer(_ param: inout CreateServerParam, _ completion: @escaping (NSError?, QChatServer?) -> Void) 
```

### getUserPushNotificationConfigByServer

``` swift
public func getUserPushNotificationConfigByServer(server: [NSNumber], _ completion: @escaping (Error?, [NIMQChatUserPushNotificationConfig]?) -> Void) 
```

### updatePushNotificationByProfile

``` swift
public func updatePushNotificationByProfile(profile: NIMPushNotificationProfile, server: UInt64, _ completion: @escaping (Error?) -> Void) 
```
