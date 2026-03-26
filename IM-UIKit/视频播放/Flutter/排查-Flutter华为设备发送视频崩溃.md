---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 视频播放
platform: Flutter
title: Flutter华为设备发送视频崩溃(MediaCodecVideoRenderer)
root_cause: Flutter视频播放时Android端VideoPlayerController未指定platformViewType导致崩溃
solution: 在Android端初始化VideoPlayerController时添加viewType:VideoPlayerType.texture或platformViewType参数指定渲染方式。
customers: ["仁人数字化科技（山东）有限公司"]
source: chat_history
tags: ["Flutter", "华为", "视频崩溃", "MediaCodecVideoRenderer", "VideoPlayerController"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Flutter Flutter华为设备发送视频崩溃(MediaCodecVideoRenderer)

## 问题详情

**现象**：
Flutter华为设备发送视频崩溃，错误信息包含MediaCodecVideoRenderer。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter on 华为设备
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
MediaCodecVideoRenderer崩溃

## 排查过程

**关键发现**：Flutter视频播放时Android端VideoPlayerController未指定platformViewType导致崩溃

## 问题原因

Flutter视频播放时Android端VideoPlayerController未指定platformViewType导致崩溃

## 解决方案

在Android端初始化VideoPlayerController时添加viewType:VideoPlayerType.texture或platformViewType参数指定渲染方式。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
