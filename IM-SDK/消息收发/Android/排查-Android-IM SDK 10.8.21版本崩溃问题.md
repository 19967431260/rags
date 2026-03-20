---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: IM SDK 10.8.21版本崩溃问题建议升级至10.9.60
root_cause: SDK 10.8.21版本存在的已知崩溃问题。
solution: 升级IM SDK至10.9.60版本，该版本已修复相关崩溃问题。
customers: ["FVIP云信-时间在线-gj"]
source: chat_history
tags: ["崩溃", "10.8.21", "10.9.60", "升级", "Bugly"]
created: 2025-11-07
updated: 2026-03-20
---

## 问题：Android IM SDK 10.8.21版本崩溃问题建议升级至10.9.60

## 问题详情

**现象**：
客户项目Bugly统计中多个版本出现SDK相关崩溃，当前使用SDK版本10.8.21。

## 排查过程

1. 收集崩溃堆栈 → 客户通过Bugly分享堆栈信息
2. 分析原因 → 客户端分析确认是已知问题
**关键发现**：该崩溃在10.9.60版本中已修复

## 问题原因

SDK 10.8.21版本存在的已知崩溃问题。

## 解决方案

升级IM SDK至10.9.60版本，该版本已修复相关崩溃问题。

## 其他触发场景

