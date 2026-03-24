---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息发送
platform: Web
title: Web端UIKit发送消息时多个会话同时触发问题
root_cause: 未正确取消会话选中状态，导致多个会话同时响应发送消息
solution: 1. 在发送消息前调用unselectSession取消所有选中状态\n2. 或使用selectSession切换到目标会话后再发送\n3. selectSession：切换对话\n4. unselectSession：取消选中所有会话
customers: ['滴聘']
source: chat_history
tags: ['sendTextMsgActive', 'selectSession', 'unselectSession', '消息发送', 'Web', 'UIKit']
created: 2025-01-25
updated: 2026-03-23
---

## 问题：Web Web端UIKit发送消息时多个会话同时触发问题

## 问题详情

**现象**：
Web端使用UIKit时，调用sendTextMsgActive发送消息，发现之前点击过的所有聊天框都会触发发送。经排查是没有正确切换/取消会话导致的。

## 排查过程

1. 客户询问sendTextMsgActive是群发还是一对一\n2. 说明scene参数控制群消息或单聊\n3. 客户反馈之前点击过的聊天都会发送消息\n4. 检查代码发现selectSession用于切换对话\n5. 建议使用unselectSession取消选中后再发送\n6. unselectSession会取消所有选中状态

## 问题原因

未正确取消会话选中状态，导致多个会话同时响应发送消息

## 解决方案

1. 在发送消息前调用unselectSession取消所有选中状态\n2. 或使用selectSession切换到目标会话后再发送\n3. selectSession：切换对话\n4. unselectSession：取消选中所有会话

## 其他触发场景

（合并时在此处追加）
