---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: Android端发送消息报错10414
root_cause: 消息内容命中反垃圾规则
solution: 1. 检查消息内容是否包含敏感词；2. 在控制台查看反垃圾配置；3. 如需调整规则，联系技术支持。
customers: ["广州豆豆信息科技有限公司"]
source: chat_history
tags: ["消息发送", "反垃圾", "10414", "Android"]
created: 2026-01-08
updated: 2026-03-15
---

## 问题：Android Android端发送消息报错10414

## 问题详情

**现象**：
Android端发送消息时报错10414（消息反垃圾命中），但iOS端发送相同内容不报错。

## 排查过程

1. 检查消息内容 → 包含敏感词
2. 对比iOS和Android → iOS不报错
3. 检查反垃圾配置 → Android端可能配置了更严格的规则

## 问题原因

消息内容命中反垃圾规则

## 解决方案

1. 检查消息内容是否包含敏感词；2. 在控制台查看反垃圾配置；3. 如需调整规则，联系技术支持。
