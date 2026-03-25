---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 初始化
platform: Android
title: NIMClient.init重复调用导致context为空崩溃
root_cause: 可能是重复初始化导致context被清空，或特定场景下getApplicationContext返回null
solution: 1. 避免重复调用NIMClient.init初始化
2. 开启SDK日志：SDKOption.consoleLogEnabled = true
3. 查看崩溃堆栈上方打印，确认context为null的原因
4. 检查是否在多线程环境下调用初始化
customers: ["融捷教育"]
source: chat_history
tags: ["初始化", "NIMClient.init", "context为空", "重复初始化", "崩溃"]
created: 2025-05-15
updated: 2025-03-20
---

## 问题：Android NIMClient.init重复调用导致context为空崩溃

## 问题详情

**现象**：
客户反馈偶尔出现崩溃，错误显示context为空，与NIMClient初始化有关。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Android

## 排查过程

1. 客户多次调用NIMClient.init(getApplicationContext(), null, options)未出现问题
2. 崩溃日志显示context为空，可能是未初始化或getApplicationContext为空
3. 客户确认context是整个项目的context，不会为null
4. 问题无法稳定复现，偶发

## 问题原因

可能是重复初始化导致context被清空，或特定场景下getApplicationContext返回null

## 解决方案

1. 避免重复调用NIMClient.init初始化
2. 开启SDK日志：SDKOption.consoleLogEnabled = true
3. 查看崩溃堆栈上方打印，确认context为null的原因
4. 检查是否在多线程环境下调用初始化

## 其他触发场景

