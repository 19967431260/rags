---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 荣耀推送
platform: Android
title: 荣耀推送intent参数为空导致推送失败
root_cause: 推送payload中intent参数为空字符串，荣耀推送要求click type=1时必须提供intent或action
solution: 确保推送payload中intent参数不为空，或修改click type为其他类型
customers: ['万象森森']
source: chat_history
tags: ['荣耀推送', 'intent', 'clickAction', 'payload']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Android 荣耀推送intent参数为空导致推送失败

## 问题详情

**现象**：
荣耀手机离线推送不成功，payload中intent参数配置问题

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈荣耀推送不成功
2. 检查payload发现intent字段为空
3. 报错: {"code":400,"message":"intent or action is required when click type=1"}
4. 客户修改intent配置后解决

## 问题原因

推送payload中intent参数为空字符串，荣耀推送要求click type=1时必须提供intent或action

## 解决方案

确保推送payload中intent参数不为空，或修改click type为其他类型

## 其他触发场景

（合并时在此处追加：`- [Android] 荣耀推送intent参数为空导致推送失败，来源：['万象森森']，2026-03-23`）
