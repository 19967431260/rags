---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: 发送消息后messageId为-1
root_cause: messageId为本地临时值，serverId和uuid才是服务端标识
solution: messageId为-1是正常现象，不需要关注，使用serverId和uuid即可
customers: ["北京微光互动-微光"]
source: chat_history
tags: ["messageId","-1","observeMsgStatus","消息发送"]
created: 2025-02-07
updated: 2025-03-20
---

## 问题：Android 发送消息后messageId为-1

## 问题详情

**现象**：
发送消息后SDK observeMsgStatus回调的IMMessage里的messageId是-1。

## 排查过程

1. 获取SDK日志分析 → 获取日志
2. 确认serverId和uuid正常即可 → 确认问题原因

**关键发现**：messageId为本地临时值

## 问题原因

messageId为本地临时值，serverId和uuid才是服务端标识。

## 解决方案

messageId为-1是正常现象，不需要关注，使用serverId和uuid即可。

## 其他触发场景

