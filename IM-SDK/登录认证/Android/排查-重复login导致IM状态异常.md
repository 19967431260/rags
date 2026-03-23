---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录认证
platform: Android
title: 重复login导致IM状态异常
root_cause: 业务层在监听到离线时自动调用login方法，导致重复登录
solution: 正常login只需在打开app时执行一次，SDK会自动重连；避免重复调用login
customers:
  - 海岛游
source: chat_history
tags:
  - 重复登录
  - Android
  - IM状态异常
  - 自动重连
created: '2025-06-10'
updated: '2025-03-23'
---

## 问题：Android 重复login导致IM状态异常

## 问题详情

**现象**：
用户反馈发不出消息，提示用户信息缺失。服务器日志显示用户一直在重复login，login过程中IM状态异常

**排查过程**：

1. 检查日志 → 服务器显示重复login
2. 分析原因 → 业务层自动调用login登录逻辑
3. 确认问题 → 重复login过程中IM状态异常，调用其他接口失败

**关键发现**：业务层在监听到离线时自动调用login方法，导致重复登录

## 问题原因

业务层在监听到离线时自动调用login方法，导致重复登录

## 解决方案

正常login只需在打开app时执行一次，SDK会自动重连；避免重复调用login
