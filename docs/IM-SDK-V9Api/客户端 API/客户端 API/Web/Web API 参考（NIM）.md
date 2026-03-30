本文介绍 Web SDK API 的概述性信息，并列出核心 API 与核心类或接口类，方便您查阅 API 信息。

- [`NIMInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html) 是 NIM SDK 的入口，负责建立长连接，登录，断开长连接，销毁实例、多端互踢等功能。
- [`EventInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html) 挂载了订阅发布事件相关的能力，如订阅，发布事件等。
- [`FriendInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html) 挂载了好友相关的 API，如获取，添加，申请，删除好友等。
- [`PassThroughInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_PassThroughInterface.PassThroughInterface.html) 挂载了透传协议。
- [`MessageExtendInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html) 挂载了消息扩展相关的 API，如 thread 消息。
- [`MessageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html) 挂载了消息相关的 API，如发送消息，发送文件消息，撤回，已读等。
- [`MessageLogInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html) 挂载了消息历史记录相关的 API，如查询历史消息。
- [`SessionInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html) 挂载了会话相关的 API，如查看会话，重置会话等
- [`SystemMessageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html) 挂载了系统消息相关的 API，如发送自定义系统通知。
- [`TeamInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html) 挂载了群相关的 API，如获取，创建，离开群，群成员管理。
- [`UserInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html) 挂载了用户及关系相关的 API，如黑名单，静音列表，我的名片。
- [`CloudSessionInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html) 挂载了云端会话服务相关的 API，如查询云端会话列表，查询某个云端会话
- [`CloudStorageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html) 挂载了云存储相关的 API，如上传并且预览文件、短链接转长链接
- [`SignalingInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html) 挂载了信令相关的 API，如创建，关闭频道
- [`SuperTeamInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html) 挂载了超级群相关的 API，如获取，创建，离开超级群
- [`MiscInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MiscInterface.MiscInterface.html) 挂载了杂项 API，如获取服务器时间戳（毫秒）
- [`PluginInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_PluginInterface.PluginInterface.html) 挂载了 NIM 扩展服务 API

## <span id="NIMGetInstance">NIM.getInstance</span>

下面是 [`NIM.getInstance`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance) 的初始化参数。这里只例举部分回调函数，完整初始化参数见 [`nim/types.NIMGetInstanceOptions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html)。

| 参数 | 说明 |
| ---- | ---- |
| [`NIMGetInstanceOptions.appKey`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#appKey) | <strong>[必填]</strong> 应用的 App Key，即您的应用在网易云信的账号 <br> <br><note type=notice>您可在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建 App Key。详情参考 <a href="https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console" target="_blank">创建应用</a>。</note> |
| [`NIMGetInstanceOptions.account`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#account) | <strong>[必填]</strong> 网易云信 IM 账号（又称 accid），即应用的用户在网易云信的唯一标识。<br><br> <note type=notice>应用本身的用户账号和网易云信的 IM 账号（accid）彼此独立。网易云信的 IM 账号只用于网易云信 IM 服务的鉴权，IM 账号并不等同于应用的用户账号。</note> |
| [`NIMGetInstanceOptions.token`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#token) | <strong>[必填]</strong> IM 账号的登录凭证 <br> 该登录凭证只会在登录 IM （建立 SDK 与网易云信服务端的长连接）时校验一次。 |
| [`NIMGetInstanceOptions.onconnect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onconnect) | SDK 与网易云信服务端建立长连接的回调 |
| [`NIMGetInstanceOptions.onwillreconnect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onwillreconnect) | SDK 与网易云信服务端即将重连的回调 |
| [`NIMGetInstanceOptions.ondisconnect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#ondisconnect) | SDK 与网易云信服务端断开连接的回调 |
| [`NIMGetInstanceOptions.onsyncdone`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsyncdone) | 初始化同步完成的回调 |
| [`NIMGetInstanceOptions.onerror`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onerror) | 初始化阶段发生错误的回调 |
| [`NIMGetInstanceOptions.onloginportschange`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onloginportschange) | 多端登录状态变化的回调 |
| [`NIMGetInstanceOptions.onsessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsessions) | 初始化同步时，接收会话列表的回调 |
| [`NIMGetInstanceOptions.onupdatesessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onupdatesessions) | 在线时批量更新会话的回调 |
| [`NIMGetInstanceOptions.onStickTopSessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onStickTopSessions) | 初始化同步或在线时，接收远端置顶会话的回调 |
| [`NIMGetInstanceOptions.onroamingmsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onroamingmsgs) | 初始化同步时，接收漫游消息的回调 |
| [`NIMGetInstanceOptions.onofflinemsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onofflinemsgs) | 初始化同步时，接收离线消息的回调 |
| [`NIMGetInstanceOptions.onmsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onmsg) | 多端同步或在线时，接收消息的回调 |
| [`NIMGetInstanceOptions.onofflinesysmsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onofflinesysmsgs) | 初始化同步时，接收离线系统通知的回调 |
| [`NIMGetInstanceOptions.onroamingsysmsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onroamingmsgs) | 初始化同步时，接收漫游的系统通知的回调 |
| [`NIMGetInstanceOptions.onDeleteMsgSelf`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onDeleteMsgSelf) | 多端同步时，单向删除消息的回调 <br> <note type=note> 用户在设备端 A 调用 deleteMsgSelf 或 deleteMsgSelfBatch 后，如果使用同一 IM 账号在设备端 B 登录，可通过该回调在设备端 B 收到消息被删除的通知。</note> |
| [`NIMGetInstanceOptions.onbroadcastmsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onbroadcastmsgs) | 初始化同步时，接收离线广播消息的回调 |
| [`NIMGetInstanceOptions.onbroadcastmsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onbroadcastmsgs) | 在接收接收广播消息的回调 |
| [`NIMGetInstanceOptions.onTeamMsgReceipt`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onTeamMsgReceipt) | 在线接收群消息已读回执通知的回调 |
| [`NIMGetInstanceOptions.onsysmsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsysmsg) | 在线接收系统通知的回调 |
| [`NIMGetInstanceOptions.onupdatesysmsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onupdatesysmsg) | 在线接收系统通知更新的回调 |
| [`NIMGetInstanceOptions.oncustomsysmsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#oncustomsysmsg) | 在线接收自定义系统通知的回调 |
| [`NIMGetInstanceOptions.onofflinecustomsysmsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onofflinecustomsysmsgs) | 初始化同步时，接收离线自定义系统通知的回调 |
| [`NIMGetInstanceOptions.onsysmsgunread`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsysmsgunread) | 初始化同步时，接收系统通知未读数的回调 |
| [`NIMGetInstanceOptions.onupdatesysmsgunread`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onupdatesysmsgunread) | 在线接收系统通知未读数变更的回调 |
| [`NIMGetInstanceOptions.onpushevents`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onpushevents) | 订阅事件的回调<br>用户通过该回调在初始化同步或者在线时接收从网易云信服务端下推的订阅事件。 |
| [`NIMGetInstanceOptions.onQuickComment`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onQuickComment) | 在线或多端同步时，接收 **添加快捷评论通知** 的回调 |
| [`NIMGetInstanceOptions.onDeleteQuickComment`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onDeleteQuickComment) | 在线或多端同步时，接收 **删除快捷评论通知** 的回调 |
| [`NIMGetInstanceOptions.onPinMsgChange`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onPinMsgChange) | 在线或多端同步时，接收 **消息置顶通知** 的回调 |
| [`NIMGetInstanceOptions.onClearServerHistoryMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onClearServerHistoryMsgs) | 多端同步或初始化同步时，接收 **清除会话历史消息** 通知的回调 |
| [`NIMGetInstanceOptions.onSyncUpdateServerSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onSyncUpdateServerSession) | 多端同步时，接收 **云端会话更新** 通知的回调 |
| [`NIMGetInstanceOptions.onblacklist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onblacklist) | 初始化时同步黑名单列表的回调 |
| [`NIMGetInstanceOptions.onsyncmarkinblacklist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsyncmarkinblacklist) | 多端同步时，接收 **拉黑/移出黑名单** 事件的回调 |
| [`NIMGetInstanceOptions.onmutelist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onmutelist) | 初始化时同步 **静音列表** 的回调。 |
| [`NIMGetInstanceOptions.onsyncmarkinmutelist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsyncmarkinmutelist) | 多端同步时，接收 **把某人静音的事件** 的回调 |
| [`NIMGetInstanceOptions.onfriends`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onfriends) | 同步好友列表的回调，会传入好友列表 |
| [`NIMGetInstanceOptions.onsyncfriendaction`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsyncfriendaction) | 多端同步时，接收好友动作的回调。好友动作包括添加好友、好友申请、通过好友申请、拒绝好友申请、删除好友和更新好友备注。 |
| [`NIMGetInstanceOptions.onmyinfo`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onmyinfo) | 初始化时同步自己的用户名片的回调。 |
| [`NIMGetInstanceOptions.onupdatemyinfo`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onupdatemyinfo) | 多端同步时，接收自己的用户名片更新的回调 |
| [`NIMGetInstanceOptions.onSuperTeams`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onSuperTeams) | 初始化同步时，接收超级群列表的回调 |
| [`NIMGetInstanceOptions.onSyncCreateSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onSyncCreateSuperTeam) | 多端同步时，接收 **创建超级群** 通知的回调 |
| [`NIMGetInstanceOptions.onUpdateSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateSuperTeam) | 在线或多端同步时，接收 **更新超级群的通知** 的回调 |
| [`NIMGetInstanceOptions.onDismissSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onDismissSuperTeam) | 在线或多端同步时，接收 **解散超级群的通知** 的回调 |
| [`NIMGetInstanceOptions.onTransferSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onTransferSuperTeam) | 在线或多端同步时，接收 **转让超级群的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateSuperTeamMember`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateSuperTeamMember) | 在线或多端同步时，接收 **超级群成员的信息变更** 的回调 |
| [`NIMGetInstanceOptions.onAddSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onAddSuperTeamMembers) | 在线或多端同步时，接收 **添加超级群成员的通知** 的回调 |
| [`NIMGetInstanceOptions.onRemoveSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onRemoveSuperTeamMembers) | 在线或多端同步时，接收 **删除超级群成员的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateSuperTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateSuperTeamManagers) | 在线或多端同步时，接收 **更新超级群管理员的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateSuperTeamMembersMute`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateSuperTeamMembersMute) | 在线或多端同步时，接收 **超级群成员被静音的通知** 的回调 |
| [`NIMGetInstanceOptions.onteams`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onteams) | 初始化时同步群列表的回调 |
| [`NIMGetInstanceOptions.onsynccreateteam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onsynccreateteam) | 多端同步时，接收 **创建群的通知** 的回调 |
| [`NIMGetInstanceOptions.onCreateTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onCreateTeam) | 在线或多端同步时，接收 **创建群的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateTeam) | 在线或多端同步时，接收 **更新群的通知** 的回调 |
| [`NIMGetInstanceOptions.onDismissTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onDismissTeam) | 在线或多端同步时，接收 **解散群的通知** 的回调 |
| [`NIMGetInstanceOptions.onTransferTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onTransferTeam) | 在线或多端同步时，接收 **转让群的通知** 的回调 |
| [`NIMGetInstanceOptions.onupdateteammember`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onupdateteammember) | 在线或多端同步时，接收 **群成员的信息变更** 的回调 |
| [`NIMGetInstanceOptions.onAddTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onAddTeamMembers) | 在线或多端同步时，接收 **添加群成员的通知** 的回调 |
| [`NIMGetInstanceOptions.onRemoveTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onRemoveTeamMembers) | 在线或多端同步时，接收 **删除群成员的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateTeamManagers) | 在线或多端同步时，接收 **更新群管理员的通知** 的回调 |
| [`NIMGetInstanceOptions.onUpdateTeamMembersMute`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_types.NIMGetInstanceOptions.html#onUpdateTeamMembersMute) | 在线或多端同步时，接收 **群成员被静音的通知** 的回调 |

## <span id="NIMInterface">NIMInterface</span>

NIM SDK 的入口，负责建立长连接，登录，断开长连接，销毁实例、多端互踢等功能，完整的 API 请参考 [`NIMInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`logout`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#logout) | 退出登录 | [`V2NIMLoginService.logout`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout)
| [`disconnect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#disconnect) | 断开 SDK 与网易云信服务端的长连接 | 无 |
| [`connect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#connect) | 建立长连接，并且登录 | 无 |
| [`destroy`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#destroy) | 销毁实例 | 同 V9 API |
| [`kick`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#kick) | 将当前用户登录的其它端踢下线 | [`V2NIMLoginService.kickOffline`](https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#kickOffline) |
| [`setOptions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#setOptions) | 更新初始化配置 | 同 V9 API |

## <span id="MessageInterface">MessageInterface</span>

消息相关的 API，如发送消息，发送文件消息，撤回，已读等，完整的 API 请参考 [`MessageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`sendText`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendText) | 发送文本消息 | <li> [`V2NIMMessageCreator.createTextMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTextMessage) <li>[`V2NIMMessageService.sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`sendFile`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendFile) | 发送文件消息 | <li> [`V2NIMMessageCreator.createFileMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createFileMessage) <li>[`V2NIMMessageServicesendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`sendCustomMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendCustomMsg) | 发送自定义消息 | <li> [`V2NIMMessageCreator.createCustomMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessage) <li>[`V2NIMMessageService.sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`sendGeo`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendGeo) | 发送地理位置消息 | <li> [`V2NIMMessageCreator.createLocationMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createLocationMessage) <li>[`V2NIMMessageService.sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`sendTipMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendTipMsg) | 发送提醒消息 | <li> [`V2NIMMessageCreator.createTipsMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTipsMessage) <li>[`V2NIMMessageService.sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`resendMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#resendMsg) | 重发消息 | 无 |
| [`forwardMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#forwardMsg) | 转发消息 | <li> [`V2NIMMessageCreator.createForwardMessage`](https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createForwardMessage) <li>[`V2NIMMessageService.sendMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage) |
| [`V2NIMMessageService.sendMsgReceipt`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendMsgReceipt) | 发送单聊消息的已读回执 | [`V2NIMMessageService.sendP2PMessageReceipt`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendP2PMessageReceipt) |
| [`sendTeamMsgReceipt`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#sendTeamMsgReceipt) | 发送群消息（高级群）的已读回执 | [`V2NIMMessageService.sendTeamMessageReceipts`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendTeamMessageReceipts) |
| [`getTeamMsgReads`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#getTeamMsgReads) | 查询群组消息的已读、未读数量 | [`V2NIMMessageService.getTeamMessageReceipts`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceipts) |
| [`getTeamMsgReadAccounts`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#getTeamMsgReadAccounts) | 查询群消息已读的账号 | [`V2NIMMessageService.getTeamMessageReceiptDetail`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceiptDetail) |
| [`recallMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#recallMsg) | 撤回消息 | [`V2NIMMessageService.revokeMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage) |
| [`deleteMsgSelf`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#deleteMsgSelf) | 单向删除消息 | [`V2NIMMessageService.deleteMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessage) |
| [`deleteMsgSelfBatch`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.MessageInterface.html#deleteMsgSelfBatch) | 批量单向删除消息 | [`V2NIMMessageService.deleteMessages`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages) |

## <span id="MessageLogInterface">MessageLogInterface</span>

消息历史记录相关的 API，如查询历史消息，完整的 API 请参考 [`MessageLogInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getHistoryMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#getHistoryMsgs) | 获取云端的消息历史记录 | [`V2NIMMessageService.getMessageList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList) |
| [`clearServerHistoryMsgsWithSync`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#clearServerHistoryMsgsWithSync) | 删除某个会话的云端消息历史记录，与漫游记录 | [`V2NIMMessageService.clearHistoryMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage) |
| [`msgFtsInServer`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#msgFtsInServer) | 云端全文检索消息(full text search)。返回的消息会按会话 session 分类返回 | [`V2NIMMessageService.searchCloudMessages`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages) |
| [`msgFtsInServerByTiming`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#msgFtsInServerByTiming) | 云端全文检索消息-按时间分页搜索。返回的消息结果按时间自然排序 | [`V2NIMMessageService.searchCloudMessages`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages) |
| [`getLocalMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#getLocalMsgs) | 获取本地数据库的消息记录 | [`V2NIMMessageService.getMessageList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList) |
| [`getLocalMsgsByIdClients`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#getLocalMsgsByIdClients) | 获取 `idClients` 对应的本地消息列表 | [`V2NIMMessageService.getMessageListByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByIds) |
| [`updateLocalMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#updateLocalMsg) | 更新本地消息。仅允许更新 `localCustom` 本地自定义扩展字段 | 无 |
| [`deleteLocalMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#deleteLocalMsg) | 删除某一条本地消息 | 无 |
| [`deleteLocalMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#deleteLocalMsgs) | 按条件删除消息 | 无 |
| [`deleteLocalMsgsBySession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#deleteLocalMsgsBySession) | 删除某个会话下所有的本地消息 | 无 |
| [`deleteAllLocalMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#deleteAllLocalMsgs) | 删除所有的本地消息 | 无 |
| [`saveMsgsToLocal`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageLogInterface.MessageLogInterface.html#saveMsgsToLocal) | 将消息存储至本地数据库 | 无 |

## <span id="EventInterface">EventInterface</span>

订阅发布事件相关的能力，如订阅，发布事件等，完整的 API 请参考 [`EventInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`publishEvent`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#publishEvent) | 发布某事件 | 无 |
| [`subscribeEvent`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#subscribeEvent) | 订阅某事件 | 无 |
| [`unSubscribeEventsByAccounts`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#unSubscribeEventsByAccounts) | 按账号取消订阅关系 | 无 |
| [`querySubscribeEventsByAccounts`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#querySubscribeEventsByAccounts) | 按账号获取指定事件的订阅关系 | 无 |
| [`unSubscribeEventsByType`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#unSubscribeEventsByType) | 取消指定事件的全部订阅关系 | 无 |
| [`querySubscribeEventsByAccounts`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#querySubscribeEventsByAccounts) | 按账号获取指定事件的订阅关系 | 无 |
| [`querySubscribeEventsByType`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_EventInterface.EventInterface.html#querySubscribeEventsByType) | 获取指定事件的订阅关系 | 无 |

## <span id="FriendInterface">FriendInterface</span>

好友相关的 API，如获取，添加，申请，删除好友等，完整的 API 请参考 [`FriendInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getFriends`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#getFriends) | 获取好友 | <li> [`V2NIMFriendService.getFriendList`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendList) <li>[`V2NIMFriendService.getFriendByIds`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendByIds) |
| [`addFriend`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#addFriend) | 直接加为好友 | [`V2NIMFriendService.addFriend`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend) |
| [`applyFriend`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#applyFriend) | 申请加为好友 | [`V2NIMFriendService.addFriend`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend) |
| [`passFriendApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#passFriendApply) | 通过好友申请 | [`V2NIMFriendService.acceptAddApplication`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#acceptAddApplication) |
| [`rejectFriendApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#rejectFriendApply) | 拒绝好友申请 | [`V2NIMFriendService.rejectAddApplication`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#rejectAddApplication) |
| [`deleteFriend`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#deleteFriend) | 删除好友 | [`V2NIMFriendService.deleteFriend`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteFriend) |
| [`updateFriend`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#updateFriend) | 更新好友 | [`V2NIMFriendService.setFriendInfo`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setFriendInfo) |
| [`isMyFriend`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_FriendInterface.FriendInterface.html#isMyFriend) | 是否为我的好友 | [`V2NIMFriendService.checkFriend`](https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#checkFriend) |

## <span id="PassThroughInterface">PassThroughInterface</span>

透传协议，完整的 API 请参考 [`PassThroughInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_PassThroughInterface.PassThroughInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`httpRequestProxy`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_PassThroughInterface.PassThroughInterface.html#httpRequestProxy) | 透传协议 | 无 |

## <span id="MessageExtendInterface">MessageExtendInterface</span>

消息扩展相关的 API，如 thread 消息，完整的 API 请参考 [`MessageExtendInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getThreadMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#getThreadMsgs) | 获取 thread 消息列表 | [`V2NIMMessageService.getMessageListByRefers`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByRefers) |
| [`getMsgsByIdServer`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#getMsgsByIdServer) | 通过消息 ID 等信息批量查询历史消息，thread 聊天专用 | [`V2NIMMessageService.getMessageListByRefers`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByRefers) |
| [`addQuickComment`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#addQuickComment) | 添加快捷评论 | [`V2NIMMessageService.addQuickComment`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addQuickComment) |
| [`deleteQuickComment`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#deleteQuickComment) | 删除快捷评论 | [`V2NIMMessageService.removeQuickComment`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeQuickComment) |
| [`getQuickComments`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#getQuickComments) | 批量查询消息的快捷评论 | [`V2NIMMessageService.getQuickCommentList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getQuickCommentList) |
| [`addCollect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#addCollect) | 添加收藏 | [`V2NIMMessageService.addCollection`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addCollection) |
| [`deleteCollects`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#deleteCollects) | 删除收藏。返回结果为被成功删除的收藏个数 | [`V2NIMMessageService.removeCollections`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeCollections) |
| [`updateCollect`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#updateCollect) | 更新收藏，只能更新 `custom` 字段 | [`V2NIMMessageService.updateCollectionExtension`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateCollectionExtension) |
| [`getCollects`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#getCollects) | 查询收藏列表 | [`V2NIMMessageService.getCollectionListByOption`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListByOption) |
| [`addMsgPin`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#addMsgPin) | Pin 住一条消息 | [`V2NIMMessageService.pinMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#pinMessage) |
| [`updateMsgPin`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#updateMsgPin) | 更新被 Pin 的消息 | [`V2NIMMessageService.updatePinMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updatePinMessage) |
| [`deleteMsgPin`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#deleteMsgPin) | 取消消息的 Pin 状态 | [`V2NIMMessageService.unpinMessage`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unpinMessage) |
| [`getMsgPins`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageExtendInterface.MessageExtendInterface.html#getMsgPins) | 查询某会话下的 Pin 消息列表 | [`V2NIMMessageService.getPinnedMessageList`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getPinnedMessageList) |

## <span id="SessionInterface">SessionInterface</span>

会话相关的 API，如查看会话，重置会话等，完整的 API 请参考 [`SessionInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getLocalSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#getLocalSession) | 通过 `sessionId` 获取本地数据库里的会话 | [`V2NIMConversationService.getConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversation) |
| [`getLocalSessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#getLocalSessions) | 分页查询本地数据库里的会话列表 | <li> [`V2NIMConversationService.getConversationList`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList) <li>[`V2NIMConversationService.getConversationListByOption`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByOption) |
| [`insertLocalSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#insertLocalSession) | 往本地数据库中插入一条会话记录 | 无 |
| [`updateLocalSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#updateLocalSession) | 更新本地数据库里的会话 | 无 |
| [`deleteLocalSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#deleteLocalSession) | 删除指定的本地数据库会话 | 无 |
| [`setCurrSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#setCurrSession) | 设置 **进入当前会话** | [`V2NIMConversationService.clearUnreadCountByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) |
| [`resetCurrSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#resetCurrSession) | 取消 `setCurrSession` 的效果 | 无 |
| [`resetSessionUnread`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#resetSessionUnread) | 重置某个会话的未读数 | [`V2NIMConversationService.clearUnreadCountByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) |
| [`resetSessionsUnread`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#resetSessionsUnread) | 重置某些会话的未读数 | [`V2NIMConversationService.clearUnreadCountByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) |
| [`resetAllSessionUnread`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#resetAllSessionUnread) | 重置所有会话的未读数 | [`V2NIMConversationService.clearUnreadCountByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds) |
| [`getStickTopSessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#getStickTopSessions) | 获取云端置顶会话的列表 | [`V2NIMConversationService.getConversationListByOption`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByOption) |
| [`addStickTopSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#addStickTopSession) | 添加云端置顶的会话 | [`V2NIMConversationService.stickTopConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation) |
| [`deleteStickTopSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#deleteStickTopSession) | 取消云端置顶的会话 | [`V2NIMConversationService.stickTopConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation) |
| [`updateStickTopSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.SessionInterface.html#updateStickTopSession) | 更新云端置顶的会话（目前仅能更新它的扩展字段） | [`V2NIMConversationService.updateConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversation) |

## <span id="SystemMessageInterface">SystemMessageInterface</span>

系统消息相关的 API，如发送自定义系统通知，完整的 API 请参考 [`SystemMessageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`sendCustomSysMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#sendCustomSysMsg) | 发送自定义系统通知 | [`V2NIMNotificationService.sendCustomNotification`](https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#sendCustomNotification) |
| [`markSysMsgRead`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#markSysMsgRead) | 向服务器回包标记系统消息端测已读，下次服务器不需要将此消息作离线系统消息发下来 | 无 |
| [`getLocalSysMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#getLocalSysMsgs) | 获取本地数据库里的系统通知 | 无 |
| [`updateLocalSysMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#updateLocalSysMsg) | 更新本地数据库里的系统通知 | 无 |
| [`deleteLocalSysMsg`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#deleteAllLocalSysMsgs) | 删除本地数据库里的系统通知 | 无 |
| [`deleteAllLocalSysMsgs`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SystemMessageInterface.SystemMessageInterface.html#deleteAllLocalSysMsgs) | 删除所有本地数据库里的系统通知 | 无 |

## <span id="TeamInterface">TeamInterface</span>

群相关的 API，如获取，创建，离开群，群成员管理，完整的 API 请参考 [`TeamInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeam) | 获取群 | [`V2NIMTeamService.getTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo) |
| [`getTeams`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeams) | 获取群列表 | [`V2NIMTeamService.getJoinedTeamList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList) |
| [`getTeamsById`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamsById) | 通过一批 `teamId` 来获取若干个群 | [`V2NIMTeamService.getTeamInfoByIds`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfoByIds) |
| [`createTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#createTeam) | 创建群 | [`V2NIMTeamService.createTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#createTeam) |
| [`updateTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#updateTeam) | 更新群 | [`V2NIMTeamService.updateTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo) |
| [`transferTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#transferTeam) | 转让群，群主可操作 | [`V2NIMTeamService.transferTeamOwner`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner) |
| [`dismissTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#dismissTeam) | 解散群，群主可操作 | [`V2NIMTeamService.dismissTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#dismissTeam) |
| [`leaveTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#leaveTeam) | 主动退群 | [`V2NIMTeamService.leaveTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam) |
| [`muteTeamAll`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#muteTeamAll) | 群组全体禁言 | [`V2NIMTeamService.setTeamChatBannedMode`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode) |
| [`getTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamMembers) | 获取群成员 | [`V2NIMTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) |
| [`getMutedTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getMutedTeamMembers) | 获取群禁言成员列表 | [`V2NIMTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) |
| [`addTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#addTeamMembers) | 添加群成员 | [`V2NIMTeamService.inviteMember`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember) |
| [`acceptTeamInvite`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#acceptTeamInvite) | （用户）接受群邀请 | [`V2NIMTeamService.acceptInvitation`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation) |
| [`rejectTeamInvite`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#rejectTeamInvite) | （用户）拒绝群邀请 | [`V2NIMTeamService.rejectInvitation`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation) |
| [`removeTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#removeTeamMembers) | 踢人出群 | [`V2NIMTeamService.kickMember`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember) |
| [`addTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#addTeamManagers) | 添加群管理员 | [`V2NIMTeamService.updateTeamMemberRole`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) |
| [`removeTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#removeTeamMembers) | 移除群管理员 | [`V2NIMTeamService.updateTeamMemberRole`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) |
| [`updateInfoInTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#updateInfoInTeam) | 修改自己在群里的信息 | [`V2NIMTeamService.updateSelfTeamMemberInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo) |
| [`updateNickInTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#updateNickInTeam) | 修改别人的群昵称 | [`V2NIMTeamService.updateTeamMemberNick`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick) |
| [`updateMuteStateInTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#updateMuteStateInTeam) | 更新群成员禁言状态 | [`V2NIMTeamService.setTeamMemberChatBannedStatus`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus) |
| [`getTeamMemberByTeamIdAndAccount`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamMemberByTeamIdAndAccount) | 通过群 ID 及成员账号获取群成员信息 | [`V2NIMTeamService.getTeamMemberListByIds`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds) |
| [`getTeamMemberInvitorAccid`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#getTeamMemberInvitorAccid) | 获取群成员的邀请者 accid | [`V2NIMTeamService.getTeamMemberInvitor`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberInvitor) |
| [`applyTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#applyTeam) | 申请入群 | [`V2NIMTeamService.applyJoinTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam) |
| [`passTeamApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#passTeamApply) | 通过群申请 | [`V2NIMTeamService.acceptJoinApplication`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication) |
| [`rejectTeamApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.TeamInterface.html#rejectTeamApply) | （管理员）拒绝群申请 | [`V2NIMTeamService.rejectJoinApplication`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication) |

## <span id="UserInterface">UserInterface</span>

用户及关系相关的 API，如黑名单，静音列表，我的名片，完整的 API 请参考 [`UserInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getUser`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#getUser) | 获取用户名片 | [`V2NIMUserService.getUserList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList) |
| [`getUsers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#getUsers) | 获取一批用户的名片，每次最多 150 个 | [`V2NIMUserService.getUserList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList) |
| [`updateMyInfo`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#updateMyInfo) | 更新我的名片 | [`V2NIMUserService.updateSelfUserProfile`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList) |
| [`isUserInBlackList`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#updateSelfUserProfile) | 查看某人是否在当前用户在黑名单里 | [`V2NIMUserService.getBlockList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList) |
| [`getRelations`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#getRelations) | 获取关系(黑名单和静音列表) | <li> [`V2NIMUserService.getBlockList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList) <li>[`V2NIMUserService.getP2PMessageMuteList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getP2PMessageMuteList) |
| [`addToBlacklist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#addToBlacklist) | 加入黑名单 | [`V2NIMUserService.addUserToBlockList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#addUserToBlockList) |
| [`removeFromBlacklist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#removeFromMutelist) | 移出黑名单 | [`V2NIMUserService.removeUserFromBlockList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#removeUserFromBlockList) |
| [`addToMutelist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#addToMutelist) | 加入静音列表 | [`V2NIMUserService.setP2PMessageMuteMode`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#setP2PMessageMuteMode) |
| [`removeFromMutelist`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#removeFromMutelist) | 移出静音列表 | [`V2NIMUserService.setP2PMessageMuteMode`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#setP2PMessageMuteMode) |
| [`isUserInBlackList`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_UserInterface.UserInterface.html#isUserInBlackList) | 查看某人是否在当前用户在黑名单里 | [`V2NIMUserService.getBlockList`](https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList) |

## <span id="CloudSessionInterface">CloudSessionInterface</span>

这里只例举部分 API，完整的 API 请参考 [`CloudSessionInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getServerSessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html#getServerSessions) | 查询云端会话列表 | [`V2NIMConversationService.getConversationList`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList) |
| [`getServerSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html#getServerSession) | 查询某个云端会话 | [`V2NIMConversationService.getConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversation) |
| [`updateServerSession`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html#updateServerSession) | 更新云端会话 | [`V2NIMConversationService.updateConversation`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversation) |
| [`deleteServerSessions`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_CloudSessionInterface.CloudSessionInterface.html#deleteServerSessions) | 删除云端会话列表 | [`V2NIMConversationService.deleteConversationListByIds`](https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversationListByIds) |

## <span id="CloudStorageInterface">CloudStorageInterface</span>

云端会话服务相关的 API，如查询云端会话列表，查询某个云端会话，完整的 API 请参考 [`CloudStorageInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`previewFile`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#previewFile) | 上传并且预览文件 | [`V2NIMStorageService.uploadFile`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#uploadFile) |
| [`getNosOriginUrl`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#getNosOriginUrl) | 短链接转长链接 | [`V2NIMStorageService.shortUrlToLong`](https://doc.yunxin.163.com/messaging2/client-apis/zQ0MDc5MjI?platform=client#shortUrlToLong) |
| [`audioToText`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#audioToText) | 音频转文字 | [`V2NIMMessageService.voiceToText`](https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#voicetotext) |
| [`stripImageMeta`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#stripImageMeta) | 去除图片元信息 | 无 |
| [`qualityImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#qualityImage) | 修改图片质量 | 无 |
| [`interlaceImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#interlaceImage) | interlace 图片 | 无 |
| [`rotateImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#rotateImage) | 旋转图片 | 无 |
| [`blurImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#blurImage) | 模糊图片 | 无 |
| [`cropImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#cropImage) | 剪裁图片 | 无 |
| [`thumbnailImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#thumbnailImage) | 生成图片的略缩图 | 无 |
| [`processImage`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#processImage) | 处理图片 | 无 |

## <span id="SignalingInterface">SignalingInterface</span>

信令相关的 API，如创建，关闭频道，详细内容见 [`SignalingInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html)。

信令相关的事件通过 `nim.on` 监听，详细内容见 [`NIMSignalingEventInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.NIMSignalingEventInterface.html)。
| 事件 | 功能描述
| --- | --- |
| [`signalingNotify`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.NIMSignalingEventInterface.html#signalingNotify) | 收到在线通知
| [`signalingMutilClientSyncNotify`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.NIMSignalingEventInterface.html#signalingMutilClientSyncNotify) | 收到多端同步通知
| [`signalingChannelsSyncNotify`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.NIMSignalingEventInterface.html#signalingChannelsSyncNotify) | 收到频道成员变更同步
| [`signalingUnreadMessageSyncNotify`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.NIMSignalingEventInterface.html#signalingUnreadMessageSyncNotify) | 收到未读信令消息通知

它的使用方式如

```js
nim.on('signalingNotify', (res) => {
  console.log('收到在线通知', res)
})
```

<style>
table th:first-of-type {
    width: 10%;
}
table th:nth-of-type(2) {
    width: 10%;
}
</style>

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> |
| ---- | ---- |
| [`signalingCallEx`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingCallEx) | 呼叫加入音视频频道：创建一个频道，己方加入，并邀请对方加入音视频的频道。 |
| [`signalingCall`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingCall) | 呼叫：创建一个频道，己方加入，并邀请对方加入频道。 |
| [`signalingCreateAndJoin`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingCreateAndJoin) | 如果不存在房间，则创建一个频道，并且己方加入。如果已存在频道，则己方直接加入。 |
| [`signalingCreate`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingCreate) | 创建频道 |
| [`signalingDelay`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingDelay) | 延长频道的有效期 |
| [`signalingClose`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingClose) | 关闭频道 |
| [`signalingGetChannelInfo`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingGetChannelInfo) | 查询频道信息。根据 `channelName` 查询房间信息。 |
| [`signalingJoin`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingJoin) | 加入频道 |
| [`signalingLeave`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingLeave) | 离开频道 |
| [`signalingInvite`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingInvite) | 邀请某人进入频道 |
| [`signalingCancel`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingCancel) | 取消邀请 |
| [`signalingReject`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingReject) | 拒绝进入频道的邀请 |
| [`signalingAccept`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingAccept) | 接受进入频道的邀请 |
| [`signalingMarkMsgRead`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingAccept) | 标记信令消息已收到, 下次不会在离线同步中收到此消息 |
| [`signalingControl`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingControl) | 发送自定义信令 |
| [`signalingJoinAndAccept`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SignalingInterface.SignalingInterface.html#signalingJoinAndAccept) | 加入频道并接受邀请 |

## <span id="SuperTeamInterface">SuperTeamInterface</span>

超级群相关的 API，如获取，创建，离开超级群，完整的 API 请参考 [`SuperTeamInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`getSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getSuperTeam) | 获取超级群 | [`V2NIMTeamService.getTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo) |
| [`getSuperTeams`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getSuperTeams) | 获取超级群列表 | [`V2NIMTeamService.getJoinedTeamList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList) |
| [`updateSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#updateSuperTeam) | 更新超级群 | [`V2NIMTeamService.updateTeamInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo) |
| [`transferSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#transferSuperTeam) | 转让超级群，群主可操作 | [`V2NIMTeamService.transferTeamOwner`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner) |
| [`leaveSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#leaveSuperTeam) | 主动退出超级群 | [`V2NIMTeamService.leaveTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam) |
| [`updateSuperTeamMute`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#updateSuperTeamMute) | 超级群全体禁言 | [`V2NIMTeamService.setTeamChatBannedMode`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode) |
| [`getSuperTeamMembersByJoinTime`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getSuperTeamMembersByJoinTime) | 分页获取超级群成员 | [`V2NIMTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) |
| [`getSuperTeamMembersByAccounts`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getSuperTeamMembersByAccounts) | 通过一批 account ID 获取若干个超级群 | [`V2NIMTeamService.getTeamMemberListByIds`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds) |
| [`getAllSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getAllSuperTeamMembers) | 获取全部超级群成员，数据量非常多时会分多次 done 返回 | [`V2NIMTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) |
| [`getMutedSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#getMutedSuperTeamMembers) | 获取超级群禁言成员列表 | [`V2NIMTeamService.getTeamMemberList`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList) |
| [`addSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#addSuperTeamMembers) | 添加超级群的成员 | [`V2NIMTeamService.inviteMember`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember) |
| [`acceptSuperTeamInvite`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#acceptSuperTeamInvite) | （用户）接受超级群邀请 | [`V2NIMTeamService.acceptInvitation`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation) |
| [`rejectSuperTeamInvite`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#rejectSuperTeamInvite) | （用户）拒绝超级群的邀请 | [`V2NIMTeamService.rejectJoinApplication`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication) |
| [`removeSuperTeamMembers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#removeSuperTeamMembers) | 踢人出超级群 | [`V2NIMTeamService.kickMember`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember) |
| [`addSuperTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#addSuperTeamManagers) | 添加超级群的管理员 | [`V2NIMTeamService.updateTeamMemberRole`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) |
| [`removeSuperTeamManagers`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#removeSuperTeamManagers) | 移除超级群的管理员 | [`V2NIMTeamService.updateTeamMemberRole`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole) |
| [`updateNickInSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#updateNickInSuperTeam) | 修改别人的超级群的昵称 | [`V2NIMTeamService.updateTeamMemberNick`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick) |
| [`updateInfoInSuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#updateInfoInSuperTeam) | 修改自己在超级群里的信息 | [`V2NIMTeamService.updateSelfTeamMemberInfo`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo) |
| [`updateSuperTeamMembersMute`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#updateSuperTeamMembersMute) | 更新超级群成员禁言状态 | [`V2NIMTeamService.setTeamMemberChatBannedStatus`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus) |
| [`applySuperTeam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#applySuperTeam) | 申请入超级群 | [`V2NIMTeamService.applyJoinTeam`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam) |
| [`passSuperTeamApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#passSuperTeamApply) | （管理员）通过超级群申请 | [`V2NIMTeamService.acceptJoinApplication`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication) |
| [`rejectSuperTeamApply`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_SuperTeamInterface.SuperTeamInterface.html#rejectSuperTeamApply) | （管理员）拒绝超级群申请 | [`V2NIMTeamService.rejectJoinApplication`](https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication) |

## <span id="MiscInterface">MiscInterface</span>

一些其它的接口，完整的 API 请参考 [`MiscInterface`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MiscInterface.MiscInterface.html)。

| <div style="width:150px;">方法</div> | <div style="width:250px;">功能描述</div> | 对应 V10 API |
| ---- | ---- | ---- |
| [`filterClientAntispam`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MiscInterface.MiscInterface.html#filterClientAntispam) | 检查客户端反垃圾 | [`V2NIMClientAntispamUtil.checkTextAntispam`](https://doc.yunxin.163.com/messaging2/client-apis/DAxNjk0Mzc?platform=client#v2nimclientantispamutil) |
| [`getClientAntispamLexicon`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MiscInterface.MiscInterface.html#getClientAntispamLexicon) | 获取反垃圾词库 | 无 |
| [`getServerTime`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/interfaces/nim_MiscInterface.MiscInterface.html#getServerTime) | 获取服务器时间戳 | 无 |