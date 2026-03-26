---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: Web
platform: Web
title: Web端selectConversation会话不在列表中会白屏：需先insertConversationActive或升级UIKit版本
root_cause: selectConversation如果会话不在当前列表中，会话消息界面不会被拉起而是白屏；可能是分页限制尚未加载导致的
solution: 如果会话不在列表中，先调用store.conversationStore.insertConversationActive创建会话，再调用selectConversation；或升级UIKit版本修复此问题
customers: ["太旗富鑫"]
source: chat_history
tags: ["Web端", "UIKit", "selectConversation", "白屏", "会话列表"]
created: 2025-07-04
updated: 2026-03-25
---

## 问题：Web端selectConversation会话不在列表中会白屏：需先insertConversationActive或升级UIKit版本

## 问题原因

selectConversation如果会话不在当前列表中，会话消息界面不会被拉起而是白屏；可能是分页限制尚未加载导致的

## 解决方案

如果会话不在列表中，先调用store.conversationStore.insertConversationActive创建会话，再调用selectConversation；或升级UIKit版本修复此问题
