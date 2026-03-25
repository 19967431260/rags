---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息收发
platform: Uniapp
title: 创建会话返回illegal state错误
root_cause: const conversationId=null声明导致的
solution: 去掉const声明，在赋值的地方直接创建conversationId
customers: ["长沙兴超教育咨询有限公司"]
source: chat_history
tags: ["IM V10","Uniapp","会话创建"]
created: 2025-05-05
updated: 2025-03-23
---

## 问题：Uniapp 创建会话返回illegal state错误

## 问题详情

**现象**：
客户创建会话时返回V2NIMError: illegal state错误。

**环境信息**：
- 平台：Uniapp
- 功能：消息收发/会话创建

## 排查过程

1. 确认错误信息 → V2NIMError: illegal state
2. 分析代码问题 → const conversationId=null声明导致
3. 提供解决方案 → 去掉const声明

**关键发现**：const conversationId=null声明导致错误

## 问题原因

const conversationId=null声明导致的。

## 解决方案

去掉const声明，在赋值的地方直接创建conversationId。

## 其他触发场景

