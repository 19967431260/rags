---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: iOS
title: RTC用户开麦但无声音
root_cause: 应用将AudioSession改为AVAudioSessionCategorySoloAmbient导致采集无声
solution: 检查应用代码，避免在RTC通话期间将AudioSession改为SoloAmbient模式
customers: ['微鲤蘑菇语音']
source: chat_history
tags: ['RTC', '无声音', 'AudioSession', '采集']
created: 2025-01-24
updated: 2026-03-23
---

## 问题：iOS RTC用户开麦但无声音

## 问题详情

**现象**：
两个用户反馈RTC没有声音，听不到房间里其他人声音，自己开麦讲话也没声音

## 排查过程

1. 分析用户日志 → 336653在12:38:41-12:38:47开麦
2. 检查AudioSession状态 → 发现audiosession被改为AVAudioSessionCategorySoloAmbient
3. 分析532445日志 → 同样在开麦期间audiosession为AVAudioSessionCategorySoloAmbient
4. 检查房间其他用户 → 其他用户开麦时音量上报正常

## 问题原因

应用将AudioSession改为AVAudioSessionCategorySoloAmbient导致采集无声

## 解决方案

检查应用代码，避免在RTC通话期间将AudioSession改为SoloAmbient模式

## 其他触发场景

（合并时在此处追加）
