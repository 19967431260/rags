---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Flutter集成
platform: Flutter
title: Flutter SDK版本依赖冲突
root_cause: nim_core和nim_core_platform_interface版本不一致，本地缓存导致自动升级到1.9.0。
solution: 1. 强行指定版本：dependency_overrides: nim_core_platform_interface: 1.9.0
2. 或清理缓存后重新拉取
3. 建议直接升级到1.9.0
customers: ["杭州东方网升"]
source: chat_history
tags: ["Flutter", "版本冲突", "依赖", "1.9.0", "1.8.2"]
created: 2025-06-25
updated: 2026-03-23
---

## 问题：Flutter Flutter SDK版本依赖冲突

## 问题详情

**现象**：
客户反馈Flutter SDK 1.9.0拉下来有类缺失，1.8.3和1.8.2也有不同报错，版本依赖混乱。

**环境信息**：
- SDK版本：1.9.0, 1.8.3, 1.8.2

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查依赖树发现版本不一致
2. 确认1.9.0新加的api在1.8没有实现
3. 可能是本地缓存导致自动升级

**关键发现**：nim_core和nim_core_platform_interface版本不一致，本地缓存导致自动升级到1.9.0。

## 问题原因

nim_core和nim_core_platform_interface版本不一致，本地缓存导致自动升级到1.9.0。

## 解决方案

1. 强行指定版本：dependency_overrides: nim_core_platform_interface: 1.9.0
2. 或清理缓存后重新拉取
3. 建议直接升级到1.9.0

## 其他触发场景

