---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间管理
platform: Android
title: onLeaveChannel和onDisconnect回调触发条件
root_cause: 被叫方未调用 leaveChannel（或房间已被删除），导致不触发 onLeaveChannel；部分用户日志拉不到无法进一步分析
solution: onLeaveChannel 只在本端调用 leaveChannel 时触发；房间被删除时应触发 onDisconnect（reason: ENGINE_ERROR_ROOM_CLOSED 30207）。如需排查，建议在出现问题的设备上复现并拉取日志进行分析。
customers: ["爱追光"]
source: chat_history
tags: ["onLeaveChannel","onDisconnect","ENGINE_ERROR_ROOM_CLOSED","RTC","通话关闭"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：Android onLeaveChannel和onDisconnect回调触发条件

## 问题详情

**现象**：
客户反映 RTC 通话时，一方收到 onLeaveChannel 回调，另一方却没有收到。onDisconnect 也没有触发。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认 onLeaveChannel 只在本端调用 leaveChannel 后才触发 → 回调触发条件
2. 如对方调用 leaveChannel 时房间已被删除，则不会回调 → 特殊场景
3. 建议监听 onDisconnect，抛出 ENGINE_ERROR_ROOM_CLOSED (30207) → 监听方案
4. 部分用户日志无法拉到，需要再次复现 → 日志问题

**关键发现**：被叫方未调用 leaveChannel（或房间已被删除），导致不触发 onLeaveChannel；部分用户日志拉不到无法进一步分析

## 问题原因

被叫方未调用 leaveChannel（或房间已被删除），导致不触发 onLeaveChannel；部分用户日志拉不到无法进一步分析

## 解决方案

onLeaveChannel 只在本端调用 leaveChannel 时触发；房间被删除时应触发 onDisconnect（reason: ENGINE_ERROR_ROOM_CLOSED 30207）。如需排查，建议在出现问题的设备上复现并拉取日志进行分析。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
