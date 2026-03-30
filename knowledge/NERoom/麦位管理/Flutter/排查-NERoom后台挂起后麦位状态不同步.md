---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 麦位管理
platform: Flutter
title: NERoom后台挂起后麦位状态不同步
root_cause: App进后台后手机系统限制网络进程，NERoom掉线，UI未刷新麦位状态
solution: 监听NERoom在线状态变更(roomConnectStateChanged)，在切回前台或网络变化时重新获取麦位列表并刷新UI
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['后台挂起', '麦位', '状态同步', '网络监听', 'Flutter']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Flutter NERoom后台挂起后麦位状态不同步

## 问题详情

**现象**：
App进入后台挂起一段时间后，其他用户看到该用户已退出房间和下麦，但该用户App仍显示在麦上。

## 排查过程

1. 确认后台网络限制
2. 检查NERoom连接状态
3. 分析麦位列表刷新逻辑

## 问题原因

App进后台后手机系统限制网络进程，NERoom掉线，UI未刷新麦位状态

## 解决方案

监听NERoom在线状态变更(roomConnectStateChanged)，在切回前台或网络变化时重新获取麦位列表并刷新UI

## 其他触发场景

（合并时在此处追加）
