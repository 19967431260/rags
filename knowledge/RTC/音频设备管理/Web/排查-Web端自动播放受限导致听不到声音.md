---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频设备管理
platform: Web
title: Web端自动播放受限导致听不到声音
root_cause: 浏览器自动播放策略限制，部分手机浏览器需要用户交互后才能播放音频
solution: 监听受限回调，提示用户手动恢复音频。参考文档：https://doc.yunxin.163.com/nertc/guide/jM3NDE0NTI?platform=web
customers: ['江苏华招网信息技术有限公司']
source: chat_history
tags: ['自动播放', '音频', 'Web', '浏览器限制', '播放策略']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Web Web端自动播放受限导致听不到声音

## 问题详情

**现象**：
Web端音视频通话时，由于浏览器自动播放策略限制，用户可能听不到声音，需要手动恢复。

## 排查过程



## 问题原因

浏览器自动播放策略限制，部分手机浏览器需要用户交互后才能播放音频

## 解决方案

监听受限回调，提示用户手动恢复音频。参考文档：https://doc.yunxin.163.com/nertc/guide/jM3NDE0NTI?platform=web

## 其他触发场景

（合并时在此处追加）
