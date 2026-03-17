---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: HarmonyOS
title: 重新打开app自动登录失败拉不到会话
root_cause: 多端登录冲突,用户被其他端踢下线
solution: 通过observeOnlineStatus监听在线状态变化,在被踢下线时提示用户重新登录。此为多端互踢的正常机制。
customers: ["北京创新一号"]
source: chat_history
tags: ["自动登录", "多端登录", "observeOnlineStatus", "被踢下线"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：HarmonyOS 重新打开app自动登录失败拉不到会话

## 问题详情

**现象**：
鸿蒙端重新打开app时自动登录失败,无法拉取会话列表。时间:2026-02-06 16:00左右,用户ID:10876458。已监听observeOnlineStatus。

## 排查过程

1. 检查日志(5_nim_sdk.log) → 发现多端登录被踢下线

**关键发现**:用户在打开app时恰好被其他端挤下线,导致登录失败

## 问题原因

多端登录冲突,用户被其他端踢下线

## 解决方案

通过observeOnlineStatus监听在线状态变化,在被踢下线时提示用户重新登录。此为多端互踢的正常机制。

## 其他触发场景

（暂无）
