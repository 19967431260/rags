---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送服务
platform: Android
title: FCM推送不携带发送方昵称
root_cause: sendNickname参数在FCM推送上无效果
solution: sendNickname在FCM推送上没效果，建议在pushContent里自己定义格式：昵称：文案。点对点消息默认title就是发送方昵称。
customers: ["海康华安"]
source: chat_history
tags: ["推送", "FCM", "昵称", "sendNickname", "pushContent"]
created: 2025-02-25
updated: 2026-03-20
---

## 问题：Android FCM推送不携带发送方昵称

## 问题详情

**现象**：
客户反馈推送消息没有携带发送方昵称，只配置了pushTitle。

## 排查过程

1. 客户查看配置发现sendNickname字段
2. 询问是否默认开启
3. 技术支持确认理论上不需要单独配置
4. 发现该参数在FCM推送上没效果

## 问题原因

sendNickname参数在FCM推送上无效果

## 解决方案

sendNickname在FCM推送上没效果，建议在pushContent里自己定义格式：昵称：文案。点对点消息默认title就是发送方昵称。

## 其他触发场景
- [Android] FCM推送不携带发送方昵称，来源：['海康华安']，2026-03-20

