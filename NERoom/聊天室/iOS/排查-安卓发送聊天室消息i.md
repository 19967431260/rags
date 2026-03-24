---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 聊天室
platform: iOS
title: 安卓发送聊天室消息iOS偶现收不到
root_cause: 偶现问题，可能房间未正常关闭导致状态异常
solution: 确保房间正常关闭，如问题复现提供日志和时间点进一步排查
customers: ["上海丁奇通教育科技"]
source: chat_history
tags: ["聊天室", "消息接收", "偶现", "跨端"]
created: 2025-02-10
updated: 2026-03-20
---

## 问题：iOS 安卓发送聊天室消息iOS偶现收不到

## 问题详情

**现象**：
安卓端使用sendBroadcastTextMessage发送消息，iOS端onReceiveChatroomMessagesWithMessages偶现收不到消息。

## 排查过程

1. 确认发送成功 → 安卓端发送成功
2. 分析接收端 → iOS端偶现收不到，后恢复正常
3. 排查原因 → 可能房间未正常关闭导致状态异常

## 问题原因

偶现问题，可能房间未正常关闭导致状态异常

## 解决方案

确保房间正常关闭，如问题复现提供日志和时间点进一步排查

## 其他触发场景

