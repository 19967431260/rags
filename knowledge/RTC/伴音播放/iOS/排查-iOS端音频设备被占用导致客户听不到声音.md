---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 伴音播放
platform: iOS
title: iOS端音频设备被占用导致客户听不到声音
root_cause: 
solution: 详见正文。
customers: ["平安银行"]
source: chat_history
tags: ["音频设备", "onAudioDeviceErr", "iOS", "设备占用", "-66637"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

通话过程中客户听不到理财经理声音，日志显示onAudioDeviceErr错误，deviceErr=12，hwErrCode=-66637。

## 排查过程

1. 客户反馈客户听不到理财经理声音 → 分析日志发现onAudioDeviceErr错误
2. 错误码分析：deviceType=3, deviceErr=12, hwErrCode=-66637 → 判断为音频设备被占用
3. 提供错误码说明文档

## 根因分析

iOS音频设备被其他应用占用，导致RTC无法打开音频设备

## 解决方案

搜索日志中的OnAudioDeviceWorkErr错误码，可通过onNERtcEngineAudioDeviceStateChange回调监听设备状态变化
