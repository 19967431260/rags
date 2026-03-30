---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "Android"
title: "VIVO推送被分类为营销消息导致收不到"
root_cause: "未配置vivo推送的私信分类，消息被默认分类为营销消息。"
solution: "需要在控制台或发消息时配置vivoField的私信分类。申请并配置私信分类后，消息会被正确分类为私信消息，可以正常收到推送。"
customers: ["FVIP云信-深圳享笑"]
source: "chat_history"
tags: ["VIVO", "离线推送", "营销消息", "私信分类", "vivoField"]
created: "2025-09-03"
updated: "2026-03-20"
---

## 问题：Android VIVO推送被分类为营销消息导致收不到

## 问题详情

**现象**：
VIVO推送消息被定义为营销消息而非私信消息，导致用户收不到推送。

## 排查过程

1. 客户提供vivo推送日志
2. 检查发现消息被分类为营销消息
3. 确认控制台和发消息时vivoField未配置私信分类

## 问题原因

未配置vivo推送的私信分类，消息被默认分类为营销消息。

## 解决方案

需要在控制台或发消息时配置vivoField的私信分类。申请并配置私信分类后，消息会被正确分类为私信消息，可以正常收到推送。

## 其他触发场景
