---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK集成
platform: Android
title: Android V9子进程ANR：Application onCreate耗时导致
root_cause: NIM SDK在主进程启动子进程（core子进程）时触发Application onCreate，若此时初始化过多耗时操作会阻塞子进程主线程导致ANR
solution: 1. 判断当前是否为子进程（通过进程名或配置区分），非主进程去掉不必要的第三方库初始化
2. 各个版本均有此设计，SDK内部通过provider获取abtest配置
3. 反馈给研发评估优化方案
customers: ["深圳岚峰创视"]
source: chat_history
tags: ["Android", "子进程", "ANR", "onCreate", "性能"]
created: 2025-07-17
updated: 2025-07-25
---

## 问题：Android V9 子进程 ANR：Application onCreate 耗时导致

## 问题详情

**现象**：
Android设备出现子进程ANR，堆栈显示在com.netease.nimlib.ipc.c.onServiceDisconnected；SDK 9.20.10版本；海外用户；部分小米手机ANR概率大幅上升。

**环境信息**：
- SDK版本：9.20.10
- 问题设备：海外用户，主要为小米手机
- 问题进程：NIM core子进程

## 排查过程

1. 分析堆栈，确认为子进程主线程阻塞
2. 根因定位：NIM SDK在子进程启动时会触发Application onCreate
3. 如果此时有大量三方库初始化在主线程执行，会导致子进程ANR
4. SDK内部通过provider获取abtest配置，这是各版本均有的设计
5. 子进程主线程阻塞不影响用户UI操作，但会被性能监控平台检测到

**关键发现**：问题根因为子进程Application onCreate中执行了过多耗时操作（大量三方库初始化），建议在onCreate中判断当前进程，非主进程跳过不必要的初始化。

## 问题原因

NIM SDK在主进程启动子进程（core子进程）时，会触发子进程的Application onCreate。如果在onCreate中初始化了大量第三方库（尤其在海外低性能设备上），会阻塞子进程主线程，导致ANR。

## 解决方案

1. 在Application onCreate中判断当前是否为子进程
   - 方法：检查当前进程名或通过SDK提供的配置判断
   - 如果是子进程或非主进程，跳过不必要的第三方库初始化
2. 各个版本SDK均有此设计（子进程通过provider获取配置）
3. 如需彻底优化，需反馈给云信研发侧评估改进
