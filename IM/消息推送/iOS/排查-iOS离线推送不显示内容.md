---
track_type: 排查类
sub_type: 使用问题
product: IM
feature: 消息推送
platform: iOS
title: iOS离线推送不显示内容
root_cause: 发送消息时未设置pushContent字段
solution: 在发送消息时设置NIMMessageSetting的apnsContent或apnsPayload字段，配置推送显示内容
customers: ['上海奇已科技']
source: chat_history
tags: ['APNS', 'iOS', 'pushContent', '离线推送']
created: 2026-01-05
updated: 2026-03-15
---

## 问题：iOS iOS离线推送不显示内容

## 问题详情

iOS端收到离线推送，但推送内容为空，只显示应用名称

## 排查过程

1. 检查推送证书配置 → 正常
2. 查看推送payload → 发现未设置pushContent
3. 确认推送配置 → 需要在发送消息时设置推送内容

## 问题原因

发送消息时未设置pushContent字段

## 解决方案

在发送消息时设置NIMMessageSetting的apnsContent或apnsPayload字段，配置推送显示内容
