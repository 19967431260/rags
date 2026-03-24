---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: RTC频道
platform: iOS
title: NERoom unmuteMyAudio失败Not in rtc channel
root_cause: RTC频道状态同步问题，SDK端已加入但服务端状态未更新
solution: 已修复，确保joinRtcChannel完成后再调用unmuteMyAudio
customers: ["上海丁奇通教育科技"]
source: chat_history
tags: ["NERoom", "unmuteMyAudio", "RTC", "语聊房"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：iOS NERoom unmuteMyAudio失败Not in rtc channel

## 问题详情

**现象**：
语聊房调用流程login -> joinRoom -> joinChatRoom -> joinRtcChannel -> unmuteMyAudio，unmuteMyAudio报错Not in rtc channel。

## 排查过程

1. 分析日志 → isInRtcChannel: sdk=true service=false
2. 确认问题 → SDK已加入RTC频道但服务端状态未同步
3. 客户自行解决 → 已修复

## 问题原因

RTC频道状态同步问题，SDK端已加入但服务端状态未更新

## 解决方案

已修复，确保joinRtcChannel完成后再调用unmuteMyAudio

## 其他触发场景

