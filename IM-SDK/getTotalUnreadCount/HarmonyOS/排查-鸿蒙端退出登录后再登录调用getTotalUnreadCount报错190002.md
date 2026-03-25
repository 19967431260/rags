---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "getTotalUnreadCount"
platform: "HarmonyOS"
title: "鸿蒙端退出登录后再登录调用getTotalUnreadCount报错190002"
root_cause: "登录成功后数据同步未完成就调用getTotalUnreadCount接口"
solution: "需要等待onSyncFinished回调完成后再调用getTotalUnreadCount等相关接口，不要仅依赖loginstatus判断"
customers: ["智己"]
source: "chat_history"
tags: ["getTotalUnreadCount", "190002", "鸿蒙", "登录", "数据同步"]
created: "2025-09-29"
updated: "2026-03-20"
---

## 问题：HarmonyOS 鸿蒙端退出登录后再登录调用getTotalUnreadCount报错190002

## 问题详情

**现象**：
退出云信后再登录，调用nim.conversationService?.getTotalUnreadCount()报错code:190002, desc:illegal state

## 排查过程

1. 确认错误信息 → 190002 illegal state
2. 检查服务注册 → 确认注册的是云端会话服务
3. 分析调用时机 → 登录成功后立即调用，但数据未同步完成
4. 确定正确时机 → 需要等onSyncFinished回调后再调用
**关键发现**：登录成功后数据同步完成前调用接口导致

## 问题原因

登录成功后数据同步未完成就调用getTotalUnreadCount接口

## 解决方案

需要等待onSyncFinished回调完成后再调用getTotalUnreadCount等相关接口，不要仅依赖loginstatus判断

## 其他触发场景
