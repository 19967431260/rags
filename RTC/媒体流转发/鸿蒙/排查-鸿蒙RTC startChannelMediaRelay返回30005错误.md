---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 媒体流转发
platform: 鸿蒙
title: 鸿蒙RTC startChannelMediaRelay返回30005错误
root_cause: appKey未传入导致channelName为空。
solution: 确保正确传入appKey配置。
customers: ["创业天下"]
source: chat_history
tags: ["RTC", "媒体流转发", "30005", "鸿蒙", "appKey"]
created: 2025-02-06
updated: 2025-03-20
---

## 问题：鸿蒙 鸿蒙RTC startChannelMediaRelay返回30005错误

## 问题详情

**现象**：
鸿蒙平台调用startChannelMediaRelay转发媒体流返回30005错误，运行设备是模拟器。

**环境信息**：
- 平台：鸿蒙
- 设备：模拟器

**相关日志**：
channelName is empty

## 排查过程

1. 收集模拟器日志
2. 分析日志发现channelName is empty错误
3. 检查appKey配置 → 发现appKey未传
4. 补充appKey后解决

**关键发现**：appKey未传入

## 问题原因

appKey未传入导致channelName为空。

## 解决方案

确保正确传入appKey配置。

## 其他触发场景
