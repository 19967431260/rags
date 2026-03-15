---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: iOS
title: iOS发送消息后收到重复的onSendMessage回调
root_cause: delegate被多次注册或消息发送逻辑存在重复调用
solution: 1. 确保delegate只注册一次；2. 检查消息发送逻辑，避免重复调用；3. 使用消息ID去重
customers: ["VIP云信-长沙奇喵宇宙网络科技有限公司"]
source: chat_history
tags: ["onSendMessage", "重复回调", "delegate", "iOS SDK"]
created: 2026-02-11
updated: 2026-03-15
---

## 问题：iOS iOS发送消息后收到重复的onSendMessage回调

## 问题详情

**现象**：
iOS端发送消息后，onSendMessage回调被触发两次，导致业务逻辑重复执行。

## 排查过程

1. 确认回调注册 → 检查是否多次注册了delegate
2. 检查消息发送逻辑 → 确认是否有重复发送
**关键发现**：可能存在多次注册delegate或消息重复发送的情况

## 问题原因

delegate被多次注册或消息发送逻辑存在重复调用

## 解决方案

1. 确保delegate只注册一次；2. 检查消息发送逻辑，避免重复调用；3. 使用消息ID去重
