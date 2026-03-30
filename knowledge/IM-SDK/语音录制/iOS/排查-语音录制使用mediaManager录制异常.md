---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 语音录制
platform: iOS
title: 语音录制使用mediaManager录制异常
root_cause: AVPlayer设置rate倍数播放音频可能影响AudioSession，导致录制异常
solution: 需要排查具体哪块代码影响AudioSession，录制前设置恢复正常
customers: ["深圳市家家顺-乐有家"]
source: chat_history
tags: ["iOS", "语音录制", "mediaManager", "AudioSession"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：语音录制使用mediaManager录制异常

## 问题详情

**现象**：
使用mediaManager录制语音时出现异常，声音变成奇怪的效果，可能受外部参数影响。

**环境信息**：
- 平台：iOS

## 排查过程

1. 确认复现场景
2. 检查AVPlayer设置
3. 分析AudioSession影响

## 根因分析

AVPlayer设置rate倍数播放音频可能影响AudioSession，导致录制异常

## 解决方案

需要排查具体哪块代码影响AudioSession，录制前设置恢复正常

## 其他触发场景

（无）
