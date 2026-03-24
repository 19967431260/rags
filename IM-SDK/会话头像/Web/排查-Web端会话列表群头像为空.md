---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话头像
platform: Web
title: Web端会话列表群头像为空
root_cause: 群信息同步未完成时获取会话列表，导致avatar字段为空
solution: 在onDataSync回调中等待V2NIM_DATA_SYNC_STATE_COMPLETED状态触发后，再调用接口获取实时数据。
customers: ['Eagle']
source: chat_history
tags: ['Web', 'V10', '会话列表', 'avatar', '群头像', '数据同步']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Web Web端会话列表群头像为空

## 问题详情

**现象**：
调用nim.V2NIMConversationService.getConversationListByOption获取会话列表时，群头像avatar字段为空。

## 排查过程

1. 客户反馈头像为空 → 技术支持查询群信息 → 确认群头像已设置 → 询问获取时机 → 发现是在会话同步完成时获取 → 建议等待数据同步完成后再获取

## 问题原因

群信息同步未完成时获取会话列表，导致avatar字段为空

## 解决方案

在onDataSync回调中等待V2NIM_DATA_SYNC_STATE_COMPLETED状态触发后，再调用接口获取实时数据。

## 其他触发场景

（合并时在此处追加）
