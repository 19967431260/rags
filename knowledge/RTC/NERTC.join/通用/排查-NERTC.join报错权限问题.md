---
track_type: "排查类"
sub_type: "配置开通咨询"
product: "RTC"
feature: "NERTC.join"
platform: "通用"
title: "NERTC.join报错权限问题"
root_cause: "appkey未开通音视频功能，之前试用已过期"
solution: "联系技术支持开通appkey的音视频功能"
customers: ["政采云"]
source: "chat_history"
tags: ["NERTC.join", "权限", "appkey", "音视频功能"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：通用 NERTC.join报错权限问题

## 问题详情

**现象**：
调用NERTC.join方法报错，经排查为appkey未开通音视频功能

## 排查过程

1. 查看报错截图 → 确认是权限问题
2. 检查appkey配置 → 发现未开通音视频功能
3. 确认状态 → 之前试用已过期
**关键发现**：appkey音视频功能未开通

## 问题原因

appkey未开通音视频功能，之前试用已过期

## 解决方案

联系技术支持开通appkey的音视频功能

## 其他触发场景
