---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: iOS
title: Unity iOS SDK初始化失败SSL is disabled
root_cause: 客户使用的Unity SDK版本较旧（2.4.8），与iOS 18.6存在兼容性问题，导致初始化失败。
solution: 1. 升级到新版本Unity SDK（v2.9.0或更高）
2. 新SDK已修复iOS 18兼容性问题
3. 参考升级文档进行迁移
4. 如无法立即升级，可尝试临时禁用SSL相关功能
customers: ["英雄互娱"]
source: chat_history
tags: ["Unity", "iOS", "初始化", "SSL", "iOS 18", "崩溃"]
created: 2025-11-06
updated: 2026-03-20
---

## 问题：iOS Unity iOS SDK初始化失败SSL is disabled

## 问题详情

**现象**：
客户在使用Unity iOS SDK（NIM Elite）时，初始化报错SSL is disabled，随后崩溃。错误日志显示Failed to set login state, core is empty or uid locker is empty。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析日志 → 发现SSL is disabled警告
2. 检查初始化流程 → SDK初始化返回result:1，但后续崩溃
3. 确认Unity版本 → 2022.3.62f2
4. 分析根因 → SDK版本较旧，与iOS 18.6兼容性问题
**关键发现**：旧版SDK在iOS 18.6上存在兼容性问题，需要升级SDK

**关键发现**：

## 问题原因

客户使用的Unity SDK版本较旧（2.4.8），与iOS 18.6存在兼容性问题，导致初始化失败。

## 解决方案

1. 升级到新版本Unity SDK（v2.9.0或更高）
2. 新SDK已修复iOS 18兼容性问题
3. 参考升级文档进行迁移
4. 如无法立即升级，可尝试临时禁用SSL相关功能

## 其他触发场景

