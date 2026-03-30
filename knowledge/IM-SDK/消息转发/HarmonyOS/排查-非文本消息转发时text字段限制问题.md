---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息转发
platform: HarmonyOS
title: 非文本消息转发时text字段限制问题
root_cause: 非标准使用场景，消息时间戳维护可能存在问题
solution: 标准转发消息使用姿势：sendMessage(createForwardMessage(getMessageList))。确保使用SDK标准接口构造转发消息
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 非文本消息转发时text字段限制问题

## 问题描述

使用createForwardMessage转发图片消息时，偶尔报错提示非文本消息但text字段必须有值

## 问题背景

1. 确认客户使用createForwardMessage接口
2. 分析发现是收到的图片消息直接转发，消息本身text字段为undefined

## 根因分析

非标准使用场景，消息时间戳维护可能存在问题

## 解决方案

标准转发消息使用姿势：sendMessage(createForwardMessage(getMessageList))。确保使用SDK标准接口构造转发消息

## 标签

- 消息转发
- createForwardMessage
- text字段
- HarmonyOS

## 客户

- 顺丰科技

## 会话日期

2025-02-21
