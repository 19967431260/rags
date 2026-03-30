---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 性能优化
platform: Android
title: 应用OutOfMemory崩溃
root_cause: 应用内存使用不当导致OOM
solution: 需要客户自行分析内存使用情况，检查当时执行代码的内存占用
customers: ['智联招聘']
source: chat_history
tags: ['OOM', '内存', '崩溃', 'OutOfMemory']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Android 应用OutOfMemory崩溃

## 问题详情

**现象**：
应用出现OOM崩溃，需要排查原因

## 排查过程

1. 查看崩溃日志 → 确认是OutOfMemoryError
2. 分析建议 → 需要客户自行分析内存使用情况

## 问题原因

应用内存使用不当导致OOM

## 解决方案

需要客户自行分析内存使用情况，检查当时执行代码的内存占用

## 其他触发场景

（合并时在此处追加）
