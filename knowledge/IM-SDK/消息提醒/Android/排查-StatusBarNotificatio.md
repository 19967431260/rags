---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息提醒
platform: Android
title: StatusBarNotificationFilter回调两次问题
root_cause: 旧版本SDK存在该问题，V9.20.15已优化
solution: 升级到V9.20.15，或兼容处理两次回调的情况；推送库需要对应升级
customers: ['北京耘想科技']
source: chat_history
tags: ['StatusBarNotificationFilter', '回调', 'Android', 'V9.20.15']
created: 2025-09-01
updated: 2026-03-25
---

## 问题：Android StatusBarNotificationFilter回调两次问题

## 问题详情

**现象**：
客户发现群里接收一个消息时，StatusBarNotificationFilter回调会执行两次。

## 解决方案

升级到V9.20.15，或兼容处理两次回调的情况；推送库需要对应升级
