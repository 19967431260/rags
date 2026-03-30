---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息撤回
platform: 通用
title: 消息撤回后只收到revoke通知无消息替换
root_cause: 云信SDK撤回只下发通知，不下发消息，消息替换为业务层实现
solution: 云信撤回只下发通知，不下发消息，消息列表替换需要业务层自行实现
customers: ["好未来-yach"]
source: chat_history
tags: ["消息撤回", "revoke", "通知"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：消息撤回后只收到revoke通知无消息替换

## 问题详情

**现象**：
客户反馈之前撤回消息后会收到revoke通知并有一条消息替换，现在只收到revoke通知，消息列表无替换。

**环境信息**：
- 平台：通用

## 排查过程

1. 确认云信SDK逻辑
2. 检查业务层逻辑
3. 要求提供消息ID验证

## 根因分析

云信SDK撤回只下发通知，不下发消息，消息替换为业务层实现

## 解决方案

云信撤回只下发通知，不下发消息，消息列表替换需要业务层自行实现

## 其他触发场景

（无）
