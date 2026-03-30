---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Web
title: Web端NERoom进出房回调异常
root_cause: 使用直播模式导致透传字段超限，网络问题导致消息乱序
solution: 使用通信模式而非直播模式，网络恢复时从业务服务器重新获取房间状态
customers: ["河南新秀金文化传媒"]
source: chat_history
tags: ["NERoom", "进出房", "回调", "直播模式", "通信模式"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：Web Web端NERoom进出房回调异常

## 问题详情

**现象**：
app进房web没有触发onMemberJoinRoom，app退出时反而触发进房事件。

## 排查过程

1. 确认使用直播模式导致问题
2. 网络原因导致消息接收不连续
3. 服务端同步消息后一次性触发回调

## 问题原因

使用直播模式导致透传字段超限，网络问题导致消息乱序

## 解决方案

使用通信模式而非直播模式，网络恢复时从业务服务器重新获取房间状态

## 其他触发场景
- [Web] Web端NERoom进出房回调异常，来源：['河南新秀金文化传媒']，2026-03-20
- [Web] Web端NERoom进出房回调异常，来源：['河南新秀金文化传媒']，2026-03-20

