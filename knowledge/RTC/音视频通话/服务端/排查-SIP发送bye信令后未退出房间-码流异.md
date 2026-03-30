---
track_type: 排查类
sub_type: 线上事故
product: RTC
feature: 音视频通话
platform: 服务端
title: SIP发送bye信令后未退出房间-码流异常
root_cause: c9设备发送异常264码流，sps解析参数异常导致媒体服务崩溃，信令无法正常处理
solution: 升级媒体服务版本增加异常码流保护。临时方案：发现异常后手动挂断房间。
customers: ['杭州华亭']
source: chat_history
tags: ['RTC', 'SIP', '264', 'sps', '码流异常', 'bye信令']
created: 2025-09-09
updated: 2026-03-25
---

## 问题：服务端 SIP发送bye信令后未退出房间-码流异常

## 问题详情

**现象**：
SIP端正常发送bye信令挂断，但服务器未收到，房间中仍显示两端在线。抓包显示bye通过新TCP连接发送。

## 解决方案

升级媒体服务版本增加异常码流保护。临时方案：发现异常后手动挂断房间。
