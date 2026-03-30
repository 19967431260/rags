---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息同步
platform: 通用
title: observeRecentContact回调消息顺序问题
root_cause: 消息分包下发，observeRecentContact可能触发多次，SDK策略不是每一条消息都会更新一次会话
solution: observeRecentContact可能触发多次，应以最后一次回调为准。或走queryRecentContacts拿到最终更新后的会话。
customers: ["智联招聘"]
source: chat_history
tags: ["消息同步", "observeRecentContact", "分包", "回调"]
created: 2025-05-28
updated: 2025-03-20
---

## 问题：通用 observeRecentContact回调消息顺序问题

## 问题详情

**现象**：
用户启动app后进入IM列表，observeRecentContact回调中拿到的最近一条消息不是真正的最后一条。

## 排查过程

**关键发现**：消息分包下发，observeRecentContact可能触发多次，SDK策略不是每一条消息都会更新一次会话

## 问题原因

消息分包下发，observeRecentContact可能触发多次，SDK策略不是每一条消息都会更新一次会话

## 解决方案

observeRecentContact可能触发多次，应以最后一次回调为准。或走queryRecentContacts拿到最终更新后的会话。
