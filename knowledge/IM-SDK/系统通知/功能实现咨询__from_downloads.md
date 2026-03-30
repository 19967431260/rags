---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "系统通知"
updated: "2026-03-20"
---
<!-- entry: platform=Web, created=2025-09-01, customers=["深圳市家家顺-乐有家"], source=chat_history, frequency=1, tags=["V9", "系统通知", "MessageServerId", "getMessageId", "群通知"] -->
## Q: Web与移动端群通知消息ID关联问题

**问题描述**：Web端和移动端群通知列表消息体需要一个唯一ID进行关联，移动端操作入群（同意或拒绝）后，Web端需要更新状态。

**答案**：目前只能考虑基于targetid、type、fromaccount三者来确认某一类群操作行为。建议一次通过就处理掉所有同类历史的申请。

---

