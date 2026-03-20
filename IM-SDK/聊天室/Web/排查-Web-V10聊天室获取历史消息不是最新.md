---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 聊天室
platform: Web
title: V10聊天室获取历史消息不是最新
root_cause: direction参数设置错误
solution: 将direction改为0（降序）即可获取最新消息
customers: ["广州欢牛"]
source: chat_history
tags: ["V10", "聊天室", "历史消息", "getMessageList", "direction"]
created: 2025-11-27
updated: 2026-03-20
---

## 问题：Web V10聊天室获取历史消息不是最新

## 问题详情

**现象**：
使用V2NIMChatroomService.getMessageList获取聊天室历史消息，获取的不是最新的5条数据。

## 排查过程

1. 复现问题
2. 分析日志
3. 确认API调用
**关键发现**：direction参数设置为1（升序）导致获取的是旧消息

## 问题原因

direction参数设置错误

## 解决方案

将direction改为0（降序）即可获取最新消息

## 其他触发场景

