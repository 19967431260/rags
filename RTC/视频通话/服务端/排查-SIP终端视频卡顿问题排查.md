---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频通话
platform: 服务端
title: SIP终端视频卡顿问题排查
root_cause: SIP设备RTP包payload type不匹配，且设备上行视频包偶尔丢失
solution: 需要检查SIP设备运行状态或SIP服务器转发是否正常，确保RTP包格式正确
customers: ['杭州华亭']
source: chat_history
tags: ['SIP', '视频卡顿', 'RTP', 'payload type', '视频通话']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：服务端 SIP终端视频卡顿问题排查

## 问题详情

**现象**：
SIP终端10671和安卓设备10672通话时，安卓设备看不到SIP终端画面，视频卡住。

## 排查过程

1. 确认音频互听正常，只有视频有问题
2. 分析发现SIP发的RTP包的payload type不对，SDP里带的是120，实际发的是102
3. 后续排查发现偶尔收不到SIP设备的上行视频包

## 问题原因

SIP设备RTP包payload type不匹配，且设备上行视频包偶尔丢失

## 解决方案

需要检查SIP设备运行状态或SIP服务器转发是否正常，确保RTP包格式正确

## 其他触发场景

（合并时在此处追加）
