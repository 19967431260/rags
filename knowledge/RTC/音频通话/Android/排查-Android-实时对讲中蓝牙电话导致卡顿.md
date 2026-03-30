---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 音频通话
platform: Android
title: 实时对讲中蓝牙电话导致卡顿
root_cause: 收到电话挂断后恢复声音的操作在主线程执行耗时，包含系统setMode和SDK native方法
solution: 将声音恢复操作放到子线程执行，预计下周三前提供修复版本4.6.1005
customers: ["北京四维云信"]
source: chat_history
tags: ["RTC", "实时对讲", "蓝牙", "卡顿", "setMode", "主线程", "车机"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Android 实时对讲中蓝牙电话导致卡顿

## 问题详情

**现象**：
实时对讲中通过蓝牙拨打电话后立即挂断，导航APP切到后台再切回前台会有卡顿，系统确认是导航内部有耗时操作引起。

## 排查过程

1. 收集卡顿堆栈和SDK日志
2. 分析CPU日志
3. 定位耗时操作
**关键发现**：电话状态监听回调主线程中耗时，setMode和native方法启动声音播放耗时

## 问题原因

收到电话挂断后恢复声音的操作在主线程执行耗时，包含系统setMode和SDK native方法

## 解决方案

将声音恢复操作放到子线程执行，预计下周三前提供修复版本4.6.1005

## 其他触发场景

