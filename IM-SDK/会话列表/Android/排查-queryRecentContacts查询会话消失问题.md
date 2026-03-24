---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Android
title: queryRecentContacts查询会话消失问题
root_cause: 待排查
solution: 需要在同步完成状态监听后调用queryRecentContacts，如仍有问题需提供日志
customers: ['壹艺科技']
source: chat_history
tags: ['Android', 'queryRecentContacts', '会话列表', '消息漫游']
created: 2025-02-12
updated: 2026-03-23
---

## 问题：Android queryRecentContacts查询会话消失问题

## 问题详情

**现象**：
发送消息后queryRecentContacts会少掉该聊天室记录，重新开启app又出现

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈发送消息后会话列表记录消失
2. 检查消息漫游已开启
3. 需要在同步完成状态监听触发后查询
4. 客户确认同步完成后再查询仍会消失
5. 需要查看日志进一步排查

## 问题原因

待排查

## 解决方案

需要在同步完成状态监听后调用queryRecentContacts，如仍有问题需提供日志

## 其他触发场景

（合并时在此处追加：`- [Android] queryRecentContacts查询会话消失问题，来源：['壹艺科技']，2026-03-23`）
