---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: SDK生命周期管理
platform: 通用
title: 异步线程销毁SDK导致重复释放崩溃
root_cause: 异步线程重进导致SDK实例被释放两次
solution: 将nrtc_engine_拷贝到临时变量tmp，然后立即将nrtc_engine_置为null，在异步线程中使用tmp进行释放。这样下次进入时判断为空就不会重复释放
customers:
- 飞虎互动
source: chat_history
tags:
- destroyNERtcEngine
- 崩溃
- 异步线程
- 重复释放
- release
created: '2026-01-08'
updated: '2026-03-15'
---

## 问题：通用 异步线程销毁SDK导致重复释放崩溃

## 问题详情

**现象**：
客户在独立线程中调用release后仍偶发destroyNERtcEngine崩溃。现象：偶现崩溃。环境：使用异步线程销毁SDK。提供了dump文件和代码截图。

## 排查过程

1. 检查客户销毁代码 → 发现在异步线程中销毁
2. 分析dump文件 → 发现存在两次释放情况
3. 分析原因 → 异步线程重进导致重复释放
**关键发现**：异步线程可能重入，导致同一个SDK实例被释放两次

## 问题原因

异步线程重进导致SDK实例被释放两次

## 解决方案

将nrtc_engine_拷贝到临时变量tmp，然后立即将nrtc_engine_置为null，在异步线程中使用tmp进行释放。这样下次进入时判断为空就不会重复释放
