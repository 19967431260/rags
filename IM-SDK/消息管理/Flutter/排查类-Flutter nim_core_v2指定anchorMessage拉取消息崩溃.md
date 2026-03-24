---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息管理
platform: Flutter
title: Flutter nim_core_v2指定anchorMessage拉取消息崩溃
root_cause: 特定内容作为anchorMessage时字符超限导致崩溃。
solution: 升级到nim_core_v2 10.3.3版本，该版本已修复此问题。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['Flutter', 'anchorMessage', '崩溃', '拉取历史消息', 'nim_core_v2']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Flutter nim_core_v2指定anchorMessage拉取消息崩溃

## 问题详情

**现象**：
使用nim_core_v2在拉取消息列表时指定anchorMessage参数会导致崩溃，版本10.3.1，安卓正常，Flutter版本出现问题。

## 排查过程

1. 客户提供崩溃日志和调用截图；2. 技术支持分析可能是字符超限导致；3. 建议用普通文本消息作为锚点测试；4. 研发确认问题并修复。

## 问题原因

特定内容作为anchorMessage时字符超限导致崩溃。

## 解决方案

升级到nim_core_v2 10.3.3版本，该版本已修复此问题。

## 其他触发场景

（合并时在此处追加）
