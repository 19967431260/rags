---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群管理
platform: 通用
title: setTeamChatBannedMode禁言无效的原因
root_cause: setTeamChatBannedMode设置的禁言仅对普通成员生效，管理员和群主不受限制；当时发送消息的恰好是管理员账号
solution: 群禁言（setTeamChatBannedMode）只限制普通成员发言，不限制管理员和群主；如需限制所有人，需使用其他禁言策略或使用NIMTeamChatBannedModeFull枚举值
customers: ["天天新鲜电子商务有限公司"]
source: chat_history
tags: ["群禁言","setTeamChatBannedMode","管理员","普通成员","禁言无效"]
created: 2025-08-22
updated: 2026-03-26
---

## 问题：通用 setTeamChatBannedMode禁言无效的原因

## 问题详情

**现象**：
调用setTeamChatBannedMode设置群禁言后，普通成员仍能发送消息。

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

**关键发现**：setTeamChatBannedMode设置的禁言仅对普通成员生效，管理员和群主不受限制；当时发送消息的恰好是管理员账号

## 问题原因

setTeamChatBannedMode设置的禁言仅对普通成员生效，管理员和群主不受限制；当时发送消息的恰好是管理员账号。

## 解决方案

群禁言（setTeamChatBannedMode）只限制普通成员发言，不限制管理员和群主；如需限制所有人，需使用其他禁言策略或使用NIMTeamChatBannedModeFull枚举值。

## 其他触发场景

（合并时在此处追加）
