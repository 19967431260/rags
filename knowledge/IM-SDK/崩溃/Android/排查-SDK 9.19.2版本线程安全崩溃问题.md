---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 崩溃
platform: Android
title: SDK 9.19.2版本线程安全崩溃问题
root_cause: 9.19.2版本存在线程安全问题，发生在日志打印上，用户频繁切换网络时概率增大
solution: 升级到9.19.10版本解决，引入basesdk、chatroom、push三个依赖
customers: ["微鲤蘑菇语音"]
source: chat_history
tags: ["崩溃", "9.19.2", "线程安全", "升级"]
created: 2025-02-24
updated: 2025-03-20
---

## 问题：Android SDK 9.19.2版本线程安全崩溃问题

## 问题详情

**现象**：
Firebase上报崩溃，指向SDK。崩溃发生在日志打印相关代码，是线程安全问题。

**环境信息**：
- 平台：Android
- SDK版本：basesdk 9.19.2

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认SDK版本 → basesdk 9.19.2
2. 分析崩溃堆栈 → 线程安全问题，发生在日志打印

**关键发现**：9.19.2版本已知问题

## 问题原因

9.19.2版本存在线程安全问题，发生在日志打印上，用户频繁切换网络时概率增大。

## 解决方案

升级到9.19.10版本解决，引入basesdk、chatroom、push三个依赖。

## 其他触发场景
