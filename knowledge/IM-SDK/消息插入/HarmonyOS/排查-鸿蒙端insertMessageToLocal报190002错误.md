---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息插入
platform: HarmonyOS
updated: 2025-08-12
---

<!-- entry: platform=HarmonyOS, created=2025-08-12, customers=["飞虎互动"], source=chat_history, frequency=1, tags=["190002", "illegal state", "insertMessageToLocal"], troubleshooting="", root_cause="未登录" -->
## Q: 鸿蒙端insertMessageToLocal报190002错误

**问题描述**：通过insertMessageToLocal插入消息时报错 code:190002 desc:illegal state

**根因**：未登录

**解决方案**：检查是否已登录，insertMessageToLocal需要在登录成功后才能调用