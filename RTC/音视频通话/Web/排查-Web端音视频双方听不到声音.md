---
track_type: 排查类
sub_type: 功能异常
product: RTC
feature: 音视频通话
platform: Web
title: Web端音视频双方听不到声音
root_cause: 播放对端音频流时默认配置audio为false，导致本地不播放对端音频流
solution: 检查play接口的audio配置，确保订阅音频流时audio设置为true；使用localStream.muteAudio或close接口控制本地音频
customers: ["SI云信-上海联通"]
source: chat_history
tags: ["Web", "音视频", "无声", "audio配置", "私有化"]
created: 2025-12-02
updated: 2026-03-23
---

## 问题：Web端音视频双方听不到声音

## 问题详情

**现象**：
私有化部署的音视频通话，双方听不到对方声音。点击解除静音时报错，初始化时未开启音频。

**环境信息**：
- 产品：RTC
- 功能：音视频通话
- 平台：Web

## 排查过程

1. 检查浏览器权限
2. 分析日志发现createStream时audio为true
3. 检查play逻辑
4. 发现默认配置audio为false导致不播放对端音频流

**关键发现**：播放对端音频流时默认配置audio为false

## 问题原因

播放对端音频流时默认配置audio为false，导致本地不播放对端音频流。

## 解决方案

1. 检查play接口的audio配置，确保订阅音频流时audio设置为true
2. 使用localStream.muteAudio或close接口控制本地音频

## 其他触发场景

