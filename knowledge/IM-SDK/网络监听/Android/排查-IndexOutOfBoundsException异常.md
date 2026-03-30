---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 网络监听
platform: Android
title: IndexOutOfBoundsException异常
root_cause: SDK 9.19.0版本存在的bug
solution: 升级nimsdk到9.19.3版本，该版本已解决IndexOutOfBoundsException问题
customers: ["台州浩瀚网络"]
source: chat_history
tags: ["Android", "IndexOutOfBoundsException", "9.19.0", "升级"]
created: 2025-06-16
updated: 2025-03-23
---

## 问题：Android IndexOutOfBoundsException异常

## 问题详情

**现象**：
Android SDK 9.19.0版本出现IndexOutOfBoundsException异常，发生在NetworkChangeRecorder。

**环境信息**：
- SDK版本：9.19.0

## 排查过程

1. 确认异常堆栈 → 2. 确认SDK版本9.19.0 → 3. 升级至9.19.3版本修复

## 问题原因

SDK 9.19.0版本存在的bug

## 解决方案

升级nimsdk到9.19.3版本，该版本已解决IndexOutOfBoundsException问题
