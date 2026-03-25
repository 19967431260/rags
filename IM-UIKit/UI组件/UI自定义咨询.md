---
track_type: 咨询类
sub_type: UI配置咨询
product: IM-UIKit
feature: UI自定义
updated: 2025-03-23
---

<!-- entry: platform=Web, created=2025-05-06, customers=["重庆橙心物流网络"], source=chat_history, frequency=1, tags=["陌生人提示", "strangerTipVisible", "UI自定义"] -->
## Q: 隐藏陌生人提示信息

**问题描述**：需要隐藏聊天界面中的陌生人提示信息。

**答案**：使用strangerTipVisible参数控制是否展示陌生人的提示信息。设置为false即可隐藏。参考文档：https://doc.yunxin.163.com/messaging-uikit/guide/Tk0NTAxNzA?platform=web

---

<!-- entry: platform=Web, created=2025-05-06, customers=["重庆橙心物流网络"], source=chat_history, frequency=1, tags=["消息滚动", "新消息", "自动滚动"] -->
## Q: 新消息自动滚动行为

**问题描述**：新消息到来时的自动滚动行为控制。

**答案**：当最后一条消息展示在可视区域时，再来新消息会自动滚动。如果用户滚动到了前面的消息（查看历史消息），新消息不会自动滚动，会提示有新消息。需要在源码中自行修改实现超过五行不滚动的逻辑。

---

<!-- entry: platform=通用, created=2025-05-06, customers=["重庆橙心物流网络"], source=chat_history, frequency=1, tags=["时间格式", "24小时制", "12小时制", "UI层"] -->
## Q: 聊天页面时间格式设置

**问题描述**：IM聊天页面的时间显示格式（24小时制或12小时制）配置。

**答案**：消息时间显示是UI层处理的，与后台和SDK无关。需要在UI层开源代码中自行修改实现。

---

<!-- entry: platform=Web, created=2025-05-06, customers=["重庆橙心物流网络"], source=chat_history, frequency=1, tags=["个人资料", "弹层自定义", "头像点击", "用户资料"] -->
## Q: 个人资料弹层自定义

**问题描述**：需要自定义点击头像弹出的个人资料弹层内容。

**答案**：当前版本暂不支持完全自定义弹层内容。下个版本支持头像点击事件拦截，可以拦截后自行弹窗。目前账号字段不支持修改，其他内容可以通过修改用户资料实现，服务器可以同步业务用户资料到IM账号。参考文档：https://doc.yunxin.163.com/messaging2/server-apis/TA0NzYzNjk?platform=server

---
