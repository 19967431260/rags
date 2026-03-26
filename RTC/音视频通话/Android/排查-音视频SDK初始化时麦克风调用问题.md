---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频
platform: Android
title: 音视频SDK初始化时麦克风调用问题
root_cause: RTC SDK在joinchannel时会默认启用麦克风，与MediaPlayer播放铃声冲突
solution: 1.初始化之后马上enablelocalaudio为false；2.改成对方同意后再加入rtc房间；3.给MediaPlayer设置setAudioAttributes setLegacyStreamType属性
customers: ["VIP-云信-北京欣欣相照"]
source: chat_history
tags: ["RTC","麦克风","MediaPlayer","joinchannel","enablelocalaudio"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：Android 音视频SDK初始化时麦克风调用问题

## 问题详情

**现象**：
客户反馈使用MediaPlayer播放拨打和接通来电铃声时，因为调用了加入房间代码导致麦克风启动，铃声声音变小1-2秒然后正常

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服建议在joinchannel之前调用enablelocalaudio为false → 方案1
2. 建议客户尝试改成对方同意后再加入rtc房间 → 方案2
3. 建议给MediaPlayer设置setAudioAttributes setLegacyStreamType属性 → 方案3

**关键发现**：RTC SDK在joinchannel时会默认启用麦克风，与MediaPlayer播放铃声冲突

## 问题原因

RTC SDK在joinchannel时会默认启用麦克风，与MediaPlayer播放铃声冲突

## 解决方案

1. 初始化之后马上enablelocalaudio为false；2. 改成对方同意后再加入rtc房间；3. 给MediaPlayer设置setAudioAttributes setLegacyStreamType属性

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
