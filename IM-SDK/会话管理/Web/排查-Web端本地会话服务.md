---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Web
title: Web端本地会话服务undefined
root_cause: 本地会话功能(V2NIMLocalConversationService)是在SDK 10.8.0版本才添加的，客户使用的10.7.1版本不支持。
solution: 升级SDK到10.8.0或更高版本以使用本地会话功能。获取会话列表应监听本地会话的onSyncFinished事件。
customers: ["北京爱和健康科技有限公司"]
source: chat_history
tags: ["Web端", "本地会话", "V2NIMLocalConversationService", "版本", "10.8.0"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：Web Web端本地会话服务undefined

## 问题详情

**现象**：
客户使用Web端SDK，尝试使用V2NIMLocalConversationService监听本地会话同步，但报错undefined。

## 排查过程

1. 确认SDK版本 → 10.7.1\n2. 确认本地会话功能版本 → 10.8.0才添加\n3. 确认问题 → 版本过低

## 问题原因

本地会话功能(V2NIMLocalConversationService)是在SDK 10.8.0版本才添加的，客户使用的10.7.1版本不支持。

## 解决方案

升级SDK到10.8.0或更高版本以使用本地会话功能。获取会话列表应监听本地会话的onSyncFinished事件。

## 其他触发场景
- [Web] Web端本地会话服务undefined，来源：['北京爱和健康科技有限公司']，2026-03-20

