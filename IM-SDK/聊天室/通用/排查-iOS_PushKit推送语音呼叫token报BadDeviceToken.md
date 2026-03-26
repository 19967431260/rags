---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: 通用
title: iOS PushKit推送语音呼叫token报BadDeviceToken
root_cause: VoIP证书本身不区分开发环境和生产环境，但苹果服务器地址在两个环境下不同，需将同一证书分别在开发和生产环境上传
solution: VoIP证书需同时上传至苹果开发环境服务器和生产环境服务器（证书本身不区分环境，但上传入口不同）。
customers: ["云信-BORUI GROUP (ASIA) CO,. LIMITED"]
source: chat_history
tags: ["PushKit", "BadDeviceToken", "VoIP证书", "iOS推送", "PushKit服务器"]
created: 2025-08-15
updated: 2026-03-26
---

## 问题：通用 iOS PushKit推送语音呼叫token报BadDeviceToken

## 问题详情

**现象**：
iOS端集成PushKit后，VoIP证书已上传，SDK日志显示rejectionReason='BadDeviceToken'，推送无法送达，导致app后台或被杀掉后无法收到呼叫推送。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
SDK日志显示rejectionReason='BadDeviceToken'，token推送至苹果PushKit服务器时报错

## 排查过程

1. 确认VoIP证书已上传 → 确认证书配置存在
2. 确认push证书（网易云信推送）未上传 → 排除另一证书问题
3. SDK日志显示token推送至苹果PushKit服务器时报BadDeviceToken → 确认问题出在苹果服务器层面
4. 检查证书与客户端环境是否匹配 → 定位到环境配置问题

**关键发现**：VoIP证书本身不区分开发环境和生产环境，但苹果服务器地址在两个环境下不同

## 问题原因

VoIP证书本身不区分开发环境和生产环境，但苹果服务器地址在两个环境下不同，需将同一证书分别在开发和生产环境上传

## 解决方案

VoIP证书需同时上传至苹果开发环境服务器和生产环境服务器（证书本身不区分环境，但上传入口不同）。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
