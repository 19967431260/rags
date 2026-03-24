---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 云端会话
platform: 通用
title: v2ConversationCreate返回forbidden错误
root_cause: 云端会话功能未在控制台开启，导致接口调用返回forbidden错误。
solution: 在网易云信管理后台开通云端会话功能。注意：云端会话需要高级版套餐。
customers: ['千花伴(江西)文化发展有限公司']
source: chat_history
tags: ['云端会话', 'v2ConversationCreate', 'forbidden', '高级版']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：v2ConversationCreate返回forbidden错误

## 问题详情

**现象**：
调用v2ConversationCreate接口时返回forbidden错误，无法创建会话。

## 排查过程

1. 客户反馈接口返回forbidden → 技术支持判断是云端会话功能未开启
2. 指导客户在管理后台开启云端会话功能

## 问题原因

云端会话功能未在控制台开启，导致接口调用返回forbidden错误。

## 解决方案

在网易云信管理后台开通云端会话功能。注意：云端会话需要高级版套餐。

## 其他触发场景

（合并时在此处追加）
