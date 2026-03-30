---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: HarmonyOS
title: RTC SDK暂不适配OpenHarmony开源系统
root_cause: RTC SDK目前主要适配HarmonyOS 5.0.0 Release或以上版本，OpenHarmony作为开源系统，系统API可能不稳定，SDK未做专门兼容适配。
solution: RTC SDK目前不对OpenHarmony开源系统做兼容适配。建议使用HarmonyOS 5.0.0 Release或以上版本，或联系OpenHarmony厂商根据崩溃堆栈修复系统问题。
customers: ["ISV云信-科蓝-视频坐席"]
source: chat_history
tags: ["HarmonyOS", "OpenHarmony", "崩溃", "适配", "5.0.0"]
created: 2025-11-18
updated: 2026-03-20
---

## 问题：HarmonyOS RTC SDK暂不适配OpenHarmony开源系统

## 问题详情

**现象**：
客户在OpenHarmony 14版本上使用鸿蒙RTC SDK出现崩溃，初始化后本地预览崩溃。

## 排查过程

1. 确认版本 → 客户使用5.9.5和5.9.11版本测试
2. 分析问题 → 崩溃堆栈显示走到系统库的http库
3. 确认适配范围 → SDK主要适配HarmonyOS 5.0.0 Release或以上版本
**关键发现**：OpenHarmony是开源系统，系统API不稳定，SDK未做专门适配

## 问题原因

RTC SDK目前主要适配HarmonyOS 5.0.0 Release或以上版本，OpenHarmony作为开源系统，系统API可能不稳定，SDK未做专门兼容适配。

## 解决方案

RTC SDK目前不对OpenHarmony开源系统做兼容适配。建议使用HarmonyOS 5.0.0 Release或以上版本，或联系OpenHarmony厂商根据崩溃堆栈修复系统问题。

## 其他触发场景

