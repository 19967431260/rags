---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: SDK集成
updated: 2025-07-25
---

<!-- entry: platform=服务端, created=2025-07-08, customers=["北京大成互联技术有限公司"], source=chat_history, frequency=1, tags=["注册","token","accid","服务端","登录"] -->
## Q: IM账号注册后需保存token，登录时需服务端返回accid和token

**问题描述**：第一次注册成功返回的token后端需要保存吗？登录流程是什么？

**答案**：需要保存token。业务服务端注册IM账号后将accid和token与用户绑定；客户端登录时由业务服务端返回accid和token用于SDK登录。

---
