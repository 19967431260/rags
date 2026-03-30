---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "会话列表"
updated: "2026-03-20"
---
<!-- entry: platform=Web, created=2025-09-12, customers=["ISV云信-和仁"], source=chat_history, frequency=1, tags=["会话列表", "分组", "sessionId", "V9", "V10"] -->
## Q: Web端会话列表分类实现方案

**问题描述**：客户询问：web端会话列表的分类如何实现，比如患者和医生的会话列表分组展示。

**答案**：V9没有会话分组功能，需要根据sessionId在业务层做过滤，区分医生会话和患者会话，然后在UI上做分组展示。V10 SDK可以使用分组功能。

---

