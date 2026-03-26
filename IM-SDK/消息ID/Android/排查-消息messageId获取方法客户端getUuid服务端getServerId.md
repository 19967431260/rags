---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息ID
platform: Android
title: 消息messageId获取方法客户端getUuid服务端getServerId
root_cause: SDK中客户端消息ID字段名为uuid而非messageId，服务端消息ID另有字段
solution: Android SDK获取消息ID方法：客户端消息ID调用MessageObject.getUuid()；服务端消息ID调用getServerId()；两者均表示消息的唯一标识但来源不同
customers: ["南宁市懂卿科技有限公司"]
source: chat_history
tags: ["getUuid","getServerId","messageId","Android","消息ID"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Android 消息messageId获取方法客户端getUuid服务端getServerId

## 问题详情

**现象**：
客户询问SDK是否有方法获取消息的messageId，因为SDK没有暴露这个方法。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户询问如何获取messageId → 确认问题
2. 客服确认安卓消息对象的uuid即为客户端消息ID，调用getUuid即可 → 解答
3. 客户确认uuid和messageId是否匹配 → 确认
4. 客服明确：客户端消息id都是uuid，调用getUuid；服务端消息id用getServerId获取 → 完整解答

**关键发现**：SDK中客户端消息ID字段名为uuid而非messageId，服务端消息ID另有字段

## 问题原因

SDK中客户端消息ID字段名为uuid而非messageId，服务端消息ID另有字段。

## 解决方案

Android SDK获取消息ID方法：客户端消息ID调用MessageObject.getUuid()；服务端消息ID调用getServerId()；两者均表示消息的唯一标识但来源不同。

## 其他触发场景

（合并时在此处追加）
