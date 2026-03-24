---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 直播
platform: iOS
title: getLiveInfo获取userUuidList为空
root_cause: userUuidList参数目前为空，不建议依赖此参数
solution: 不建议使用userUuidList，应在onMemberJoinRtcChannel回调中订阅其他用户的视频流
customers: ["上海丁奇通教育科技"]
source: chat_history
tags: ["getLiveInfo", "userUuidList", "直播", "订阅"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：iOS getLiveInfo获取userUuidList为空

## 问题详情

**现象**：
iOS端获取直播信息时userUuidList为空，但房间内有用户在推流。

## 排查过程

1. 确认房间状态 → 有用户在推流
2. 分析参数来源 → userUuidList是startLive时传入的参数
3. 确认问题 → 该参数目前确实为空
4. 提供替代方案 → 使用onMemberJoinRtcChannel回调订阅

## 问题原因

userUuidList参数目前为空，不建议依赖此参数

## 解决方案

不建议使用userUuidList，应在onMemberJoinRtcChannel回调中订阅其他用户的视频流

## 其他触发场景

