---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: 微信小程序
title: V9小程序会话updateTime异常不等于lastMsg.time
root_cause: V9版本在处理消息更新或流式消息时，会话updateTime数据同步逻辑有问题
solution: 临时方案：取lastMsg.time作为会话更新时间，正常情况下updateTime应该与lastMsg.time相同。正式方案：预计月底发布V9 fix版本修复该问题。
customers: ["上海抱朴"]
source: chat_history
tags: ["V9", "微信小程序", "updateTime", "lastMsg", "流式消息", "消息更新"]
created: 2026-01-15
updated: 2026-03-15
---

## 问题：微信小程序 V9小程序会话updateTime异常不等于lastMsg.time

## 问题详情

**现象**：
使用V9.20.17版本，使用了消息更新或流式消息后，会话的updateTime与lastMsg.time不一致。现象：多个会话的updateTime都出现异常值，与lastMsg.time不相等。

## 排查过程

1. 检查会话数据 → 发现updateTime与lastMsg.time不一致
2. 确认SDK版本 → V9.20.17
3. 确认使用场景 → 使用了消息更新或流式消息
4. 研发分析日志 → onsessions底层打印没有异常时间戳，但业务层回调中出现
5. 提供复现项目 → 研发确认是消息更新/流式消息数据同步逻辑问题
**关键发现**：使用消息更新或流式消息时，会话updateTime同步逻辑存在bug

## 问题原因

V9版本在处理消息更新或流式消息时，会话updateTime数据同步逻辑有问题

## 解决方案

临时方案：取lastMsg.time作为会话更新时间，正常情况下updateTime应该与lastMsg.time相同。正式方案：预计月底发布V9 fix版本修复该问题。

## 其他触发场景

（合并时在此处追加）
