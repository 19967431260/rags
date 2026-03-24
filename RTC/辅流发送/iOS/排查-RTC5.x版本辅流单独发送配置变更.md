---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 辅流发送
platform: iOS
title: RTC 5.x版本辅流单独发送配置变更
root_cause: RTC 5.x版本默认辅流单独发送，不需要再通过setParameters设置kNERtcKeyAudioMixSendEnabledWithoutMic等参数。设置这些参数反而会导致问题
solution: RTC 5.x版本（包括鸿蒙）默认辅流单独发送，无需配置setParameters。如果在4.6.x版本中设置了kNERtcKeyAudioMixSendEnabledWithoutMic（iOS）或KEY_AUDIOMIX_ENABLE_WITHOUT_MIC（Android），升级到5.x后需要移除这些配置。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# RTC 5.x版本辅流单独发送配置变更

## 问题描述

客户从RTC 4.6.x升级到5.7.0后，发现之前通过setParameters设置辅流发送不依赖主流的配置在5.x版本导致对端听不到伴音

## 问题背景

- 检查setParameters配置项，对比4.x和5.x版本的差异

## 根因分析

RTC 5.x版本默认辅流单独发送，不需要再通过setParameters设置kNERtcKeyAudioMixSendEnabledWithoutMic等参数。设置这些参数反而会导致问题

## 解决方案

RTC 5.x版本（包括鸿蒙）默认辅流单独发送，无需配置setParameters。如果在4.6.x版本中设置了kNERtcKeyAudioMixSendEnabledWithoutMic（iOS）或KEY_AUDIOMIX_ENABLE_WITHOUT_MIC（Android），升级到5.x后需要移除这些配置。

## 标签

- RTC
- 辅流
- 伴音
- 5.x
- setParameters
- 版本升级

## 客户

- G2-SVIPS云信-平安银行

## 会话日期

2025-02-08
