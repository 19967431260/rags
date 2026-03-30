---
track_type: 排查类
sub_type: 功能异常
product: RTC
feature: 音视频通话
platform: Web
title: Web端打开摄像头失败-InvalidAccessError
root_cause: SDK版本问题或浏览器兼容性问题
solution: 升级到SDK 5.8.33版本
customers: ["SI云信-上海联通"]
source: chat_history
tags: ["Web", "摄像头", "InvalidAccessError", "setRemoteDescription"]
created: 2025-12-10
updated: 2026-03-23
---

## 问题：Web端打开摄像头失败-InvalidAccessError

## 问题详情

**现象**：
打开摄像头时出现错误：`InvalidAccessError Failed to execute 'setRemoteDescription' on 'RTCPeerConnection'`

**环境信息**：
- 产品：RTC
- 功能：音视频通话
- 平台：Web

## 排查过程

1. 收集浏览器版本信息
2. 确认SDK版本5.8.32
3. 研发分析中
4. 建议升级到5.8.33

**关键发现**：SDK版本问题或浏览器兼容性问题

## 问题原因

SDK版本问题或浏览器兼容性问题。

## 解决方案

升级到SDK 5.8.33版本。

## 其他触发场景

