---
track_type: "咨询类"
sub_type: "功能实现咨询"
product: "IM-SDK"
feature: "消息提醒"
updated: "2026-03-20"
---
<!-- entry: platform=Android, created=2025-09-01, customers=["北京耘想科技"], source=chat_history, frequency=1, tags=["@消息", "消息提醒", "Android", "StatusBarNotificationFilter"] -->
## Q: 群聊@消息自定义提醒方式

**问题描述**：客户在群聊天界面，收到普通消息时没有声音和震动提醒，但收到@自己的消息时有声音和震动。希望改为收到@消息时只有震动没有声音。

**答案**：在StatusBarNotificationFilter中返回DENY拦截SDK提醒，自己通过系统接口控制震动和声音；升级到V9.20.15可解决回调两次的问题

---


<!-- entry: platform=Android, created=2025-09-01, customers=['北京耘想科技'], source=chat_history, frequency=1, tags=['@消息', '消息提醒', 'Android', 'StatusBarNotificationFilter'] -->
## Q: 群聊@消息自定义提醒方式

**问题描述**：客户在群聊天界面，收到普通消息时没有声音和震动提醒，但收到@自己的消息时有声音和震动。希望改为收到@消息时只有震动没有声音。

**答案**：在StatusBarNotificationFilter中返回DENY拦截SDK提醒，自己通过系统接口控制震动和声音；升级到V9.20.15可解决回调两次的问题

---
