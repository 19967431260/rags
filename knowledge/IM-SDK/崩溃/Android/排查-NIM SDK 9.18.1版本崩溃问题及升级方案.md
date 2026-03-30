---
track_type: 排查类
sub_type: SDK问题
product: IM-SDK
feature: 崩溃
platform: Android
title: NIM SDK 9.18.1版本崩溃问题及升级方案
root_cause: SDK内部LinkedList在线程池操作时存在并发安全问题，导致ConcurrentModificationException和NullPointerException
solution: 升级NIM SDK到9.20.12版本，两个崩溃均已在该版本修复
customers: ["武汉无毁"]
source: chat_history
tags: ["崩溃","ConcurrentModificationException","NullPointerException","LinkedList","版本升级"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：Android NIM SDK 9.18.1版本崩溃问题及升级方案

## 问题详情

**现象**：
Android端使用NIM SDK 9.18.1版本出现两个崩溃：1）ConcurrentModificationException: LinkedList$ListItr并发修改异常；2）NullPointerException: LinkedList$Node.next空指针异常。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：9.18.1
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

客户提供Sentry崩溃日志，tech确认两个崩溃均为SDK内部线程安全问题 → 根因确认

**关键发现**：SDK内部LinkedList在线程池操作时存在并发安全问题，导致ConcurrentModificationException和NullPointerException

## 问题原因

SDK内部LinkedList在线程池操作时存在并发安全问题，导致ConcurrentModificationException和NullPointerException。

## 解决方案

升级NIM SDK到9.20.12版本，两个崩溃均已在该版本修复。

## 其他触发场景

（合并时在此处追加）
