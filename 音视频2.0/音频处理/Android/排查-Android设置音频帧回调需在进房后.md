---
track_type: 排查类
sub_type: 使用问题
product: 音视频2.0
feature: 音频处理
platform: Android
title: Android设置音频帧回调需在进房后
root_cause: setAudioFrameObserver在joinchannel之前调用时，返回的音频帧数据为空；需要在进房成功（收到onJoinChannel回调）后再设置
solution: setAudioFrameObserver需要在进房成功后再调用才能获取有效音频帧数据；同时需要先调用setRecordingAudioFrameParameters配置音频采样参数。
customers: ["飞虎互动"]
source: chat_history
tags: ["Android", "音频帧", "setAudioFrameObserver", "进房后"]
created: 2025-07-01
updated: 2025-07-25
---

## 问题：Android Android设置音频帧回调需在进房后

## 问题详情

**现象**：

## 问题原因

setAudioFrameObserver在joinchannel之前调用时，返回的音频帧数据为空；需要在进房成功（收到onJoinChannel回调）后再设置

## 解决方案

setAudioFrameObserver需要在进房成功后再调用才能获取有效音频帧数据；同时需要先调用setRecordingAudioFrameParameters配置音频采样参数。
