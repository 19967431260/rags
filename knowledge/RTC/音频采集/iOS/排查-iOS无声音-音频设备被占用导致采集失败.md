---
track_type: 排查类
sub_type: 线上事故
product: RTC
feature: 音频采集
platform: iOS
title: iOS无声音-音频设备被占用导致采集失败
root_cause: 系统音频采集设备被其他应用占用或打开失败，SDK无法获取原始音频数据，导致发送音量为0。本端能播放是因为本地播放不依赖SDK发送。
solution: 1. 通过系统监听检测音频设备变化：[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(audioInputDeviceChanged:) name:AVAudioSessionRouteChangeNotification object:nil]
2. 当音频设备为空时，音量回调理论上为0或不回调
3. 设置kNERtcKeyAudioMixSendEnabledWithoutMic参数，使伴音不依赖主流音频采集
customers: ['平安银行']
source: chat_history
tags: ['无声音', '设备被占用', 'iOS', '音频采集', '伴音']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：iOS iOS无声音-音频设备被占用导致采集失败

## 问题详情

**现象**：
客户反馈生产环境出现无声音问题，理财经理侧话术播报过程中突然丢失声音。

## 排查过程

1. 客户提供录制文件和日志 → 客服发现QS上有数据但发送音量为0
2. 分析日志 → 发现系统采集设备回调为空，SDK编码没有原始音频
3. 确认根因 → 设备被占用导致打开失败
4. 提供检测方案 → 可通过系统监听AVAudioSessionRouteChangeNotification检测音频设备变化

## 问题原因

系统音频采集设备被其他应用占用或打开失败，SDK无法获取原始音频数据，导致发送音量为0。本端能播放是因为本地播放不依赖SDK发送。

## 解决方案

1. 通过系统监听检测音频设备变化：[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(audioInputDeviceChanged:) name:AVAudioSessionRouteChangeNotification object:nil]
2. 当音频设备为空时，音量回调理论上为0或不回调
3. 设置kNERtcKeyAudioMixSendEnabledWithoutMic参数，使伴音不依赖主流音频采集

## 其他触发场景

（合并时在此处追加）
