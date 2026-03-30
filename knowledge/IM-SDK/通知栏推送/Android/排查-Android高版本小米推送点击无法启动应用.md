---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: Android高版本小米推送点击无法启动应用
root_cause: 高版本Android系统限制后台启动Activity，需要通过PendingIntent方式设置点击行为
solution: 发送消息时在payload中按小米要求设置点击行为和intentUri，参考小米官网文档配置
customers: ["顺丰科技"]
source: chat_history
tags: ["小米推送", "targetSdk34", "PendingIntent", "通知栏"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android高版本小米推送点击无法启动应用

## 问题详情

**现象**：
Android升级targetSdk到34后，小米推送6.0.1版本，点击通知栏消息无法启动应用，触发后台无法启动activity限制

**环境信息**：
- 平台：Android

## 根因分析

高版本Android系统限制后台启动Activity，需要通过PendingIntent方式设置点击行为

## 解决方案

发送消息时在payload中按小米要求设置点击行为和intentUri，参考小米官网文档配置

## 其他触发场景

（无）
