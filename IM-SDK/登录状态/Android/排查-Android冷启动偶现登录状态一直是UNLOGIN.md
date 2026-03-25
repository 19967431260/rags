---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "登录状态"
platform: "Android"
title: "Android冷启动偶现登录状态一直是UNLOGIN"
root_cause: "待排查，需要复现时的日志"
solution: "一般登录成功后离线会自动重连，不需要主动login；重复登录第二次可能会报错；建议复现时获取完整日志分析"
customers: ["杭州晓宇"]
source: "chat_history"
tags: ["Android", "冷启动", "UNLOGIN", "登录状态", "自动重连"]
created: "2025-09-19"
updated: "2026-03-20"
---

## 问题：Android Android冷启动偶现登录状态一直是UNLOGIN

## 问题详情

**现象**：
Android客户端已登录情况下冷启动，会偶现不登录的情况，登录状态一直是UNLOGIN，第二次冷启动才登录成功

## 排查过程

1. 确认问题现象 → 偶现，冷启动后登录状态为UNLOGIN
2. 获取日志 → 日志被清理，无法获取问题发生时的日志
3. 分析自动重连机制 → 登录成功后离线会自动重连
4. 确认兜底方案 → 不建议主动调用login重试
**关键发现**：需要复现时日志才能定位具体原因

## 问题原因

待排查，需要复现时的日志

## 解决方案

一般登录成功后离线会自动重连，不需要主动login；重复登录第二次可能会报错；建议复现时获取完整日志分析

## 其他触发场景
