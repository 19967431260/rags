---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 屏幕共享
platform: Android
title: 投影仪屏幕共享颜色异常
root_cause: 投影仪特定机型的解码器兼容性问题
solution: 针对特定设备型号调整配置，重启应用后生效。提供了video dump配置代码用于问题排查
customers: ["深圳康佳"]
source: chat_history
tags: ["RTC", "屏幕共享", "投影仪", "颜色异常", "解码器", "康佳"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Android 投影仪屏幕共享颜色异常

## 问题详情

**现象**：
康佳投影仪屏幕共享时蓝色变成橙色，橙色变成蓝色，仅该机型出现，其他Android/iOS/Web端正常。

## 排查过程

1. 确认问题范围
2. 对比腾讯会议测试
3. 收集日志和dump
4. 调整配置测试
**关键发现**：投影仪解码器问题，需要针对设备型号配置

## 问题原因

投影仪特定机型的解码器兼容性问题

## 解决方案

针对特定设备型号调整配置，重启应用后生效。提供了video dump配置代码用于问题排查

## 其他触发场景

