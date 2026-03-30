---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息收发
platform: Uniapp
title: 创建会话conversationId格式错误
root_cause: conversationId格式不正确
solution: 单聊会话ID格式为：自己的accid|1|对端的accid。建议使用工具构建：nim.V2NIMConversationIdUtil.p2pConversationId('对端accid')
customers: ["长沙兴超教育咨询有限公司"]
source: chat_history
tags: ["IM V10","Uniapp","会话创建","conversationId"]
created: 2025-05-05
updated: 2025-03-23
---

## 问题：Uniapp 创建会话conversationId格式错误

## 问题详情

**现象**：
客户创建会话时返回validateConversationId错误，conversationId格式不正确。

**环境信息**：
- 平台：Uniapp
- 功能：消息收发/会话创建

## 排查过程

1. 确认错误信息 → validateConversationId错误
2. 分析问题原因 → conversationId格式不正确
3. 确认正确格式 → 自己的accid|1|对端的accid
4. 提供解决方案 → 使用工具构建conversationId

**关键发现**：conversationId格式不正确导致错误

## 问题原因

conversationId格式不正确。

## 解决方案

单聊会话ID格式为：自己的accid|1|对端的accid。建议使用工具构建：nim.V2NIMConversationIdUtil.p2pConversationId('对端accid')。

## 其他触发场景

