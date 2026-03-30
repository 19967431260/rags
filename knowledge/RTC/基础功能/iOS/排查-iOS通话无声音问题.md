---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 基础功能
platform: iOS
title: iOS通话无声音问题
root_cause: iOS系统API激活AVAudioSession失败，被更高优先级应用占用
solution: 确认后台是否有其他app使用audioSession，或正在系统通话中
customers:
  - 杭州知聊
source: chat_history
tags:
  - 无声音
  - iOS
  - AVAudioSession
  - 系统通话
  - 音频占用
created: '2025-06-17'
updated: '2026-03-23'
---

## 问题：iOS 通话无声音问题

## 问题详情

**现象**：
用户反馈通话没有声音

**环境信息**：
- 平台：iOS
- 时间：2025-06-17

## 排查过程

1. 分析客户端上报 → errorcode为40532
2. 查询错误码含义 → iOS系统API激活AVAudioSession失败
3. 分析原因 → 比SDK更高优先级的应用（如电话）在使用audioSession

**关键发现**：40532错误表示AVAudioSession被占用

## 问题原因

iOS系统API激活AVAudioSession失败，被更高优先级的应用占用，导致麦克风和扬声器失效

## 解决方案

1. 确认后台是否开启了其他app
2. 确认是否正在系统通话中
3. 结束其他占用音频的应用后重试
4. 检查音频会话配置
