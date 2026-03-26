---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 集成
platform: iOS
title: iOS App上传App Store bitcode问题
root_cause: 旧版 NERtcSDK 默认包含 bitcode，Apple 已不支持 bitcode
solution: 将 pod 'NERtcSDK', '5.5.10' 替换为 pod 'NERtcSDK/RtcBasic', '5.6.50'；如仍有问题可升级 NERtcCallKit/NOS 到 2.5.2 版本。
customers: ["爱追光"]
source: chat_history
tags: ["App Store","bitcode","NERtcCallKit","NERtcSDK","上架被拒"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：iOS iOS App上传App Store bitcode问题

## 问题详情

**现象**：
客户上传 App Store 时遇到 NERtcCallKit/NOS 相关的 bitcode 报错，旧版 NERtcSDK 5.5.10 默认带 bitcode。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服建议替换 NERtcSDK 版本到 5.6.50 → 版本升级
2. 新版本不会带 bitcode → 版本确认
3. 如脚本处理后仍不行，可升级 NERtcCallKit/NOS 到 2.5.2 版本 → 备选方案

**关键发现**：旧版 NERtcSDK 默认包含 bitcode，Apple 已不支持 bitcode

## 问题原因

旧版 NERtcSDK 默认包含 bitcode，Apple 已不支持 bitcode

## 解决方案

将 pod 'NERtcSDK', '5.5.10' 替换为 pod 'NERtcSDK/RtcBasic', '5.6.50'；如仍有问题可升级 NERtcCallKit/NOS 到 2.5.2 版本。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
