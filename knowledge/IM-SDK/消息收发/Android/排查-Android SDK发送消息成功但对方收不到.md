---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: Android SDK发送消息成功但对方收不到
root_cause: 
solution: 需要提供发送方accid、接收方accid、消息发送时间，以便查询服务器日志确认消息是否到达服务器及是否下发给接收方。
customers: ["VIP云信-吉林易联众信息技术有限公司"]
source: chat_history
tags: ["消息收发", "Android", "消息未送达"]
created: 2026-02-25
updated: 2026-03-15
---

## 问题：Android Android SDK发送消息成功但对方收不到

## 问题详情

**现象**：
客户反馈Android SDK发送消息显示成功，但对方收不到消息。appkey: 4c6eb6e0b2e0e6b0b2e0e6b0b2e0e6b0

## 排查过程

1. 检查发送端日志 → 显示发送成功
2. 检查接收端是否在线 → 需确认
3. 检查服务器日志 → 需提供accid和消息时间

## 问题原因



## 解决方案

需要提供发送方accid、接收方accid、消息发送时间，以便查询服务器日志确认消息是否到达服务器及是否下发给接收方。
