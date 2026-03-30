---
track_type: "排查类"
sub_type: "使用问题"
product: "RTC"
feature: "音视频通话"
platform: "微信小程序"
title: "RTC通话端对端延迟很高"
root_cause: "医生端网络情况导致延迟达到9s，buffer排空较慢"
solution: "将应用调度改到BGP机房优化网络"
customers: ["北京汉医健康科技"]
source: "chat_history"
tags: ["RTC", "延迟", "BGP", "网络"]
created: "2025-09-23"
updated: "2026-03-20"
---

## 问题：微信小程序 RTC通话端对端延迟很高

## 问题详情

**现象**：
医生和患者端端对端延迟很高，房间ID：1349358888734661。

## 排查过程

1. 客户提供房间ID → 技术支持分析
2. 服务端研发排查 → 发现医生端网络延迟达到9s
3. 分析buffer排空 → 排空较慢导致延迟一直存在
4. 优化调度 → 将应用调度改到BGP机房

## 问题原因

医生端网络情况导致延迟达到9s，buffer排空较慢

## 解决方案

将应用调度改到BGP机房优化网络

## 其他触发场景
