---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息列表
platform: Web
title: getConversation获取单个会话信息提示资源不存在
root_cause: 数据同步未完成即调用接口获取会话信息
solution: 需要在触发onDataSync回调之后，再去调用getConversation获取会话信息。
customers: ['山西闪数科技']
source: chat_history
tags: ['getConversation', '资源不存在', 'onDataSync', 'Web']
created: 2025-01-11
updated: 2026-03-23
---

## 问题：Web getConversation获取单个会话信息提示资源不存在

## 问题详情

**现象**：
客户反馈会话列表有信息，但调用getConversation获取单个会话信息时提示资源不存在。

## 排查过程



## 问题原因

数据同步未完成即调用接口获取会话信息

## 解决方案

需要在触发onDataSync回调之后，再去调用getConversation获取会话信息。

## 其他触发场景

（合并时在此处追加）
