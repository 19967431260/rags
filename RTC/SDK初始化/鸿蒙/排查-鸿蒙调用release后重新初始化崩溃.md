---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: SDK初始化
platform: 鸿蒙
title: 鸿蒙调用release后重新初始化崩溃
root_cause: 调用release后重新初始化时崩溃，可能是SDK内部资源释放与重新初始化的问题。
solution: 需要进一步排查，负责的同事请假，周一给答复。
customers: ["创业天下"]
source: chat_history
tags: ["RTC", "release", "崩溃", "鸿蒙", "初始化"]
created: 2025-02-08
updated: 2025-03-20
---

## 问题：鸿蒙 鸿蒙调用release后重新初始化崩溃

## 问题详情

**现象**：
鸿蒙平台调用NERtcSDK.getInstance().release()后再次开播时崩溃，注释掉释放后正常。

**环境信息**：
- 平台：鸿蒙
- SDK版本：5.7.0

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认SDK版本 → 5.7.0
2. 确认调用流程 → 释放后会重新初始化
3. 分析崩溃位置 → 重新初始化开启预览设置参数时崩溃

**关键发现**：重新初始化时崩溃

## 问题原因

调用release后重新初始化时崩溃，可能是SDK内部资源释放与重新初始化的问题。

## 解决方案

需要进一步排查，负责的同事请假，周一给答复。

## 其他触发场景
