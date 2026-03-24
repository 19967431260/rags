---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音量控制
platform: iOS
title: RTC iOS adjustRecordingSignalVolume静音后未重置导致无声
root_cause: 调用adjustRecordingSignalVolume静音后，leaveChannel不会重置音量，保持上次的值。
solution: SDK内部控制逻辑，leaveChannel不会重置音量。建议在joinChannel后手动重置音量。SDK暂时不会修改此逻辑，因为其他客户可能已沿用此逻辑。
customers: ["知聊"]
source: chat_history
tags: ["RTC", "音量", "静音", "adjustRecordingSignalVolume", "iOS"]
created: 2025-02-21
updated: 2025-03-20
---

## 问题：iOS RTC iOS adjustRecordingSignalVolume静音后未重置导致无声

## 问题详情

**现象**：
iOS端视频通话中，用户听不到对方声音。调查发现调用adjustRecordingSignalVolume静音后，没有重置音量。

**环境信息**：
- 平台：iOS

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 查询通话记录
2. 分析API调用
3. 确认音量设置状态
4. 测试验证接口行为

**关键发现**：leaveChannel不会重置音量

## 问题原因

调用adjustRecordingSignalVolume静音后，leaveChannel不会重置音量，保持上次的值。

## 解决方案

SDK内部控制逻辑，leaveChannel不会重置音量。建议在joinChannel后手动重置音量。SDK暂时不会修改此逻辑，因为其他客户可能已沿用此逻辑。

## 其他触发场景
