---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 屏幕共享
platform: Android
title: 另一平台投影仪屏幕共享颜色异常
root_cause: 投影仪解码器兼容性问题
solution: 需要根据设备型号单独配置，重启应用生效
customers: ["深圳康佳"]
source: chat_history
tags: ["RTC", "屏幕共享", "投影仪", "颜色异常"]
created: 2025-11-21
updated: 2026-03-20
---

## 问题：Android 另一平台投影仪屏幕共享颜色异常

## 问题详情

**现象**：
另一平台也出现相同的屏幕共享颜色问题。

## 排查过程

1. 确认问题相同
2. 收集日志
3. 应用设备配置
**关键发现**：同一问题在不同平台复现

## 问题原因

投影仪解码器兼容性问题

## 解决方案

需要根据设备型号单独配置，重启应用生效

## 其他触发场景

