---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 兼容性
platform: Android
title: NERTC SDK Android 16KB page size兼容性说明
root_cause: NERTC部分so库（如libNERtcAiDenoise.so、libNERtcAudio3D.so等）未做16KB对齐，Android 15+设备不兼容
solution: NERTC SDK nertc-base版本5.5.33起已支持16KB page size；如使用meeting SDK，建议使用4.16.0版本；仅需保留libnertc_sdk.so，其他so可删除或exclude
customers: ["壹艺科技-dx"]
source: chat_history
tags: ["16KB","Android15","NERTC","so库","page size"]
created: 2025-08-28
updated: 2026-03-26
---

## 问题：Android NERTC SDK Android 16KB page size兼容性说明

## 问题详情

**现象**：
Google Play要求2025年11月起所有更新必须支持Android 15+（16KB page size），NERTC SDK的so库存在兼容性问题。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android 15+
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：NERTC部分so库（如libNERtcAiDenoise.so、libNERtcAudio3D.so等）未做16KB对齐，Android 15+设备不兼容

## 问题原因

NERTC部分so库（如libNERtcAiDenoise.so、libNERtcAudio3D.so等）未做16KB对齐，Android 15+设备不兼容。

## 解决方案

NERTC SDK nertc-base版本5.5.33起已支持16KB page size；如使用meeting SDK，建议使用4.16.0版本；仅需保留libnertc_sdk.so，其他so可删除或exclude。

## 其他触发场景

（合并时在此处追加）
