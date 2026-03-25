---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: SIP网关
platform: Server
title: SIP呼叫RTC远端画面混流问题
root_cause: 个别SIP节点thruster版本未回退到正确版本导致混流
solution: 检查并确保所有SIP节点thruster版本回退到正确版本（81为混流版本，82为非混流版本）
customers: ["杭州华亭"]
source: chat_history
tags: ["SIP", "RTC", "混流", "thruster", "版本"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：SIP呼叫RTC远端画面混流问题

## 问题详情

**现象**：
SIP呼叫RTC时出现远端画面混流，本端画面和远端画面重叠显示

**环境信息**：
- 平台：服务端

## 排查过程

1. 确认问题现象 → SIP端看到本端和远端画面混流
2. 检查引擎版本 → 确认thruster版本是否回退
3. 分析日志 → 检查SIP信令和媒体转发
4. 确认问题原因 → 个别节点版本未回退导致

## 问题原因

个别SIP节点thruster版本未回退到正确版本导致混流

## 解决方案

检查并确保所有SIP节点thruster版本回退到正确版本（81为混流版本，82为非混流版本）

## 其他触发场景

（无）
