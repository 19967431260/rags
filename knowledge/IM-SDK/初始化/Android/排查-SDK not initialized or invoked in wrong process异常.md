---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: SDK not initialized or invoked in wrong process异常
root_cause: SDK初始化不在主进程或调用在错误进程
solution: 确保NIMClient.init和NIMClient.initDelay都在主进程中执行，使用NIMUtil.isMainProcess(this)判断
customers: ['景群數位互動有限公司']
source: chat_history
tags: ['初始化', 'wrong process', '主进程', 'NIMClient.init', 'NIMClient.initDelay']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Android SDK not initialized or invoked in wrong process异常

## 问题详情

**现象**：
出现SDK not initialized or invoked in wrong process错误

## 排查过程



## 问题原因

SDK初始化不在主进程或调用在错误进程

## 解决方案

确保NIMClient.init和NIMClient.initDelay都在主进程中执行，使用NIMUtil.isMainProcess(this)判断

## 其他触发场景

（合并时在此处追加）
