---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Web
title: Web端录制的AAC语音在iOS无法播放
root_cause: iOS播放代码问题，非音频格式问题。云信语音URL本身正常
solution: 检查iOS端音频播放代码实现，使用正确的音频播放方式
customers: ['成都瑞安云科技股份有限公司']
source: chat_history
tags: ['AAC', '语音消息', 'iOS', 'Web', '音频播放']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Web Web端录制的AAC语音在iOS无法播放

## 问题详情

**现象**：
Web端自己写的音频录制功能，发送的语音在安卓能播放，但在苹果浏览器放不出声。使用uni.createInnerAudioContext()播放

## 排查过程

1. 检查语音URL格式
2. 确认iOS端播放代码
3. 验证云信URL本身正常，下载后重命名可播放

## 问题原因

iOS播放代码问题，非音频格式问题。云信语音URL本身正常

## 解决方案

检查iOS端音频播放代码实现，使用正确的音频播放方式

## 其他触发场景

（合并时在此处追加）
