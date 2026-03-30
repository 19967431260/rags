---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息漫游
platform: Flutter
title: Flutter端getMessageList获取群历史消息只能返回一条
root_cause: Flutter端getMessageList获取群历史消息参数配置问题或消息数量限制
solution: 检查getMessageList参数中的limit设置和时间范围配置，确保正确设置消息数量和时间范围。
customers: ["北京智域创芯科技有限公司"]
source: chat_history
tags: ["Flutter", "getMessageList", "群历史消息", "消息数量"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：Flutter Flutter端getMessageList获取群历史消息只能返回一条

## 问题详情

**现象**：
Flutter端getMessageList获取群历史消息只能返回一条。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：Flutter端getMessageList获取群历史消息参数配置问题或消息数量限制

## 问题原因

Flutter端getMessageList获取群历史消息参数配置问题或消息数量限制

## 解决方案

检查getMessageList参数中的limit设置和时间范围配置，确保正确设置消息数量和时间范围。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
