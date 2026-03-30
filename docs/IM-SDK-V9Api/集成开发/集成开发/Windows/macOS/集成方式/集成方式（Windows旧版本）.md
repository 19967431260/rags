
### <span id="快速集成">快速集成</span>
关于如何快速集成SDK到现有项目，初始化SDK登录退出，发送/接收第一条IM消息，发送/接收第一条聊天室消息，如何开始基于IM Demo源码(官网下载页面可以下载)开发的信息请前往[Windows(PC) SDK Getting Started](https://dev.yunxin.163.com/docs/product/通用/新手接入/即时通讯/WindowsGettingStarted)
 
### <span id="SDK说明">SDK说明</span>
#### <span id="SDK 目录结构及主要文件介绍">SDK 目录结构及主要文件介绍</span>

Windows C++ SDK 导出目录结构：

```
├─bin                           # SDK 二进制文件（*.dll）
├─include                       # SDK 头文件包含目录
├─lib                           # SDK C 库导出的符号描述文件（*.lib）
└─wrapper                       # SDK C++ 封装层源代码目录
    ├─nim_chatroom_cpp_wrapper  # 聊天室 SDK C++ 封装层源代码
    ├─nim_cpp_wrapper           # 即时通讯 SDK C++ 封装层源代码
    ├─nim_tools_cpp_wrapper     # HTTP 及 Audio C++ 封装层源代码
    └─nim_wrapper_util          # C++ 封装层工具类
```

macOS C++ SDK 导出目录结构：

```
├─framework                     # SDK 二进制文件（*.framework）
│  ├─nim.framework             
│  └─nim_chatroom.framework    
├─lib                           # SDK 依赖的动态库文件（*.dylib）
└─wrapper                       # SDK C++ 封装层源代码目录
    ├─nim_chatroom_cpp_wrapper  # 聊天室 SDK C++ 封装层源代码
    ├─nim_cpp_wrapper           # 即时通讯 SDK C++ 封装层源代码
    ├─nim_tools_cpp_wrapper     # HTTP 及 Audio C++ 封装层源代码
    └─nim_wrapper_util          # C++ 封装层工具类
```

**SDK不提供debug版本的动态链接库供开发者调试，如果遇到问题请联系技术支持或在线客服。**

#### <span id="类库说明">类库说明</span>

* C++

在需要使用即时通讯 SDK 的地方包含头文件"nim\_cpp\_api.h"即可，该头文件是以下头文件的集合。

|类|头文件|常量定义头文件|说明|
|---|---|---|---|
|Client|nim\_cpp\_client.h|nim_client_def.h|SDK接入，主要包括SDK初始化/清理、客户端登录/退出/重连/掉线/被踢等流程，属于即时通讯SDK|
|DataSync|nim_cpp_data_sync.h|nim_data_sync_def.h|数据同步，属于即时通讯SDK|
|Friend|nim_cpp_friend.h|nim_friend_def.h|好友，属于即时通讯SDK|
|Global|nim_cpp_global.h|nim_global_def.h|辅助能力，包括内存管理和代理相关设置，属于即时通讯SDK|
|MsgLog|nim_cpp_msglog.h|nim_msglog_def.h|消息历史，属于即时通讯SDK|
|NOS|nim_cpp_nos.h|nim_nos_def.h|NOS云存储服务，属于即时通讯SDK|
|PluginIn|nim_cpp_plugin_in.h|nim_plugin_in_def.h|插件接入，接入聊天室需要调用该接口，属于即时通讯SDK|
|Robot|nim_cpp_robot.h|nim_robot_def.h|智能机器人，属于即时通讯SDK|
|Session|nim_cpp_session.h|nim_session_def.h|最近会话列表，属于即时通讯SDK|
|SubscribeEvent|nim_cpp_subscribe_event.h|nim_subscribe_event_def.h|事件订阅|
|SystemMsg|nim_cpp_sysmsg.h|nim_sysmsg_def.h|系统（自定义）消息，属于即时通讯SDK|
|Talk|nim_cpp_talk.h|nim_talk_def.h|P2P和群组聊天，属于即时通讯SDK|
|Team|nim_cpp_team.h|nim_team_def.h|群组，属于即时通讯SDK|
|Tool|nim_cpp_tools.h|nim_tools_def.h|工具类，提供了包括获取用户/应用目录，计算MD5，计算UUID，语音转文字等功能，属于即时通讯SDK|
|User|nim_cpp_user.h|nim_user_def.h|用户数据，属于即时通讯SDK|	
|DocTrans|nim_cpp_doc_trans.h|nim_doc_trans_def.h|文档转换，属于即时通讯SDK|
|VChat|nim_cpp_vchat.h|nim_vchat_def.h/nim_device_def.h|音视频与设备，属于即时通讯SDK|
|Rts|nim_cpp_rts.h|nim_rts_def.h|实时会话（数据通道），属于即时通讯SDK|
|Signaling|nim_cpp_signaling.h|nim_signaling_def.h|信令，属于即时通讯SDK|

* C#

* C

|接口头文件|对应的常量定义头文件|说明|
|---|---|---|
|nim\_sdk\_api.h|-|接口头文件集合，在需要使用即时通讯 SDK 的地方包含该头文件即可|
|nim\_chatroom.h|nim\_chatroom\_def.h|聊天室，在需要使用聊天室 SDK 的地方包含该头文件即可|
|nim\_client.h|nim_client_def.h|SDK接入，主要包括SDK初始化/清理、客户端登录/退出/重连/掉线/被踢等流程，<br>属于即时通讯SDK|
|nim_data_sync.h|nim_data_sync_def.h|数据同步，属于即时通讯SDK|
|nim_friend.h|nim_friend_def.h|好友，属于即时通讯SDK|
|nim_global.h|nim_global_def.h|辅助能力，包括内存管理和代理相关设置，属于即时通讯SDK|
|nim_msglog.h|nim_msglog_def.h|消息历史，属于即时通讯SDK|
|nim_nos.h|nim_nos_def.h|NOS云存储服务，属于即时通讯SDK|
|nim_plugin_in.h|nim_plugin_in_def.h|插件接入，接入聊天室需要调用该接口，属于即时通讯SDK|
|nim_robot.h|nim_robot_def.h|智能机器人，属于即时通讯SDK|
|nim_session.h|nim_session_def.h|最近会话列表，属于即时通讯SDK|
|nim_subscribe_event.h|nim_subscribe_event_def.h|事件订阅，属于即时通讯SDK|
|nim_sysmsg.h|nim_sysmsg_def.h|系统（自定义）消息，属于即时通讯SDK|
|nim_talk.h|nim_talk_def.h|P2P和群组聊天，属于即时通讯SDK|
|nim_team.h|nim_team_def.h|群组，属于即时通讯SDK|
|nim_tools.h|nim_tools_def.h|工具类，提供了包括获取用户/应用目录，计算MD5，计算UUID，语音转文字等功能，<br>属于即时通讯SDK|
|nim_user.h|nim_user_def.h|用户数据，属于即时通讯SDK|
|nim_doc_trans.h|nim_doc_trans_def.h|文档转换，属于即时通讯SDK|
|nim_vchat.h|nim_vchat_def.h|音视频，属于即时通讯SDK|
|nim_device.h|nim_device_def.h|音视频设备，属于即时通讯SDK|
|nim_rts.h|nim_rts_def.h|实时会话（数据通道），属于即时通讯SDK|
|nim_signaling.h|nim_signaling_def.h|信令，属于即时通讯SDK|

#### <span id="数据与资源目录">数据与资源目录</span>
当收到多媒体消息后，开发者可通过[初始化时配置特殊参数](/docs/TM5MzM5Njk/zE1MTQwMTY#初始化特殊参数说明)的方式允许SDK 自动下载多媒体文件（图片和语音），同时SDK 还要记录一些log，因此SDK 需要一个数据持久化目录。该目录由第三方App 通过[初始化接口](/docs/TM5MzM5Njk/zE1MTQwMTY#初始化)传入，默认为存放到系统的AppData 目录下，App 传入一个目录名即可，SDK 会自动生成用户数据持久化目录。数据持久化目录默认为"{系统的AppData 目录}\\{App 传入的目录名}\\NIM\\{某个用户对应的用户数据目录}”，还可以由App 完全自定义用户数据目录，需要传入完整的路径，并确保读写权限正确。如果第三方App 需要清除缓存功能，可扫描该目录下的文件，按照开发者自定义规则清理即可。
具体某个用户对应的缓存目录下面包含但不限于以下目录：

- image：图片消息文件
- audio：语音消息文件
- res：其他资源文件

SDK 提供了以下接口来获取应用的数据目录以及登录账号对应的数据目录包括具体类型的数据目录（如图片消息文件存放目录，语音消息文件存放目录等）。

* C++

	* 获取指定类型资源的目录：

		**static std::string GetSpecificAppdataDir(const std::string app\_account,enum NIMAppDataType appdata\_type);**

		File: nim\_cpp\_tool.h

		Namespace: NIM 
	
		Class：Tool	

	* 获取当前登录账号的用户数据目录：

		**static std::string GetUserAppdataDir (const std::string &app_account)**

		File: nim\_cpp\_tool.h

		Namespace: NIM 
	
		Class：Tool

	* 获取应用的用户数据根目录：

		**static std::string GetLocalAppdataDir ()**
	
		File: nim\_cpp\_tool.h

		Namespace: NIM 
	
		Class：Tool

* C#

	* 获取指定类型资源的目录：

		**static string GetUserSpecificAppDataDir (string appAccount, NIMAppDataType appdataType)**

		Namespace: NIM 
	
		Class：ToolsAPI

	* 获取当前登录账号的用户数据目录：

		**static string GetUserAppDataDir (string appAccount)**

		Namespace: NIM 
	
		Class：ToolsAPI

	* 获取应用的用户数据根目录：

		**static string GetLocalAppDataDir ()**
	
		Namespace: NIM 
	
		Class：ToolsAPI	

* C

	* 获取指定类型资源的目录：

		**NIM\_SDK\_DLL\_API const char \* nim\_tool\_get\_user\_specific\_appdata\_dir (const char \*app_account, enum NIMAppDataType appdata\_type)**

		File: nim\_tool.h

	* 获取当前登录账号的用户数据目录：

		**NIM\_SDK\_DLL\_API const char \*nim\_tool\_get\_user\_appdata\_dir (const char \*app_account)**

		File: nim\_tool.h

	* 获取应用的用户数据根目录：

		**NIM\_SDK\_DLL\_API const char \*nim\_tool\_get\_local\_appdata\_dir ()**
	
		File: nim\_tool.h

	**注意**：通过C接口返回的字符串是由动态库动态申请的内存，开发者使用完毕后需要调用以下接口释放该块内存，防止内存泄漏。

	* 释放内存：

		**NIM\_SDK\_DLL\_API void nim\_global\_free\_buf (void \*data)**

		File: nim\_global.h

### <span id="调用规则">调用规则</span>

SDK 提供的所有API 都是 **C接口** ，根据模块划分为不同的API 文件，根据业务需要可以显式或者隐式的调用（3.4.0开始）。显式调用下，开发者可以在程序进行到任何时间点按需加载SDK dll， 功能完成后如果不需要继续使用NIM可以卸载SDK dll， 更加灵活和节省内存， 该模式下开发者只需要将SDK包里nim\_c\_sdk\include 目录下的模块定义头文件（命名方式如nim\_xxx\_def.h）加入到工程项目中。隐式调用下，开发者除了链接lib文件外，需要将SDK包里nim\_c\_sdk 目录里的API 头文件（命名方式如nim\_xxx.h）以及相关常量定义的头文件等其他头文件一并加入到工程项目中。一般来说，每个模块都有对应的API 头文件和相关常量的定义头文件，命名上一一对应。

SDK 提供了3种类型的接口。

1. 全局广播类通知的注册接口。
	
	常见的几类消息或通知是通过该注册的回调函数中通知开发者的，比如收到的消息，会话数据更新，用户相关数据的变更等，开发者需要在登录前提前注册好这些接口，例如：

C++

```C++
//注册数据同步结果的回调
nim::DataSync::RegCompleteCb(nbase::Bind(&nim_comp::DataSyncCallback::SyncCallback, std::placeholders::_1, std::placeholders::_2, std::placeholders::_3));

/* 以下注册的回调函数，都是在收到服务器推送的消息或事件时执行的。因此需要在程序开始时就注册好。 */
//注册重连、被踢、掉线、多点登录、把移动端踢下线的回调
nim::Client::RegReloginCb(&nim_comp::LoginCallback::OnReLoginCallback);
nim::Client::RegKickoutCb(&nim_comp::LoginCallback::OnKickoutCallback);
nim::Client::RegDisconnectCb(&nim_comp::LoginCallback::OnDisconnectCallback);
nim::Client::RegMultispotLoginCb(&nim_comp::LoginCallback::OnMultispotLoginCallback);
nim::Client::RegKickOtherClientCb(&nim_comp::LoginCallback::OnKickoutOtherClientCallback);
nim::Client::RegSyncMultiportPushConfigCb(&nim_comp::MultiportPushCallback::OnMultiportPushConfigChange);

//注册返回发送消息结果的回调，和收到消息的回调。
nim::Talk::RegSendMsgCb(nbase::Bind(&nim_comp::TalkCallback::OnSendMsgCallback, std::placeholders::_1));
nim::Talk::RegReceiveCb(nbase::Bind(&nim_comp::TalkCallback::OnReceiveMsgCallback, std::placeholders::_1));
nim::Talk::RegRecallMsgsCallback(nbase::Bind(&nim_comp::TalkCallback::OnReceiveRecallMsgCallback, std::placeholders::_1, std::placeholders::_2));
nim::Talk::RegReceiveMessagesCb(nbase::Bind(&nim_comp::TalkCallback::OnReceiveMsgsCallback, std::placeholders::_1));
nim::MsgLog::RegMessageStatusChangedCb(nbase::Bind(&nim_comp::TalkCallback::OnMsgStatusChangedCallback, std::placeholders::_1));
```

C#

```C++
//注册数据同步结果的回调
NIM.DataSync.RegCompleteCb(DataSyncDelegate cb);
//登录结果通知，开发者可以通过注册该事件获取登录结果，或者在调用登录接口NIM.ClientAPI.Login 时填充回调函数
NIM.ClientAPI.LoginResultHandler
//注册客户端掉线回调
NIM.ClientAPI.RegDisconnectedCb(Action handler);
//注册客户端多点登录通知回调
NIM.ClientAPI.RegMultiSpotLoginNotifyCb(MultiSpotLoginNotifyResultHandler handler);
//注册将登录当前账号的其他端踢下线的结果回调
NIM.ClientAPI.RegKickOtherClientCb(KickOtherClientResultHandler handler);
//注册当前客户端被踢下线通知回调
NIM.ClientAPI.RegKickoutCb(KickoutResultHandler handler)
//注册自动重连结果回调
NIM.ClientAPI.RegAutoReloginCb(LoginResultDelegate handler, string jsonExtension = null)

	//接收消息
NIM.TalkAPI.OnReceiveMessageHandler += ReceiveMessageHandler;
//发送消息结果
NIM.TalkAPI.OnSendMessageCompleted += SendMessageResultHandler;
//注册消息撤回结果回调
NIM.TalkAPI.RegRecallMessageCallback(RecallMessageDelegate cb);
```

C

```C++
// 数据同步结果通知(nim_data_sync)
void nim_data_sync_reg_complete_cb(nim_data_sync_cb_func cb, const void *user_data);		
// 接收会话消息通知(nim_talk)
void nim_talk_reg_receive_cb(const char *json_extension, nim_talk_receive_cb_func cb, const void *user_data);		
// 接收系统消息通知(nim_sysmsg)
void nim_sysmsg_reg_sysmsg_cb(const char *json_extension, nim_sysmsg_receive_cb_func cb, const void *user_data);	
// 发送消息结果通知(nim_talk)
void nim_talk_reg_arc_cb(const char *json_extension, nim_talk_arc_cb_func cb, const void *user_data);
// 发送自定义系统通知的结果通知(nim_talk)
void nim_talk_reg_custom_sysmsg_arc_cb(const char *json_extension, nim_custom_sysmsg_arc_cb_func cb, const void *user_data);
// 群组事件通知(nim_team)
void nim_team_reg_team_event_cb(const char *json_extension, nim_team_event_cb_func cb, const void *user_data);	
// 帐号被踢通知(nim_client)
void nim_client_reg_kickout_cb(const char *json_extension, nim_json_transport_cb_func cb, const void *user_data);		
// 网络连接断开通知(nim_client)
void nim_client_reg_disconnect_cb(const char *json_extension, nim_json_transport_cb_func cb, const void *user_data);	
// 将本帐号的其他端踢下线的结果通知(nim_client)
void nim_client_reg_kickout_other_client_cb(const char *json_extension, nim_json_transport_cb_func cb, const void *user_data); 
// 好友通知 
void nim_friend_reg_changed_cb(const char *json_extension, nim_friend_change_cb_func cb, const void *user_data);	
// 用户特殊关系通知
void nim_user_reg_special_relationship_changed_cb(const char *json_extension, nim_user_special_relationship_change_cb_func cb, const void *user_data);	
```


2. 异步接口。

	回调函数作为参数，传入执行接口，然后执行接口时，会触发传入的回调函数。注意，回调函数中如果涉及到跨线程资源的需要开发者切换线程操作，即使不涉及到资源问题，也要保证回调函数中不会处理耗时任务，以免堵塞SDK底层线程。

3. 同步接口。

	为方便开发者使用，我们提供了一些同步接口，调用接口获取的内容同步返回，以block命名的都是同步接口，该类会堵塞SDK线程，谨慎使用。

**从版本2.7.0开始，服务器和客户端上线了频控策略，与服务器有交互的接口(接口命名结尾为_online的查询接口以及命令类接口，如同意群邀请等)增加频控控制，开发者关注错误码416。** 

#### <span id="CPP SDK">C++ SDK</span>
为了方便桌面应用开发者更快的接入网易云信SDK，PC SDK下载包中还提供了官方的[C++ 封装层 项目文件及源码](https://github.com/netease-im/NIM_PC_SDK-CPP-)，接入和使用方法请看[Windows(PC) SDK开发手册(C++ 封装层)](https://dev.yunxin.163.com/docs/product/通用/Demo源码导读/PC通用/C++封装层)，目前IM Demo(C++)源码就是通过接入和调用该SDK完成IM功能的。

#### <span id="CSharp SDK">C# SDK</span>
网易云信SDK还提供了C# 程序集，方便.net 开发人员接入，PC SDK下载包中包括官方的[C# 封装层 项目文件及源码](https://github.com/netease-im/NIM_PC_SDK-CSharp)，接入和使用方法请看[Windows(PC) SDK开发手册(C# 封装层)](https://dev.yunxin.163.com/docs/product/通用/Demo源码导读/PC通用/CSharp封装层)，目前IM Demo(C#)源码就是通过接入和调用该SDK完成IM功能的。

**如果开发者在调用C接口过程中或者解析接口返回结果过程中出现疑问，可以参考和借鉴C++封装层。**
