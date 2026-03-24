---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间管理
platform: Server
title: 永久房+语聊房模板CLOSE_ROOM抄送异常
root_cause: 房间创建时设置为永久房+语聊房模板，永久房优先级更高导致NERoom房间未关闭，但RTC房间结束触发了抄送
solution: 永久房场景下不会触发房间关闭，抄送逻辑后续会优化。业务侧需根据房间实际状态判断
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['永久房', '语聊房', 'CLOSE_ROOM', '抄送', '生命周期']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Server 永久房+语聊房模板CLOSE_ROOM抄送异常

## 问题详情

**现象**：
房间设置为永久房并使用语聊房模板，所有用户退出后收到CLOSE_ROOM和USER_LEAVE_ROOM抄送，但房间实际未关闭，仍可进入。

## 排查过程

1. 确认房间模板设置
2. 检查房间是否为永久房
3. 分析抄送逻辑

## 问题原因

房间创建时设置为永久房+语聊房模板，永久房优先级更高导致NERoom房间未关闭，但RTC房间结束触发了抄送

## 解决方案

永久房场景下不会触发房间关闭，抄送逻辑后续会优化。业务侧需根据房间实际状态判断

## 其他触发场景

（合并时在此处追加）
