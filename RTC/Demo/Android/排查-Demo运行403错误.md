---
track_type: 排查类
sub_type: Demo问题
product: RTC
feature: Demo
platform: Android
title: Demo运行403错误
root_cause: 安全模式开启导致鉴权失败
solution: 到控制台关闭安全模式，打开调试模式即可正常运行Demo。
customers: ["武汉语舟科技有限公司-dx"]
source: chat_history
tags: ["Demo","403","安全模式","调试模式"]
created: 2025-06-07
updated: 2025-06-07
---

## 问题：Android Demo运行403错误

## 问题详情

**现象**：
客户运行NERtc-Api-Example等Demo提示403错误。

## 排查过程

1. 查看日志发现netcall.g2 unsafe mode is closed → 查看日志
2. 需要关闭安全模式打开调试模式 → 解决方案

**关键发现**：安全模式开启导致鉴权失败

## 问题原因

安全模式开启导致鉴权失败

## 解决方案

到控制台关闭安全模式，打开调试模式即可正常运行Demo。

## 其他触发场景

