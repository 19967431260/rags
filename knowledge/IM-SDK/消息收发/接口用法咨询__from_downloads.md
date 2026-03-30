---
track_type: "咨询类"
sub_type: "接口用法咨询"
product: "IM-SDK"
feature: "消息收发"
updated: "2026-03-20"
---
<!-- entry: platform=Android, created=2025-09-04, customers=["广州欢牛"], source=chat_history, frequency=1, tags=["安全通", "敏感词", "拦截", "v2NIMSendMessageResult"] -->
## Q: 安全通命中结果返回位置

**问题描述**：咨询安全通命中敏感词后的返回结果在哪里获取，以及本地拦截库和服务器拦截的区别。

**答案**：1.服务器拦截词库命中结果在v2NIMSendMessageResult中返回，不会回调onSendMessage回调；2.本地拦截直接不发送到服务器，本地直接展示；3.控制台配置新的本地拦截库后，客户端需要重新登录才会下发新词库。

---


<!-- entry: platform=Android, created=2025-09-04, customers=['广州欢牛'], source=chat_history, frequency=1, tags=['安全通', '敏感词', '拦截', 'v2NIMSendMessageResult'] -->
## Q: 安全通命中结果返回位置

**问题描述**：咨询安全通命中敏感词后的返回结果在哪里获取，以及本地拦截库和服务器拦截的区别。

**答案**：1.服务器拦截词库命中结果在v2NIMSendMessageResult中返回，不会回调onSendMessage回调；2.本地拦截直接不发送到服务器，本地直接展示；3.控制台配置新的本地拦截库后，客户端需要重新登录才会下发新词库。

---
