---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: FCM推送设置优先级
root_cause: 未设置FCM推送优先级导致消息可能被延迟或丢弃
solution: 在fcmFieldV1.message.android.notification中设置notification_priority为PRIORITY_HIGH
customers: ["VIP云信-武汉量子千寻科技有限公司"]
source: chat_history
tags: ["FCM", "推送", "优先级", "Android", "notification_priority", "fcmFieldV1"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：FCM推送设置优先级

## 问题详情

**现象**：
Android端FCM推送需要设置消息优先级

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈FCM推送成功率低
2. 分析发现未设置优先级
3. 建议在fcmFieldV1中设置notification_priority
4. 确认字段层级和名称与FCM文档一致

## 根因分析

未设置FCM推送优先级导致消息可能被延迟或丢弃

## 解决方案

在fcmFieldV1.message.android.notification中设置notification_priority为PRIORITY_HIGH

## 其他触发场景

（无）
