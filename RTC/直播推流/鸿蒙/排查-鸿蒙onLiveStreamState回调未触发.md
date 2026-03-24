---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 直播推流
platform: 鸿蒙
title: 鸿蒙onLiveStreamState回调未触发
root_cause: addTask入参有问题导致添加失败。
solution: 检查addTask的入参，确保参数正确。
customers: ["创业天下"]
source: chat_history
tags: ["RTC", "直播推流", "onLiveStreamState", "鸿蒙"]
created: 2025-02-06
updated: 2025-03-20
---

## 问题：鸿蒙 鸿蒙onLiveStreamState回调未触发

## 问题详情

**现象**：
鸿蒙平台调用直播推流相关接口，onLiveStreamState回调没有触发。

**环境信息**：
- 平台：鸿蒙

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 收集SDK日志
2. 分析日志时间戳确认测试时间
3. 重新生成日志分析
4. 发现AddLiveStreamTask失败

**关键发现**：addTask入参有问题

## 问题原因

addTask入参有问题导致添加失败。

## 解决方案

检查addTask的入参，确保参数正确。

## 其他触发场景
