---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 信令
platform: HarmonyOS
title: 鸿蒙signallingService joinRoom后监听事件问题
root_cause: 
solution: joinRoom成功后事件监听可能有短暂延迟，属正常现象。如长时间未收到需检查网络连接。
customers: ['中讯邮电咨询设计院']
source: chat_history
tags: ['鸿蒙', '信令', 'joinRoom', 'onOnlineEvent']
created: 2025-09-05
updated: 2026-03-25
---

## 问题：HarmonyOS 鸿蒙signallingService joinRoom后监听事件问题

## 问题详情

**现象**：
signallingService.joinRoom()执行成功，但signallingService.on('onOnlineEvent')监听事件没有立即收到消息。

## 解决方案

joinRoom成功后事件监听可能有短暂延迟，属正常现象。如长时间未收到需检查网络连接。
