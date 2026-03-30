---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Android
title: NERoom上麦时音频多次调用导致漏音
root_cause: 麦位和音视频混用导致。handleSeatListItemChanged中调用开麦，同时同意上麦也调用开麦，造成重复调用。另外updateMemberProperty和mute/unmute混用
solution: 1. 麦位和音视频分开处理，handleSeatListItemChanged中不要处理开麦
2. 统一使用muteMyAudio/unmuteMyAudio，不要混用updateMemberProperty
3. 限制刚进直播间时的闭麦时机
customers: ['VIP云信-高途预见塔塔项目']
source: chat_history
tags: ['NERoom', '漏音', '上麦', '音频', 'handleSeatListItemChanged', 'muteMyAudio']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Android NERoom上麦时音频多次调用导致漏音

## 问题详情

**现象**：
主播刚开播立即关闭声音时出现漏音问题。进房间调用了多次打开音频的操作

## 排查过程

1. 检查日志发现进房间调用了3次打开音频操作
2. 确认业务逻辑：上麦时调用，更新麦位时也调用
3. 分析时序问题：进房操作后立即关闭麦克风可能存在时序问题
4. 定位到handleSeatListItemChanged回调中也调用了开麦
5. 发现unmuteMyAudio和updateMemberProperty混用问题

## 问题原因

麦位和音视频混用导致。handleSeatListItemChanged中调用开麦，同时同意上麦也调用开麦，造成重复调用。另外updateMemberProperty和mute/unmute混用

## 解决方案

1. 麦位和音视频分开处理，handleSeatListItemChanged中不要处理开麦
2. 统一使用muteMyAudio/unmuteMyAudio，不要混用updateMemberProperty
3. 限制刚进直播间时的闭麦时机

## 其他触发场景

（合并时在此处追加）
