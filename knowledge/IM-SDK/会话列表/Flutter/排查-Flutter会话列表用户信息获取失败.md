---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Flutter
title: Flutter会话列表用户信息获取失败
root_cause: fetchUserInfoList每次最多获取150个用户，超过后需要分批获取。
solution: 会话超过150条时，需要分批调用fetchUserInfoList获取用户信息，或使用增量获取会话列表。
customers: ['深圳问津']
source: chat_history
tags: ['Flutter', '会话列表', '用户信息', '150条限制']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Flutter Flutter会话列表用户信息获取失败

## 问题详情

**现象**：
Flutter端获取会话列表后，用户信息显示为空，首次安装正常，使用一段时间后出现问题。

**环境信息**：
- 平台：Flutter
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查会话列表获取方式 → 使用querySessionList
2. 检查用户信息获取方式 → 使用getUserInfoList
3. 确认问题场景 → 会话超过150条后出现问题
4. 定位根因 → fetchUserInfoList每次最多获取150个用户

## 问题原因

fetchUserInfoList每次最多获取150个用户，超过后需要分批获取。

## 解决方案

会话超过150条时，需要分批调用fetchUserInfoList获取用户信息，或使用增量获取会话列表。

## 其他触发场景

（合并时在此处追加：`- [Flutter] Flutter会话列表用户信息获取失败，来源：['深圳问津']，2026-03-23`）
