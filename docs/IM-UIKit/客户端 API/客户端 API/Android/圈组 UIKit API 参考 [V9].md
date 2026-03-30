QChatKit 模块提供了圈组 QChatKit-UI 使用到的接口。接口都是基于 NIM SDK 接口进行业务封装，在开发过程中，如果没有则可以使用 NIM SDK 提供的接口来实现。


### QChatServerRepo

该类提供与社区相关的接口，示例代码如下：

```java 
QChatServerRepo.createServerAndCreateChannel(
        "社区名字",
        "话题名字1",
        "话题名字2",
        "https://.....",
        new FetchCallback<QChatServerWithSingleChannel>() {
          @Override
          public void onSuccess(@Nullable QChatServerWithSingleChannel param) {
           //成功的回调
          }

          @Override
          public void onFailed(int code) {
            // 失败回调
          }

          @Override
          public void onException(@Nullable Throwable exception) {
           // 失败回调
          }
        });

```

具体接口如下：
接口名称 |参数| 接口说明
:---- | :-------------- | :--------- |:-------
`createServer` | <li>name: String 社区名称<li>iconUrl: String 社区图标，可为空<li>callBack: FetchCallback 异步创建结果回调，可空 |创建服务器
`createServerAndCreateChannel` | <li>name: String 社区名称<li>channelName1: String 话题1名 <li>channelName2: String 话题2名称<li>iconUrl: String 社区图标，可为空<li>callBack: FetchCallback 异步创建结果回调，可空 |创建服务器，同时在该服务器下创建两个频道
`createAnnouncementServer` | <li>name: String 社区名称<li>iconUrl: String 社区图标，可为空<li>authMap: Map<QChatRoleResource, QChatRoleOption> 权限参数，可空<li>callBack: FetchCallback 异步创建结果回调，可空 |创建公告频道（参考官网说明，公告频道规则）
`updateServer` | <li>serverId: Long 社区ID<li>name: String 社区名称<li>iconUrl: String 社区图标，可为空<li>custom: String 社区扩展参数，可为空<li>callBack: FetchCallback 异步结果回调，可空 |修改服务器信息
`deleteServer` | <li>serverId: Long 社区ID<li>callBack: FetchCallback 异步结果回调，可空 |删除服务器
`leaveServer` | <li>serverId: Long 社区ID<li>callBack: FetchCallback 异步结果回调，可空> |主动离开服务器
`fetchServerList` | <li>timeTag: Long 拉取服务起始时间戳（毫秒）<li>limit: Int 分页接口查询数量<li>callBack: FetchCallback 异步结果回调|通过分页信息查询服务器
`getServers` | <li>serverIdList: List<Long> 社区ID列表 <li>callBack: FetchCallback 异步结果回调|通过ServerId列表查询服务器
`getServer` | <li>serverId: Long 社区ID<li>callBack: FetchCallback 异步结果回调<QChatServerInfo> |通过 ServerId 查询服务器
`uploadServerIcon` | <li>file: File 社区图标文件<li>callBack: FetchCallback 异步结果回调 |通过 NOS 上传图片文件，并返回 URL 地址
`getServerMembers` | <li>dataList: List<Pair<Long, String>> 成员ACCID<li>callBack: FetchCallback 异步结果回调|通过accid查询服务器成员
`searchServerById` | <li>serverId: Long 社区ID<li>isAnnouncement: Boolean 是否为公告频道，默认false<li>callBack: FetchCallback 异步结果回调 | 根据服务器ID 查询服务器，并查询当前登录账号是否加入到该服务中
`applyServerJoin` | <li>serverId: Long 社区ID<li>postscript: String 申请留言，可为空<li>callBack: FetchCallback 异步结果回调 |申请加入服务
`inviteServerMembers` | <li>serverId: Long 社区ID<li>accIdList: List<String> 邀请成员accID列表<li>postscript: String 申请留言，可为空<li>callBack: FetchCallback 异步结果回调，可空|邀请加入服务
`updateOtherMember` | <li>serverId: Long 社区ID<li>accid: String 被修改用户accID<li>nick: String 被修改用户昵称<li>avatar: String 被修改用户头像，可为空<li>callBack: FetchCallback 异步结果回调，可空 |修改其他人的服务器成员信息
`updateMyMember` | <li>serverId: Long 社区ID<li>nick: String 昵称<li>avatar: String 用户头像，可为空<li>custom: String 扩展参数，可为空<li>callBack: FetchCallback 异步结果回调，可空 |修改服务器个人信息
`fetchServerMemberInfoWithRolesList` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询服务器成员列表，并查询该成员加入的身份组列表
`fetchServerMemberInfoWithRolesByAccId` | <li>serverId: Long 社区ID<li>accId: String 查询用户accID<li>callBack: FetchCallback 异步结果回调 |查询服务中用户信息，并包括该用户的身份组信息
`fetchServerMemberWithoutChannel` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询服务器下，不在某个频道的所有成员信息
`fetchServerMembersWithRolesFilter` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询服务器成员列表，并过滤掉某个身份组的成员
`fetchServerMembersWithWhiteBlackFilter` | <li>serverId: Long 社区ID<li>channelId: Long 话题I<li>channelType:Int 话题类型<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询服务器成员列表，并过滤掉黑名单成员
`getAnnounceServerNormalMemberByPage` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>roleId: Long 身份证ID<li>ownerId: String 创建者accID<li>callBack: FetchCallback 异步结果回调 |分页查询公告频道订阅者成员列表，查询结果去除创建者和管理员
`getAnnounceServerManagerMemberByPage` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>roleId: Long 身份证ID<li>ownerId: String 创建者accID<li>anchorAccId: String 分页查询起始accID，首页传入空<li>callBack: FetchCallback 异步结果回调 |分页查询公告频道管理员成员列表，查询结果去除创建者
`enterAsVisitor` |<li>serverIdList: List<Long> 社区ID<li>callBack: FetchCallback 异步结果回调，可空 |以游客身份加入服务器
`leaveAsVisitor` |<li>serverIdList: List<Long> 社区ID<li>callBack: FetchCallback 异步结果回调，可空 |以游客身份离开服务器
`subscribeAsVisitor` |<li>serverIdList: List<Long> 社区ID<li>register: Boolean 注册或取消注册<li>callBack: FetchCallback 异步结果回调，可空 |以游客身份订阅服务器
`kickMember` | <li>serverId: Long 社区ID<li>serverId: Long 社区ID<li>accid: String 被踢出用户accID<li>callBack: FetchCallback 异步结果回调，可空 |踢除服务器成员




### QChatRoleRepo
该类提供与社区身份组相关的接口，示例代码如下：

```java 
QChatRoleRepo.createRoleWithMember(
    serverId,
    name,
    memberList,
    result -> {
      // 结果回调
      return null;
    });
```

具体接口如下：
接口名称 |参数| 接口说明
:---- | :-------------- | :--------- |:-------
`createRoleWithMember` | <li>serverId: Long 社区ID<li>name: String 身份组名称<li>type: QChatRoleType 身份组类型，可为空<li>members: List<String> 添加成员的accID<li>icon: String 身份组头像<li> extension: String 身份组扩展信息<li>inform:  ((ResultInfo<QChatCreateServerRoleResult>) -> Unit) 创建结果回调，可空 |新增服务器身份组，并将成员加入
`createRole` | <li>serverId: Long 社区ID<li>name: String 身份组名称<li>type: QChatRoleType 身份组类型，可为空<li>icon: String 身份组头像<li> extension: String 身份组扩展信息<li>inform:  ((ResultInfo<QChatCreateServerRoleResult>) -> Unit) 创建结果回调，可空 |新增服务器身份组
`fetchServerRoleMember` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>accId: String 分页查询最后用户accID，首页传空<li>callBack: FetchCallback 异步结果回调 |查询某服务器下某身份组下的成员列表
`removeServerRoleMember` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>accIds: List<String> 移除用户accID列表<li>callBack: FetchCallback 异步结果回调 |将某些人移出某服务器身份组
`removeServerRoleMemberForResult` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>accIds: List<String> 移除用户accID列表<li>callBack: FetchCallback 异步结果回调 |将某些人移出某服务器身份组
`addServerRoleMember` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>accIds: List<String> 用户accID列表<li>callBack: FetchCallback 异步结果回调 |将某些人加入某服务器身份组
`addChannelRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>parentRoleId: Long 需要继承的身份组ID<li>callBack: FetchCallback 异步结果回调 |新增Channel身份组
`updateChannelRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>roleId: Long 身份组ID<li>option: Map<QChatRoleResourceEnum, QChatRoleOptionEnum> 修改的权限配置<li>callBack: FetchCallback 异步结果回调 |修改频道下某身份组的权限
`deleteChannelRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>roleId: Long 身份组ID<li>callBack: FetchCallback 异步结果回调 |删除频道身份组
`addChannelMemberRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID<li>callBack: FetchCallback 异步结果回调 |为某个人定制某频道的权限
`updateChannelMember` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID<li>option: Map<QChatRoleResourceEnum, QChatRoleOptionEnum>修改的权限配置<li>callBack: FetchCallback 异步结果回调 |修改某人的定制权限
`deleteChannelMemberRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID<li>callBack: FetchCallback 异步结果回调 |为某个人定制某频道的权限
`updateRole` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>name: String 身份组名称<li>icon: String 身份组头像<li> extension: String 身份组扩展信息<li>option: Map<QChatRoleResourceEnum, QChatRoleOptionEnum>修改的权限配置<li>callBack: FetchCallback 异步结果回调  |新增服务器身份组
`fetchServerRoles` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询服务器下身份组列表，第一页返回结果额外包含everyone身份组，自定义身份组数量充足的情况下会返回limit+1个身份组
`fetchServerRolesWithoutChannel` | serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 查询服务器下身份组列表，第一页返回结果额外包含everyone身份组，并移除频道下身份组
`fetchMemberJoinedRoles` | <li>serverId: Long 社区ID<li>accId: String 用户accID<li>callBack: FetchCallback 异步结果回调 | 查询ACCID用户加入的身份组列表，结果只有自定义身份组，不包含everyone身份组
`deleteServerRole` | <li>serverId: Long 社区ID<li>roleId: Long 身份组ID<li>callBack: FetchCallback 异步结果回调 | 移除服务器身份组
`updateRolesPriorities` | <li>serverId: Long 社区ID<li>topPriority: Long 优先级<li> rolesList: List<QChatServerRoleInfo> 优先级列表 <li>callBack: FetchCallback 异步结果回调 | 批量修改服务器身份组优先级
`checkPermission` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li> resource: QChatRoleResource 查询权限 <li>callBack: FetchCallback 异步结果回调 | 查询自己是否拥有某个权限
`checkPermissions` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li> resource: List<QChatRoleResource> 查询权限 <li>callBack: FetchCallback 异步结果回调 | 批量查询自己是否拥有某个权限
`getMemberRoles` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 |查询channel下某人的定制权限
`addMemberRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID <li>callBack: FetchCallback 异步结果回调 |查询channel下某人的定制权限
`removeMemberRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID <li>callBack: FetchCallback 异步结果回调 |删除频道下某人的定制权限
`updateMemberRole` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accId: String 用户accID <li>auths: Map<QChatRoleResource, QChatRoleOption> 权限信息<li>callBack: FetchCallback 异步结果回调 |修改某人的定制权限
`updateEveryonePermissionForAnnounce` | <li>serverId: Long 社区ID<li>auths: Map<QChatRoleResource, QChatRoleOption> 权限信息<li>callBack: FetchCallback 异步结果回调 |更新公告频道订阅者的权限


### QChatChannelRepo

该类提供与话题相关的接口，示例代码如下：

```java 
QChatChannelRepo.fetchServerRolesByAccId(
        serverId,
        accId,
        0,
        QChatConstant.MEMBER_PAGE_SIZE,
        new FetchCallback<List<QChatServerRoleInfo>>() {
          @Override
          public void onSuccess(@Nullable List<QChatServerRoleInfo> param) {
            //成功的回调
          }

          @Override
          public void onFailed(int code) {
            // 失败回调
          }

          @Override
          public void onException(@Nullable Throwable exception) {
            // 失败回调
          }
        });

```
具体接口如下：
接口名称 |参数| 接口说明
:---- | :-------------- | :---------
`subscribeAsVisitor` |<li>serverIdList: Long 社区ID<li>channelIdList: List<Long> 话题ID列表<li>register: Boolean 注册或取消注册<li>callBack: FetchCallback 异步结果回调，可空 |以游客身份订阅话题
`fetchChannelUnreadInfoList` | <li>idPairList: List<QChatServerChannelIdPair> 话题ID列表 <li>callBack: FetchCallback 异步结果回调，可空 |查询未读信息
`fetchChannelsByServerId` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 通过分页接口查询频道
`fetchMaxChannelIdsByServerIdForVisitor` |<li> serverId: Long 社区ID<li>callBack: FetchCallback 异步结果回调 | 查询100个频道（分页限制最多100个）
`fetchChannelsByServerIdWithLastMessage` | <li>serverId: Long 社区ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 通过分页接口查询频道和频道里面最后的会话消息数据
`fetchServerRolesByAccId` | <li>serverId: Long 社区ID<li>accId: String 用户accID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 通过accid查询该accid所属的服务器身份组列表，结果只有自定义身份组，不包含everyone身份组
`createChannel` | <li>serverId: Long 社区ID<li>channelName: String 话题名称<li>topic: String 主题<li>mode: QChatChannelModeEnum 话题模式<li>type: QChatChannelTypeEnum 话题类型 <li>callBack: FetchCallback 异步结果回调 |创建话题
`fetchChannelInfo` | <li>channelId: Long 话题ID <li>callBack: FetchCallback 异步结果回调，可空 | 通过话题Id查询话题信息
`updateChannel` | <li>channelId: Long 话题ID <li>channelName: String 话题名称<li>topic: String 主题<li>callBack: FetchCallback 异步结果回调，可空 | 修改话题信息
`deleteChannel` | <li>channelId: Long 话题ID <li>callBack: FetchCallback 异步结果回调，可空 | 通过话题Id删除话题
`fetchChannelRoles` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 查询某话题下的身份组信息列表
`fetchChannelRoleMembers` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 查询某话题下的身份组信息列表
`fetchChannelMembers` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 通过分页接口查询话题成员
`fetchChannelBlackWhiteMembers` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>timeTag: Long 分页查询时间戳<li>type: QChatChannelModeEnum 话题模式<li> limit: Int 分页数量<li>callBack: FetchCallback 异步结果回调 | 分页查询话题黑白名单成员列表，公开话题查询黑名单，私有话题查询白名单
`addChannelBlackWhiteMembers` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>accIdList: List<String> 用户accID<li>callBack: FetchCallback 异步结果回调 | 添加话题黑白名单成员
`removeChannelBlackWhiteMembers` | <li>serverId: Long 社区ID<li>channelId: Long 话题ID<li>channelType: Int 话题类型<li>accIdList: List<String> 用户accID<li>callBack: FetchCallback 异步结果回调 | 添加话题黑白名单成员


### QChatMessageRepo
该类提供与圈组消息的接口，该类提供静态方法，可以直接使用，示例代码如下：

```java 
QChatMessageRepo.sendMessage(
        sendMessageParam,
        new FetchCallback<QChatMessageInfo>() {
          @Override
          public void onSuccess(@Nullable QChatMessageInfo param) {
           //成功的回调
          }

          @Override
          public void onFailed(int code) {
            // 失败回调
          }

          @Override
          public void onException(@Nullable Throwable exception) {
           // 失败回调
          }
        });

```

具体接口如下：

接口名称 |参数| 接口说明
:---- | :-------------- | :---------
`sendMessage` | <li>msg: QChatSendMessageParam 所发生消息参数信息<li>callBack: FetchCallback 异步结果回调 | 发送消息
`resendMessage` | <li>msg: QChatMessageInfo 消息对象<li>callBack: FetchCallback 异步结果回调 | 发送消息
`addQuickComment` | <li>msg: QChatMessageInfo 消息对象<li>comment: Int 快捷评论ID<li>callBack: FetchCallback 异步结果回调 | 添加一条快捷评论
`removeQuickComment` | <li>msg: QChatMessageInfo 消息对象<li>comment: Int 快捷评论ID<li>callBack: FetchCallback 异步结果回调 | 删除一条快捷评论
`getQuickComment` | <li>serverId: Long 社区ID<li> channelId: Long 话题ID<li> msgList: List<QChatMessageInfo> 消息对象<li>callBack: FetchCallback 异步结果回调 | 批量查询快捷评论
`markMessageRead` | <li>serverId: Long 社区ID<li> channelId: Long 话题ID<li> ackTime: Long 标记时间<li>callBack: FetchCallback 异步结果回调 | 标记消息已读，该接口存在频控，300ms内只能调用1次
`deleteMessage` | <li>msg: QChatMessageInfo 消息对象<li>callBack: FetchCallback 异步结果回调 | 删除消息
`revokeMessage` | <li>msg: QChatMessageInfo 消息对象<li>callBack: FetchCallback 异步结果回调 | 撤回消息
`revokeMessage` | <li>revokeParam: QChatRevokeMessageParam 消息参数<li>callBack: FetchCallback 异步结果回调 | 撤回消息
`downloadAttachment` | <li>msg: QChatMessageInfo 消息对象<li>thumb: Boolean 是否下载缩略图（图片消息）<li>callBack: FetchCallback 异步结果回调 | 下载消息附件，默认情况下（SDKOPtions::preloadAttach为true），DK收到多媒体消息后，图片和视频会自动下载缩略图，音频会自动下载文件。 如果下载原图或者原视频等，可调用该接口下载附件
`fetchMessageHistory` | <li>serverId: Long 社区ID<li> channelId: Long 话题ID<li> fromTime: Long 起始时间<li> toTime: Long 结束时间<li> limit: Int 查询数量<li>reverse: Boolean 查询结果是否翻转<li>callBack: FetchCallback 异步结果回调 | 标记消息已读，该接口存在频控，300ms内只能调用1次
`getMessageCache` | <li>serverId: Long 社区ID<li> channelId: Long 话题ID<li>reverse: Boolean 查询结果是否翻转<li>callBack: FetchCallback 异步结果回调 | 指定通道查询消息缓存
`getLastMessageOfChannels` | <li>serverId: Long 社区ID<li> channelIdList: List<Long> 话题ID<li>callBack: FetchCallback 异步结果回调 | 指定通道查询消息缓存
