---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史记录
platform: Android
title: clearChattingHistory异常频繁调用导致消息自动删除
root_cause: 业务代码中clearChattingHistory接口被异常频繁调用（1秒内多次），导致聊天记录被清空。
solution: 排查业务代码中clearChattingHistory的调用逻辑，检查是否存在循环调用、重复触发等异常情况。建议添加调用日志和防抖逻辑。
customers:
- 武汉奔赴远方
source: chat_history
tags:
- clearChattingHistory
- 消息删除
- 异常调用
created: '2026-01-06'
updated: '2026-03-15'
---

## 问题：Android clearChattingHistory异常频繁调用导致消息自动删除

## 问题详情

**现象**：
用户反馈聊天记录自动删除，会话列表中用户存在但进入后聊天记录为空。代码中删除操作都有二次确认弹窗，但仍出现消息自动删除。

## 排查过程

1. 检查删除逻辑 → 代码有二次确认
2. 提取SDK日志 → 发现clearChattingHistory在1秒内被调用多次
**关键发现**：日志显示clearChattingHistory异常频繁调用，不像正常业务逻辑。

## 问题原因

业务代码中clearChattingHistory接口被异常频繁调用（1秒内多次），导致聊天记录被清空。

## 解决方案

排查业务代码中clearChattingHistory的调用逻辑，检查是否存在循环调用、重复触发等异常情况。建议添加调用日志和防抖逻辑。
