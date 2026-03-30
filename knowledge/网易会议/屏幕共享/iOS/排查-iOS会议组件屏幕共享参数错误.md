---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 屏幕共享
platform: iOS
title: iOS会议组件屏幕共享参数错误
root_cause: ""
solution: 需要按照文档实现流程配置屏幕共享：在苹果开发者平台创建App Groups，配置相关证书和标识符，添加Broadcast Upload Extension target，配置kAppGroup参数。使用NEMeetingKit 4.8.0版本，执行pod repo update更新依赖
customers: ["和仁"]
source: chat_history
tags: ["屏幕共享","iOS","参数错误","App Groups","Flutter"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：iOS iOS会议组件屏幕共享参数错误

## 问题详情

**现象**：
Flutter iOS端，会议视频语音聊天小窗口都正常，但共享屏幕报参数错误-1。

**环境信息**：
- 平台：Flutter iOS

**相关日志**：
startScreenShare: iosAppGroup=null
engine startScreenCapture error: -1 参数错误

## 排查过程

排查过程未在会话中详细记录。

**关键发现**：iosAppGroup参数为null导致参数错误

## 问题原因

根因未明确记录

## 解决方案

需要按照文档实现流程配置屏幕共享：在苹果开发者平台创建App Groups，配置相关证书和标识符，添加Broadcast Upload Extension target，配置kAppGroup参数。使用NEMeetingKit 4.8.0版本，执行pod repo update更新依赖。

## 其他触发场景

（暂无）
