---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: SEI消息
platform: Android
title: sendSEIMsg返回30004错误
root_cause: 纯音频包(nertc-audio)没有SEI能力
solution: 将com.netease.yunxin:nertc-audio:5.6.50替换为com.netease.yunxin:nertc:5.8.15(带视频的包)。iOS使用pod 'NERtcSDK', '~> 5.8.15'。
customers: ["微鲤命理寻真"]
source: chat_history
tags: ["SEI", "sendSEIMsg", "30004", "纯音频", "nertc"]
created: 2025-05-21
updated: 2025-03-20
---

## 问题：Android sendSEIMsg返回30004错误

## 问题详情

**现象**：
调用sendSEIMsg发送SEI消息返回30004错误，无法收到onRecvSEIMsg回调。使用com.netease.yunxin:nertc-audio:5.6.50版本。

## 排查过程

**关键发现**：纯音频包(nertc-audio)没有SEI能力

## 问题原因

纯音频包(nertc-audio)没有SEI能力

## 解决方案

将com.netease.yunxin:nertc-audio:5.6.50替换为com.netease.yunxin:nertc:5.8.15(带视频的包)。iOS使用pod 'NERtcSDK', '~> 5.8.15'。
