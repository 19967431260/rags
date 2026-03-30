---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: iOS
title: createConversation方法报错问题
root_cause: 传入的ID错误
solution: 检查传入createConversation的conversationId参数是否正确。
customers: ["济南时代"]
source: chat_history
tags: ["createConversation", "会话创建", "iOS", "参数错误"]
created: 2025-02-17
updated: 2026-03-20
---

## 问题：iOS createConversation方法报错问题

## 问题详情

**现象**：
客户对不同用户调用createConversation创建会话方法，有的会报错，但用户确实存在。

## 排查过程

1. 客户反馈调用createConversation报错
2. 技术支持要求提供完整传参
3. 客户自查发现传错ID
4. 确认是传入参数错误导致

## 问题原因

传入的ID错误

## 解决方案

检查传入createConversation的conversationId参数是否正确。

## 其他触发场景
- [iOS] createConversation方法报错问题，来源：['济南时代']，2026-03-20
- [iOS] createConversation方法报错问题，来源：['济南时代']，2026-03-20

