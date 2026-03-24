---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: IM群消息接收延迟问题排查
root_cause: SDK日志显示消息已收到，怀疑是业务层没有正确展示自定义消息，监听可能被remove或处理逻辑有问题
solution: 在addMessageListener、onReceiveMessages、removeMessageListener、onReceiveMessages、addConversationListener、onConversationChanged等位置打印日志排查业务层处理逻辑
customers: ['VIP云信-邯郸市趣网传媒技术有限公司']
source: chat_history
tags: ['消息延迟', '群消息', '消息监听', 'Android']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Android IM群消息接收延迟问题排查

## 问题详情

**现象**：
服务端发送的群消息，一个手机立即收到，另一个手机需要一段时间后才能收到。重新登录后一下收到所有消息。期间其他用户语音发言可以听到

## 排查过程

1. 检查消息ID和接收方日志 → 发现消息在服务端已发送
2. 检查SDK日志 → 消息确实已收到（notify received messages）
3. 怀疑业务层监听问题 → 建议检查addMessageListener/onReceiveMessages和addConversationListener/onConversationChanged回调

## 问题原因

SDK日志显示消息已收到，怀疑是业务层没有正确展示自定义消息，监听可能被remove或处理逻辑有问题

## 解决方案

在addMessageListener、onReceiveMessages、removeMessageListener、onReceiveMessages、addConversationListener、onConversationChanged等位置打印日志排查业务层处理逻辑

## 其他触发场景

（合并时在此处追加）
