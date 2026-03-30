---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息撤回
platform: Web
title: 撤回消息后接收方未收到deleteMsg系统通知
root_cause: 消息撤回的系统通知需要通过系统通知回调监听，而非普通消息回调。
solution: 使用系统通知回调（如onsysmsg）监听撤回消息通知，而非onMsg。
customers: ["湖南春播万象科技有限公司"]
source: chat_history
tags: ["消息撤回", "deleteMsg", "系统通知", "Web", "回调"]
created: 2025-05-21
updated: 2025-03-20
---

## 问题：Web 撤回消息后接收方未收到deleteMsg系统通知

## 问题详情

**现象**：
使用nim.recallMsg撤回消息后，按照文档接收方应该收到类型为deleteMsg的系统通知，但实际未收到。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Web

## 排查过程

1. 客户反馈撤回消息接收方无通知 → 技术支持检查回调监听
2. 发现客户使用onMsg监听消息 → 需要使用系统通知回调
3. 提供正确的回调方法

## 问题原因

消息撤回的系统通知需要通过系统通知回调监听，而非普通消息回调。

## 解决方案

使用系统通知回调（如onsysmsg）监听撤回消息通知，而非onMsg。

## 其他触发场景

