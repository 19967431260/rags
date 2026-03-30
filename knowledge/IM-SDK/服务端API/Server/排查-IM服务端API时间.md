---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: Server
title: IM服务端API时间戳参数需使用UTC秒
root_cause: 时间戳参数需要使用秒级UTC时间，而非毫秒级
solution: curTime参数使用UTC时间取秒（10位数字），而不是毫秒（13位数字）
customers: ["黄岛区爱水龙五金商贸行"]
source: chat_history
tags: ["IM-SDK", "Server", "时间戳", "curTime", "API调用"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：Server IM服务端API时间戳参数需使用UTC秒

## 问题详情

**现象**：
调用IM服务端API时，curTime参数使用System.currentTimeMillis()获取的毫秒时间戳报错，需要确认时间戳格式。

## 排查过程

1. 客户使用System.currentTimeMillis()获取当前时间戳
2. API调用返回null
3. 确认需要使用UTC时间取秒，而不是毫秒

## 问题原因

时间戳参数需要使用秒级UTC时间，而非毫秒级

## 解决方案

curTime参数使用UTC时间取秒（10位数字），而不是毫秒（13位数字）

## 其他触发场景
- [Server] IM服务端API时间戳参数需使用UTC秒，来源：['黄岛区爱水龙五金商贸行']，2026-03-20
- [Server] IM服务端API时间戳参数需使用UTC秒，来源：['黄岛区爱水龙五金商贸行']，2026-03-20

