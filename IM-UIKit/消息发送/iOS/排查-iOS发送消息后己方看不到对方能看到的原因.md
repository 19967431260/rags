---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息发送
platform: iOS
title: iOS发送消息后己方看不到对方能看到的原因（ChatDeduplicationHelper）
root_cause: iOS端发送消息去重逻辑ChatDeduplicationHelper导致己方看不到消息
solution: 检查ChatDeduplicationHelper配置，确保消息去重逻辑正确。
customers: ["武汉市渺寇午科技有限公司"]
source: chat_history
tags: ["iOS", "ChatDeduplicationHelper", "消息去重", "发送"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS iOS发送消息后己方看不到对方能看到的原因（ChatDeduplicationHelper）

## 问题详情

**现象**：
iOS发送消息后己方看不到对方能看到。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：iOS端发送消息去重逻辑ChatDeduplicationHelper导致己方看不到消息

## 问题原因

iOS端发送消息去重逻辑ChatDeduplicationHelper导致己方看不到消息

## 解决方案

检查ChatDeduplicationHelper配置，确保消息去重逻辑正确。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
