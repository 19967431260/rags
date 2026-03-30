---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK稳定性
platform: Android
title: IM SDK 9.19.2版本IndexOutOfBoundsException崩溃问题
root_cause: SDK 9.19.2版本存在已知的崩溃问题
solution: 升级到9.14.4版本修复该崩溃问题
customers: ['ISV云信-智慧丘比特-dx']
source: chat_history
tags: ['崩溃', 'IndexOutOfBoundsException', '9.19.2', '升级']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：Android IM SDK 9.19.2版本IndexOutOfBoundsException崩溃问题

## 问题详情

**现象**：
客户反馈安卓端升级云信SDK到9.19.2版本后出现IndexOutOfBoundsException崩溃，崩溃发生在网络模块。

## 排查过程

1. 客户提供崩溃日志，显示IndexOutOfBoundsException: Index: 11, Size: 10
2. 崩溃堆栈指向网络模块和日志模块
3. 技术支持建议升级到9.14.4版本

## 问题原因

SDK 9.19.2版本存在已知的崩溃问题

## 解决方案

升级到9.14.4版本修复该崩溃问题

## 其他触发场景

（合并时在此处追加）
