---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 推流
platform: iOS
title: iOS 16小程序webview自己看不到本地视频
root_cause: 未调用play()方法播放本地视频流，可能是其他报错影响了代码执行。
solution: open采集后需要调用play()方法预览本地视频。检查是否有其他报错影响代码执行流程。
customers: ["银河视界"]
source: chat_history
tags: ["本地预览","play","iOS16","小程序"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：iOS iOS 16小程序webview自己看不到本地视频

## 问题详情

**现象**：
iOS 16系统在小程序webview中推流，自己看不到自己但别人能看到。控制台持续打印错误日志。

## 排查过程

1. 检查上报日志 → 发现用户多次加入离开房间
2. 分析操作记录 → 用户不停开关设备
3. 查找play调用 → 未发现播放本地视频的操作

**关键发现**：open只是采集、编码、发送，没有预览，预览需要调用play()方法

## 问题原因

未调用play()方法播放本地视频流，可能是其他报错影响了代码执行。

## 解决方案

open采集后需要调用play()方法预览本地视频。检查是否有其他报错影响代码执行流程。

## 其他触发场景

