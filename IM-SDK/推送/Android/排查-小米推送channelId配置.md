---
track_type: 排查类
sub_type: 配置问题
product: IM-SDK
feature: 推送
platform: Android
title: 小米推送channelId配置
root_cause: 小米channelId未配置或配置不匹配。
solution: 需要在发送消息时在pushpayload中设置channelId，或在云信控制台配置。确认小米后台channelId已申请通过，客户端创建对应通知通道。
customers: ['爱聊伊恋']
source: chat_history
tags: ['小米推送', 'channelId', '推送', 'Android']
created: 2025-02-05
updated: 2026-03-23
---

## 问题：Android 小米推送channelId配置

## 问题详情

**现象**：
小米推送返回invalid channel info错误，消息无法收到推送。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

小米channelId未配置或配置不匹配。

## 解决方案

需要在发送消息时在pushpayload中设置channelId，或在云信控制台配置。确认小米后台channelId已申请通过，客户端创建对应通知通道。

## 其他触发场景

（合并时在此处追加：`- [Android] 小米推送channelId配置，来源：['爱聊伊恋']，2026-03-23`）
