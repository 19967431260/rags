---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 锁屏通话
platform: Android
title: Android锁屏后语音通话采集/进入房间异常
root_cause: 高版本Android系统对退后台继续采集敏感操作限制严格，需要开启前台服务。
solution: 1. 开启前台服务(Foreground Service)以支持锁屏后继续采集
2. 参考：https://developer.android.com/reference/android/app/Service
3. 锁屏后Activity onCreate受限是系统行为，建议用户交互解锁后选择接通或挂断
4. 监听远端麦克风状态使用onUserAudioStart/onUserAudioStop
customers: ["广州元沣"]
source: chat_history
tags: ["RTC", "锁屏", "前台服务", "Android", "采集", "onCreate"]
created: 2025-02-22
updated: 2026-03-20
---

## 问题：Android Android锁屏后语音通话采集/进入房间异常

## 问题详情

**现象**：
客户反馈Android设备锁屏后，语音通话本端采集不到声音，且无法进入房间，亮屏后才收到进入房间通知。

## 排查过程

1. 确认锁屏时能听到对方声音但本端采集不到
2. 确认锁屏后无法进入房间
3. 询问是否有前台服务
4. 开启前台服务后声音采集问题解决
5. 锁屏后Activity无法调用onCreate是系统限制

## 问题原因

高版本Android系统对退后台继续采集敏感操作限制严格，需要开启前台服务。

## 解决方案

1. 开启前台服务(Foreground Service)以支持锁屏后继续采集
2. 参考：https://developer.android.com/reference/android/app/Service
3. 锁屏后Activity onCreate受限是系统行为，建议用户交互解锁后选择接通或挂断
4. 监听远端麦克风状态使用onUserAudioStart/onUserAudioStop

## 其他触发场景

