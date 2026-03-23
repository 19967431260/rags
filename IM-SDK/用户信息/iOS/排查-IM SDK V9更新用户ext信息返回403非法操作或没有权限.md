---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 用户信息
platform: iOS
title: IM SDK V9更新用户ext信息返回403非法操作或没有权限
root_cause: 权限问题或参数不正确
solution: 检查appkey、accid是否正确，确认操作时间点和日志
customers: ["FVIP-深圳秀蛋"]
source: chat_history
tags: ["iOS", "IM V9", "ext信息", "403", "权限错误"]
created: 2025-12-24
updated: 2026-03-23
---

## 问题：iOS IM SDK V9更新用户ext信息返回403非法操作或没有权限

## 问题详情

**现象**：
iOS IM SDK V9更新用户ext信息时返回403错误，提示"非法操作或没有权限"。

**环境信息**：
- SDK 版本：V9
- 平台：iOS

## 排查过程

1. 检查appkey和accid → 确认是否正确
2. 分析操作时间点和日志 → 定位权限问题

**关键发现**：403错误通常表示权限问题或参数不正确

## 问题原因

权限问题或参数不正确导致更新失败。

## 解决方案

检查appkey、accid是否正确，确认操作时间点和日志。

## 其他触发场景

