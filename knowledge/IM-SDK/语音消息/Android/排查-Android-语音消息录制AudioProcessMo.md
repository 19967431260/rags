---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Android
title: 语音消息录制AudioProcessModule崩溃问题
root_cause: 语音消息录制接口在降噪处理时出现的崩溃，该库暂无更新计划。
solution: 如崩溃数量较多，建议改用系统自带的语音录制接口替代SDK的语音消息录制功能。
customers: ["FVIP云信-时间在线-gj"]
source: chat_history
tags: ["语音消息", "AudioProcessModule", "崩溃", "降噪", "录制"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Android 语音消息录制AudioProcessModule崩溃问题

## 问题详情

**现象**：
Android SDK 9.19.4和10.9.20版本出现com.netease.share.media.internal.audio.AudioProcessModule相关的崩溃，数量较多。

## 排查过程

1. 收集崩溃日志 → 客户提供crash堆栈
2. 分析原因 → 确认是语音消息录制接口降噪处理时的问题
**关键发现**：语音消息录制模块的降噪处理库存在问题

## 问题原因

语音消息录制接口在降噪处理时出现的崩溃，该库暂无更新计划。

## 解决方案

如崩溃数量较多，建议改用系统自带的语音录制接口替代SDK的语音消息录制功能。

## 其他触发场景

