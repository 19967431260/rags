---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送SDK版本不兼容导致No static method异常
root_cause: NIM SDK 8.7.0与OPPO推送SDK 3.4.0版本不匹配，8.7.0仅适配OPPO推送2.1.0版本。
solution: 两种解决方案：1）降级OPPO推送SDK到2.1.0版本；2）升级NIM SDK到9.16.0版本（已适配OPPO推送3.4.0）。
customers: ["杭州亦闲信息"]
source: chat_history
tags: ["OPPO推送", "No static method", "isSupportPush", "版本兼容", "崩溃"]
created: 2025-05-12
updated: 2025-03-20
---

## 问题：Android OPPO推送SDK版本不兼容导致No static method异常

## 问题详情

**现象**：
Android线上出现崩溃异常：No static method isSupportPush()Z in class Lcom/heytap/msp/push/HeytapPushManager。当前使用NIM SDK 8.7.0，OPPO推送SDK版本为3.4.0。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Android

## 排查过程

1. 客户反馈线上出现OPPO推送相关崩溃 → 技术支持判断为SDK版本不匹配
2. 客户确认使用com.assist-v3:oppo:3.4.0和NIM SDK 8.7.0 → 技术支持指出8.7.0适配的是OPPO推送2.1.0
3. 提供两种解决方案：降级OPPO推送SDK或升级NIM SDK

## 问题原因

NIM SDK 8.7.0与OPPO推送SDK 3.4.0版本不匹配，8.7.0仅适配OPPO推送2.1.0版本。

## 解决方案

两种解决方案：1）降级OPPO推送SDK到2.1.0版本；2）升级NIM SDK到9.16.0版本（已适配OPPO推送3.4.0）。

## 其他触发场景

