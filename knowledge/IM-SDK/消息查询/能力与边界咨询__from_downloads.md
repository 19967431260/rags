---
track_type: "咨询类"
sub_type: "能力与边界咨询"
product: "IM-SDK"
feature: "消息查询"
updated: "2026-03-20"
---
<!-- entry: platform=iOS, created=2025-09-04, customers=["FVIP云信-时间在线-gj"], source=chat_history, frequency=1, tags=["iOS", "serverId", "消息查询", "定位消息"] -->
## Q: iOS没有queryMessageListByServerId接口

**问题描述**：客户咨询iOS是否有类似Android的queryMessageListByServerIdBlock接口用serverId查询消息。

**答案**：iOS没有直接通过serverId查询消息的接口。如需在聊天消息列表中定位到某条消息（包含未加载的历史消息），需要根据未读消息数+历史消息查询，由业务层自行实现。

---

