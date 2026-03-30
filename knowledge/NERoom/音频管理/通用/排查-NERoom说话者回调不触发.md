---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 音频管理
platform: 通用
title: NERoom说话者回调不触发
root_cause: 未开启enableAudioVolumeIndication参数导致说话者音量回调不触发。
solution: 将enableAudioVolumeIndication参数设置为true，开启音量指示回调。
customers: ['海南群云文化']
source: chat_history
tags: ['enableAudioVolumeIndication', '说话者回调', '音量指示', 'NERoom']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：通用 NERoom说话者回调不触发

## 问题详情

**现象**：
客户实现语音房功能时，谁在说话的回调无法执行到。

## 排查过程

1. 检查enableAudioVolumeIndication参数设置 → 2. 确认设置为true后解决

## 问题原因

未开启enableAudioVolumeIndication参数导致说话者音量回调不触发。

## 解决方案

将enableAudioVolumeIndication参数设置为true，开启音量指示回调。

## 其他触发场景

（合并时在此处追加）
