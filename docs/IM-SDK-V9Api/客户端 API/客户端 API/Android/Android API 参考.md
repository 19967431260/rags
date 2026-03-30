<!--keywords: API 参考,API参考, 接口概述, SDK API，API概述, API 概述 -->
 
本文介绍 Android SDK API 的概述性信息，并列出核心 API 与核心类或接口类，方便您查阅 API 信息。

## SDK API 概述

<details><summary>点击查看 API 概述</summary>


#### 接口类型

NIM Android SDK （以下简称 SDK）提供两种接口类，供开发者使用：


<div style="width:180px">类型</div> |说明
------ |  ------
主动发起请求 | 接口名均以 `Service` 结尾，例如 `AuthService` 
作为观察者监听事件和变化 | 接口名均以 `ServiceObserver` 结尾，例如 `AuthServiceObserver`。个别太长的类名则直接以 `Observer` 结尾，例如 `SystemMessageObserver`。


::: note notice
- SDK 接口调用必须在主进程中进行，请在主进程中调用 SDK 的 `XXXService` 提供的方法，在主进程中注册 `XXXServiceObserver` 的观察者（有事件变更，会回调给主进程的主线程）。
- 如果您的模块运行在非主进程，请自行实现主进程与非主进程的通信（`AIDL/Messenger/ContentProvider/BroadcastReceiver`等 IPC 渠道）将主进程回调或监听返回的数据传递给非主进程。
:::

#### 返回值类型


SDK 提供三种接口返回值：
- 基本数据类型（同步接口）
- `InvocationFuture`（异步接口）
- `AbortableFuture`（异步接口）：异步接口基本都从主进程发起调用，然后在后台进程执行，最后再将结果返回给主进程

::: note note
如果调用 `AbortableFuture` 异步接口，传输大量数据或者出现耗时很长的情况，可通过 `abort` 方法中断请求。例如上传下载、登录等。 
:::

<br>


异步接口可通过 `RequestCallback` 和 `RequestCallbackWrapper` 两种方式设置回调函数。

| 异步接口回调函数 | 说明 |
| :-------- | :--------|
| `RequestCallback` | 需要实现三个接口：<br> 成功`onSuccess`, 失败 `onFailed`, 异常 `onException`|
| `RequestCallbackWrapper` | 需要实现 `onResult`。封装了成功、失败和异常三个接口，在参数上进行区分|


#### SDK API 调用框架

自 v4.4.0 起，API 调用框架增强：
- 支持带 Looper 的非 UI 线程发起的异步 API 调用，直接回调到调用者线程。v4.4.0 之前版本会默认回调到 UI 线程。
- 提供异步强制转成同步的接口：`NIMClient#syncRequest`，允许设置最大同步等待时间，支持非 UI 线程里需要同步调用云信 API的场景。
- 添加自动生成的 NIM SDK 类，您可直接采用 `NIMSDK#getXXXService` 方法获取服务接口，不再需要传递 XXXService.class，简化 API 调用方式。其他插件自动生成的调用入口类为：`NIMChatRoomSDK`、`NIMLuceneSDK`。例如采用 `NIMSDK.getAuthService().login()` 替换`NIMClient.getService(AuthService.class).login()`。


</details>



## SDK API 参考


点此进入：**[Android SDK API 参考](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/index.html)**

## SDK 核心 API 


以下仅列出 SDK 的部分核心 API，如需查阅其他 SDK API 信息，请参考下文的<b>[SDK 核心类/接口类](#sdk-核心类接口类)</b>或者直接进入[Android SDK API 参考](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/annotated.html)查询 API 名称。


#### 初始化与登录



<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a48056b399acd7f84ebcf5176b1cfde16" target="_blank">init</a> </td><td>在 Application#onCreate 中初始化 SDK</td><td> <a href="https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#aa8e0e524f223d29e8f2499557a2ae2e5">NIMClient#initV2</a> </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a734a21a3519b5d930d873e731078c967" target="_blank">config</a> </td><td>在 Application#onCreate 中进行初始化配置<note type=notice>调用该方法<b>仅仅是进行初始化配置</b>，调用该方法后还需调用下文的 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a0abf9936dbb83e34d97c35f508c9ec94" target="_blank">initSDK</a> 方法进行真正的初始化</note></td><td>同上
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a0abf9936dbb83e34d97c35f508c9ec94" target="_blank">initSDK</a> </td><td>在 UI 进程主线程上按需进行初始化SDK，支持通过 SDKOptions#asyncInitSDK 配置为同步或异步初始化，并支持通过 SDKOptions#reducedIM 配置为弱 IM 模式，延迟加载push进程服务<note type=notice><ul><li>调用该方法前，必须先在 Application#onCreate 中调用上文的 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a734a21a3519b5d930d873e731078c967" target="_blank">config</a> 方法。</li><li>请不要再 Application#onCreate 中调用该方法。</li></ul></note></td><td>同上
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#af2e4356fb14fd8077caabcb3d9570b4b" target="_blank">getService</a>  </td><td>获取各服务接口，例如获取 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html" target="_blank">MsgService</a></td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a88efc6b9ae135e431ebe968bf2158d5a" target="_blank">getStatus</a>  </td><td>获取当前用户的登录状态（在线状态）
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginStatus" target="_blank">V2NIMLoginService#getLoginStatus</a>
           </td></tr>    
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a1ea68ab492c3db4074a998774deab14d" target="_blank">getCurrentAccount</a>  </td><td>获取当前用户的 IM 账号（accid）
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginUser" target="_blank">V2NIMLoginService#getLoginUser</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a71cdb1efcf3495408632f72a87ac9a92" target="_blank">updateStrings</a>  </td><td>当系统语言发生变化时，更新文案配置。配置不能立即生效，所有文案均需要在下次使用时才会生效
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a9236de78fc7c5086c4eaecf882c1d7bd" target="_blank">getSdkStorageDirPath</a>  </td><td>获取SDK数据目录路径，<b>需要在初始化 SDK 之后调用</b>
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#ad860b320cdea1d30f0133eb5075c3f07" target="_blank">getSDKVersion</a></td><td>运行时获取当前 SDK 版本号
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#ae9f6be76fc29def4b382bfc813ef0214" target="_blank">login</a>  </td><td>登录 IM
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#login" target="_blank">V2NIMLoginService#login</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#aaa048a03d2f8fce4c31b0f8a3945a09b" target="_blank">logout</a>  </td><td>登出 IM
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout" target="_blank">V2NIMLoginService#logout</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#a27bbb08421c17476cf6faeee95cde8eb" target="_blank">kickOtherClient</a>  </td><td>将同时在线的其他设备端踢下线
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#kickOffline" target="_blank">V2NIMLoginService#kickOffline</a>
           </td></tr>
</table>






#### 消息（单聊与群聊）

<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a29772394b4a5d39cc5e9c0cf2180d775" target="_blank">createTextMessage</a> </td><td>构建一条文本消息，构建后需调用  <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTextMessage" target="_blank">V2NIMMessageCreator#createTextMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a28f3837208922649f5db98b791ed8013" target="_blank">createImageMessage</a> </td><td>构建一条图片消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createimagemessage" target="_blank">V2NIMMessageCreator#createImageMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a4154d7634916d5e3672d6a21c25a35e1" target="_blank">createAudioMessage</a> </td><td>构建一条语音消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createAudioMessage" target="_blank">V2NIMMessageCreator#createAudioMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a97218a09d2436e2033858fbb54eca3a3" target="_blank">createVideoMessage</a> </td><td>构建一条视频消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createVideoMessage" target="_blank">V2NIMMessageCreator#createVideoMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a38dde500f113b8fab19c2e5f0143d973" target="_blank">createFileMessage</a> </td><td>构建一条文件消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createFileMessage" target="_blank">V2NIMMessageCreator#createFileMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a289dd7b8dc1fa81a3a6e7b88d7b4f9d8" target="_blank">createLocationMessage</a> </td><td>构建一条地理位置消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createLocationMessage" target="_blank">V2NIMMessageCreator#createLocationMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a323e53e9239ccaf90c269aed5185c600" target="_blank">createTipMessage</a> </td><td>构建一条提示消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTipMessage" target="_blank">V2NIMMessageCreator#createTipMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a70e8fc18778c2fcf681ed5dfb12a9496" target="_blank">createCustomMessage</a> </td><td>构建一条自定义消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createCustomMessage" target="_blank">V2NIMMessageCreator#createCustomMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#ac51ed9ee4c0236cc0ac225daaea5e961" target="_blank">createEmptyMessage</a> </td><td>构建一条空消息，仅可设置聊天对象、会话类型和时间点，用于记录查询。构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a06be6f1d6be57a8810e4e1fe4b4c4f52" target="_blank">createForwardMessage</a> </td><td>构建一条转发消息，构建后需调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createForwardMessage" target="_blank">V2NIMMessageCreator#createForwardMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html#a676c3503255b3a5eace865e76a8545c0" target="_blank">createForwardMessageListFileDetail</a> </td><td>创建多条待合并转发的消息，构建后需调用  <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> 方法发送
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a74db65f6720c4e2ba7a5d2a9e72ebda8" target="_blank">sendMessage</a> </td><td>发送消息，如果需要更新发送进度，请调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service_observe.html#a18702631b4650ca3b0d71a7dad52be6a" target="_blank">MsgServiceObserve#observeMsgStatus</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addmessagelistener" target="_blank">V2NIMMessageService#addMessageListener</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a709785dc3503238b2f37de38ca439929" target="_blank">saveMessageToLocalEx</a> </td><td>保存消息到本地数据库，但不发送到服务器端。用于应用保存本地提醒一类的消息。与其他 SDK API 的组合调用示例，可参见<a href="https://doc.yunxin.163.com/messaging/docs/jk0NDM1NjA?platform=android#收发提示消息" target="_blank">收发提示消息</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#insertMessageToLocal" target="_blank">V2NIMMessageService#insertMessageToLocal</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a9a66029ffd3e317c9c77bf4dcb86c2de" target="_blank">sendMessageReceipt</a> </td><td>发送单聊（P2P）消息的已读回执</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendP2PMessageReceipt" target="_blank">V2NIMMessageService#sendP2PMessageReceipt</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a420ac9d7a92bf830b2defbddf76911ed" target="_blank">deleteMsgSelf</a> </td><td>单向删除多条消息</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deletemessages" target="_blank">V2NIMMessageService#deleteMessages</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a7f0104ba3b45ae7743755c20643f9c45" target="_blank">updateIMMessage</a> </td><td>更新消息。目前只能更新本地扩展字段 LocalExtension</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension" target="_blank">V2NIMMessageService#updateMessageLocalExtension</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ac9da465b65fd37a8cabcae1e87dbdc73" target="_blank">updateIMMessageStatus</a> </td><td>更新消息记录的状态。可更新：
<ul><li>消息状态 IMMessage#getStatus() 不为 null 时更新</li>
<li>附件状态 IMMessage#getAttachStatus() 不为 null 时更新</li>
<li>附件内容 IMMessage#getAttachment() 不为 null 时更新</li></ul></a>
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a4b9a786b266ed3e6f83d53d4b46b4900" target="_blank">revokeMessage</a> </td><td>撤回消息，并设置相应的第三方推送配置（包括IOS平台的推送）与未读数变化
</a>
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage" target="_blank">V2NIMMessageService#revokeMessage</a>
           </td></tr>
</table>



#### 历史消息

<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ab4ea3d61551def04dda340e4da60434e" target="_blank">clearServerHistory</a> </td><td>清空服务端的单聊历史消息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#clearHistoryMessage" target="_blank">V2NIMMessageService#clearHistoryMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a6189b18b6e9123694dfcd9527c4ba20b" target="_blank">deleteRangeHistory</a> </td><td>根据时间范围删除本地历史消息
    </td><td>无
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a85b45ed6280989d711f3aa2597191acc" target="_blank">searchMessageHistory</a> </td><td>从本地消息数据库搜索消息历史
    </td><td>无
    </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a26eba2fafa7027348bafd7c757694fc7" target="_blank">queryMessageListByUuid</a> </td><td>通过 uuid 批量获取历史消息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByIds" target="_blank">V2NIMMessageService#getMessageListByIds</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#af2fe20b07effedd5d9ecd968c983fee2" target="_blank">pullMessageHistoryEx</a> </td><td>从服务器拉取消息历史记录
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList" target="_blank">V2NIMMessageService#getMessageList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a79f3d361d62c830cacea16cfa847e8b9" target="_blank">searchRoamingMsg</a> </td><td>云端聊天记录关键词查询
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages" target="_blank">V2NIMMessageService#searchCloudMessages</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a929d9b4195052becb17e7a9bf6663107" target="_blank">queryLastMessage</a> </td><td>查询同指定用户的最近一条消息
    </td><td>同 V9 API
           </td></tr>
</table>


#### 消息扩展

<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#afdd431393b6442cededec3adabedc8fb" target="_blank">replyMessage</a> </td><td>引用一条消息进行回复，形成消息回复树状结构（Thread）
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#replyMessage" target="_blank">V2NIMMessageService#replyMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#afb5910a0d80d605e26f7ab37dc863519" target="_blank">queryThreadTalkHistory</a> </td><td>查询 Thread 聊天云端历史（支持单聊、群聊、超大群）
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getThreadMessageList" target="_blank">V2NIMMessageService#getThreadMessageList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a2f8364ccbfa0b89fe067ab5c2a6cdc6b" target="_blank">addQuickComment</a> </td><td>添加快捷评论，如表情等 reaction
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addQuickComment" target="_blank">V2NIMMessageService#addQuickComment</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#af5f48c7d0023d3e49db26843401b8cba" target="_blank">removeQuickComment</a> </td><td>移除快捷评论
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeQuickComment" target="_blank">V2NIMMessageService#removeQuickComment</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a1ffcb5fdce67ac85ec1aa4404c2db61b" target="_blank">queryQuickComment</a> </td><td>获取快捷评论列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getQuickCommentList" target="_blank">V2NIMMessageService#getQuickCommentList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#af3d13614404cf4faadcb9acc11635288" target="_blank">addCollect</a> </td><td>将某条消息添加为收藏
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addCollection" target="_blank">V2NIMMessageService#addCollection</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a94b735c575c197d19edae56b77ce9cf2" target="_blank">removeCollect</a> </td><td>批量移除收藏
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeCollections" target="_blank">V2NIMMessageService#removeCollections</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ab1001e031449cbd095d357728540c8ac" target="_blank">addMsgPin</a> </td><td>PIN 一条消息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#pinMessage" target="_blank">V2NIMMessageService#pinMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a3d9d0d569b904c2cbea996a45fc2d508" target="_blank">updateMsgPin</a> </td><td>更新一条消息的 PIN
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updatePinMessage" target="_blank">V2NIMMessageService#updatePinMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a6829a478d3142e46b9b70c3972ebfb0a" target="_blank">removeMsgPin</a> </td><td>移除一条消息的 PIN
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unpinMessage" target="_blank">V2NIMMessageService#unpinMessage</a>
           </td></tr>
</table>

#### 会话列表



<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a38a658546108907823fe60090b19d24b" target="_blank">queryRecentContacts</a> </td><td>查询最近联系人会话列表数据，可按时间逆序或者正序查询指定数量的最新会话列表数据
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList" target="_blank">V2NIMConversationService#getConversationList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ab8482e4cdc2882b69f9f4b39ec64fc8d" target="_blank">queryMySession</a> </td><td>获取某一个会话
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationList" target="_blank">V2NIMConversationService#getConversationList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a93032b11c36b58aebc9eb5a08b59a594" target="_blank">updateRecentAndNotify</a> </td><td>更新一条最近联系人会话的属性，并会触发MsgServiceObserve#observeRecentContact(Observer, boolean)的通知 。
如果仅仅是想更新最近联系人会话但不想收到通知， 可调用<a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#afcb373be37a4daa709ec8dec9ef22bf8" target="_blank">MsgService#updateRecent(RecentContact) </a>
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#updateConversation" target="_blank">V2NIMConversationService#updateConversation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a742803e9a9e58273f7a03b1af6cf396e" target="_blank">deleteRecentContact</a> </td><td>删除最近联系人记录
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#deleteConversation" target="_blank">V2NIMConversationService#deleteConversation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ae9912dbac6d7238f69742a72eff0065a" target="_blank">createEmptyRecentContact </a> </td><td>创建一条空的联系人会话
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#createConversation" target="_blank">V2NIMConversationService#createConversation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a150179a433210b768b113c6e1785142b" target="_blank">getTotalUnreadCount</a> </td><td>获取未读数总数
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getTotalUnreadCount" target="_blank">V2NIMConversationService#getTotalUnreadCount</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a67db8698c2511a166fde7b40b44ec652" target="_blank">queryUnreadMessageList</a> </td><td>根据会话ID和会话类型查找未读消息列表
    </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a9bab6e3ebb5918f3560ded979826b9b1" target="_blank">clearUnreadCount</a> </td><td>将指定会话类型的未读数清零(标记已读)
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds" target="_blank">V2NIMConversationService#clearUnreadCountByIds</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a6a02a89f98b75d94edfc3ddd5ebf7ed2" target="_blank">queryCollect</a> </td><td>从服务的分页查询收藏列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListByOption" target="_blank">V2NIMConversationService#getCollectionListByOption</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a82a401aa48a177bad7b6b09c8026d52a" target="_blank">addStickTopSession</a> </td><td>添加一个置顶会话
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation" target="_blank">V2NIMConversationService#stickTopConversation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#a7b0e97f389315645347c5fb4759962d0" target="_blank">removeStickTopSession</a> </td><td>删除置顶会话
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#stickTopConversation" target="_blank">V2NIMConversationService#stickTopConversation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#ad605089f26c4ae7354cd5f085cb31f7a" target="_blank">updateStickTopSession</a> </td><td>更新一个置顶会话的扩展字段
    </td><td>无
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html#abd7c20736b0fe02f2e25b7ed78d8ae53" target="_blank">queryStickTopSessionBlock</a> </td><td>获取置顶会话信息的列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#getConversationListByOption" target="_blank">V2NIMConversationService#getConversationListByOption</a>
           </td></tr>
</table>





#### 离线推送与消息提醒


<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1mixpush_1_1_mix_push_service.html#aec0da212bcdc70f399a610a4f5a84ec9" target="_blank">enable</a> </td><td>开启/关闭第三方离线推送服务
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1mixpush_1_1_mix_push_service.html#a578faa03a768f29e1e4b35b3b72659cd" target="_blank">setPushNoDisturbConfig</a> </td><td>设置推送免打扰时间
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1mixpush_1_1_mix_push_service.html#a25a66f9eb2df305ce76561c3cbd26aad" target="_blank">setPushShowNoDetail</a> </td><td>设置离线推送是否不展示推送文案详情
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#acf600d293b07830cf63c687d9a3e5b7d" target="_blank">toggleNotification</a> </td><td>通知栏提醒开关控制。该方法只有在 <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_s_d_k_options.html#ad6f29e122619e6ad3fd2d299f99d42a8" target="_blank">SDKOptions#StatusBarNotificationConfig</a> 配置不为空时调用才有效
           </td><td>同 V9 API
           </td></tr>
</table>


#### 群组



<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a9826694f5b7e6e3f0f76dddbeab2065e" target="_blank">createTeam</a> </td><td>创建一个群组
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#createTeam" target="_blank">V2NIMTeamService#createTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#abec097965b173fe4290a6ccf4321b200" target="_blank">addMembersEx</a> </td><td>添加成员
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember" target="_blank">V2NIMTeamService#inviteMember</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a20ae7fc5ea1ca2f06ea09a392c4681cb" target="_blank">removeMember</a> </td><td>移除单个成员，只有群组创建者有此权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember" target="_blank">V2NIMTeamService#kickMember</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a1b2a0a4284127202d36219a00c0f550e" target="_blank">updateTeam</a> </td><td>更新群组资料
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo" target="_blank">V2NIMTeamService#updateTeamInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a1059d2e53c24abcdf4d7fb43cb4d2318" target="_blank">dismissTeam</a> </td><td>解散群，只有群主有权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#dismissTeam" target="_blank">V2NIMTeamService#dismissTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a749eb0cb0c4fefeca7335b67d8a0c757" target="_blank">quitTeam</a> </td><td>退出群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam" target="_blank">V2NIMTeamService#leaveTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#ae06cb166750bc8defd312a9b81a05713" target="_blank">queryTeam</a> </td><td>查询群资料，如果本地没有群组资料，则去服务器查询。
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo" target="_blank">V2NIMTeamService#getTeamInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a43d2f817f25a2500221fc419bf37b8aa" target="_blank">queryTeamList</a> </td><td>获取自己加入的群列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList" target="_blank">V2NIMTeamService#getJoinedTeamList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a7647a8fa10899d1d13ba0ff4e1f3cc04" target="_blank">queryTeamListById</a> </td><td>根据群 ID 列表批量查询群信息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfoByIds" target="_blank">V2NIMTeamService#getTeamInfoByIds</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a7db2143df769b4251a56bcd32ba637e7" target="_blank">searchTeam</a> </td><td>从服务器上查询群资料信息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo" target="_blank">V2NIMTeamService#getTeamInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a2a613a4e68778979c726a3b17b3e4d57" target="_blank">applyJoinTeam</a> </td><td>申请加入群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam" target="_blank">V2NIMTeamService#applyJoinTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a1d72c5874bb833b754426d269103bc23" target="_blank">passApply</a> </td><td>同意入群申请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication" target="_blank">V2NIMTeamService#acceptJoinApplication</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#aab1da14d38c086f3c76c179baf14dcc2" target="_blank">rejectApply</a> </td><td>拒绝入群申请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication" target="_blank">V2NIMTeamService#rejectJoinApplication</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a0325b0a119e6fdc37be02dc322cd1e33" target="_blank">addManagers</a> </td><td>添加管理员，仅群主有此权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">V2NIMTeamService#updateTeamMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#ae9d769e7f6221309e0455fcdecd860eb" target="_blank">removeManagers</a> </td><td>移除管理员，仅群主有此权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">V2NIMTeamService#updateTeamMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a53fee02785c301101af8feb8950e3cbe" target="_blank">transferTeam</a> </td><td>转让群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner" target="_blank">V2NIMTeamService#transferTeamOwner</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a7aad728319e95c577f594e0643a53d85" target="_blank">acceptInvite</a> </td><td>接受别人的入群邀请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation" target="_blank">V2NIMTeamService#acceptInvitation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#af677249820ce40d584a0025eeb0ed8c3" target="_blank">declineInvite</a> </td><td>拒绝别人的入群邀请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation" target="_blank">V2NIMTeamService#rejectInvitation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a64b12c92f82f97615cf5f48f0f541a75" target="_blank">queryMemberList</a> </td><td>获取指定群的成员信息列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">V2NIMTeamService#getTeamMemberList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a167e24f7a7d1180c5eec74d62501c8f5" target="_blank">muteTeamMember</a> </td><td>对群成员禁言或解除禁言
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus" target="_blank">V2NIMTeamService#setTeamMemberChatBannedStatus</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#ac4e199f1836fb406982242636562f211" target="_blank">muteAllTeamMember</a> </td><td>对整个群禁言或解除禁言，对普通成员生效，只有群主和管理员有权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode" target="_blank">V2NIMTeamService#setTeamChatBannedMode</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#a9ed7759e934234b025e96e3d16b97ca8" target="_blank">queryMutedTeamMembers</a> </td><td>查询被禁言群成员列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">V2NIMTeamService#getTeamMemberList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html#aa1e80df6be8096921a77ecf913b1e658" target="_blank">sendTeamMessageReceipt</a> </td><td>(群消息接收方)标记群组消息已读
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendteammessagereceipts" target="_blank">V2NIMMessageService#sendTeamMessageReceipts</a>
           </td></tr>
</table>



#### 超大群
<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a0f7f07c900db8c57fd9b331a5e159c66" target="_blank">addMembers</a> </td><td>添加超大群成员
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember" target="_blank">V2NIMTeamService#inviteMember</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a2ce5cb73b361a7c6d2757d4b53d7ff10" target="_blank">removeMembers</a> </td><td>移出超大群的群成员，只有群主有权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember" target="_blank">V2NIMTeamService#kickMember</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#aa7217ee7fbf756ed36f4e4917ce3a240" target="_blank">quitTeam</a> </td><td>退出超大群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam" target="_blank">V2NIMTeamService#leaveTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a9bdcc37b6f8a68394e3581b7d3f357aa
" target="_blank">transferTeam</a> </td><td>转让超大群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner" target="_blank">V2NIMTeamService#transferTeamOwner</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a97033a7f4e32e16b078e8ea0c8bae57e" target="_blank">applyJoinTeam</a> </td><td>申请加入超大群
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam" target="_blank">V2NIMTeamService#applyJoinTeam</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a3220900ed0fa66990f9b0dbc7948f07f" target="_blank">passApply</a> </td><td>同意入群申请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication" target="_blank">V2NIMTeamService#acceptJoinApplication</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#ab99b38db1e78123a0ac8fec0068ac62a" target="_blank">rejectApply</a> </td><td>拒绝入群申请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication" target="_blank">V2NIMTeamService#rejectJoinApplication</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#ae85a462e4ea86272c4c3f63a66733c35" target="_blank">acceptInvite</a> </td><td>接受别人的入群邀请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation" target="_blank">V2NIMTeamService#acceptInvitation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a7d1604edc1c5597c71b24ec21d539e53" target="_blank">declineInvite</a> </td><td>拒绝别人的入群邀请
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation" target="_blank">V2NIMTeamService#rejectInvitation</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a19a29d23640fe204ec374f3a743db311" target="_blank">addManagers</a> </td><td>添加管理员，仅群主有此权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">V2NIMTeamService#updateTeamMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a556c3b4b8bf389c800ec99d47ec5a200" target="_blank">removeManagers</a> </td><td>移除管理员，仅群主有此权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">V2NIMTeamService#updateTeamMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a21b63c816e56529d19e5a8b4a07a4392" target="_blank">muteTeamMembers</a> </td><td>禁言或解除禁言
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus" target="_blank">V2NIMTeamService#setTeamMemberChatBannedStatus</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#aac28cb5920791a5af69c7515045eecd6" target="_blank">muteAllTeamMember</a> </td><td>对整个群禁言或解除禁言，对普通成员生效，只有群主和管理员有权限
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode" target="_blank">V2NIMTeamService#setTeamChatBannedMode</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a034058e1d18405af16a2eee4d47e7477" target="_blank">queryMutedTeamMembers</a> </td><td>查询被禁言群成员列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">V2NIMTeamService#getTeamMemberList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a7efd13737199d0f405556d7c49a733e3" target="_blank">updateTeam</a> </td><td>更新超大群的资料
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo" target="_blank">V2NIMTeamService#updateTeamInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#af42811ccdd196719c18c1312108a7303" target="_blank">queryTeamList</a> </td><td>获取自己已加入的超大群列表
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getJoinedTeamList" target="_blank">V2NIMTeamService#getJoinedTeamList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a7d117bc3ae9a476abf775da6ef6465fd" target="_blank">sendMessage</a> </td><td>在超大群里发送消息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TY4MDg4MTk?platform=client#createTextMessage" target="_blank">V2NIMMessageCreator#createTextMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#a18c1e4f40749071d9968852f1724c867" target="_blank">revokeMessage</a> </td><td>撤回超大群消息
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage" target="_blank">V2NIMMessageService#revokeMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#abfeb02bdc0f0fa5bad735c07ca5fc5cf" target="_blank">replyMessage</a> </td><td>引用一条超大群消息进行回复，形成回复树状结构（Thread）
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#replyMessage" target="_blank">V2NIMMessageService#replyMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html#ae98397a7b05fb5572c503abea63e7345" target="_blank">clearUnreadCount</a> </td><td>将指定超大群的未读数清零(标记已读)
    </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zA4NjQzOTQ?platform=client#clearUnreadCountByIds" target="_blank">V2NIMConversationService#clearUnreadCountByIds</a>
           </td></tr>
</table>

#### 聊天室


<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#aa91edbe1fd30e177c8c6031e2b53b6db" target="_blank">enterChatRoomEx</a> </td><td>进入聊天室
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#enter" target="_blank">V2NIMChatroomClient#enter</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a700f9f1d817eb6d5bca67f7de2cf30d1" target="_blank">getEnterErrorCode</a> </td><td>获取进入聊天室失败的错误码
           </td><td>无
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#aa000bcbe1e7b664669bdca9e69e91143" target="_blank">exitChatRoom</a> </td><td>退出聊天室
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#exit" target="_blank">V2NIMChatroomClient#exit</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a4e3df84f42ab2ff61750bf50b4b3e225" target="_blank">sendMessage</a> </td><td>在聊天室内发送消息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#sendMessage" target="_blank">V2NIMChatroomService#sendMessage</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a1701047a828f62e93677b2f7bb293e03" target="_blank">pullMessageHistoryEx</a> </td><td>获取聊天室历史消息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getmessagelist" target="_blank">V2NIMChatroomService#getMessageList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a195c96ddae2ff14e4486750de9b274ae" target="_blank">getMessagesByTags</a> </td><td>按标签从云端拉取聊天室消息，每一个标签代表的是某个标签化分组下的聊天室成员
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getmessagelistbytag" target="_blank">V2NIMChatroomService#getMessageListByTag</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a0cece0fd2163ee80a504bce4f73c534a" target="_blank">kickMember</a> </td><td>将特定成员踢出聊天室
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#kickMember" target="_blank">V2NIMChatroomService#kickMember</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#ab434c70a3a84318368593885fcd20b36" target="_blank">fetchRoomMembers</a> </td><td>获取聊天室成员信息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByOption" target="_blank">V2NIMChatroomService#getMemberListByOption</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#ae57dd99446b245d30f4bc59105acfabb" target="_blank">fetchRoomMembersByIds</a> </td><td>根据用户的 IM 账号（accid）获取聊天室成员信息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberByIds" target="_blank">V2NIMChatroomService#getMemberByIds</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#ac73ebdf916ba3bf873ee680fe206ef12" target="_blank">markChatRoomBlackList</a> </td><td>将用户添加或移出聊天室黑名单
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberBlockedStatus" target="_blank">V2NIMChatroomService#setMemberBlockedStatus</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a0f9a3e934d54905762755a809ef80627" target="_blank">markChatRoomMutedList</a> </td><td>将用户添加到禁言名单或取消禁言
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberChatBannedStatus" target="_blank">V2NIMChatroomService#setMemberChatBannedStatus</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#ad78b70c9a8545b2645499634702e77ee" target="_blank">markChatRoomTempMute</a> </td><td>设置聊天室成员临时禁言
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberTempChatBanned" target="_blank">V2NIMChatroomService#setMemberTempChatBanned</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a951e132451974e9bc9c19c98ef5cb950" target="_blank">markNormalMember</a> </td><td>将用户设为聊天室普通成员，或取消其普通成员角色
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateMemberRole" target="_blank">V2NIMChatroomService#updateMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a9d44e4daf0fccbf027ac41489b1c5926" target="_blank">markChatRoomManager</a> </td><td>将用户设为聊天室管理员，或取消其聊天室管理员角色
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateMemberRole" target="_blank">V2NIMChatroomService#updateMemberRole</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a1da865d4dbf5760610dcd2ec607c783c" target="_blank">markChatRoomTempMuteByTag</a> </td><td>禁言某个标签的用户的发言，只有管理员或创建者能操作。
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setTempChatBannedByTag" target="_blank">V2NIMChatroomService#setTempChatBannedByTag</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a5d6356ca743b2b5c12110803e2641857" target="_blank">updateMyRoomRole</a> </td><td>更新本人在聊天室内的信息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateSelfMemberInfo" target="_blank">V2NIMChatroomService#updateSelfMemberInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a1486aab9cb3cf71d2b81698a620c0181" target="_blank">updateRoomInfo</a> </td><td>更新聊天室信息
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomInfo" target="_blank">V2NIMChatroomService#updateChatroomInfo</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a4661d21600f9a442cd2681f4e1e66e66" target="_blank">updateQueue</a> </td><td>加入或者更新聊天室队列的元素。聊天室队列指聊天室（房间）中由多个元素（key-value 键值对）构成的队列，应用于直播间中的连麦队列场景和礼物队列展示等涉及队列化展示的场景，其中的元素可以是麦位、礼物展示位等
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a743ac7746aab083fb1104d2b4cf86ef9" target="_blank">batchUpdateQueue</a> </td><td>批量更新聊天室队列的元素
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#ac2d5e01bd0d266e333f1a06e2bba3d28" target="_blank">pollQueue</a> </td><td>取出聊天室队列的头部元素或者其他指定元素
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a6805a65fe17f4c57e4c5d207ed7de96b" target="_blank">fetchQueue</a> </td><td>排序列出聊天室队列的所有元素
           </td><td>同 V9 API
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html#a74d413158d79ffa040a40d5af86d7222" target="_blank">dropQueue</a> </td><td>删除聊天室队列
           </td><td>同 V9 API
           </td></tr>
</table>


#### 圈组

圈组的 SDK API 数量较多，请前往下文的[圈组核心类/接口类](#圈组相关)查阅圈组的 SDK API。




#### 用户资料


<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_service.html#a5559bf96fe33969054d8c5eebb1f239d" target="_blank">fetchUserInfo</a> </td><td>从服务器获取用户资料
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList" target="_blank">V2NIMUserService#getUserList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_service.html#aa7d3d8c6355b68fdf526608ed57ccec7" target="_blank">getAllUserInfo</a> </td><td>获取本地数据库中所有用户资料
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList" target="_blank">V2NIMUserService#getUserList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_service.html#a010c74c39442d33b924434df00660673" target="_blank">updateUserInfo</a> </td><td>更新本人的用户资料
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList" target="_blank">V2NIMUserService#getUserList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_service.html#a4aa9d14dcc3ecfd4805caea91b3161f6" target="_blank">searchUserInfosByKeyword</a> </td><td>搜索与关键字匹配的所有用户
           </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#searchUserByOption" target="_blank">V2NIMUserService#searchUserByOption</a>
           </td></tr>
</table>




#### 好友关系



<table>
<thead>
    <tr> <th style="width:180px">API</th><th>说明</th><th style="width:180px">对应 V10 API</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#aa3446aa2e519d287769266e672f86960" target="_blank">addFriend</a> </td><td>添加好友
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend" target="_blank">V2NIMFriendService#addFriend</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#a899638fe533bef2f39ef89334152fc03" target="_blank">ackAddFriendRequest</a> </td><td>同意/拒绝好友请求
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#acceptAddApplication" target="_blank">V2NIMFriendService#acceptAddApplication</a>/<a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#rejectAddApplication" target="_blank">V2NIMFriendService#rejectAddApplication</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#aac7e13e53b4efb1c7e186e3945c095c8" target="_blank">deleteFriend</a> </td><td>删除好友
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteFriend" target="_blank">V2NIMFriendService#deleteFriend</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#a62205a19fc1cb63dcbe268b8d30633d4" target="_blank">getFriendAccounts</a> </td><td>获取我的所有好友账号
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendList" target="_blank">V2NIMFriendService#getFriendList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#a1458ff768828fee3c22da916857494fc" target="_blank">addToBlackList</a> </td><td>将用户添加至黑名单
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addUserToBlockList" target="_blank">V2NIMFriendService#addUserToBlockList</a>
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html#a5b71dc5ab90049f35e1fcf587e5f0c47" target="_blank">searchFriendsByKeyword</a> </td><td>搜索与关键字匹配的所有好友
       </td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#searchFriendByOption" target="_blank">V2NIMFriendService#searchFriendByOption</a>
           </td></tr>
</table>


## SDK 核心类/接口类


::: note note 
以下仅列出 SDK 的核心类和接口类，如需查阅其他类或接口类的信息，请进入[Android SDK API 参考](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/annotated.html)搜索与查阅。
:::


#### 初始化与登录相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html" target="_blank">NIMClient</a> </td><td>SDK 核心类，提供初始化 SDK，获取各个服务能力接口，获取当前状态等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1lifecycle_1_1_sdk_lifecycle_observer.html" target="_blank">SdkLifecycleObserver</a> </td><td>SDK 生命周期观察者接口类，提供监听主进程初始化状态的接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1misc_1_1_misc_service.html" target="_blank">MiscService</a> </td><td>杂项接口类，提供日志文件上传、SDK 本地缓存、获取云信服务端时间等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html" target="_blank">AuthService</a>  </td><td>用户认证服务接口类，提供用户登录登出业务相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service_observer.html" target="_blank">AuthServiceObserver</a>  </td><td>用户认证服务观察者接口类，提供用户登录登出相关监听接口
           </td></tr>
</table>

#### 消息（单聊 & 群聊）与会话相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_message_builder.html" target="_blank">MessageBuilder</a> </td><td>云信 IM 消息构造器，提供构建各类型消息的接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service.html" target="_blank">MsgService</a>  </td><td>云信消息服务接口类，提供消息发送、消息查询、历史消息、消息扩展功能、获取未读数、已读回执、会话列表等相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_msg_service_observe.html" target="_blank">MsgServiceObserve</a> </td><td>云信 IM 消息服务观察者接口类，提供消息、会话等的监听接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1media_1_1record_1_1_audio_recorder.html" target="_blank">AudioRecorder</a> </td><td>高清语音录制工具类，提供语音录制相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1media_1_1player_1_1_audio_player.html" target="_blank">AudioPlayer</a> </td><td>和AudioRecorder对应音频播放器，提供语音播放相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1nos_1_1_nos_service.html" target="_blank">NosService</a> </td><td>网易云存储服务（NOS）接口类，提供云存储相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_system_message_service.html" target="_blank">SystemMessageService</a> </td><td>云信 IM 系统通知接口类，提供系统通知查询和管理接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1msg_1_1_system_message_observer.html" target="_blank">SystemMessageObserver</a> </td><td>云信 IM 系统通知观察者接口类，提供系统通知相关监听接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1lucene_1_1_lucene_service.html" target="_blank">LuceneService</a> </td><td>全文检索接口类，提供会话检索相关接口
           </td></tr>
</table>




#### 第三方离线推送相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1mixpush_1_1_mix_push_service.html" target="_blank">MixPushService</a> </td><td>IM 的第三方离线推送服务接口类，提供 IM 的第三方离线推送服务相关配置接口
        </td></tr>
</table>

#### 群组相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service.html" target="_blank">TeamService</a> </td><td> 群组接口类，提供创建群组、添加群成员等群组操作相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1team_1_1_team_service_observer.html" target="_blank">TeamServiceObserver</a> </td><td> 群组观察者接口类，提供监听群组成员变动、资料变动等的监听接口
           </td></tr>
</table>



#### 超大群相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service.html" target="_blank">SuperTeamService</a> </td><td> 超大群服务接口类，提供超大群成员管理、超大群消息发送、超大群资料管理等相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1superteam_1_1_super_team_service_observer.html" target="_blank">SuperTeamServiceObserver</a> </td><td>超大群观察者接口类，提供超大群监听接口
           </td></tr>
</table>



#### 聊天室相关


<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service.html" target="_blank">ChatRoomService</a> </td><td> 聊天室服务接口类，提供进出聊天室、发送聊天室消息、聊天室成员管理、聊天室队列服务、聊天室标签等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_message_builder.html" target="_blank">ChatRoomMessageBuilder</a> </td><td>聊天室消息构造器，提供构造各类型聊天室消息的接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1chatroom_1_1_chat_room_service_observer.html" target="_blank">ChatRoomServiceObserver</a> </td><td>聊天室观察者接口类， 提供聊天室监听接口
           </td></tr>
</table>





#### 圈组相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_service.html" target="_blank">QChatService</a> </td><td>圈组接口类，提供圈组登录登出相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_server_service.html" target="_blank">QChatServerService</a> </td><td>圈组服务器接口类，提供圈组服务器相关接口，如果创建服务器、邀请服务器成员、查询服务器成员等
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_channel_service.html" target="_blank">QChatChannelService</a> </td><td>圈组频道接口类，提供圈组频道相关接口，如果创建频道、查询频道、查询频道未读信息等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_message_service.html" target="_blank">QChatMessageService</a> </td><td>圈组消息接口类，提供发送消息、撤回消息、发送消息正在输入事件等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1_q_chat_service_observer.html" target="_blank">QChatServiceObserver</a> </td><td>圈组观察者接口类，提供圈组监听接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1mixpush_1_1_q_chat_push_service.html" target="_blank">QChatPushService</a> </td><td>圈组的第三方离线推送服务接口类，提供圈组的第三方离线推送服务相关配置接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_media_kit.html" target="_blank">QChatMediaKit</a> </td><td>圈组多媒体频道接口类，提供圈组多媒体频道的初始化、连接、修改多媒体频道参数等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_controller.html" target="_blank">QChatRTCChannelController</a> </td><td>圈组多媒体频道控制器，提供多媒体频道成员管理、摄像头切换、扬声器管理、视频画布设置等接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1qcmedia_1_1_q_chat_r_t_c_channel_listener.html" target="_blank">QChatRTCChannelListener</a> </td><td>圈组多媒体频道事件监听器，提供多媒体频道的监听接口
           </td></tr>
</table>


#### 用户资料相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_service.html" target="_blank">UserService</a> </td><td> 用户资料操作相关接口，如更新本人的用户资料、搜索与关键字匹配的用户等
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1uinfo_1_1_user_info_provider.html" target="_blank">UserInfoProvider</a> </td><td> 用户信息提供者，由开发者提供用户信息给 SDK
           </td></tr>
</table>



#### 好友关系相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th></tr></thead>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service.html" target="_blank">FriendService</a> </td><td> 好友关系服务接口类，提供好友管理、好友关系、黑名单、消息提醒等相关接口
           </td></tr>
    <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1friend_1_1_friend_service_observe.html" target="_blank">FriendServiceObserve</a> </td><td>好友关系、黑名单变更等的监听接口 
           </td></tr>
</table>



















