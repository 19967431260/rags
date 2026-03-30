---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 最近会话
platform: Android
title: deleteRecentContact删除会话后未读数还在
root_cause: SDK注释误导，REMAIN不会删除会话，LOCAL才是仅删除会话不删消息。删除会话后未读数需要单独处理
solution: 1. 使用DeleteTypeEnum.LOCAL删除会话（不删除本地历史消息）
2. 需要清除未读数时，配合调用clearChattingHistory（同时清除未读数）或clearUnreadCount
3. 注意异步回调问题，删除成功后再获取会话列表
customers: ['VIP云信_初晴_核芯']
source: chat_history
tags: ['deleteRecentContact', '最近会话', '未读数', 'DeleteTypeEnum', 'Android']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android deleteRecentContact删除会话后未读数还在

## 问题详情

**现象**：
调用deleteRecentContact删除会话（设置不删除聊天记录），再次获取最近联系人时会话还在，未读数也还在

## 排查过程

1. 确认删除回调 → 回调成功
2. 检查删除类型 → 设置DeleteTypeEnum.REMAIN
3. 分析问题 → REMAIN只是保留消息，但不会删除会话
4. 确认注释误导 → SDK注释存在问题，导致理解偏差
5. 正确做法 → 使用DeleteTypeEnum.LOCAL删除会话但保留本地消息
6. 未读数处理 → 需要配合clearChattingHistory或clearUnreadCount

## 问题原因

SDK注释误导，REMAIN不会删除会话，LOCAL才是仅删除会话不删消息。删除会话后未读数需要单独处理

## 解决方案

1. 使用DeleteTypeEnum.LOCAL删除会话（不删除本地历史消息）
2. 需要清除未读数时，配合调用clearChattingHistory（同时清除未读数）或clearUnreadCount
3. 注意异步回调问题，删除成功后再获取会话列表

## 其他触发场景

（合并时在此处追加）
