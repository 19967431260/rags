
本文介绍 iOS SDK API 的概述性信息，并列出核心 API 与核心类或接口类，方便您查阅 API 信息。 

## SDK API 概述

<details><summary>点击查看 API 概述</summary>

### 调用方式

IM 所有业务均通过 NIMSDK 单例进行调用。虽然所有的云信接口都是线程安全的，但为了防范于未然，推荐您只在主线程调用相应接口。

```
@interface NIMSDK : NSObject
/**
 *  获取SDK实例
 *  @return NIMSDK实例
 */
+ (instancetype)sharedSDK;
@end
```

以获取聊天管理类为例：

```
id<NIMChatManager> chatManager = [[NIMSDK sharedSDK] chatManager];
```


### 通知方式

IM iOS SDK 通过以下两种方式通知上层 API 调用结果。两种方式都只在主线程触发。
- 回调（callback），一般回调接口直接反映在对应接口的 `completion` 参数上，调用时设置即可。
- 委托（delegate），委托则需要开发者在合适的时机，在对应管理类上进行添加和移除：一般推荐在相应 `ViewController` 或管理类初始化进行委托注册，在其销毁时进行移除。

例如，开发者需要在会话页上监听消息的发送结果。

```
@implementation MySessionViewController
- (void)dealloc
{
  ...
    [[NIMSDK sharedSDK].chatManager removeDelegate:self];
  ...
}
- (void)viewDidLoad 
{
  ...
    [[NIMSDK sharedSDK].chatManager addDelegate:self];
  ...
}
#pragma mark - NIMChatManagerDelegate
- (void)sendMessage:(NIMMessage *)message didCompleteWithError:(NSError *)error
{
    //发送结果
}
```

所有调用错误都会以 `NSError` 的形式暴露。针对不同场景，我们将错误进行分类，主要分为以下两种错误域和对应错误码：


| 错误域               | 错误码             | 说明                 |
|----------------------|--------------------|----------------------|
| NIMLocalErrorDomain  | [`NIMLocalErrorCode`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/db/d9d/_n_i_m_global_defs_8h.html#a6f9aab7b0429e98728e92077c66067ed)  | 本地操作出错导致     |
| NIMRemoteErrorDomain | [`NIMRemoteErrorCode`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/db/d9d/_n_i_m_global_defs_8h.html#ab784655e99fbd2ef91fc353ebcdd233a) | 与服务器交互出错导致 |


在开发过程中遇到错误情况，可以对照错误域和错误码进行排查，具体定义可以参考 [`NIMGlobalDefs.h`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/db/d9d/_n_i_m_global_defs_8h.html)。您也可以通过 `NSError` 中 `userInfo` 对应的错误描述信息定位问题。


</details>

## SDK API 参考


- 客户端 API 参考（iOS）：[NIM SDK-iOS](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/index.html)

    ::: note note 
    如需查看圈组 API 参考，请在进入上述链接后搜索“QChat”。
    :::
- NIMQChatMediaKit API 参考（iOS）：[NIMQChatMediaKit-iOS](https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/index.html)

    ::: note note
    NIMQChatMediaKit 是实现圈组实时互动频道的必要插件，引入 NIMQChatMediaKit 才能实现圈组的[实时互动频道](https://doc.yunxin.163.com/TM5MzM5Njk/docs/DYzMDM1MjM?platform=iOS)相关功能。
    :::


## SDK 核心 API

以下仅列出 SDK 的部分核心 API，如需查阅其他 SDK API 信息，请参考上述 API 参考。

### 初始化 & 登录

<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#af48773fab3390f4e2f665740bd51560a" target="_blank"> registerWithOption:</a> </td><td>初始化 SDK</td><td> <a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a4140971377bec8212dabd66fdea0bbb3" target="_blank"> registerWithOptionV2:v2Option:</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a396c37435659c3b0966336c4b349e1df" target="_blank"> sdkVersion</a> </td><td>获取 SDK 版本号</td><td>同 V9 API
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a4e0700424d6e77e47939e3adfbdbe42c" target="_blank"> sharedSDK</a> </td><td>获取 SDK 实例</td><td>同 V9 API
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#adf8e3787e36a122d51dfbbc8070cd4ec" target="_blank"> appKey</a> </td><td>获取 AppKey</td><td>同 V9 API
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a075db650901791cc08043314ed3e1fd0" target="_blank"> updateApnsToken:</a> </td><td>更新 APNS Token<note type=note>若需要设置自定义推送文案，请使用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#ab84b0a2d91225c8b10de070205fd9d2a" target="_blank">updateApnsToken:customContentKey:</a>或<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a76e4b4325d3ae560eedfab3e67e3afff" target="_blank">updateApnsToken:customContentKey:qchatCustomContentKey:</a>（含圈组自定义推送文案）</note></td><td>同 V9 API
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#a464f820cb43e0f4385fc23281e516357" target="_blank"> updatePushKitToken:</a> </td><td>更新 PushKit Token<note type=note>目前仅支持 PKPushTypeVoIP</note></td><td>同 V9 API
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html#af2035d0f810e9facfd528fd0557a35fa" target="_blank"> qchatWithOption:</a> </td><td>设置圈组选项，用于设置圈组推送证书</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html#a8e1980b6675f9ae40a13204c01065701" target="_blank">  sharedConfig</a> </td><td>获取配置项实例<note type=note><a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html" target="_blank">NIMSDKConfig</a> 是一个单例，用于多样的初始化配置，包括设置缩略动图等，推荐在调用初始化接口前配置</note></td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#af19374f0237b69dcb61b04499dcf1454" target="_blank">  login:token:completion:</a> </td><td>手动登录<note type=note>若需要选择鉴权方式进行登录，请使用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7dedc10fcbadf36fb66ce9cc9710b8f6" target="_blank">login:token:authType:loginExt:completion:</a></note></td><td> <a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#login" target="_blank">login:token:option:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a8c05c17ff5369ce9b70c6c7d33d6622e" target="_blank"> autoLogin:token:</a> </td><td>自动登录</td><td>同上
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a60f99812a55cecb9069e748ed586513b" target="_blank"> logout:</a></td><td>登出</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#logout" target="_blank">logout:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#adc1ca83617c1ace26541488881d90541" target="_blank">kickOtherClient:completion:</a> </td><td>踢人</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#kickOffline" target="_blank">kickOffline:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#aca722d98fdda2e28e877a8aabfb86afa" target="_blank">currentAccount</a> </td><td>获取当前登录账号</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginUser" target="_blank">getLoginUser</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a9a15a6e943bcea6b2a019c32b6cb3767" target="_blank">currentAuthMode</a> </td><td>获取当前的 SDK 鉴权模式</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a055c3df878ee55c5e492f43444e2f8f3" target="_blank">currentLoginClients</a> </td><td>获取当前登录的设备列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginClients" target="_blank">getLoginClients</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/messaging/references/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a94179d558b63663a2390aa2a74b50bda" target="_blank">isLogined</a> </td><td>是否已登录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TQ5NTUwNzQ?platform=client#getLoginStatus" target="_blank">getLoginStatus</a>
           </td></tr>
</table>



### 消息（单聊 & 群聊 & 聊天室）

<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a88b87af2e32adf7f65832fc3fbfe5591" target="_blank">sendMessage:toSession:completion:</a> </td><td>发送消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendMessage" target="_blank">sendMessage:conversationId:params:success:failure:progress:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#ad7cced74208726dbc56fb42dcb0393a4" target="_blank">resendMessage:error:</a> </td><td>重新发送消息</td><td>同上
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a0e958f0b41ecec979df02b6a9fcb78d4" target="_blank">cancelSendingMessage:</a> </td><td>取消正在发送的消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#cancelMessageAttachmentUpload" target="_blank">cancelMessageAttachmentUpload:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#ab756e6d5a5d54d9d74f07e3b08ceaebc" target="_blank">forwardMessage:toSession:error:</a> </td><td>转发消息</td><td>同 V9 API
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a5d0c14ffef33a61cf6f41bfc3b2fd39f" target="_blank">makeForwardMessageFromMessage:error:</a> </td><td>生成转发消息，得到转发消息后，开发者需要再调用<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a8d9da2d171023c675ffc84b7520aff8e" target="_blank">sendForwardMessage:toSession:error:</a> 进行发送</td><td>同 V9 API
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a9b320d36c9d7956e434a436088505376" target="_blank">sendMessageReceipt:completion:</a> </td><td>发送单聊消息已读回执</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendP2PMessageReceipt" target="_blank">sendP2PMessageReceipt:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#ae1635a9642adbc5a0486d8d57c4f8abb" target="_blank">sendTeamMessageReceipts:completion:</a> </td><td>发送群聊消息已读回执</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#sendTeamMessageReceipts" target="_blank">sendTeamMessageReceipts:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a89fddd03150a1c2a4d3cfebfebea11aa" target="_blank">refreshTeamMessageReceipts:</a> </td><td>刷新群组消息已读、未读数量</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceipts" target="_blank">getTeamMessageReceipts:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#aeb9f293adf69da1e008423a54fc7f2e1" target="_blank">queryMessageReceiptDetail:completion:</a> </td><td>查询群组消息回执情况</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getTeamMessageReceiptDetail" target="_blank">getTeamMessageReceiptDetail:memberAccountIds:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a8922676089ac66dbab2432db12f88156" target="_blank">queryMessageReceiptDetail:accountSet:completion:</a> </td><td>查询群组消息指定用户的回执详情</td><td>同上
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#ac426aea8e1b9f2dac305ac8b81ea085a" target="_blank">localMessageReceiptDetail:</a> </td><td>从本地数据库查询单条群组消息已读、未读账号列表</td><td>同上
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a52fd8155c790832ebf302c51c2c543ac" target="_blank">revokeMessage:option:completion:</a> </td><td>撤回消息，撤回时可设置推送内容，否计入未读数等</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#revokeMessage" target="_blank">revokeMessage:revokeParams:success:failure:</a>
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a998647681f2588fd1b1651eafdda6442" target="_blank">fetchMessageAttachment:error:</a> </td><td>收取消息附件</td><td>同 V9 API
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a2187f62c4e2280a3964070baf2274179" target="_blank">cancelFetchingMessageAttachment:</a> </td><td>取消收取消息附件</td><td>同 V9 API
           </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a6192b3d5446cbe8a91cc975b892e1a34" target="_blank">messageInTransport:</a> </td><td>消息是否正在传输 （发送/接受附件）</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html#a81cfaddca8f718e89dcd3b7e4ee99bb9" target="_blank">messageTransportProgress:</a> </td><td>传输消息的进度 （发送/接受附件）</td><td>同 V9 API
    </td></tr>
        <tr> <td>无</td><td>获取单聊消息已读回执</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getP2PMessageReceipt" target="_blank">getP2PMessageReceipt:success:failure:</a>
    </td></tr>
        <tr> <td>无</td><td>查询单聊消息是否已读</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#isPeerRead" target="_blank">isPeerRead:</a>
    </td></tr>
        <tr> <td>无</td><td>语音转文字</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#voiceToText" target="_blank">voiceToText:success:failure:</a>
    </td></tr>
</table>


### 消息扩展

<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a50bb3a128f313d8878344e2aca92702e" target="_blank">reply:to:completion:</a> </td><td>引用一条消息进行回复，形成消息回复树状结构（Thread）</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#replyMessage" target="_blank">replyMessage:replyMessage:params:success:failure:progress:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a3402950c64d3ea7e5283df98e833396b" target="_blank">subMessages:</a> </td><td>本地获取 Thread Talk 的消息列表</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a15fe38eebf3ec2e5258bfc2afcca5c05" target="_blank">subMessagesCount:</a> </td><td>本地获取 Thread Talk 的消息数量</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a0979ab549079956cfcb1dab3bc20bfff" target="_blank">fetchSubMessages:option:completion:</a> </td><td>获取指定消息的 Thread Talk 子消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a097862599be7bf7ffdb3de77a6ef6161" target="_blank">fetchHistoryMessages:syncToDB:completion:</a> </td><td>根据 MessageId 等获取历史消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a5e1ea974e0cf1161d09a8dce9c3ce477" target="_blank">addQuickComment:toMessage:completion:</a> </td><td>添加快捷评论，如表情等 reaction</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addQuickComment" target="_blank">addQuickComment:index:serverExtension:pushConfig:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#abcc5f65e1f1544ac22d191c665953a27" target="_blank"> deleteQuickComment:completion:</a> </td><td>从服务端删除快捷评论</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeQuickComment" target="_blank">removeQuickComment:index:serverExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a2237b76b3decf83f8db3b35ea205474e" target="_blank">fetchQuickComments:completion:</a> </td><td>批量获取快捷评论列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getQuickCommentList" target="_blank">getQuickCommentList:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#acf4683bf7e3a08f46c8cf9ee93fc5e97" target="_blank">quickCommentsByMessage:completion:</a> </td><td>根据消息本地获取对应的快捷评论</td><td>同上
    </td></tr>
   <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#aec628ead8a6e61c9276d66a95a6d9cd9" target="_blank">addCollect:completion:</a> </td><td>将某条消息添加为收藏</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#addCollection" target="_blank">addCollection:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a1fddba256cf609fb06537b1ae622fb32" target="_blank">removeCollect:completion:</a> </td><td>批量移除收藏</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#removeCollections" target="_blank">removeCollections:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a1fff3fbcbceee41454eddf1389bdd6a7" target="_blank">updateCollect:completion:</a> </td><td>更新收藏的扩展信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateCollectionExtension" target="_blank">updateCollectionExtension:serverExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#abf4894007c54b2d46e2835f717e0f50f" target="_blank">queryCollect:completion:</a> </td><td>分页查询收藏列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getCollectionListByOption" target="_blank">getCollectionListByOption:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#abe058e39fb2f309171442b2f54221d11" target="_blank">addStickTopSession:completion:</a> </td><td>添加一条置顶记录</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a00783806cce5a85daa94e39bcf9c2b17" target="_blank">removeStickTopSession:completion:</a> </td><td>删除一条置顶记录</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a1acaa829a468604d495f8384d896f396" target="_blank">udpateStickTopSession:completion:</a> </td><td>更新一条置顶记录的扩展信息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a9b7722154f79149840e29500d1bcad15" target="_blank">loadStickTopSessionInfos:</a> </td><td>查询所有的置顶记录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getPinnedMessageList" target="_blank">getPinnedMessageList:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#aac6bc9f094767613aee56c4d8dee7083" target="_blank">loadRecentSessionsWithOptions:completion:</a> </td><td>按照置顶会话获取最近会话列表</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a2181be623b1e6acbb221b760ded1cf6c" target="_blank">sortRecentSessions:withStickTopInfos:</a> </td><td>根据置顶信息排序最近会话</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a3a42b2837c96c627353540d357ef25ed" target="_blank">stickTopInfoForSession:</a> </td><td>查询某个会话的置顶信息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#aa528038a22641d3e730541e11c27583e" target="_blank">addMessagePin:completion:</a> </td><td>PIN 一条消息，即添加一条 PIN 记录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#pinMessage" target="_blank">pinMessage:serverExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#af9fadad219dac737380145ed743fd848" target="_blank">removeMessagePin:completion:</a> </td><td>删除一条消息的 PIN 记录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#unpinMessage" target="_blank">unpinMessage:serverExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#acd010955f79c732810895f690d0b2fa8" target="_blank">updateMessagePin:completion:</a> </td><td>更新一条消息的 PIN 记录的扩展信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updatePinMessage" target="_blank">updatePinMessage:serverExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#ae98229888aedabbe5424e46b86c56ba6" target="_blank">loadMessagePinsForSession:completion:</a> </td><td>查询所有的 PIN 记录（登录后首次查询该会话会触发一次网络同步）</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getPinnedMessageList" target="_blank">getPinnedMessageList:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html#a8a389d4350b869147328bed1931effa6" target="_blank">pinItemForMessage:</a> </td><td>查询某条消息的 PIN 记录</td><td>同 V9 API
    </td></tr>
</table>

### 会话列表


<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a4294fd32d0c7831892498b56263847bd" target="_blank">deleteMessage:option:</a> </td><td>删除某条消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessage" target="_blank">deleteMessage:serverExtension:onlyDeleteLocal:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a181cfe4f50e03afd1a12e92df070e29b" target="_blank">deleteAllmessagesInSession:option:</a> </td><td>删除某个会话的所有消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages" target="_blank">deleteMessages:serverExtension:onlyDeleteLocal:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#ae5fc504cd661454b3a6cfb8d4286d8eb" target="_blank">deleteAllMessages:</a> </td><td>删除所有会话消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages" target="_blank">deleteMessages:serverExtension:onlyDeleteLocal:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#ac25709ba2c8bdf65be0887f12b927a10" target="_blank">deleteServerSessions:completion:</a> </td><td>删除服务端所有会话消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a5cba23eacf88be9c834cab2ab3d04917" target="_blank">deleteMessagesInSession:option:completion:</a> </td><td>删除指定范围内的消息，如指定时间范围</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#deleteMessages" target="_blank">deleteMessages:serverExtension:onlyDeleteLocal:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a2d3e92d0f551e6975685b31c4f4f953d" target="_blank">deleteRecentSession:option:completion:</a> </td><td>删除某个最近会话</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a2770f058b011e8d1179dd5378474445c" target="_blank">addEmptyRecentSessionBySession:option:</a> </td><td>增加某个最近会话</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a533aee08f60b701cb8141aa4f74dba70" target="_blank">markAllMessagesRead</a> </td><td>设置所有会话消息为已读</td><td>同 V9 API
       </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a6148020908a3bc85c55720002ca7d2e2" target="_blank">markAllMessagesReadInSession:completion:</a> </td><td>设置一个会话里所有消息为已读</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a5f23695ae241e8e28b359eeea8d77d14" target="_blank">batchMarkMessagesReadInSessions:completion:</a> </td><td>批量设置多个会话消息已读</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#accef3d610c102acd8a2cdee489d18b15" target="_blank">updateMessage:forSession:completion:</a> </td><td>更新本地已存的消息记录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension" target="_blank">updateMessageLocalExtension:localExtension:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#af1a8312314bd9fd3775b7412b3cd824c" target="_blank">saveMessage:forSession:completion:</a> </td><td>保存会话消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#insertMessageToLocal" target="_blank">insertMessageToLocal:conversationId:senderId:createTime:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a449b150e280f4eeae11adbddc1325aec" target="_blank"> importRecentSessions:completion:</a> </td><td>导入最近会话</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#acdb9b2c4e4c3127c2c2d55728eba4640" target="_blank">getMessagesDynamically:completion:</a> </td><td>动态查询历史消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageList" target="_blank">getMessageList:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#af6c9cbd529fc72cdc0496fb43610b28d" target="_blank">messagesInSession:messageIds:</a> </td><td>根据消息 ID 查询消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a00d36c0ff742ed767fc27fb65a6125e2" target="_blank">allUnreadCount:</a> </td><td>获取所有的最近会话未读数</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a268a67cf3e73dd97fb9d559f0f682a27" target="_blank">allUnreadMessagesInSession:completion:</a> </td><td>获取所有的未读会话消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a834c8b81ddc338b7acdd75dc4ad9f9ee" target="_blank">fetchServerSessions:completion:</a> </td><td>从服务端分页获取历史会话列表</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a5275314757df18fdc5c6a34aecfdea17" target="_blank">fetchServerSessionBySession:completion:</a> </td><td>从服务端根据当前 session 获取会话信息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a6b909f70d38231c21c2b036fd3730a12" target="_blank">updateRecentLocalExt:recentSession:</a> </td><td>更新最近会话的本地扩展</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a30717ff6bc0721f339db6958f81ef095" target="_blank">fetchMessageHistory:option:result:</a> </td><td>从服务器上获取一个会话里某条消息之前的若干条的消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByRefers" target="_blank">getMessageListByRefers:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a27bcc47e8d7e947b40c0a6655d802001" target="_blank">retrieveServerMessages:option:result:</a> </td><td>根据关键字从服务器上检索消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#searchCloudMessages" target="_blank">searchCloudMessages:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#af9d22c7d35f36aab99898d5cdf92a8c8" target="_blank">searchMessages:option:result:</a> </td><td>搜索本地会话内消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#a213c7a7c0084090609d7248674b4c5d5" target="_blank">exportMeessageInfosWithDelegate:progress:completion:</a> </td><td>导出历史消息到本地文件</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#adf7766fe6da814b2eff236a92a4b3c5e" target="_blank">importMessageInfosAtPath:delegate:progress:completion:</a> </td><td>导入历史消息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html#adf7766fe6da814b2eff236a92a4b3c5e" target="_blank">importMessageInfosAtPath:delegate:progress:completion:</a> </td><td>导入历史消息</td><td>同 V9 API
    </td></tr>
      <tr> <td>无</td><td>根据消息客户端 ID 获取历史消息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#getMessageListByIds" target="_blank">getMessageListByIds:success:failure:</a>
    </td></tr>
</table>


### APNs 离线推送


<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6f/protocol_n_i_m_apns_manager-p.html#a1b7237baf559d298ef3badc090ed875b" target="_blank">currentMultiportConfig</a> </td><td>获取当前多端推送策略配置</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6f/protocol_n_i_m_apns_manager-p.html#a6a5eeff3c18fe83dad12ee376512b9eb" target="_blank">updateApnsMultiportConfig:completion:</a> </td><td>设置推送自定义多端推送策略配置</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6f/protocol_n_i_m_apns_manager-p.html#ad0762030b07a317dff5a68ce610a161a" target="_blank">currentSetting</a> </td><td>获取当前的推送免打扰设置</td><td>同 V9 API
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6f/protocol_n_i_m_apns_manager-p.html#aa85cc2cc7eb9f432b2642d29b55e4df9" target="_blank">updateApnsSetting:completion:</a> </td><td>更新推送免打扰设置</td><td>同 V9 API
           </td></tr>
</table>


### 群组


<table>
<thead>
    <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aa451717d26bc70053da5820453952daa" target="_blank">createTeam:users:completion:</a> </td><td>创建群组</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#createTeam" target="_blank">createTeam:inviteeAccountIds:postscript:antispamConfig:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aacfc27ca5b9158de7992f147abf25037" target="_blank">addUsers:toTeam:postscript:attach:completion:</a> </td><td>邀请用户入群</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember" target="_blank">inviteMember:teamType:inviteeAccountIds:postscript:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aa8a62870ebcd426d10e24aa4e9ace291" target="_blank">kickUsers:fromTeam:completion:</a> </td><td>从群组中移除成员，只有群主和管理员有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember" target="_blank">kickMember:teamType:memberAccountIds:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a0e56af75d4bc3926905663369087d8fd" target="_blank">dismissTeam:completion:</a> </td><td>解散群组，只有群主有权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#dismissTeam" target="_blank">dismissTeam:teamType:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#adaabefa04debd6b3d2a80450ef4650fb" target="_blank">quitTeam:completion:</a> </td><td>退出群组</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam" target="_blank">leaveTeam:teamType:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a910dc932f569db7bf9bf5a6f86be63e5" target="_blank">allMyTeams</a> </td><td>获取我的所有群组</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getjoinedteamlist" target="_blank">getJoinedTeamList:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a4ac02fcc4f36f7da0314a9cf2dc39fe4" target="_blank">updateTeamInfos:teamId:completion:</a> </td><td>修改群组信息，可一次性修改群组的多个属性，如名称,公告等，传入的数据键值对是 {@(NIMTeamUpdateTag) : NSString}，无效数据将被过滤<note type=note>同时 SDK 支持修改单个群组属性的接口，如只修改群组名称：<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#adb896ceb51f1a9cb7a8cdab798f197af"target="_blank">updateTeamName:teamId:completion:</a><br/>更多群组属性修改的接口请参见<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html" target="_blank">NIMTeamManager</a></note></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo" target="_blank">updateTeamInfo:teamType:updateTeamInfoParams:antispamConfig:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#ae9c4a8fcddbb29b187ba15b0b395a037" target="_blank">updateTInfosLocal:</a> </td><td>更新群组的本地信息</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a16d652c0444c0f4e41073ed462bf61da" target="_blank">updateUserNick:newNick:inTeam:completion:</a> </td><td>修改群成员昵称，只有群主才有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick" target="_blank">updateTeamMemberNick:teamType:accountId:teamNick:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a7e9402f28c57daedaf257a882ce43e03" target="_blank">updateMyCustomInfo:inTeam:completion:</a> </td><td></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo" target="_blank">updateSelfTeamMemberInfo:teamType:memberInfoParams:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#acba814a3ebb956944bc22aeb9d737b32" target="_blank">fetchTeamInfo:completion:</a> </td><td>查询单个群组信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo" target="_blank">getTeamInfo:teamType:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a672f8aab33af4715fff0527ccbd3ed7e" target="_blank"> fetchTeamsWithTimestamp:completion:</a> </td><td>查询所有的群组信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">getTeamMemberList:teamType:queryOption:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aedebcd1b3ea14e4abe4340e7b93599b3" target="_blank">teamById:</a> </td><td>根据群 ID 查询具体的单个群信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo" target="_blank">getTeamInfo:teamType:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a92c2bfe2dad31e0bb076cec49d368d12" target="_blank"> fetchTeamInfoList:completion:</a> </td><td>根据群 ID 查询具体的群列表信息，最多10个</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfoByIds" target="_blank">getTeamInfoByIds:teamType:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a99c45d3c1c037565c656e2fd20a26dc2" target="_blank">searchTeamWithOption:completion:</a> </td><td>根据关键字等选项搜索群组</td><td>同 V9 API
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a73618ed08c6a6fd056b18222b1c03ea0" target="_blank">applyToTeam:message:completion:</a> </td><td>申请加入群组</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam" target="_blank">applyJoinTeam:teamType:postscript:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a0db8a5eb8054e80a0ac684c5c299ae85" target="_blank">passApplyToTeam:userId:completion:</a> </td><td>同意入群申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication" target="_blank">acceptJoinApplication:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a4c20011145877be9ebdfff552b7c123d" target="_blank">rejectApplyToTeam:userId:rejectReason:completion:</a> </td><td>拒绝入群申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication" target="_blank">rejectJoinApplication:postscript:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#af7c2a53bf19d0a361ca752ae7c12f66c" target="_blank">addManagersToTeam:users:completion:</a> </td><td>添加管理员，仅群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">updateTeamMemberRole:teamType:memberAccountIds:memberRole:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a535ffb0a05f029c8480d40cf65d6d2a5" target="_blank">removeManagersFromTeam:users:completion:</a> </td><td>移除管理员，仅群主有此权限</td><td>同上
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#ac4ec9959417bda6c4a9827ee3c66b52f" target="_blank">transferManagerWithTeam:newOwnerId:isLeave:completion:</a> </td><td>转让群组，只有群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner" target="_blank">transferTeamOwner:teamType:accountId:leave:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aee60c03642d42b53395ab97051764e05" target="_blank">acceptInviteWithTeam:invitorId:completion:</a> </td><td>接受别人的入群邀请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation" target="_blank">acceptInvitation:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#ae800ceef71b6a74ce4613556d1a219ac" target="_blank">rejectInviteWithTeam:invitorId:rejectReason:completion:</a> </td><td>拒绝别人的入群邀请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation" target="_blank">rejectInvitation:postscript:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a7475399ce94a7004e191dab75b23d6de" target="_blank">teamMember:inTeam:</a> </td><td>获取指定的单个群成员信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds" target="_blank">getTeamMemberListByIds:teamType:accountIds:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#af16d368640ccd44649fa72e8cbf3dd3b" target="_blank">fetchTeamMembers:completion:</a> </td><td>获取群成员列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">getTeamMemberList:teamType:queryOption:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#ac3a3d7872920fba5077d0304e149506a" target="_blank">fetchTeamMembersFromServer:completion:searchTeam</a> </td><td>从服务器上查询群组成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">getTeamMemberList:teamType:queryOption:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aeca1589da7e0ed2e484af689b01eba81" target="_blank">updateMuteState:userId:inTeam:completion:</a> </td><td>禁言/解除禁言某个群成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus" target="_blank">setTeamMemberChatBannedStatus:teamType:accountId:chatBanned:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#ab4368dde360a23704b1911d14c50c823" target="_blank">updateMuteState:inTeam:completion:</a> </td><td>对整个群禁言或解除禁言，对普通成员生效，只有群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode" target="_blank">setTeamChatBannedMode:teamType:chatBannedMode:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aecb664b44d5018a262e826e588e07c5a" target="_blank">fetchTeamMutedMembers:completion:</a> </td><td>查询被禁言群成员列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">getTeamMemberList:teamType:queryOption:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#adea61d0ff2fc0516e1745c2328b625c1" target="_blank">fetchInviterAccids:withTargetMembers:completion:</a> </td><td>查询群成员邀请人账号</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberInvitor" target="_blank">getTeamMemberInvitor:teamType:accountIds:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#a8d35465936ccabdb5d036b11c8abe761" target="_blank">updateNotifyState:inTeam:completion:</a> </td><td>修改群通知状态</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setteammessagemutemode" target="_blank">setTeamMessageMuteMode:teamType:muteMode:success:failure:</a>
    </td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#adbf464f8123c5d583326e89258811ef7" target="_blank">notifyStateForNewMsg:</a> </td><td>获取群通知状态</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getTeamMessageMuteMode" target="_blank">getTeamMessageMuteMode:teamType:</a>
    </td></tr>
</table>



### 超大群
<table>
   <thead>
      <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a814ff195484e8b9f1f205fce08bd3d5c" target="_blank">addUsers:toTeam:postscript:attach:completion:</a> </td><td>邀请用户加入超大群</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#inviteMember" target="_blank">inviteMember:teamType:inviteeAccountIds:postscript:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a75250a6a47feba307300bf46814ac35c" target="_blank">kickUsers:fromTeam:completion:</a> </td><td>从超大群中移除成员，只有群主和管理员有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#kickMember" target="_blank">kickMember:teamType:memberAccountIds:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a89b32b987fb8a313438d7e4bd98d3523" target="_blank">quitTeam:completion:</a> </td><td>退出超大群</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#leaveTeam" target="_blank">leaveTeam:teamType:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#aed06b83b4c076caa4124a9c11c8d5c8d" target="_blank">allMyTeams</a> </td><td>获取我的所有超大群</a></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getjoinedteamlist" target="_blank">getJoinedTeamList:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a46032157bb9ca93b8658f5a6037da52a" target="_blank">updateTeamInfos:teamId:completion:</a> </td><td>修改超大群信息，可一次性修改超大群的多个属性，如名称,公告等，传入的数据键值对是 {@(NIMTeamUpdateTag) : NSString}，无效数据将被过滤<note type=note>同时 SDK 支持修改单个超大群属性的接口，如只修改超大群名称：<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a2993fbc149ca40a70c72d1afac15b2d8" target="_blank">updateTeamName:teamId:completion:</a><br/>更多超大群属性修改的接口请参见<a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html" target="_blank">NIMSuperTeamManagerr</a></note></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamInfo" target="_blank">updateTeamInfo:teamType:updateTeamInfoParams:antispamConfig:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#ab09ee03b15b63984699b795972c1e117" target="_blank">updateUserNick:newNick:inTeam:completion:</a> </td><td>修改群成员昵称，只有群主才有此权限</a></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberNick" target="_blank">updateTeamMemberNick:teamType:accountId:teamNick:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a21ec766a980831d1c83d483d7fe65b57" target="_blank">updateMyCustomInfo:inTeam:completion:</a> </td><td>修改超大群中自己的扩展字段</a></td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateSelfTeamMemberInfo" target="_blank">updateSelfTeamMemberInfo:teamType:memberInfoParams:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a9d54b3c9d847dfc552cdc91c5c59c30f" target="_blank">fetchTeamInfo:completion:</a> </td><td>查询单个超大群信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamInfo" target="_blank">getTeamInfo:teamType:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a8843e6adba9e71f241747706baa2367c" target="_blank">teamById:</a> </td><td>根据群 ID 查询具体的单个超大群信息</td><td>同上
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a6522af71ded2f2e6704a5d6610684ec0" target="_blank">applyToTeam:message:completion:</a> </td><td>申请加入超大群</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#applyJoinTeam" target="_blank">applyJoinTeam:teamType:postscript:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a053757a74af7c4403f540dd3753faed1" target="_blank">passApplyToTeam:userId:completion:</a> </td><td>同意加入超大群的申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptJoinApplication" target="_blank">acceptJoinApplication:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#afa6640118160ba191a7adc6d75335a09" target="_blank">rejectApplyToTeam:userId:rejectReason:completion:</a> </td><td>拒绝加入超大群的申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectJoinApplication" target="_blank">rejectJoinApplication:postscript:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#aa025e60f8eddc59debf3b7b9d8481761" target="_blank">addManagersToTeam:users:completion:</a> </td><td>添加超大群管理员，仅群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#updateTeamMemberRole" target="_blank">updateTeamMemberRole:teamType:memberAccountIds:memberRole:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a3802158480cc2fafcce41487da130d6f" target="_blank">removeManagersFromTeam:users:completion:</a> </td><td>移除超大群管理员，仅群主有此权限</td><td>同上
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#ac64b11ed3c6196021b6895d11a01ad8a" target="_blank">transferManagerWithTeam:newOwnerId:isLeave:completion:</a> </td><td>转让超大群，只有群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#transferTeamOwner" target="_blank">transferTeamOwner:teamType:accountId:leave:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#acef98776921d86718541e0aea1ad0176" target="_blank">acceptInviteWithTeam:invitorId:completion:</a> </td><td>接受别人的加入超大群的邀请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#acceptInvitation" target="_blank">acceptInvitation:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#ad6b8f2d7453975b8db68ae8a47f67efd" target="_blank">rejectInviteWithTeam:invitorId:rejectReason:completion:</a> </td><td>拒绝别人的加入超大群的邀请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#rejectInvitation" target="_blank">rejectInvitation:postscript:success:failure:</a>
</td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a81257a8ca44218c9663c470888bebfcc" target="_blank">teamMember:inTeam:</a> </td><td>获取指定的单个群成员信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberListByIds" target="_blank">getTeamMemberListByIds:teamType:accountIds:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#aa8693b4d06d92fd6fb5ba5de4f672c49" target="_blank">fetchTeamMembers:completion:</a> </td><td>获取超大群成员列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#getTeamMemberList" target="_blank">getTeamMemberList:teamType:queryOption:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a1004dcf788e397fd3d7ef0bf572d1c81" target="_blank">fetchTeamMutedMembers:completion:</a> </td><td>查询被禁言群成员列表</td><td>同上
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a26a51644d8e0a35f812c46846106a255" target="_blank">updateMuteState:userIds:inTeam:completion:</a> </td><td>禁言/解除禁言某个群成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus" target="_blank">setTeamMemberChatBannedStatus:teamType:accountId:chatBanned:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a0949b0608b26db17657ff055eb9bdd05" target="_blank">updateMuteState:inTeam:completion:</a> </td><td>对整个超大群禁言或解除禁言，对普通成员生效，只有群主有此权限</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamChatBannedMode" target="_blank">setTeamChatBannedMode:teamType:chatBannedMode:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a5ce619b525906cc346561bc66a18dbd9" target="_blank">updateNotifyState:inTeam:completion:</a> </td><td>修改超大群通知状态</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#setTeamMessageMuteMode" target="_blank">setTeamMessageMuteMode:teamType:muteMode:success:failure:</a>
</td></tr>
         <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html#a44b4bb5b83e9387477eebf2018a64783" target="_blank">notifyStateForNewMsg:</a> </td><td>获取超大群通知状态</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TMwMTgwMDA?platform=client#getTeamMessageMuteMode" target="_blank">getTeamMessageMuteMode:teamType:</a>
</td></tr>
      <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html#aeca1589da7e0ed2e484af689b01eba81" target="_blank">updateMuteState:userId:inTeam:completion:</a> </td><td>禁言/解除禁言某个超大群成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/TU0MTQ3MTg?platform=client#setTeamMemberChatBannedStatus" target="_blank">setTeamMemberChatBannedStatus:teamType:accountId:chatBanned:success:failure:</a>
</table>

### 聊天室


<table>
   <thead>
      <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td>无</td><td>创建聊天室实例</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#newInstance" target="_blank">newInstance</a>
        <tr> <td>无</td><td>销毁聊天室实例</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyInstance" target="_blank">destroyInstance</a>
        <tr> <td>无</td><td>获取指定聊天室实例</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstance" target="_blank">getInstance</a>
        <tr> <td>无</td><td>获取指定聊天室实例列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getInstanceList" target="_blank">getInstanceList</a>
        <tr> <td>无</td><td>销毁所有当前存在的聊天室实例</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#destroyAll" target="_blank">destroyAll</a>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a5a01d1ce57be83aca891bbfb9d2d98b8" target="_blank">enterChatroom:completion:</a> </td><td>进入聊天室</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#enter" target="_blank">enter:enterParams:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a93c9557df2bd92a5a9a623d6d3e75433" target="_blank">exitChatroom:completion:</a> </td><td>退出聊天室</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#exit" target="_blank">exit</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#aef75fcabda970069a2eeaf1e72b48492" target="_blank">chatroomAuthMode:</a> </td><td>聊天室登录模式</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a6b5662d25a53f6b77a7a51ccc33db26b" target="_blank">updateLocation:completion:</a> </td><td>更新坐标</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomLocationInfo" target="_blank">updateChatroomLocationInfo:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a6ba47d9955c3facd9953638ca45fe0ac" target="_blank">fetchMessageHistory:option:result:</a> </td><td>查询服务器保存的聊天室消息记录</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageList" target="_blank">getMessageList:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a35290fa5a9b593a070bb8383e6ca2112" target="_blank">getMessagesByTags:completion:</a> </td><td>按标签从云端拉取聊天室消息，每一个标签代表的是某个标签化分组下的聊天室成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMessageListByTag" target="_blank">getMessageListByTag:success:failure:</a>
           </td></tr>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#aec4d2182867279027cef23a6297def04" target="_blank">kickMember:completion:</a> </td><td>将特定成员踢出聊天室</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#kickMember" target="_blank">kickMember:notificationExtension:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a8207b4f144c6f1dbdbbf646b50d66846" target="_blank">fetchChatroomInfo:completion:</a> </td><td>获取聊天室信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DYyMTk0NjE?platform=client#getChatroomInfo" target="_blank">getChatroomInfo</a>
           </td></tr>   
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a3c42bf5805ecf53b06ec0904c662ecab" target="_blank">fetchChatroomMembers:completion:</a> </td><td>获取聊天室成员信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByOption" target="_blank">getMemberListByOption:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#accd847c0b8e0db9cfab1d5a12ac2452d" target="_blank">fetchChatroomMembersByIds:completion:</a> </td><td>根据用户的 IM 账号（accid）获取聊天室成员信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberByIds" target="_blank">getMemberByIds:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a32c8f59b8542c8d99457d341eef2c9c1" target="_blank">fetchChatroomMembersByTag:completion:</a> </td><td>根据标签获取聊天室内该标签下的成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberListByTag" target="_blank">getMemberListByTag:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a24eb898074ac29485dde28375719039d" target="_blank">queryChatroomMembersCountByTag:completion:</a> </td><td>根据标签查询聊天室内该标签下的在线成员数量</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#getMemberCountByTag" target="_blank">getMemberCountByTag:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a1eb5fe9bbe2631bf74dc7d5f43f18d87" target="_blank">updateTags:completion:</a> </td><td>更新标签</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomTags" target="_blank">updateChatroomTags:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#ac57d509d9ef134a4dc5e6c638fb7b5c9" target="_blank">updateMemberBlack:completion:</a> </td><td>将用户添加或移出聊天室黑名单</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberBlockedStatus" target="_blank">setMemberBlockedStatus:blocked:notificationExtension:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a88156bb003e99839a3f2805454514fb9" target="_blank">updateMemberMute:completion:</a> </td><td>将用户添加到禁言名单或取消禁言</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberChatBannedStatus" target="_blank">setMemberChatBannedStatus:chatBanned:notificationExtension:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#af9a982203d5cf9435e0f88eacb680ec6" target="_blank">updateMemberTempMute:duration:completion:</a> </td><td>设置聊天室成员临时禁言</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setMemberTempChatBanned" target="_blank">setMemberTempChatBanned:tempChatBannedDuration:notificationEnabled:notificationExtension:succes</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a8bc3ca5b786e7f15fde8c556bfcee89b" target="_blank">markNormalMember:completion:</a> </td><td>将用户设为聊天室普通成员</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateMemberRole" target="_blank">updateMemberRole:updateParams:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a1f2eb343b35f6d7aba5f7b182c544d6a" target="_blank"> markMemberManager:completion:</a> </td><td>将用户设为聊天室管理员</td><td>同上
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a9ce3ca561f09e60e15aab2c09d0d2d45" target="_blank">tempMuteTag:completion:</a> </td><td>针对标签更新聊天室临时禁言状态</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#setTempChatBannedByTag" target="_blank">setTempChatBannedByTag:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a3ee333de0dfad4d76d64340df891fed6" target="_blank">updateMyChatroomMemberInfo:completion:</a> </td><td>更新本人在聊天室内的信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateSelfMemberInfo" target="_blank">updateSelfMemberInfo:antispamConfig:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a5afbfb1c024c6f2d49a12669a3371c2d" target="_blank">updateChatroomInfo:completion:</a> </td><td>更新聊天室信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/DQyODIyODI?platform=client#updateChatroomInfo" target="_blank">updateChatroomInfo:antispamConfig:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#abe03c4df458d56c36ff4aec719389e05" target="_blank">updateChatroomQueueObject:completion:</a> </td><td>加入或者更新聊天室队列的元素。聊天室队列指聊天室（房间）中由多个元素（key-value 键值对）构成的队列，应用于直播间中的连麦队列场景和礼物队列展示等涉及队列化展示的场景，其中的元素可以是麦位、礼物展示位等</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#af0b6c1493040ae534f707f49889125b4" target="_blank">batchUpdateChatroomQueueObject:completion:</a> </td><td>批量更新聊天室队列的元素</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a726d1392ca658d43f0d8f0ed99979b9c" target="_blank">dropChatroomQueue:completion:</a> </td><td>删除聊天室队列</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a6aae39cdb7067550a7e7591a1d6fed74" target="_blank">fetchChatroomQueue:completion:</a> </td><td>获取聊天室队列</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html#a9edc7efbf4dce522d8c6def532d67152" target="_blank">removeChatroomQueueObject:completion:</a> </td><td>移除聊天室队列元素</td><td>同 V9
           </td></tr>
</table>


### 圈组

圈组的 SDK API 数量较多，请前往下文的[圈组核心类/接口类](#圈组相关)查阅圈组的 SDK API。


### 用户信息 & 用户关系


<table>
   <thead>
      <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a52729571d32313818c80f48bda44f999" target="_blank">fetchUserInfos:completion:</a> </td><td>从服务器批量获取用户资料</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getUserList" target="_blank">getUserList:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a324dd14e163cfe3958668786e3e09d37" target="_blank">userInfo:</a> </td><td>获取本地数据库中所有用户资料</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#ac22f07a7febb681079abb188319ee072" target="_blank">updateMyUserInfo:completion:</a> </td><td>更新本人的用户资料</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#updateSelfUserProfile" target="_blank">updateSelfUserProfile:success:failure:</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a47a54d0909faedd8b09378d097be55b2" target="_blank">searchUserWithOption:completion:</a> </td><td>搜索用户</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a52729571d32313818c80f48bda44f999" target="_blank">fetchUserInfos:completion:</a> </td><td>从服务器批量获取用户资料</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendByIds" target="_blank">getFriendByIds:success:failure:</a>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#ac859ea681b437e6231c8bf779690cc81" target="_blank">requestFriend:completion:</a> </td><td>添加好友</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#addFriend" target="_blank">addFriend:params:success:failure:</a>
       </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#aae81b8f53c032f389f6b9a2f63a732cb" target="_blank">deleteFriend:removeAlias:completion:</a> </td><td>删除好友</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#deleteFriend" target="_blank">deleteFriend:params:success:failure:</a>
       </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#aa307e9ead35fd4f6ddd59bc7afb75b96" target="_blank">myFriends</a> </td><td>获取我的所有好友账号</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getFriendList" target="_blank">getFriendList:failure:</a>
       </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a47d0881cf0384d99f85866b71107856a" target="_blank">addToBlackList:completion:</a> </td><td>将用户添加至黑名单</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#addUserToBlockList" target="_blank">addUserToBlockList:success:failure:</a>
       </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#ac7f9ccbb0584ac55c42dcccf9295c1ff" target="_blank">removeFromBlackBlackList:completion:</a> </td><td>将用户从黑名单中移除</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#removeUserFromBlockList" target="_blank">removeUserFromBlockList:success:failure:</a>
       </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#ac48b035571d013b60443e2448706cae9" target="_blank">updateNotifyState:forUser:completion:</a> </td><td>设置消息提醒</td><td>同 V9
       </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#a58443aa7955d17c01b1e8f64233f01d6" target="_blank">myBlackList</a> </td><td>获取我的黑名单中用户列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jc0MTUyODY?platform=client#getBlockList" target="_blank">getBlockList:failure:</a>
       </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html#abf80ed3023b245e72197e738cf982d76" target="_blank">updateUser:completion:</a> </td><td>修改自己与目标用户的关系</td><td>同 V9
       </td></tr>
      <tr> <td>无</td><td>接受好友申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#acceptAddApplication" target="_blank">acceptAddApplication:success:failure:</a>
       </td></tr>
      <tr> <td>无</td><td>拒绝好友申请</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#rejectAddApplication" target="_blank">rejectAddApplication:postscript:success:failure:</a>
       </td></tr>
      <tr> <td>无</td><td>设置好友信息</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#setFriendInfo" target="_blank">setFriendInfo:params:success:failure:</a>
       </td></tr>
      <tr> <td>无</td><td>获取申请添加好友信息列表</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/jM1MTQ0NDQ?platform=client#getAddApplicationList" target="_blank">getAddApplicationList:success:failure:</a>
       </td></tr>
</table>


### 系统通知

<table>
   <thead>
      <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#abdd436a7e194ecbbc53d9dcc7968f033" target="_blank">sendCustomNotification:toSession:completion:</a> </td><td>发送自定义系统通知</td><td><a href="https://doc.yunxin.163.com/messaging2/client-apis/zk5MTUxMzA?platform=client#sendCustomNotification" target="_blank">sendCustomNotification</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a79feaa5873f67525009350db39c3e774" target="_blank">fetchSystemNotifications:limit:filter:</a> </td><td>获取本地存储的系统通知</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#afa0e434a3b5dd129f061558cc5cb0095" target="_blank">allUnreadCount:</a> </td><td>获取系统通知未读数</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a96f8fd3ce53326d2d164f76f067a015b" target="_blank">deleteNotification:</a> </td><td>删除单条系统通知</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a0cdb04b66a8718a72df48521321b9fba" target="_blank">deleteAllNotifications</a> </td><td>删除所有系统通知</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a065b77d91f0763fcc9e014732b1c3434" target="_blank">deleteAllNotifications:</a> </td><td>根据通知类型删除系统通知</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a2e49d42bc851cc509caa6862d4315792" target="_blank">markNotificationsAsRead:</a> </td><td>标记单条系统通知已读</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a8a57ad947f6fd5da3d275d0a53d2a601" target="_blank">markAllNotificationsAsRead </a> </td><td>标记所有系统通知已读</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html#a5d16c823f06a36086d1495701c9f79ac" target="_blank">markAllNotificationsAsRead: </a> </td><td>根据通知类型标记系统通知已读</td><td>同 V9
           </td></tr>
</table>


### 事件订阅

<table>
   <thead>
      <tr> <th>V9 API</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html#ade858cd5fa0693c465c2a87b7df674be" target="_blank">publishEvent:completion:</a> </td><td>发布事件</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html#a4998eed004df834e2b75261e8dd38f59" target="_blank">subscribeEvent:completion:</a> </td><td>订阅事件</td><td>同 V9
            </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html#aa517688e8aff473ce63c1459ce56e3a9" target="_blank">querySubscribeEvent:completion:</a> </td><td>查询订阅事件</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html#af0ea5da924413a65ba44250d38ba646d" target="_blank">unSubscribeEvent:completion:</a> </td><td>取消订阅事件</td><td>同 V9
            </td></tr>
</table>


## SDK 核心类/接口类


::: note note 
以下仅列出 SDK 的核心类和接口类，如需查阅其他类或接口类的信息，请进入[iOS SDK API 参考](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/annotated.html)搜索与查阅。
:::


### 初始化 & 登录相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html" target="_blank">NIMSDK</a> </td><td>SDK 核心类，提供初始化 SDK，获取各个服务能力接口，获取当前版本等接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/de/de3/interface_n_i_m_s_d_k.html" target="_blank">NIMSDK</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html" target="_blank">NIMSDKConfig</a> </td><td>SDK 配置项修改的接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html" target="_blank">NIMSDKConfig</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d1d/interface_n_i_m_server_setting.html" target="_blank">NIMServerSetting</a>  </td><td>服务器配置接口，私有化需要自定义设置，必须在注册 AppKey 完成之前设置</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/df/d1d/interface_n_i_m_server_setting.html" target="_blank">NIMServerSetting</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html" target="_blank">NIMLoginManager</a> </td><td>登录接口类，提供鉴权、登录、登出、踢人等接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d71/protocol_v2_n_i_m_login_service-p.html" target="_blank">V2NIMLoginService</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html" target="_blank">NIMLoginManagerDelegate</a> </td><td>登录的委托接口，提供登录、登出、踢人等事件注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/db/d4e/protocol_v2_n_i_m_login_listener-p.html" target="_blank">V2NIMLoginListener</a>
           </td></tr>

</table>



### 消息（单聊 & 群聊 & 聊天室）与会话相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/de5/protocol_n_i_m_chat_extend_manager-p.html" target="_blank">NIMChatExtendManager</a> </td><td>IM 消息扩展接口类，提供收藏消息、快捷评论等接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/dd7/protocol_v2_n_i_m_message_service-p.html" target="_blank">V2NIMMessageService</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d4/dd3/protocol_n_i_m_chat_extend_manager_delegate-p.html" target="_blank">NIMChatExtendManagerDelegate</a> </td><td>IM 消息扩展委托接口，提供收藏消息、快捷评论等事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d08/protocol_v2_n_i_m_message_listener-p.html" target="_blank">V2NIMMessageListener</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d6e/protocol_n_i_m_chat_manager-p.html" target="_blank">NIMChatManager</a> </td><td>IM 消息管理接口类，提供消息发送、消息查询、消息撤回等相关接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/dd7/protocol_v2_n_i_m_message_service-p.html" target="_blank">V2NIMMessageService</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/da7/protocol_n_i_m_chat_manager_delegate-p.html" target="_blank">NIMChatManagerDelegate</a> </td><td>IM 消息管理委托接口，提供消息发送、消息查询、消息撤回等相关事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d08/protocol_v2_n_i_m_message_listener-p.html" target="_blank">V2NIMMessageListener</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d94/protocol_n_i_m_conversation_manager-p.html" target="_blank">NIMConversationManager</a>  </td><td>会话管理接口类，提供获取/删除会话消息、设置会话消息已读等相关接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d16/protocol_v2_n_i_m_conversation_service-p.html" target="_blank">V2NIMConversationService</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/dfa/protocol_n_i_m_conversation_manager_delegate-p.html" target="_blank">NIMConversationManagerDelegate</a> </td><td>会话管理委托接口，提供会话相关事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/de/d4f/protocol_v2_n_i_m_conversation_listener-p.html" target="_blank">V2NIMConversationListener</a>
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dc/d9e/protocol_n_i_m_doc_transcoding_manager-p.html" target="_blank">NIMDocTranscodingManager</a> </td><td>文档转码管理接口类，提供查询文档转码信息、删除转码文档等接口</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/ddc/protocol_n_i_m_media_manager-p.html" target="_blank">NIMMediaManager</a> </td><td>录制和播放音频管理接口类，提供语音录制和播放相关接口</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d29/protocol_n_i_m_media_manager_delegate-p.html" target="_blank">NIMMediaManagerDelegate</a> </td><td>音频管理委托接口，提供录制、播放音频等事件的注册接口</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/dde/protocol_n_i_m_resource_manager-p.html" target="_blank">NIMResourceManager</a> </td><td>资源管理接口类，提供下载、搜索、查询资源等接口</td><td>同 V9
           </td></tr>
        <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d7/d40/protocol_n_i_m_index_manager-p.html" target="_blank">NIMIndexManager</a> </td><td>消息检索接口类，提供消息检索相关接口</td><td>同 V9
           </td></tr>
</table>







### APNs 离线推送相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6f/protocol_n_i_m_apns_manager-p.html" target="_blank">NIMApnsManager</a> </td><td>IM 的 APNs 离线推送服务接口类，提供 IM 的 APNs 离线推送服务相关配置接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/db/d68/protocol_v2_n_i_m_setting_service-p.html" target="_blank">V2NIMSettingService</a>
        </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/dbd/protocol_n_i_m_apns_manager_delegate-p.html" target="_blank">NIMApnsManagerDelegate</a> </td><td>IM 的 APNs 离线推送服务委托接口，提供 IM 的 APNs 离线推送服务相关配置事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d4/d03/protocol_v2_n_i_m_setting_listener-p.html" target="_blank">V2NIMSettingListener</a>
        </td></tr>
</table>

### 群组相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d54/protocol_n_i_m_team_manager-p.html" target="_blank">NIMTeamManager</a> </td><td> 群组接口类，提供创建群组、添加群成员等群组操作相关接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d2/d0c/protocol_v2_n_i_m_team_service-p.html" target="_blank">V2NIMTeamService</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/df3/protocol_n_i_m_team_manager_delegate-p.html" target="_blank">NIMTeamManagerDelegate</a> </td><td> 群组委托接口，提供群组成员变动、资料变动等事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/db/db7/protocol_v2_n_i_m_team_listener-p.html" target="_blank">V2NIMTeamListener</a>
           </td></tr>
</table>



### 超大群相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d49/protocol_n_i_m_super_team_manager-p.html" target="_blank">NIMSuperTeamManager</a> </td><td> 超大群服务接口类，提供超大群成员管理、超大群消息发送、超大群资料管理等相关接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d2/d0c/protocol_v2_n_i_m_team_service-p.html" target="_blank">V2NIMTeamService</a>
           </td></tr>
</table>



### 聊天室相关


<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/de7/protocol_n_i_m_chatroom_manager-p.html" target="_blank">NIMChatroomManager</a> </td><td> 聊天室服务接口类，提供进出聊天室、发送聊天室消息、聊天室成员管理、聊天室队列服务、聊天室标签等接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/df/dce/protocol_v2_n_i_m_chatroom_client_listener-p.html" target="_blank">V2NIMChatroomClientListener</a>&<a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d9/d01/protocol_v2_n_i_m_chatroom_listener-p.html" target="_blank">V2NIMChatroomListener</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d8/d34/protocol_n_i_m_chatroom_manager_delegate-p.html" target="_blank">NIMChatroomManagerDelegate</a> </td><td>聊天室委托接口， 提供聊天室相关事件的注册接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d3/daa/interface_v2_n_i_m_chatroom_client.html" target="_blank">V2NIMChatroomClient</a>&<a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/de/dd4/protocol_v2_n_i_m_chatroom_service-p.html" target="_blank">V2NIMChatroomService</a>
           </td></tr>
</table>





### 圈组相关

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d81/protocol_n_i_m_q_chat_manager-p.html" target="_blank">NIMQChatManager</a> </td><td>圈组接口类，提供圈组登录登出相关接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/da1/protocol_n_i_m_q_chat_manager_delegate-p.html" target="_blank">NIMQChatManagerDelegate</a> </td><td>圈组委托接口，提供圈组登录登出相关事件的注册接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/dac/protocol_n_i_m_q_chat_server_manager-p.html" target="_blank">NIMQChatServerManager</a> </td><td>圈组服务器接口类，提供圈组服务器相关接口，如创建服务器、邀请服务器成员、查询服务器成员等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/df/d6b/protocol_n_i_m_q_chat_channel_manager-p.html" target="_blank">NIMQChatChannelManager</a> </td><td>圈组频道接口类，提供圈组频道相关接口，如创建频道、查询频道、查询频道未读信息等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d39/protocol_n_i_m_q_chat_role_manager-p.html" target="_blank">NIMQChatRoleManager</a> </td><td>圈组身份组接口类，提供圈组身份组相关接口，如将某人加入身份组、查询自己的权限等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/db1/protocol_n_i_m_q_chat_message_manager-p.html" target="_blank">NIMQChatMessageManager</a> </td><td>圈组消息接口类，提供发送消息、撤回消息、发送消息正在输入事件等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d4/d3f/protocol_n_i_m_q_chat_message_manager_delegate-p.html" target="_blank">NIMQChatMessageManagerDelegate</a> </td><td>圈组消息委托接口，提供圈组消息相关事件的注册接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/dd/d4f/protocol_n_i_m_q_chat_apns_manager-p.html" target="_blank">NIMQChatApnsManager</a> </td><td>圈组的 APNs 离线推送服务接口类，提供圈组的 APNs 离线推送服务相关配置接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d0/de1/protocol_n_i_m_q_chat_r_t_c_channel_manager-p.html" target="_blank">NIMQChatRTCChannelManager </a> </td><td>圈组实时互动频道接口类，提供更新、查询实时互动频道信息等接口</td><td>同 V9
           </td></tr>
              <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/d9c/protocol_n_i_m_q_chat_message_extend_manager-p.html" target="_blank">NIMQChatMessageExtendManager</a> </td><td>圈组消息扩展接口类，提供发送、删除快捷评论等接口</td><td>同 V9
           </td></tr>
</table>

### 圈组实时互动频道模块（QChatMedia）

<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
<tr> <td> <a href="https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Classes/NIMQChatMediaKit.html" target="_blank">NIMQChatMediaKit</a> </td><td>圈组实时互动频道接口类，提供圈组实时互动频道的初始化接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelManager.html" target="_blank">NIMQChatMediaChannelManager </a> </td><td>圈组实时互动频道管理接口类，提供实时互动频道成员管理、摄像头切换、扬声器管理、视频画布设置等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/messaging/references/iOS/doxygen/V9.3.0/zh/Protocols/NIMQChatMediaChannelDelegate.html" target="_blank">NIMQChatMediaChannelDelegate</a> </td><td>圈组实时互动频道委托接口，提供实时互动频道相关事件的注册接口</td><td>同 V9
           </td></tr>
</table>

### 用户资料 & 用户关系相关
<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/da/d54/protocol_n_i_m_user_manager-p.html" target="_blank">NIMUserManager</a> </td><td> 用户信息与用户关系操作相关接口类，提供用户信息管理和好友关系管理相关接口</td><td> <a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d9/d06/protocol_v2_n_i_m_user_service-p.html" target="_blank">V2NIMUserService</a>&<a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d6/d31/protocol_v2_n_i_m_friend_service-p.html" target="_blank">V2NIMFriendService</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d1/deb/protocol_n_i_m_user_manager_delegate-p.html" target="_blank">NIMUserManagerDelegate</a> </td><td> 用户信息与好友关系委托接口，提供好友状态变化，黑名单列表变化等事件的注册接口</td><td> <a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/da/db7/protocol_v2_n_i_m_user_listener-p.html" target="_blank">V2NIMUserListener</a>&<a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/dd/d02/protocol_v2_n_i_m_friend_listener-p.html" target="_blank">V2NIMFriendListener</a>
           </td></tr>
</table>



### 系统通知相关


<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/de/d93/protocol_n_i_m_system_notification_manager-p.html" target="_blank">NIMSystemNotificationManager</a> </td><td> 系统通知接口类，提供发送、标记、删除系统通知等接口</td><td><a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/d6/def/protocol_v2_n_i_m_notification_service-p.html" target="_blank">V2NIMNotificationService</a>
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d2/d52/protocol_n_i_m_system_notification_manager_delegate-p.html" target="_blank">NIMSystemNotificationManagerDelegate</a> </td><td>系统通知委托接口， 提供系统通知相关事件的注册接口</td><td> <a href="https://doc.yunxin.163.com/messaging2/references/iOS/doxygen/Latest/zh/dd/d46/protocol_v2_n_i_m_notification_listener-p.html" target="_blank">V2NIMNotificationListener</a>
           </td></tr>
</table>


### 事件订阅相关


<table>
<thead>
    <tr> <th style="width:180px">类/接口</th><th>说明</th><th>对应 V10 API</th></tr></thead>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d3/d20/protocol_n_i_m_event_subscribe_manager-p.html" target="_blank">NIMEventSubscribeManager</a> </td><td> 事件订阅接口类，提供发布、查询、订阅事件等接口</td><td>同 V9
           </td></tr>
       <tr> <td> <a href="https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d7/d81/protocol_n_i_m_event_subscribe_manager_delegate-p.html" target="_blank">NIMEventSubscribeManagerDelegate</a> </td><td>事件订阅委托接口， 提供事件订阅相关事件的注册接口</td><td>同 V9
           </td></tr>
</table>












































