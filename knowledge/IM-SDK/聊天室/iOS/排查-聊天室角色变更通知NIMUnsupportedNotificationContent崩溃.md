---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 聊天室
platform: iOS
title: 聊天室角色变更通知NIMUnsupportedNotificationContent崩溃
root_cause: 为兼容V10逻辑，服务端同时下发V9和V10两种类型通知消息，V9 SDK无法识别V10的326类型
solution: 关闭双消息下发配置，仅保留V9类型消息。如需支持V10，需升级SDK版本
customers: ['YOOY语音']
source: chat_history
tags: ['聊天室', '角色变更', 'NIMUnsupportedNotificationContent', '崩溃', 'V9', 'V10', '326']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：iOS 聊天室角色变更通知NIMUnsupportedNotificationContent崩溃

## 问题详情

**现象**：
iOS端聊天室用户角色变更时收到NIMUnsupportedNotificationContent类型消息，强转时崩溃。服务端同时下发V9和V10两种类型消息。

## 排查过程

1. 客户反馈聊天室角色变更消息类型变为NIMUnsupportedNotificationContent
2. 客户业务代码强转该类型获取eventType属性导致崩溃
3. 排查发现服务端为兼容V10逻辑同时下发两条通知消息
4. 确认V9类型消息event_id为307，V10新类型为326
**关键发现**：V9 SDK无法识别326类型，显示为unknowNotificationContent

## 问题原因

为兼容V10逻辑，服务端同时下发V9和V10两种类型通知消息，V9 SDK无法识别V10的326类型

## 解决方案

关闭双消息下发配置，仅保留V9类型消息。如需支持V10，需升级SDK版本

## 其他触发场景

（合并时在此处追加）
