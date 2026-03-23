---
track_type: 排查类
sub_type: SDK崩溃
product: IM-UIKit
feature: 基础库
platform: Android
title: UIKit Android V10.1.0版本alog库部分设备崩溃
root_cause: alog so文件加载异常
solution: 检查安装包是否包含该so文件，确认打包配置是否正确
customers: ["FVIP-深圳秀蛋"]
source: chat_history
tags: ["IM UIKit", "Android", "V10.1.0", "alog", "崩溃"]
created: 2025-12-24
updated: 2026-03-23
---

## 问题：IM UIKit Android V10.1.0版本alog库部分设备崩溃

## 问题详情

**现象**：
IM UIKit Android V10.1.0版本在部分设备上出现alog库崩溃。

**环境信息**：
- SDK 版本：V10.1.0
- 平台：Android

## 排查过程

1. 分析崩溃日志 → 发现alog so文件加载异常
2. 检查打包配置 → 确认so文件是否正确打包

**关键发现**：alog so文件加载异常导致崩溃

## 问题原因

alog so文件加载异常导致崩溃。

## 解决方案

1. 检查安装包是否包含该so文件
2. 确认打包配置是否正确

后续版本会增加异常捕获。

## 其他触发场景

