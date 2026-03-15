---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 会话列表
platform: Web
title: Web端会话列表未读数不更新
root_cause: 未监听会话更新事件，无法更新UI
solution: 监听onSessionUpdate事件，收到会话更新通知后更新会话列表UI和未读数。
customers: ["云信-北京中科金财科技股份有限公司-gj"]
source: chat_history
tags: ['Web', '会话列表', '未读数', 'onSessionUpdate']
created: 2026-02-17
updated: 2026-03-15
---

## 问题：Web Web端会话列表未读数不更新

## 问题详情

**现象**：
Web端会话列表中的未读数不更新，收到新消息后未读数没有变化。

## 排查过程

1. 检查消息接收 → 正常
2. 检查未读数 → 不更新
3. 检查事件监听 → 未监听会话更新
**关键发现**：未监听会话更新事件

## 问题原因

未监听会话更新事件，无法更新UI

## 解决方案

监听onSessionUpdate事件，收到会话更新通知后更新会话列表UI和未读数。
