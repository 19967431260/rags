---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 发送消息接口参数key错误
root_cause: Demo中消息类型参数写的是type，实际接口需要的是message_type。
solution: 调用发送消息接口时，消息类型参数key应使用message_type，而非type。
customers: ['北京中软融鑫计算机系统工程有限公司']
source: chat_history
tags: ['IM', '服务端API', '发送消息', '参数']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：服务端 发送消息接口参数key错误

## 问题详情

**现象**：
客户调用发送消息接口时，消息类型参数使用错误，导致发送失败。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈发送消息失败 → 检查参数
2. 发现客户使用type作为消息类型参数key → 实际应为message_type
3. 修改参数key后 → 发送成功

## 问题原因

Demo中消息类型参数写的是type，实际接口需要的是message_type。

## 解决方案

调用发送消息接口时，消息类型参数key应使用message_type，而非type。

## 其他触发场景

（合并时在此处追加：`- [服务端] 发送消息接口参数key错误，来源：['北京中软融鑫计算机系统工程有限公司']，2026-03-23`）
