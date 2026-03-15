---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: SDK生命周期管理
platform: 通用
title: 调用destroyNERtcEngine偶发崩溃
root_cause: 客户接口调用有问题，未正常创建SDK就直接销毁，或者重复销毁SDK实例
solution: 确保SDK创建和销毁的配对调用，避免未创建就销毁或重复销毁的情况
customers:
- 飞虎互动
source: chat_history
tags:
- destroyNERtcEngine
- 崩溃
- SDK销毁
- 生命周期管理
created: '2026-01-04'
updated: '2026-03-15'
---

## 问题：通用 调用destroyNERtcEngine偶发崩溃

## 问题详情

**现象**：
客户在调用destroyNERtcEngine时偶发崩溃。现象：偶现崩溃。环境：Windows平台，使用RTC SDK。提供了dump文件分析。

## 排查过程

1. 检查dump文件 → 发现接口调用顺序有问题
2. 分析崩溃原因 → 怀疑未正常创建SDK就直接销毁，或重复销毁
**关键发现**：客户代码中存在SDK生命周期管理问题

## 问题原因

客户接口调用有问题，未正常创建SDK就直接销毁，或者重复销毁SDK实例

## 解决方案

确保SDK创建和销毁的配对调用，避免未创建就销毁或重复销毁的情况
