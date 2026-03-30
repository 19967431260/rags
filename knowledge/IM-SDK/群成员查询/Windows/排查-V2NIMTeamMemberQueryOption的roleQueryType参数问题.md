---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群成员查询
platform: Windows
title: V2NIMTeamMemberQueryOption的roleQueryType参数问题
root_cause: SDK实现问题，optional字段实际为必填
solution: 当前版本必须传值，后续版本会优化
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["群成员", "roleQueryType", "optional", "参数错误"]
created: 2025-11-03
updated: 2026-03-20
---

## 问题：Windows V2NIMTeamMemberQueryOption的roleQueryType参数问题

## 问题详情

**现象**：
V2NIMTeamMemberQueryOption结构体中roleQueryType字段虽然是optional类型，但请求时必须传值，否则会报错。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认错误现象 → 提示参数错误
2. 分析代码 → optional字段实际为必填
**关键发现**：文档与实现不一致

**关键发现**：

## 问题原因

SDK实现问题，optional字段实际为必填

## 解决方案

当前版本必须传值，后续版本会优化

## 其他触发场景

