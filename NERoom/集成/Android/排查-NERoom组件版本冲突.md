---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 集成
platform: Android
title: NERoom组件版本冲突
root_cause: 版本不匹配导致。
solution: 升级nimcore版本到10.4.0，这两个版本适配。需要gradle 8.0+、kotlin 1.6+、jdk 11+。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['NERoom', '版本冲突', 'nim_core', 'roomkit']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Android NERoom组件版本冲突

## 问题详情

**现象**：
接入NERoom组件报冲突错误，nim_core_v2 10.3.3与netease_roomkit ^1.34.0版本不兼容。

**环境信息**：
- 平台：Android
- 产品：NERoom

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

版本不匹配导致。

## 解决方案

升级nimcore版本到10.4.0，这两个版本适配。需要gradle 8.0+、kotlin 1.6+、jdk 11+。

## 其他触发场景

（合并时在此处追加：`- [Android] NERoom组件版本冲突，来源：['海南无限链科技有限公司']，2026-03-23`）
