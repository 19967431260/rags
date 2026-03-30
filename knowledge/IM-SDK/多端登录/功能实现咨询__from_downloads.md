---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "多端登录"
updated: "2026-03-20"
---
<!-- entry: platform=通用, created=2025-09-24, customers=["智己"], source=chat_history, frequency=1, tags=["多端登录", "设备限制", "踢人机制", "聊天室"] -->
## Q: 多端登录设备数量限制及踢人机制

**问题描述**：咨询多端登录时各设备是否都能收到消息，以及超过10个设备的处理机制

**答案**：多端登录时各设备都可以收到消息；登录第11个设备时会踢掉第1个登录的设备，以此类推。聊天室多端登录被挤下线需要监听chatroomBeKicked

---

