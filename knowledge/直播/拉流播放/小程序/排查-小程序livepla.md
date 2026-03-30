---
track_type: 排查类
sub_type: 使用问题
product: 直播
feature: 拉流播放
platform: 小程序
title: 小程序live-player拉流清晰度问题
root_cause: live-player是微信小程序官方组件，云信无法控制其拉流效果
solution: 用VLC等第三方工具拉流验证实际推流质量，确认推流端正常后，小程序端清晰度由微信live-player组件控制
customers: ["北京艺典"]
source: chat_history
tags: ["live-player", "清晰度", "微信小程序", "拉流"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：微信小程序 小程序live-player拉流清晰度问题

## 问题详情

**现象**：
客户反馈小程序端直播画面清晰度不如抖音和视频号，已设置1080P推流。

## 排查过程

1. 确认推流端设置 → 已设置为1080P
2. 建议用VLC拉流验证 → VLC拉流显示非常高清
**关键发现**：问题在小程序live-player组件端

## 问题原因

live-player是微信小程序官方组件，云信无法控制其拉流效果

## 解决方案

用VLC等第三方工具拉流验证实际推流质量，确认推流端正常后，小程序端清晰度由微信live-player组件控制

## 其他触发场景

