---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频处理/回声消除
platform: 安卓
title: TV端语音通话回声问题
root_cause: 电视型号差异和音频采集参数配置不当导致回声消除效果不佳
solution: 1. 调整服务器音频配置参数
2. 如需最佳效果建议提供特定电视型号进行适配测试
3. 或使用Java自定义音频采集：AudioSource.MIC, SAMPLE_RATE=16000, CHANNEL=2
customers: ['深圳康佳']
source: chat_history
tags: ['回声', '音频', 'setAudioProfile', 'TV', 'V660', '屏幕镜像']
created: 2025-09-25
updated: 2026-03-25
---

## 问题：安卓 TV端语音通话回声问题

## 问题详情

**现象**：
屏幕镜像+语音通话场景，TV端为发送端，接收端为Android手机或小程序，接收端听到明显回声。设备为康佳V660电视，SDK版本5.8.21-SNAPSHOT。

## 解决方案

1. 调整服务器音频配置参数
2. 如需最佳效果建议提供特定电视型号进行适配测试
3. 或使用Java自定义音频采集：AudioSource.MIC, SAMPLE_RATE=16000, CHANNEL=2
