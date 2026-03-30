---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Android
title: vivo推送SDK版本不适配报错api_key is null
root_cause: vivo推送SDK版本过低，与云信SDK不兼容
solution: 将vivo推送SDK升级到4.0.4.0_504版本。
customers: ["VIP云信-郑州开缘商贸有限公司"]
source: chat_history
tags: ["vivo推送", "api_key", "SDK版本", "初始化失败"]
created: 2025-11-07
updated: 2026-03-20
---

## 问题：Android vivo推送SDK版本不适配报错api_key is null

## 问题详情

**现象**：
集成vivo推送SDK后初始化报错，日志显示com.vivo.push.api_key is null，版本使用3.0.0.0_480。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查日志 → 发现com.vivo.push.api_key is null错误
2. 检查SDK版本 → 使用3.0.0.0_480
3. 确认版本兼容性 → 需要使用4.0.4.0_504版本
**关键发现**：SDK版本不兼容导致初始化失败

**关键发现**：

## 问题原因

vivo推送SDK版本过低，与云信SDK不兼容

## 解决方案

将vivo推送SDK升级到4.0.4.0_504版本。

## 其他触发场景

