---

  "track_type": "咨询类",
  "sub_type": "功能实现咨询",
  "product": "IM-SDK",
  "feature": "聊天室",
  "updated": "2026-03-20"

---

<!-- entry: platform=Web, created=2025-02-06, customers=["广州益乐互动"], source=chat_history, frequency=1, tags=["聊天室", "黑名单", "查询"] -->
## Q: 聊天室黑名单查询

**问题描述**：客户希望在登录聊天室之前判断自己是否被拉入黑名单。

**答案**：聊天室黑名单用户无法进入聊天室，如需提前查询只能通过服务端API查询，客户端无法直接查询

---
<!-- entry: platform=Web, created=2025-02-08, customers=["VIP云信-上海移云信息科技有限公司"], source=chat_history, frequency=1, tags=["聊天室", "getInstance", "单例", "多房间", "Web"] -->
## Q: Web端聊天室同时进入多个房间方案

**问题描述**：Web端SDK.Chatroom.getInstance调用后自动进入聊天室，但需要同时进入2个房间（一个用于聊天业务，一个用于接收业务消息）

**答案**：方案1：使用iframe嵌入两个web tab页面实现多端登录效果
方案2：直接new一个实例自己维护（推荐），不用getInstance

---
