---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Android
title: UIKit群解散后会话自动删除问题
root_cause: UIKit层默认逻辑在收到群解散通知后会自动删除本地会话
solution: 源码集成UIKit，修改conversationkit-ui库，删除getSessionList中filterSession方法的解散群过滤逻辑
customers: ['杭州跨客技术服务有限公司']
source: chat_history
tags: ['UIKit', '群解散', '会话列表', 'filterSession', 'Android']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Android UIKit群解散后会话自动删除问题

## 问题详情

**现象**：
客户使用UIKit组件，服务端解散群组后，移动端会话列表自动删除了该群会话。客户希望群解散后仍能在会话列表中查看聊天记录。

## 排查过程

1. 检查SDK层 → SDK不会主动删除会话
2. 检查UIKit层 → UIKit在收到群解散通知后会自动删除会话
3. 定位到ConversationRepo.deleteLocalSession和filterSession方法

## 问题原因

UIKit层默认逻辑在收到群解散通知后会自动删除本地会话

## 解决方案

源码集成UIKit，修改conversationkit-ui库，删除getSessionList中filterSession方法的解散群过滤逻辑

## 其他触发场景

（合并时在此处追加）
