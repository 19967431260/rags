---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: Android
title: 修改群昵称后IMMessage.getFromNick()获取旧昵称
root_cause: 客户端本端发消息的nickname使用自身信息缓存，不会随群昵称修改而更新。收到其他用户消息时会刷新对应缓存
solution: 需要展示群内昵称时，可直接使用TeamMember对象获取
customers: ['东莞市伊洛信息科技有限公司']
source: chat_history
tags: ['群昵称', 'getFromNick', 'Android', '缓存', 'TeamMember']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Android 修改群昵称后IMMessage.getFromNick()获取旧昵称

## 问题详情

**现象**：
Android端修改自己在群里的昵称后，发送消息时自己看到的是旧昵称，别人看到的是新昵称。

## 排查过程

1. 确认问题现象：自己看是旧昵称，别人看是新昵称
2. 分析日志发现发送成功时fromnick已是新昵称
3. 确认客户端本端发消息的nickname缓存机制
**关键发现**：客户端本端发消息的nickname是提前写好的自身信息缓存，不会随群昵称修改而更新

## 问题原因

客户端本端发消息的nickname使用自身信息缓存，不会随群昵称修改而更新。收到其他用户消息时会刷新对应缓存

## 解决方案

需要展示群内昵称时，可直接使用TeamMember对象获取

## 其他触发场景

（合并时在此处追加）
