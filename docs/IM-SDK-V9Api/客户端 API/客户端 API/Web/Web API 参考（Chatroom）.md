<p>网易云信聊天室基于网易云信实时通信网络，提供完整的聊天室服务。</p>
<ul>
<li><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html">NIMChatroomInterface</a> 是 Chatroom <code>SDK</code> 的入口，负责建立长连接，登录，断开长连接，销毁实例等功能。</li>
<li><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html">NIMChatroomMemberInterface</a> 挂载了聊天室成员相关的 API，如设置管理员，设置禁言，更新自己在聊天室中的信息等。</li>
<li><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html">NIMChatroomMessageInterface</a> 挂载了聊天室消息相关的 API，如发送消息，查询历史消息。</li>
<li><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html">NIMChatroomQueueInterface</a> 挂载了聊天室队列相关的 API，如更新队列、获取聊天室队列列表。</li>
<li><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html">CloudStorageInterface</a> 挂载了云存储相关的 API，如上传并且预览文件、短链接转长链接。</li>
</ul>

## <span id="Chatroom.getInstance">Chatroom.getInstance</span>
<p>下面是 <a href="classes/chatroom.Chatroom.html#getInstance">Chatroom.getInstance</a> 的初始化参数。这里只例举部分回调函数，完整初始化参数见 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html">chatroom/types.NIMChatroomGetInstanceOptions</a>。</p>
<table>
<thead>
<tr>
<th>参数</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#appKey">appKey</a></td>
<td>[必填]应用的 appKey。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#account">account</a></td>
<td>[必填]账号 ID。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#token">token</a></td>
<td>[必填]账号的登录凭证。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#chatroomId">chatroomId</a></td>
<td>[必填]聊天室房间号。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#chatroomAddresses">chatroomAddresses</a></td>
<td>[必填]聊天室长连接地址。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#isAnonymous">isAnonymous</a></td>
<td>是否匿名登录。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#tags">tags</a></td>
<td>当前连接标签组。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#onconnect">onconnect</a></td>
<td>钩子函数-连接建立后的回调。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#onwillreconnect">onwillreconnect</a></td>
<td>钩子函数-即将重连的回调。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#ondisconnect">ondisconnect</a></td>
<td>钩子函数-断开链接的回调。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#onmsgs">onmsgs</a></td>
<td>钩子函数-(多端同步/在线)收到消息的回调。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_types.NIMChatroomGetInstanceOptions.html#onTagsUpdate">onTagsUpdate</a></td>
<td>钩子函数-当前用户标签被更新的回调。</td>
</tr>
</tbody></table>

## <span id="NIMChatroomInterface">NIMChatroomInterface</span>
<!--
## <span id="NIMChatroomInterface">NIMChatroomInterface</span>
 --><p>Chatroom <code>SDK</code> 的入口，负责建立长连接，登录，断开长连接，销毁实例等功能，完整的 API 请参考 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html">NIMChatroomInterface</a></p>
<table>
<thead>
<tr>
<th>方法</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#logout">logout</a></td>
<td>退出登录。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#disconnect">disconnect</a></td>
<td>断开连接。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#connect">connect</a></td>
<td>连接。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#destroy">destroy</a></td>
<td>销毁实例。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#updateTags">updateTags</a></td>
<td>更新当前长连接的标签。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#getChatroom">getChatroom</a></td>
<td>获取当前聊天室的属性。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#closeChatroom">closeChatroom</a></td>
<td>关闭聊天室。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomInterface.NIMChatroomInterface.html#updateChatroom">updateChatroom</a></td>
<td>更新聊天室属性。</td>
</tr>
</tbody></table>

## <span id="NIMChatroomMemberInterface">NIMChatroomMemberInterface</span>
<p>聊天室成员相关的 API，如设置管理员，设置禁言，更新自己在聊天室中的信息等，完整的 API 请参考 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html">NIMChatroomMemberInterface</a></p>
<table>
<thead>
<tr>
<th>方法</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#updateMyChatroomMemberInfo">updateMyChatroomMemberInfo</a></td>
<td>更新自己在聊天室内的信息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#getChatroomMembers">getChatroomMembers</a></td>
<td>获取聊天室成员列表。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#getChatroomMembersByTag">getChatroomMembersByTag</a></td>
<td>获取带有某标签的在线的聊天室成员数量。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#getChatroomMemberCountByTag">getChatroomMemberCountByTag</a></td>
<td>查询某个标签下的在线人数。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#markChatroomIdentity">markChatroomIdentity</a></td>
<td>设置聊天室成员身份。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#markChatroomManager">markChatroomManager</a></td>
<td>设置聊天室管理员。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#markChatroomCommonMember">markChatroomCommonMember</a></td>
<td>设置聊天室普通成员。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#markChatroomBlacklist">markChatroomBlacklist</a></td>
<td>设置聊天室黑名单。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#markChatroomGaglist">markChatroomGaglist</a></td>
<td>设置聊天室禁言名单。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#kickChatroomMember">kickChatroomMember</a></td>
<td>踢聊天室成员。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#updateChatroomMemberTempMute">updateChatroomMemberTempMute</a></td>
<td>设置聊天室临时禁言。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#updateTagMembersTempMute">updateTagMembersTempMute</a></td>
<td>根据标签设置聊天室临时禁言。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMemberInterface.NIMChatroomMemberInterface.html#updateCoordinate">updateCoordinate</a></td>
<td>更新坐标。</td>
</tr>
</tbody></table>

## <span id="ChatroomMessageInterface">ChatroomMessageInterface</span>
<p>聊天室消息相关的 API，如发送消息，查询历史消息，完整的 API 请参考 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html">NIMChatroomMessageInterface</a></p>
<table>
<thead>
<tr>
<th>方法</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#sendText">sendText</a></td>
<td>发送文本消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#sendFile">sendFile</a></td>
<td>发送文件消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#sendCustomMsg">sendCustomMsg</a></td>
<td>发送自定义消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#sendTipMsg">sendTipMsg</a></td>
<td>发送 tip 消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#sendGeo">sendGeo</a></td>
<td>发送地理位置消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#getHistoryMsgs">getHistoryMsgs</a></td>
<td>获取聊天室历史消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#getHistoryMsgsByTags">getHistoryMsgsByTags</a></td>
<td>根据标签获取聊天室历史消息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomMessageInterface.NIMChatroomMessageInterface.html#resendMsg">resendMsg</a></td>
<td>重发消息。</td>
</tr>
</tbody></table>

## <span id="NIMChatroomQueueInterface">NIMChatroomQueueInterface</span>
<ul>
<li>聊天室队列指聊天室（房间）中由多个元素（key-value 键值对）构成的队列，应用于直播间中的连麦场景和礼物队列展示等场景。</li>
<li>下面是聊天室队列相关的 API，如更新队列、获取聊天室队列列表，完整的 API 请参考 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html">NIMChatroomQueueInterface</a></li>
</ul>

<table>
<thead>
<tr>
<th>方法</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#queueOffer">queueOffer</a></td>
<td>新加(更新)队列元素。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#queuePoll">queuePoll</a></td>
<td>删除队列元素。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#queueList">queueList</a></td>
<td>获取聊天室队列列表。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#peak">peak</a></td>
<td>获取聊天室队列中第一个元素。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#queueDrop">queueDrop</a></td>
<td>清除聊天室队列。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/chatroom_NIMChatroomQueueInterface.NIMChatroomQueueInterface.html#queueChange">queueChange</a></td>
<td>批量更新聊天室队列。</td>
</tr>
</tbody></table>

## <span id="CloudStorageInterface">CloudStorageInterface</span>
<p>云端会话服务相关的 API，如查询云端会话列表，查询某个云端会话，完整的 API 请参考 <a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html">CloudStorageInterface</a></p>
<table>
<thead>
<tr>
<th>方法</th>
<th>功能描述</th>
</tr>
</thead>
<tbody><tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#previewFile">previewFile</a></td>
<td>上传并且预览文件。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#getNosOriginUrl">getNosOriginUrl</a></td>
<td>短链接转长链接。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#audioToText">audioToText</a></td>
<td>音频转文字。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#stripImageMeta">stripImageMeta</a></td>
<td>去除图片元信息。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#qualityImage">qualityImage</a></td>
<td>修改图片质量。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#interlaceImage">interlaceImage</a></td>
<td>interlace 图片。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#rotateImage">rotateImage</a></td>
<td>旋转图片。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#blurImage">blurImage</a></td>
<td>模糊图片。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#cropImage">cropImage</a></td>
<td>剪裁图片。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#thumbnailImage">thumbnailImage</a></td>
<td>生成图片的略缩图。</td>
</tr>
<tr>
<td><a href="https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/Chatroom/interfaces/common_CloudStorageInterface.CloudStorageInterface.html#processImage">processImage</a></td>
<td>处理图片。</td>
</tr>
</tbody></table>