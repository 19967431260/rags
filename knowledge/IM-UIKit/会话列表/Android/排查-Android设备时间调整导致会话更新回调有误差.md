---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Android
title: Android设备时间调整导致会话更新回调有误差
root_cause: 会话列表更新时机问题，发消息后马上更新，未等待消息状态变为成功
solution: 通过observeMsgStatus监听消息发送状态，成功后再去获取或更新会话。V10版本已修复，V9可从源码调整。
customers: ["广州启倬信息"]
source: chat_history
tags: ["Android", "ChatKit", "设备时间", "会话更新", "消息状态", "V9"]
created: 2025-05-22
updated: 2025-03-20
---

## 问题：Android Android设备时间调整导致会话更新回调有误差

## 问题详情

**现象**：
Android设备时间往前调2小时，自己发消息后，ConversationObserverRepo.registerSessionChangedObserver收到的会话更新回调会有一条消息的误差。

## 排查过程

**关键发现**：会话列表更新时机问题，发消息后马上更新，未等待消息状态变为成功

## 问题原因

会话列表更新时机问题，发消息后马上更新，未等待消息状态变为成功

## 解决方案

通过observeMsgStatus监听消息发送状态，成功后再去获取或更新会话。V10版本已修复，V9可从源码调整。
