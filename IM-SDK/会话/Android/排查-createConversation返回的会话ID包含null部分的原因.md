---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话
platform: Android
title: createConversation返回的会话ID包含null部分的原因
root_cause: 手动创建会话时传入的参数中，sessionType参数传了null值，导致conversationId拼接时将null字符串拼接进去
solution: 检查createConversation调用时的参数，确保sessionType等参数为有效值而非null；conversationId格式为 accid|sessionType|xxx，null会被直接拼入字符串
customers: ["武汉梦匠科技有限公司"]
source: chat_history
tags: ["createConversation","conversationId","null","会话ID"]
created: 2025-08-29
updated: 2026-03-26
---

## 问题：Android createConversation返回的会话ID包含null部分的原因

## 问题详情

**现象**：
调用createConversation返回的conversationId中包含null字符串，如：t1_im_400|1|null。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：手动创建会话时传入的参数中，sessionType参数传了null值，导致conversationId拼接时将null字符串拼接进去

## 问题原因

手动创建会话时传入的参数中，sessionType参数传了null值，导致conversationId拼接时将null字符串拼接进去。

## 解决方案

检查createConversation调用时的参数，确保sessionType等参数为有效值而非null；conversationId格式为 accid|sessionType|xxx，null会被直接拼入字符串。

## 其他触发场景

（合并时在此处追加）
