---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 系统线程
platform: Android
title: ConnectivityThread线程高负载问题排查
root_cause: 使用ConnectivityManager.registerNetworkCallback注册网络状态回调时，回调中执行了占用性能的操作。
solution: 检查registerNetworkCallback的使用，避免在回调中执行耗时操作；负载过高时抓取CPU track日志分析具体原因。
customers: ["vivo-v消息"]
source: chat_history
tags: ["ConnectivityThread", "线程高负载", "CPU占用", "网络回调"]
created: 2025-06-03
updated: 2025-03-23
---

## 问题：Android ConnectivityThread线程高负载问题排查

## 问题详情

**现象**：
客户反馈线程高负载（ConnectivityThread），需要排查原因。

## 排查过程

1. 确认线程性质 → ConnectivityThread是系统线程，分发网络变化事件
2. 分析原因 → CPU占用过高可能是注册的网络状态回调里做了占用性能的操作
3. 排查建议 → 记录堆栈，查看负载过高时线程执行的方法，抓CPU track日志

**关键发现**：使用ConnectivityManager.registerNetworkCallback注册网络状态回调时，回调中执行了占用性能的操作

## 问题原因

使用ConnectivityManager.registerNetworkCallback注册网络状态回调时，回调中执行了占用性能的操作。

## 解决方案

检查registerNetworkCallback的使用，避免在回调中执行耗时操作；负载过高时抓取CPU track日志分析具体原因。

## 其他触发场景

