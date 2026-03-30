---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送服务
platform: Android
title: NimService启动崩溃：SDK未初始化
root_cause: 客户开启了NimService自启动，子进程启动时未调用初始化方法，向主进程获取配置信息失败时SDK会自杀。
solution: 1. 关闭NimService自启动（推荐）；2. 如必须开启自启动，需改造初始化方法调用逻辑，确保子进程也能正确初始化。
customers: ["vivo-v消息"]
source: chat_history
tags: ["崩溃", "NimService", "SDK初始化", "自启动", "PushSelfKiller"]
created: 2025-02-05
updated: 2025-03-20
---

## 问题：Android NimService启动崩溃：SDK未初始化

## 问题详情

**现象**：
Android端监控检测到高频崩溃：java.lang.IllegalStateException: SDK not initialized。崩溃发生在NimService.onCreate，导致软件崩溃率升高十倍。客户已确保在Application.onCreate中调用SDK初始化。

**环境信息**：
- 平台：Android
- 功能：推送服务

**相关日志**：
java.lang.IllegalStateException: SDK not initialized

## 排查过程

1. 检查NimService自启动配置 → 客户反馈已关闭自启动
2. 确认初始化位置 → 确认在Application.onCreate中初始化
3. 分析崩溃堆栈 → 发现崩溃由PushSelfKiller.safeQuitPushProcess引起
4. 问题定位 → 开启自启动后子进程启动时未调用初始化，向主进程获取配置失败导致SDK自杀

**关键发现**：自启动导致子进程未初始化

## 问题原因

客户开启了NimService自启动，子进程启动时未调用初始化方法，向主进程获取配置信息失败时SDK会自杀。

## 解决方案

1. 关闭NimService自启动（推荐）；2. 如必须开启自启动，需改造初始化方法调用逻辑，确保子进程也能正确初始化。

## 其他触发场景
