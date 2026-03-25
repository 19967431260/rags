---
track_type: "咨询类"
sub_type: "配置开通咨询"
product: "IM-SDK"
feature: "云端会话"
updated: "2026-03-20"
---
<!-- entry: platform=服务端, created=2025-09-16, customers=["FVIP-云信-上海抱朴"], source=chat_history, frequency=1, tags=["云端会话", "收费", "旗舰版", "API", "未读数"] -->
## Q: 云端会话功能收费及API使用说明

**问题描述**：客户咨询开启云端会话功能是否需要额外收费，以及服务端API获取云端会话列表的方式。

**答案**：云端会话功能在旗舰版套餐中不额外收费。开启后可通过服务端接口GET https://{endpoint}/im/v2.1/conversations获取云端会话列表，从开启时开始记录。注意：客户端未升级到V10时，服务端获取的会话未读数与客户端可能对不齐，需要客户端升级V10后才能对齐。

---

