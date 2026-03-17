---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: iOS
title: 会话列表lastMessage为null原因
root_cause: 调用deleteConversation删除会话时选择了删除会话内的消息
solution: 删除会话时注意deleteConversation的参数设置，避免误删会话内消息
tags: ["lastMessage", "null", "deleteConversation", "会话列表", "iOS"]
customers: ["上海数悦信息科技有限公司"]
source: chat_history
created: 2026-02-06
updated: 2026-03-17
---

## 问题：iOS 会话列表lastMessage为null原因

## 问题详情

**现象**：
拉取会话列表时，某个会话的lastMessage字段为null。消息是服务端发送的，非本地创建会话。

## 排查过程

1. 检查会话创建方式 → 非本地创建
2. 检查SDK日志 → 发现该会话有deleteConversation和createConversation调用
3. 检查删除会话操作 → deleteConversation时选择了删除会话内消息
**关键发现**：删除会话时同时删除了消息，导致lastMessage为null

## 问题原因

调用deleteConversation删除会话时选择了删除会话内的消息

## 解决方案

删除会话时注意deleteConversation的参数设置，避免误删会话内消息

## 其他触发场景

