---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Flutter
title: Flutter RTC未离开房间导致无法加入
root_cause: RTC房间未正确退出，Flutter热重载可能导致未完全退出房间
solution: 加入新房间前主动调用engine.leaveChannel()离开RTC房间，或杀掉App进程重开
customers: ['VIP云信-北京未来星图']
source: chat_history
tags: ['Flutter', 'RTC', 'leaveChannel', '房间未退出']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Flutter Flutter RTC未离开房间导致无法加入

## 问题详情

**现象**：
Flutter端RTC音视频通话后未正确离开房间，导致下次无法加入新房间。

## 排查过程

1. 客户反馈创建不了新房间。
2. 查询后台发现设备还在之前的房间内。
3. 建议调用leaveChannel离开房间或杀掉进程重开。
4. 客户页面退出但进程还在，需要主动调用RTC的leaveChannel。

## 问题原因

RTC房间未正确退出，Flutter热重载可能导致未完全退出房间

## 解决方案

加入新房间前主动调用engine.leaveChannel()离开RTC房间，或杀掉App进程重开

## 其他触发场景

（合并时在此处追加）
