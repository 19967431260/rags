---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 信令
platform: Web
title: Web端离线信令接收问题
root_cause: web端离线信令不会自动同步，需手动调用接口
solution: 监听signalingUnreadMessageSyncNotify事件，登录时手动调用signalingSync方法同步离线信令
customers: ["VIP云信-数字传递"]
source: chat_history
tags: ["信令", "离线消息", "signalingSync", "Web"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Web Web端离线信令接收问题

## 问题详情

**现象**：
Web端SDK发离线信令，app端登录可以接收到，但web端登录时收不到离线信令消息。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认在线状态 → web在线时可以收到
2. 分析回调 → 监听signalingNotify
3. 确认离线方案 → 需手动调用signalingSync
**关键发现**：web端需手动调用signalingSync获取离线信令

**关键发现**：

## 问题原因

web端离线信令不会自动同步，需手动调用接口

## 解决方案

监听signalingUnreadMessageSyncNotify事件，登录时手动调用signalingSync方法同步离线信令

## 其他触发场景

