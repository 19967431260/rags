---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 多端登录
platform: Web
title: onLoginPortsChange监听问题
root_cause: 第一次触发监听的长连接没断开，所以不会重复回调Android设备。
solution: 这是正常行为。长连接未断开时不会重复回调已在线的设备信息。
customers: ["融捷教育"]
source: chat_history
tags: ["onLoginPortsChange", "多端登录", "Web", "Android", "回调"]
created: 2025-06-20
updated: 2026-03-23
---

## 问题：Web onLoginPortsChange监听问题

## 问题详情

**现象**：
客户反馈安卓端在线时，web端登录onLoginPortsChange没有监听到安卓端在线；web端被挤下线后重新登录，该回调没有触发。

**环境信息**：
- 平台：Web, Android

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 复现问题并收集web端console日志
2. 分析日志发现SDK有触发监听
3. 确认问题：第一次web登录回调了Android设备多端登录，但web端长连接未断开，之后其他web端登录触发的onLoginPortsChange，不会重复回调Android设备

**关键发现**：第一次触发监听的长连接没断开，所以不会重复回调Android设备。

## 问题原因

第一次触发监听的长连接没断开，所以不会重复回调Android设备。

## 解决方案

这是正常行为。长连接未断开时不会重复回调已在线的设备信息。

## 其他触发场景

