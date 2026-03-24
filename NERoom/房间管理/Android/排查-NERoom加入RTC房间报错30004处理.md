---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Android
title: NERoom加入RTC房间报错30004处理
root_cause: 客户离开页面时部分逻辑被销毁，但重复调用joinRtcChannel时出现30004错误。
solution: 客户自行优化页面生命周期管理，避免离开页面时错误销毁底层资源。
customers: ['海南群云文化']
source: chat_history
tags: ['30004', 'joinRtcChannel', 'NERoom', 'RTC房间']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Android NERoom加入RTC房间报错30004处理

## 问题详情

**现象**：
客户加入neroom后调用joinRtcChannel返回错误30004(Join channel error)，然后打开麦克风提示Not in rtc channel。服务端查询用户确实在RTC房间。

## 排查过程

1. 客户自行排查 → 2. 发现是离开页面时部分逻辑底层销毁导致 → 3. 需要优化页面生命周期管理

## 问题原因

客户离开页面时部分逻辑被销毁，但重复调用joinRtcChannel时出现30004错误。

## 解决方案

客户自行优化页面生命周期管理，避免离开页面时错误销毁底层资源。

## 其他触发场景

（合并时在此处追加）
