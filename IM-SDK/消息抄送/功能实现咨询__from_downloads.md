---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "消息抄送"
updated: "2026-03-20"
---
<!-- entry: platform=Web, created=2025-09-09, customers=["政采云"], source=chat_history, frequency=1, tags=["消息抄送", "多tab", "登录登出", "Web", "多端登录"] -->
## Q: Web多tab登录登出抄送优化咨询

**问题描述**：Web端多tab场景下，相同账号多tab会创建多个链接，导致登录登出抄送量过多，希望优化

**答案**：每个tab都是一个独立实例和长连接，算多端登录，每个实例登录都会产生抄送，这是正常机制

---

<!-- entry: platform=Server, created=2025-09-24, customers=["LEYANG YU HANGLUK SAMPHEARAK"], source=chat_history, frequency=1, tags=["IM", "抄送", "服务端", "消息发送"] -->
## Q: 服务端发消息的抄送机制

**问题描述**：咨询服务端发的消息是否可以收到抄送，以及抄送消息与发送消息的数据一致性。

**答案**：服务端发送消息成功后会有抄送。抄送消息与发送消息基本一致，但发送时用于控制漫游、推送等参数不一定在抄送中体现。需要在控制台配置抄送地址并勾选事件类型，个人聊天和群聊数据都能收到。抄送不影响IM消息发送。

---


<!-- entry: platform=Server, created=2025-09-24, customers=['LEYANG YU HANGLUK SAMPHEARAK'], source=chat_history, frequency=1, tags=['IM', '抄送', '服务端', '消息发送'] -->
## Q: 服务端发消息的抄送机制

**问题描述**：咨询服务端发的消息是否可以收到抄送，以及抄送消息与发送消息的数据一致性。

**答案**：服务端发送消息成功后会有抄送。抄送消息与发送消息基本一致，但发送时用于控制漫游、推送等参数不一定在抄送中体现。需要在控制台配置抄送地址并勾选事件类型，个人聊天和群聊数据都能收到。抄送不影响IM消息发送。

---
