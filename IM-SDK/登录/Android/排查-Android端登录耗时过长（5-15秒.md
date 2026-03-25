---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: Android端登录耗时过长（5-15秒）
root_cause: 设备后台服务限制导致云信子进程被系统杀死(signal 9)，SDK需要重新启动子进程造成登录延迟
solution: 检查设备是否开启了后台服务限制等设置；抓取完整logcat日志分析：1. adb logcat -c 清理日志 2. adb logcat > test.log 抓取日志 3. 设置SDKOption.consoleLogEnabled=true将SDK日志输出到logcat
customers: ['西安触手']
source: chat_history
tags: ['登录慢', 'signal 9', '子进程', 'Android', '后台限制']
created: 2025-09-29
updated: 2026-03-25
---

## 问题：Android Android端登录耗时过长（5-15秒）

## 问题详情

**现象**：
Android端APP启动后登录云信，耗时5-15秒才登录成功，iOS端正常。问题必现，每次打开APP都出现。设备包括三星和OPPO手机。

## 解决方案

检查设备是否开启了后台服务限制等设置；抓取完整logcat日志分析：1. adb logcat -c 清理日志 2. adb logcat > test.log 抓取日志 3. 设置SDKOption.consoleLogEnabled=true将SDK日志输出到logcat
