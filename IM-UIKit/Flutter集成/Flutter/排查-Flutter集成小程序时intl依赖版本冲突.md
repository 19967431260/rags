---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: Flutter集成
platform: Flutter
title: Flutter集成小程序时intl依赖版本冲突
root_cause: fluttertoast 8.2.12和云信小程序SDK对intl版本要求不兼容（fluttertoast要求web ^1.0.0，而云信小程序SDK内部依赖intl >=0.20.0 <0.20.1）
solution: 在主包pubspec.yaml中添加dependency_overrides强制指定intl版本：dependency_overrides: intl: 0.20.2，然后重新执行flutter pub get
customers: ["深圳陌缘/海南颜陌-dx"]
source: chat_history
tags: ["Flutter","intl","依赖冲突","pubspec","fluttertoast","dependency_overrides"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：Flutter Flutter集成小程序时intl依赖版本冲突

## 问题详情

**现象**：
Flutter升级到3.7.3集成云信IM小程序SDK时，遇到intl依赖版本冲突报错：Because intl >=0.20.0 <0.20.1 depends on web ^0.5.0 and fluttertoast 8.2.12 depends on web ^1.0.0, version solving failed。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：Flutter 3.7.3
- 系统版本 / 设备：Flutter
- 其他：集成云信IM小程序SDK

**相关日志**：
Because intl >=0.20.0 <0.20.1 depends on web ^0.5.0 and fluttertoast 8.2.12 depends on web ^1.0.0, version solving failed

## 排查过程

1. 客户反馈Flutter集成小程序SDK时intl依赖冲突 → 确认依赖版本冲突
2. 客服确认可以通过在主包pubspec.yaml中添加dependency_overrides强制指定版本 → 找到解决方案

**关键发现**：fluttertoast 8.2.12和云信小程序SDK对intl版本要求不兼容

## 问题原因

fluttertoast 8.2.12和云信小程序SDK对intl版本要求不兼容（fluttertoast要求web ^1.0.0，而云信小程序SDK内部依赖intl >=0.20.0 <0.20.1）

## 解决方案

在主包pubspec.yaml中添加dependency_overrides强制指定intl版本：
```yaml
dependency_overrides:
  intl: 0.20.2
```
然后重新执行flutter pub get

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
