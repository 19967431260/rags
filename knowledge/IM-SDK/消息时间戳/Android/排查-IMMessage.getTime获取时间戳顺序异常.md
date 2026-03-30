---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息时间戳
platform: Android
title: IMMessage.getTime获取时间戳顺序异常
root_cause: 创建消息时getTime获取的是本地时间戳，非服务器时间。需在消息发送成功回调中获取服务器返回的时间戳。
solution: 消息创建时的时间戳是本地时间，要在消息发送成功的回调里获取服务器实际发送成功后的消息时间戳。
customers: ['北京四维云信']
source: chat_history
tags: ['时间戳', 'getTime', '自定义消息', 'Android', '本地时间']
created: 2025-01-01
updated: 2026-03-23
---

## 问题：Android IMMessage.getTime获取时间戳顺序异常

## 问题详情

**现象**：
客户创建两条自定义消息，先创建的消息getTime时间戳反而大于后创建的消息。

## 排查过程

1. 检查服务器消息时间戳确认顺序正确；2. 分析发现客户获取的是本地创建时间；3. 确认手机本地时间与北京时间偏差31秒。

## 问题原因

创建消息时getTime获取的是本地时间戳，非服务器时间。需在消息发送成功回调中获取服务器返回的时间戳。

## 解决方案

消息创建时的时间戳是本地时间，要在消息发送成功的回调里获取服务器实际发送成功后的消息时间戳。

## 其他触发场景

（合并时在此处追加）
