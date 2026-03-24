---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 云端会话
platform: Web
title: Web端获取会话列表无数据
root_cause: 未开启云端会话功能
solution: 在云信控制台开启云端会话功能。
customers: ['Eagle']
source: chat_history
tags: ['Web', 'V10', '会话列表', '云端会话', 'getConversationListByOption']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Web Web端获取会话列表无数据

## 问题详情

**现象**：
已经建了群并发送消息，但web端调用nim.V2NIMConversationService.getConversationListByOption获取到的会话列表没有数据。

## 排查过程

1. 客户反馈会话列表无数据 → 技术支持询问是否开启云端会话 → 客户确认开启后问题解决

## 问题原因

未开启云端会话功能

## 解决方案

在云信控制台开启云端会话功能。

## 其他触发场景

（合并时在此处追加）
