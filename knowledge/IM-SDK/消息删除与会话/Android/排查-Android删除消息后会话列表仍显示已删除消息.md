---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息删除与会话
platform: Android
title: Android删除消息后会话列表仍显示已删除消息
root_cause: deleteMessage只删除消息，会话的最后一条消息信息需要额外更新
solution: 调用deleteMessage之前先调用deleteMessageLocal，这样会话数据会正常更新
customers: ["广州启倬信息"]
source: chat_history
tags: ["Android", "deleteMessage", "deleteMessageLocal", "会话列表", "消息删除"]
created: 2025-05-14
updated: 2025-03-20
---

## 问题：Android Android删除消息后会话列表仍显示已删除消息

## 问题详情

**现象**：
使用ChatRepo.deleteMessage删除最新消息后，ConversationRepo.getSessionList查询出来的会话还是显示这条已删除的消息。

## 排查过程

**关键发现**：deleteMessage只删除消息，会话的最后一条消息信息需要额外更新

## 问题原因

deleteMessage只删除消息，会话的最后一条消息信息需要额外更新

## 解决方案

调用deleteMessage之前先调用deleteMessageLocal，这样会话数据会正常更新
