---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: iOS
title: NIMUnsupportedNotificationContent消息类型
root_cause: 为兼容v9和v10，服务器会同时下发两条通知消息(326和307/308/309/310)。326是新版本事件ID，旧版本SDK解析不出来会显示为NIMUnsupportedNotificationContent
solution: 服务器同时下发新旧两种格式，旧版本SDK可解析307/308/309/310。客户端遇到NIMUnsupportedNotificationContent类型直接丢弃即可，同时间还会收到一条能解析的消息
customers: ['VIP云信-广州触海网络科技']
source: chat_history
tags: ['聊天室', 'NIMUnsupportedNotificationContent', '326', '角色更新', 'iOS', '兼容']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS NIMUnsupportedNotificationContent消息类型

## 问题详情

**现象**：
iOS端收到NIMUnsupportedNotificationContent类型消息，聊天室成员角色更新时触发

## 排查过程

1. 确认消息类型 → 聊天室通知消息，messageType为5
2. 分析消息内容 → 发现是角色更新相关，event_id为326
3. 对比SDK版本 → SDK 9.18.0支持到325，服务器下发326

## 问题原因

为兼容v9和v10，服务器会同时下发两条通知消息(326和307/308/309/310)。326是新版本事件ID，旧版本SDK解析不出来会显示为NIMUnsupportedNotificationContent

## 解决方案

服务器同时下发新旧两种格式，旧版本SDK可解析307/308/309/310。客户端遇到NIMUnsupportedNotificationContent类型直接丢弃即可，同时间还会收到一条能解析的消息

## 其他触发场景

（合并时在此处追加）
