---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 后台保活
platform: Android
title: Android 14后台消息接收问题
root_cause: Android 14系统对后台服务限制更严格，越高版本系统后台服务限制速度越快，导致IM连接被断开
solution: 接入厂商离线推送解决后台消息接收问题
customers: ['北京创新一号']
source: chat_history
tags: ['Android 14', '后台保活', 'observeReceiveMessage', '离线推送', '后台限制']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Android Android 14后台消息接收问题

## 问题详情

**现象**：
客户反馈Android 14系统上，App切到后台后observeReceiveMessage订阅不触发，回到前台才恢复。

## 排查过程

1. 检查是否为后台服务限制导致离线 → 确认日志显示离线时无日志输出，切前台后重新走登录流程
2. 判断为系统后台服务限制问题

## 问题原因

Android 14系统对后台服务限制更严格，越高版本系统后台服务限制速度越快，导致IM连接被断开

## 解决方案

接入厂商离线推送解决后台消息接收问题

## 其他触发场景

（合并时在此处追加）
