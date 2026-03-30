---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 登录监听
updated: 2025-07-25
---

<!-- entry: platform=iOS, created=2025-07-30, customers=["智己群"], source=chat_history, frequency=1, tags=["Swift","V2NIMLoginListener","V2NIMLoginDetailListener","多代理"] -->
## Q: V10 Swift同时实现V2NIMLoginListener和V2NIMLoginDetailListener

**问题描述**：Swift中如何同时实现V2NIMLoginListener和V2NIMLoginDetailListener两个代理？

**答案**：需要分别调用：NIMSDK.shared().v2LoginService.add(self as V2NIMLoginListener) 和 NIMSDK.shared().v2LoginService.add(self as V2NIMLoginDetailListener)，两个代理监听器需要分别注册。

---
