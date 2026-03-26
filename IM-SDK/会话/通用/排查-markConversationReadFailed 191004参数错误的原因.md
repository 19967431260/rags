---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话
platform: 通用
title: markConversationReadFailed 191004参数错误的原因
root_cause: conversationId参数格式错误，不符合云信conversationId的固定拼接规则
solution: 检查conversationId格式是否符合拼接规则；conversationId需通过固定规则从accid等字段拼接，错误格式会导致参数校验失败
customers: ["武汉无毁"]
source: chat_history
tags: ["markConversationReadFailed","191004","conversationId","参数错误"]
created: 2025-08-29
updated: 2026-03-26
---

## 问题：通用 markConversationReadFailed 191004参数错误的原因

## 问题详情

**现象**：
调用markConversationReadFailed接口返回错误码191004（invalid parameter）。

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

**关键发现**：conversationId参数格式错误，不符合云信conversationId的固定拼接规则

## 问题原因

conversationId参数格式错误，不符合云信conversationId的固定拼接规则。

## 解决方案

检查conversationId格式是否符合拼接规则；conversationId需通过固定规则从accid等字段拼接，错误格式会导致参数校验失败。

## 其他触发场景

（合并时在此处追加）
