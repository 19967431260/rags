---
track_type: 排查类
sub_type: 功能实现咨询
product: 其他
feature: 基础功能
platform: Android
title: 腾讯库API必须在主进程调用问题
root_cause: 腾讯库的API必须在主进程中调用
solution: 使用NIMUtil.isMainProcess进行进程判断
customers:
  - 深圳岚峰创视
source: chat_history
tags: []
created: 2025-06-24
updated: 2025-03-23
---

## 问题：腾讯库API必须在主进程调用问题

## 问题详情

**现象**：
应用中出现异常，经排查是腾讯的一个库的API调用问题。

## 问题原因

腾讯的库API必须在主进程中调用。

## 解决方案

使用NIMUtil.isMainProcess进行进程判断，确保在主进程中调用：
```java
if (NIMUtil.isMainProcess(context)) {
    // 调用腾讯库API
}
```

## 其他触发场景
