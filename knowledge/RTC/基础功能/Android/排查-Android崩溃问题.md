---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 基础功能
platform: Android
title: Android崩溃问题排查
root_cause: ""
solution: "提供带符号的so替换重现，收集完整core dump和日志"
customers: ["SVIPS云信"]
source: chat_history
tags: []
created: 2025-06-05
updated: 2025-03-23
---

## 问题：Android崩溃问题排查

## 问题详情

**现象**：
通话4个小时没问题，希望确认具体问题在哪里，能否在使用的版本加调试信息复现确认。

**环境信息**：
- 平台：Android
- 版本：9.16.11

## 排查过程

1. 提供9.16.11带符号的so → 替换重现
2. 清理日志 → 如重现收集完整core dump
3. 分析崩溃栈 → 已有符号信息但只有一个线程

## 问题原因

崩溃栈信息有限，需要结合其他线程和日志分析

## 解决方案

1. 使用带符号的so替换重现
2. 重现前清理日志
3. 如重现，收集完整core dump（压缩后发送）
4. 收集log目录和hav_comp目录下的日志
5. 使用thread apply all bt将所有线程调用栈写入文件

## 其他触发场景

