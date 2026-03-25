---
track_type: "咨询类"
sub_type: "接口用法咨询"
product: "IM-SDK"
feature: "聊天室"
updated: "2026-03-20"
---
<!-- entry: platform=HarmonyOS, created=2025-09-03, customers=["FVIP-云信-上海麦色"], source=chat_history, frequency=1, tags=["鸿蒙", "HarmonyOS", "聊天室", "serverExtension", "扩展字段", "V2NIMChatroomMessage"] -->
## Q: 鸿蒙聊天室消息设置serverExtension扩展字段

**问题描述**：客户咨询鸿蒙版IM聊天室发送消息时如何设置扩展字段（类似Android的message.setRemoteExtension），用于标识管理员或创建者身份。

**答案**：鸿蒙端设置聊天室消息扩展字段的方法：先构造V2NIMChatroomMessage消息，构造完成后调用setServerExtension配置扩展字段。注意serverExtension与remoteExtension的区别，确保两端配置一致。

---

