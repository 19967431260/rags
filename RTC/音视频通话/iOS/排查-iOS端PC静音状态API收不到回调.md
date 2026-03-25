---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: iOS
title: iOS端PC静音状态API收不到回调
root_cause: PC端使用adjustAudioRecordSignalVolume调整音量静音，该接口不会触发静音状态回调；只有muteLocalAudio接口会触发回调
solution: 静音场景建议使用muteLocalAudio接口，该接口不会操作音频硬件，仅控制网络音频数据发送，房间内其他用户会收到onNERtcEngineUser:audioMuted:回调
customers: ["深圳联友"]
source: chat_history
tags: ["muteLocalAudio", "adjustAudioRecordSignalVolume", "静音回调", "iOS", "PC互通"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS端PC静音状态API收不到回调

## 问题详情

**现象**：
iOS端无法收到PC端静音状态变更的回调通知，需要确认muteLocalAudio和adjustAudioRecordSignalVolume的区别

**环境信息**：
- 平台：iOS

## 排查过程

1. 检查PC端静音实现方式 → 发现PC端使用adjustAudioRecordSignalVolume而非enableLocalAudio
2. 确认回调触发机制 → 只有调用muteLocalAudio才会触发onNERtcEngineUser:audioMuted:回调
3. 建议替代方案 → 使用muteLocalAudio或音量设置为0

## 问题原因

PC端使用adjustAudioRecordSignalVolume调整音量静音，该接口不会触发静音状态回调；只有muteLocalAudio接口会触发回调

## 解决方案

静音场景建议使用muteLocalAudio接口，该接口不会操作音频硬件，仅控制网络音频数据发送，房间内其他用户会收到onNERtcEngineUser:audioMuted:回调

## 其他触发场景

（无）
