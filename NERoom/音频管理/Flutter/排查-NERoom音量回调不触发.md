---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 音频管理
platform: Flutter
title: NERoom音量回调不触发
root_cause: 未开启音量检测功能
solution: 调用enableAudioVolumeIndication接口设置为true，初始化组件sdk之后调用即可。远端走onRtcRemoteAudioVolumeIndication，本地走onRtcLocalAudioVolumeIndication。注意离开RTC房间后设置失效，重新加入需再次调用
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['音量回调', 'enableAudioVolumeIndication', '音频', 'Flutter']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Flutter NERoom音量回调不触发

## 问题详情

**现象**：
房间内的音量回调没有事件触发，无法获取用户音量。

## 排查过程



## 问题原因

未开启音量检测功能

## 解决方案

调用enableAudioVolumeIndication接口设置为true，初始化组件sdk之后调用即可。远端走onRtcRemoteAudioVolumeIndication，本地走onRtcLocalAudioVolumeIndication。注意离开RTC房间后设置失效，重新加入需再次调用

## 其他触发场景

（合并时在此处追加）
