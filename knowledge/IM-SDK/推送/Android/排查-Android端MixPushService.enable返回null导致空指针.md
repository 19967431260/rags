---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: Android端MixPushService.enable返回null导致空指针
root_cause: Kotlin代码中enable()方法返回null，直接调用setCallback导致空指针
solution: 使用?.安全调用：NIMClient.getService(MixPushService::class.java)?.enable(false)?.setCallback，或改用Java代码实现
customers: ["北京久幺幺"]
source: chat_history
tags: ["MixPushService", "enable", "空指针", "Kotlin", "setCallback"]
created: 2025-05-27
updated: 2025-03-20
---

## 问题：Android Android端MixPushService.enable返回null导致空指针

## 问题详情

**现象**：
在Kotlin代码中调用NIMClient.getService(MixPushService::class.java).enable(false).setCallback时，enable方法返回null，导致调用setCallback时出现空指针异常。该问题在Java代码中正常，仅在Kotlin中出现。

## 排查过程

**关键发现**：Kotlin代码中enable()方法返回null，直接调用setCallback导致空指针

## 问题原因

Kotlin代码中enable()方法返回null，直接调用setCallback导致空指针

## 解决方案

使用?.安全调用：NIMClient.getService(MixPushService::class.java)?.enable(false)?.setCallback，或改用Java代码实现
