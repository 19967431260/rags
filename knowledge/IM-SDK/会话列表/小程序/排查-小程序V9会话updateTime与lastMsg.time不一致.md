---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: 小程序
title: 小程序V9会话updateTime与lastMsg.time不一致
root_cause: 使用消息更新或流式消息时，SDK内部数据同步逻辑有问题导致updateTime与lastMsg.time不一致
solution: 临时方案：取lastMsg.time作为会话时间。正式修复：研发已确认问题，预计月底发布新版本（包括V9的fix版本）优化该问题。
customers: ["上海抱朴"]
source: chat_history
tags: ["updateTime", "lastMsg", "会话列表", "流式消息", "消息更新", "V9"]
created: 2026-01-15
updated: 2026-03-15
---

## 问题：小程序 小程序V9会话updateTime与lastMsg.time不一致

## 问题详情

**现象**：
使用IM V9.20.17小程序SDK，发现会话列表中部分会话的updateTime与lastMsg.time不一致。客户使用了消息更新或流式消息功能。

**环境信息**：
- 平台：小程序

## 排查过程

1. 检查会话数据 → 发现updateTime与lastMsg.time存在差异
2. 确认是否使用消息更新或流式消息 → 确认使用了该功能
3. 研发分析日志 → 发现onsessions底层打印与业务层回调数据不一致
4. 研发复现问题 → 确认是数据同步逻辑问题
**关键发现**：使用消息更新或流式消息时，会话updateTime同步逻辑存在问题

## 问题原因

使用消息更新或流式消息时，SDK内部数据同步逻辑有问题导致updateTime与lastMsg.time不一致

## 解决方案

临时方案：取lastMsg.time作为会话时间。正式修复：研发已确认问题，预计月底发布新版本（包括V9的fix版本）优化该问题。

## 其他触发场景

