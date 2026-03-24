---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 语音房
platform: iOS
title: iOS NELoginSampleLog调用崩溃
root_cause: NELoginSampleLog是demo层代码，业务层不应调用。
solution: 业务层移除NELoginSampleLog调用，避免使用demo层的日志上报方法。SDK内部会评估优化apiLog方法，但发版需要时间，建议业务层先移除调用规避问题。
customers: ['海南通通智能科技有限公司北京分公司']
source: chat_history
tags: ['iOS', '崩溃', 'NELoginSampleLog', 'demo', 'apiLog']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：iOS NELoginSampleLog调用崩溃

## 问题详情

**现象**：
线上偶现崩溃，堆栈显示在NELoginSampleLog方法调用时崩溃。

## 排查过程

1. 分析崩溃日志发现是demo层业务逻辑导致；2. 确认NELoginSampleLog是demo项目演示使用；3. 建议业务层移除该调用。

## 问题原因

NELoginSampleLog是demo层代码，业务层不应调用。

## 解决方案

业务层移除NELoginSampleLog调用，避免使用demo层的日志上报方法。SDK内部会评估优化apiLog方法，但发版需要时间，建议业务层先移除调用规避问题。

## 其他触发场景

（合并时在此处追加）
