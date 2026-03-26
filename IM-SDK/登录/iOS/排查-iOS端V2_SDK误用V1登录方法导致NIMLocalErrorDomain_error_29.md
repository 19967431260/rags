---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: iOS
title: iOS端V2 SDK误用V1登录方法导致NIMLocalErrorDomain error 29
root_cause: iOS端V2 SDK使用了V1的登录方法导致错误
solution: iOS端V2 SDK需要使用V2的登录方法，参考V2 SDK文档重新实现登录逻辑。
customers: ["成都超林科技有限公司"]
source: chat_history
tags: ["NIMLocalErrorDomain", "error 29", "V1登录", "V2 SDK", "iOS"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS iOS端V2 SDK误用V1登录方法导致NIMLocalErrorDomain error 29

## 问题详情

**现象**：
iOS端V2 SDK误用V1登录方法导致NIMLocalErrorDomain error 29。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：V2 SDK
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
NIMLocalErrorDomain error 29

## 排查过程

**关键发现**：iOS端V2 SDK使用了V1的登录方法导致错误

## 问题原因

iOS端V2 SDK使用了V1的登录方法导致错误

## 解决方案

iOS端V2 SDK需要使用V2的登录方法，参考V2 SDK文档重新实现登录逻辑。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
