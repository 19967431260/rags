---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: iOS
title: deleteAllMessages后lastMessage不为空
root_cause: iOS SDK在清空历史记录后会插入一个空消息占位，这是正常行为
solution: text没有值即为正常，UI上显示最后一条消息为空
customers: ["VIP云信-东莞市伊洛信息科技有限公司"]
source: chat_history
tags: ["deleteAllMessages", "lastMessage", "iOS", "清空记录", "会话"]
created: 2025-02-05
updated: 2026-03-20
---

## 问题：iOS deleteAllMessages后lastMessage不为空

## 问题详情

**现象**：
iOS端调用conversationManager.deleteAllMessages删除会话聊天记录后，查询对应会话lastMessage不为空，messageType为0

## 排查过程

1. 确认删除行为 → 正常清空历史记录会删除会话历史消息
2. 确认SDK行为 → iOS会插入一个空消息
3. 验证text值 → text没有值表示正常

## 问题原因

iOS SDK在清空历史记录后会插入一个空消息占位，这是正常行为

## 解决方案

text没有值即为正常，UI上显示最后一条消息为空

## 其他触发场景

