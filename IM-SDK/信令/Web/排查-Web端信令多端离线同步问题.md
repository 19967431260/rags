---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 信令
platform: Web
title: Web端信令多端离线同步问题
root_cause: V9版本Web端需要业务层主动调用signalingMarkMsgRead，默认autoMarkRead为true但Web端逻辑不同
solution: Web端收到INVITE事件时调用signalingMarkMsgRead标记已收到，msgid从Event中获取
customers: ["中讯邮电咨询设计院"]
source: chat_history
tags: ["signalingMarkMsgRead","多端同步","离线信令","Web"]
created: 2025-02-17
updated: 2025-03-20
---

## 问题：Web Web端信令多端离线同步问题

## 问题详情

**现象**：
Web端先收到信令被叫事件并拒绝后，Android端上线后仍能同步到被叫事件，导致重复收到来电邀请。

## 排查过程

1. 排查发现Web端autoMarkRead参数设置问题 → 定位参数
2. V9 SDK中Web端需要业务层主动调用signalingMarkMsgRead标记已收到 → 确认机制
3. 移动端内部已实现自动标记 → 对比差异

**关键发现**：V9版本Web端需要业务层主动调用signalingMarkMsgRead

## 问题原因

V9版本Web端需要业务层主动调用signalingMarkMsgRead，默认autoMarkRead为true但Web端逻辑不同。

## 解决方案

Web端收到INVITE事件时调用signalingMarkMsgRead标记已收到，msgid从Event中获取。

## 其他触发场景

