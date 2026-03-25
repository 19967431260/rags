---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "会话管理"
updated: "2026-03-20"
---
<!-- entry: platform=通用, created=2025-09-02, customers=["FVIP-云信-上海抱朴"], source=chat_history, frequency=1, tags=["V10", "本地会话", "云端会话", "V2NIMLocalConversationService", "V2NIMConversationService", "升级"] -->
## Q: IM V10本地会话与云端会话区别

**问题描述**：客户咨询IM V10版本中本地会话(V2NIMLocalConversationService)与云端会话(V2NIMConversationService)的区别，以及V9升级到V10时的数据兼容性问题。

**答案**：V10的本地会话和云端会话是完全独立的两个概念：本地会话是客户端收到消息后本地存储，云端会话是服务器侧存储。初始化时需要配置好使用哪个会话服务，不能两个切换使用。V9升级到V10覆盖安装后，不会同步之前的会话数据，但已收到的消息不会丢失。

---

