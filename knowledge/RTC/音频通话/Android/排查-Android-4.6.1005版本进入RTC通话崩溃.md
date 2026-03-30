---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音频通话
platform: Android
title: 4.6.1005版本进入RTC通话崩溃
root_cause: 缺少必要的工具包依赖
solution: 集成时需要加上三个工具包：report:2.1.0、catcher:1.0.2、nos:1.0.3
customers: ["北京四维云信"]
source: chat_history
tags: ["RTC", "崩溃", "4.6.1005", "工具包", "依赖"]
created: 2025-11-19
updated: 2026-03-20
---

## 问题：Android 4.6.1005版本进入RTC通话崩溃

## 问题详情

**现象**：
升级到4.6.1005后进入RTC通话就崩溃。

## 排查过程

1. 分析崩溃日志
2. 确认版本兼容性
**关键发现**：需要集成工具包依赖

## 问题原因

缺少必要的工具包依赖

## 解决方案

集成时需要加上三个工具包：report:2.1.0、catcher:1.0.2、nos:1.0.3

## 其他触发场景

