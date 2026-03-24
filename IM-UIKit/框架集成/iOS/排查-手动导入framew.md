---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 框架集成
platform: iOS
title: 手动导入framework打包报错
root_cause: framework包含x86模拟器架构，与真机打包冲突
solution: 使用lipo命令去除framework的x86架构：lipo -remove x86_64 -remove i386
customers: ["上海丁奇通教育科技"]
source: chat_history
tags: ["framework", "打包", "x86", "lipo", "手动导入"]
created: 2025-02-05
updated: 2026-03-20
---

## 问题：iOS 手动导入framework打包报错

## 问题详情

**现象**：
iOS手动导入UIKit framework后打包报错。

## 排查过程

1. 确认导入方式 → 手动导入framework
2. 分析报错原因 → framework包含x86架构导致
3. 执行解决方案 → 使用lipo命令去除x86架构

## 问题原因

framework包含x86模拟器架构，与真机打包冲突

## 解决方案

使用lipo命令去除framework的x86架构：lipo -remove x86_64 -remove i386

## 其他触发场景

