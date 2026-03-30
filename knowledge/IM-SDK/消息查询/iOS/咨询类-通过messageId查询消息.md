---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息查询
platform: iOS
title: 通过messageId查询消息
root_cause: 
solution: SDK没有提供通过messageId找NIMMessage的方法。可以使用queryMessageListByIds方法，传入messageId和sessionId查询到NIMMessage后再构建。
customers: ['杭州晶达网络科技有限公司']
source: chat_history
tags: ['messageId', 'NIMMessageReceipt', '已读回执', 'queryMessageListByIds']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：通过messageId查询消息

## 问题详情

**现象**：
客户咨询只知道messageId的情况下如何构造NIMMessageReceipt发送已读回执。

## 排查过程



## 问题原因



## 解决方案

SDK没有提供通过messageId找NIMMessage的方法。可以使用queryMessageListByIds方法，传入messageId和sessionId查询到NIMMessage后再构建。

## 其他触发场景

（合并时在此处追加）
