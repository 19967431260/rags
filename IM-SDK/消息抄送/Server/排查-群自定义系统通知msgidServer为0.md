---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息抄送
platform: Server
title: 群自定义系统通知msgidServer为0
root_cause: 发送群自定义系统通知时设置了不存离线，服务端没有入库操作，因此没有msgidServer。普通消息有存离线、存漫游、存云端等配置，只要有一个为true就会入库有id。
solution: 如需msgidServer，需要设置存离线或存漫游或存云端至少一个为true
customers: ['北京唐吉诃德科技有限公司']
source: chat_history
tags: ['消息抄送', 'msgidServer', '群自定义消息', '不存离线', 'CUSTOM_TEAM_MSG']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Server 群自定义系统通知msgidServer为0

## 问题详情

**现象**：
客户反馈群自定义消息类型CUSTOM_TEAM_MSG在消息抄送中msgidServer值为0，而单聊自定义消息有值。

## 排查过程

1. 确认消息类型 → 群自定义系统通知
2. 检查存储配置 → 发现设置了不存离线
3. 关键发现：不存离线的消息服务端不入库，因此没有msgidServer

## 问题原因

发送群自定义系统通知时设置了不存离线，服务端没有入库操作，因此没有msgidServer。普通消息有存离线、存漫游、存云端等配置，只要有一个为true就会入库有id。

## 解决方案

如需msgidServer，需要设置存离线或存漫游或存云端至少一个为true

## 其他触发场景

（合并时在此处追加）
