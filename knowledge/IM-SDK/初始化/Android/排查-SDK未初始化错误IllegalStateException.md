---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: SDK未初始化错误IllegalStateException
root_cause: 调用NIMClient.getService()等方法前未初始化IM SDK
solution: 确保在调用任何SDK方法前先调用初始化方法，初始化是同步的，调用一下即可不会阻塞
customers: ["云信+乐次元"]
source: chat_history
tags: ["初始化", "IllegalStateException", "SDK not initialized", "Android"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android SDK未初始化错误IllegalStateException

## 问题详情

**现象**：
Android端调用SDK方法时报错：java.lang.IllegalStateException: SDK not initialized or invoked in wrong process!

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程



**关键发现**：

## 问题原因

调用NIMClient.getService()等方法前未初始化IM SDK

## 解决方案

确保在调用任何SDK方法前先调用初始化方法，初始化是同步的，调用一下即可不会阻塞

## 其他触发场景

