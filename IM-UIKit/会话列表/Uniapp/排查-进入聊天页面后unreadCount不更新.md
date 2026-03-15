---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Uniapp
title: 进入聊天页面后unreadCount不更新
root_cause: ""
solution: 需要调用resetConversation方法清除未读数,参考文档：https://doc.yunxin.163.com/messaging2/references/web/typedoc//IMUIKit/Latest/classes/LocalConversationStore.html#resetConversation。如果报错"conversation not found",需检查conversationId是否正确传递。
customers: ["冰耀信息科技（苏州）有限公司"]
source: chat_history
tags: ["unreadCount", "resetConversation", "LocalConversationStore", "会话未读数", "UIKit"]
created: 2026-02-26
updated: 2026-03-15
---

## 问题：Uniapp 进入聊天页面后unreadCount不更新

## 问题详情

**现象**：
使用IM V10 UIKit Uniapp版本,进入pages/Chat/index页面后,localConversation的unreadCount一直不变化,未能自动清零。调用resetConversation方法时提示"conversation not found"错误,但selectConversation方法使用同一个conversationId不报错。

**环境信息**：
- SDK 版本：IM V10 UIKit Uniapp

**相关日志**：
调用resetConversation时报错："conversation not found"

## 排查过程

（从会话提取的排查过程不完整）

## 问题原因

（根本原因未明确）

## 解决方案

需要调用resetConversation方法清除未读数,参考文档：https://doc.yunxin.163.com/messaging2/references/web/typedoc//IMUIKit/Latest/classes/LocalConversationStore.html#resetConversation。如果报错"conversation not found",需检查conversationId是否正确传递。

## 其他触发场景
