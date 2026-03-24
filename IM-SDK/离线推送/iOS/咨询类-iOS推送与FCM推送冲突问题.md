---
track_type: 咨询类
sub_type: 能力与边界咨询
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS推送与FCM推送冲突问题
root_cause: 
solution: 不会冲突，云信推送本身依赖厂商底层推送。iOS走APNs推送，Android走厂商推送。
customers: ['太旗富鑫']
source: chat_history
tags: ['推送', 'FCM', 'APNs', 'iOS', 'Android', '冲突']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS推送与FCM推送冲突问题

## 问题详情

**现象**：
客户咨询同时集成云信推送和FCM推送是否会冲突。

## 排查过程



## 问题原因



## 解决方案

不会冲突，云信推送本身依赖厂商底层推送。iOS走APNs推送，Android走厂商推送。

## 其他触发场景

（合并时在此处追加）
