---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息同步
platform: HarmonyOS
title: 点通知启动APP消息列表无最新消息
root_cause: 点通知启动时APP数据未同步完成，直接跳消息页拉不到最新消息
solution: 监听onDataSync，在主数据同步完成后再调用getMessageList刷新UI
customers: ["好未来-yach"]
source: chat_history
tags: ["鸿蒙", "通知", "消息同步", "onDataSync", "getMessageList"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：点通知启动APP消息列表无最新消息

## 问题详情

**现象**：
点击通知拉起APP跳入消息列表页时，列表页没有显示最新消息，返回再点击会话才有。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 确认消息同步时机
2. 检查getMessageList调用时机
3. 监听onDataSync同步完成

## 根因分析

点通知启动时APP数据未同步完成，直接跳消息页拉不到最新消息

## 解决方案

监听onDataSync，在主数据同步完成后再调用getMessageList刷新UI

## 其他触发场景

（无）
