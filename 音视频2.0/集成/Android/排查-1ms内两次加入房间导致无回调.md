---
track_type: 排查类
sub_type: 使用问题
product: 音视频2.0
feature: 集成
platform: Android
title: 1ms内两次调用加入房间导致onJoinChannel无回调
root_cause: 连续极短时间内两次调用joinChannel，第二次调用可能打断第一次的回调通知，导致onJoinChannel无回调；但实际加入可能成功
solution: 避免在1ms内连续调用joinChannel两次；加入房间应等待onJoinChannel回调返回后再进行后续操作；若出现无声问题，需检查SDK日志确认实际加入状态
customers: ["vivo-v消息"]
source: chat_history
tags: ["onJoinChannel", "两次加入房间", "无回调"]
created: 2025-07-14
updated: 2025-07-25
---

## 问题：1ms内两次调用加入房间导致onJoinChannel无回调

## 问题原因

连续极短时间内两次调用joinChannel，第二次调用可能打断第一次的回调通知，导致onJoinChannel无回调；但实际加入可能成功

## 解决方案

避免在1ms内连续调用joinChannel两次；加入房间应等待onJoinChannel回调返回后再进行后续操作；若出现无声问题，需检查SDK日志确认实际加入状态
