---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 在线状态订阅
platform: Android
title: Android在线状态订阅重复订阅问题
root_cause: 重复订阅逻辑问题
solution: 避免重复订阅，同时配置NIMOnlineClient参数
customers: ["广州启倬信息"]
source: chat_history
tags: ["Android", "在线状态订阅", "重复订阅", "V9"]
created: 2025-05-15
updated: 2025-03-20
---

## 问题：Android Android在线状态订阅重复订阅问题

## 问题详情

**现象**：
V9版本在线状态订阅功能，重复订阅后后续订阅不一定会回调结果。

## 排查过程

**关键发现**：重复订阅逻辑问题

## 问题原因

重复订阅逻辑问题

## 解决方案

避免重复订阅，同时配置NIMOnlineClient参数
