---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 呼叫流程
platform: Flutter
title: Flutter呼叫组件升级后NERtcSDK版本冲突
root_cause: nertc_core_platform_interface会默认拉取最新版本5.9.20，与呼叫组件依赖的NERtcSDK 5.9.11版本冲突
solution: 在pubspec.yaml中同时指定nertc_core: 5.9.11和nertc_core_platform_interface: 5.9.11（不带^符号），然后执行flutter clean、删除pubspec.lock后重新flutter pub get。
customers: ["福州市玄星网络科技有限公司"]
source: chat_history
tags: ["Flutter","呼叫组件","版本冲突","NERtcSDK","5.9.11"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Flutter Flutter呼叫组件升级后NERtcSDK版本冲突

## 问题详情

**现象**：
Flutter项目升级呼叫组件到4.1.0后，iOS端pod install报错：NERtcSDK版本冲突。nertc_core依赖5.9.20，netease_callkit_ui依赖5.9.11。

## 排查过程

1. 检查依赖版本 → nertc_core解析到5.9.20，callkit依赖5.9.11
2. 尝试指定nertc_core版本 → 仍报错
3. 检查pubspec.lock → 发现nertc_core_platform_interface默认拉取5.9.20

**关键发现**：nertc_core_platform_interface会默认拉取最新版本5.9.20导致不兼容

## 问题原因

nertc_core_platform_interface会默认拉取最新版本5.9.20，与呼叫组件依赖的NERtcSDK 5.9.11版本冲突

## 解决方案

在pubspec.yaml中同时指定nertc_core: 5.9.11和nertc_core_platform_interface: 5.9.11（不带^符号），然后执行flutter clean、删除pubspec.lock后重新flutter pub get。

## 其他触发场景

