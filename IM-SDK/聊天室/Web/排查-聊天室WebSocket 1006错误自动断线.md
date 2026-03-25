---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: Web
title: 聊天室WebSocket 1006错误自动断线
root_cause: 白板与IM聊天室同时挂载到同一网页下存在冲突
solution: 白板与IM聊天室两个独立SDK理论上不冲突，但客户环境存在兼容问题，建议拆分功能或提供demo工程进一步排查。
customers: ["智慧树"]
source: chat_history
tags: ["聊天室", "WebSocket", "1006", "自动断线", "白板冲突"]
created: 2025-05-19
updated: 2025-03-20
---

## 问题：Web 聊天室WebSocket 1006错误自动断线

## 问题详情

**现象**：
客户反馈聊天室连接约1分钟后自动断开，WebSocket返回1006错误码，已排除网络不畅原因。

## 排查过程

**关键发现**：白板与IM聊天室同时挂载到同一网页下存在冲突

## 问题原因

白板与IM聊天室同时挂载到同一网页下存在冲突

## 解决方案

白板与IM聊天室两个独立SDK理论上不冲突，但客户环境存在兼容问题，建议拆分功能或提供demo工程进一步排查。
