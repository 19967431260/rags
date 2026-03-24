---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 表情评论
platform: Android
title: Android表情评论数据缺失
root_cause: 服务端问题，具体原因待查
solution: 服务端升级后持续观察，如复现提供具体消息ID和时间点
customers: ["千橡"]
source: chat_history
tags: ["表情评论","Android","数据缺失","消息评论"]
created: 2025-02-21
updated: 2025-03-20
---

## 问题：Android Android表情评论数据缺失

## 问题详情

**现象**：
Android端发送表情评论后，无法获取到表情评论数据。

## 排查过程

1. 确认问题存在 → 确认问题
2. 服务端增加debug日志 → 增加日志
3. 客户提供测试数据：messageId、messageTime、会话ID → 获取数据
4. 服务端升级包后复现查看日志 → 升级观察
5. 问题仍在排查中 → 持续跟进

**关键发现**：服务端问题，具体原因待查

## 问题原因

服务端问题，具体原因待查。

## 解决方案

服务端升级后持续观察，如复现提供具体消息ID和时间点。

## 其他触发场景

