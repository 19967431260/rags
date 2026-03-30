---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: Android
title: gson库版本冲突
root_cause: 不同SDK依赖的gson版本不同（2.8.6 vs 2.8.9）
solution: 排除其中一个gson依赖，使用统一版本
customers: ["北京具象"]
source: chat_history
tags: ["Android", "gson", "版本冲突", "Duplicate class"]
created: 2025-05-12
updated: 2025-03-20
---

## 问题：Android gson库版本冲突

## 问题详情

**现象**：
升级SDK后与别的SDK发生gson库冲突。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Android

## 排查过程



## 问题原因

不同SDK依赖的gson版本不同（2.8.6 vs 2.8.9）

## 解决方案

排除其中一个gson依赖，使用统一版本

## 其他触发场景

