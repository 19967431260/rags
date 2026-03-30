---
track_type: 排查类
sub_type: BUG问题
product: IM-SDK
feature: 消息已读
platform: Android
title: MessageReceiptHelper崩溃sessionId为null
root_cause: MessageReceiptHelper.getReceivedReceiptTime时传入的sessionId为null
solution: 在kit代码里增加一个判空来规避；后续SDK会发版本优化避免崩溃
customers: ["即客"]
source: chat_history
tags: ["崩溃", "MessageReceiptHelper", "sessionId", "null", "Android"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：Android MessageReceiptHelper崩溃sessionId为null

## 问题详情

**现象**：
Android端出现崩溃，bugly收集到的错误，版本9.16.3。

## 排查过程

1. 收集崩溃日志和堆栈信息
2. 分析崩溃原因 → 发现是MessageReceiptHelper.getReceivedReceiptTime时传入的sessionId为null导致

## 问题原因

MessageReceiptHelper.getReceivedReceiptTime时传入的sessionId为null

## 解决方案

在kit代码里增加一个判空来规避；后续SDK会发版本优化避免崩溃

## 其他触发场景
- [Android] MessageReceiptHelper崩溃sessionId为null，来源：['即客']，2026-03-20
- [Android] MessageReceiptHelper崩溃sessionId为null，来源：['即客']，2026-03-20

