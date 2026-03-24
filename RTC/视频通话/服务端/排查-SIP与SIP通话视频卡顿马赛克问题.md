---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频通话
platform: 服务端
title: SIP与SIP通话视频卡顿马赛克问题
root_cause: SIP设备RTP payload type不匹配，且服务器存在异常
solution: 需要检查SIP设备配置确保payload type一致，同时检查服务器网络状态
customers: ['杭州华亭']
source: chat_history
tags: ['SIP', '视频卡顿', '马赛克', 'payload type', '服务器']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：服务端 SIP与SIP通话视频卡顿马赛克问题

## 问题详情

**现象**：
SIP终端10670和10671通话时视频卡顿、马赛克。

## 排查过程

1. 确认音频正常，只有视频卡
2. 发现RTP包payload type不对，协商的是124，发的是120
3. 发现125.124.142.33服务器回包特别慢

## 问题原因

SIP设备RTP payload type不匹配，且服务器存在异常

## 解决方案

需要检查SIP设备配置确保payload type一致，同时检查服务器网络状态

## 其他触发场景

（合并时在此处追加）
