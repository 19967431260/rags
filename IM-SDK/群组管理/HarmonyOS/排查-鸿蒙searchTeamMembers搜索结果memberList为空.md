---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: HarmonyOS
title: 鸿蒙searchTeamMembers搜索结果memberList为空
root_cause: searchTeamMembers按群成员昵称搜索，而非用户信息
solution: 如需按用户信息搜索群成员，使用getTeamMembers获取全量列表后自行过滤
customers: ["圆通"]
source: chat_history
tags: ["searchTeamMembers", "getTeamMembers", "群成员搜索", "HarmonyOS"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：HarmonyOS 鸿蒙searchTeamMembers搜索结果memberList为空

## 问题详情

**现象**：
鸿蒙SDK使用searchTeamMembers搜索群成员时，result有值但memberList为空，实际群中有该成员。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 确认群成员昵称信息 → searchTeamMembers按群成员昵称搜索
2. 对比getTeamMembers结果 → 确认群成员存在
3. 确认搜索逻辑 → searchTeamMembers不支持按用户信息搜索

**关键发现**：searchTeamMembers按群成员昵称搜索，而非用户信息

## 问题原因

searchTeamMembers按群成员昵称搜索，而非用户信息

## 解决方案

如需按用户信息搜索群成员，使用getTeamMembers获取全量列表后自行过滤

## 其他触发场景

（无）
