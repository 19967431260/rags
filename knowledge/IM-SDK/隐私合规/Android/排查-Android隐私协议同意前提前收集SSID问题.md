---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 隐私合规
platform: Android
title: Android隐私协议同意前提前收集SSID问题
root_cause: 在网络监听回调里打印WiFi信息时触发了SSID获取，这是之前版本引入的监听，导致同意隐私前调用config时会触发监听执行。
solution: 升级到9.19.11版本修复。9.19.10版本修复了打印WiFi信息的问题，9.19.11版本修复了监听在隐私协议前触发的问题。iOS 9.17.2不受影响，但建议同步版本。
customers: ["智联招聘"]
source: chat_history
tags: ["隐私合规", "SSID", "WiFi", "安全检测", "Android", "9.19.11"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android隐私协议同意前提前收集SSID问题

## 问题详情

**现象**：
安全检测发现云信在隐私协议同意前，有提前收集SSID（WiFi信息）的行为。

**环境信息**：
- 平台：Android

## 根因分析

在网络监听回调里打印WiFi信息时触发了SSID获取，这是之前版本引入的监听，导致同意隐私前调用config时会触发监听执行。

## 解决方案

升级到9.19.11版本修复。9.19.10版本修复了打印WiFi信息的问题，9.19.11版本修复了监听在隐私协议前触发的问题。iOS 9.17.2不受影响，但建议同步版本。

## 其他触发场景

（无）
