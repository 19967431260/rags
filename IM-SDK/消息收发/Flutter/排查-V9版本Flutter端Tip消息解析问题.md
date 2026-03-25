---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息收发
platform: Flutter
title: V9版本Flutter端Tip消息解析问题
root_cause: V9版本的Flutter端Tip消息(类型10)解析存在Bug，content字段无法正确获取消息内容
solution: 1. 升级到V10版本；2. 或使用自定义消息(类型100)替代Tip消息，将内容放在text字段中
customers: ["深圳市灵感起源科技有限公司"]
source: chat_history
tags: ["Tip消息","自定义消息","Flutter","V9","消息解析"]
created: 2025-05-09
updated: 2025-03-23
---

## 问题：Flutter V9版本Flutter端Tip消息解析问题

## 问题详情

**现象**：
后台发送提示消息(Tip消息)，内容放在body中，前端获取时content字段为null，无法正确解析消息内容。必现问题。

**环境信息**：
- SDK 版本：IM V9 Flutter
- 平台：Flutter

## 排查过程

1. 确认消息发送方式 → 后台发送Tip消息(类型10)，内容放在body字段
2. 确认前端获取结果 → Flutter端获取时content字段为null，无法显示消息内容
3. 对比其他端表现 → 其他端(iOS/Android/Web)正常解析，仅Flutter端有问题
4. 确认问题根因 → V9版本的Flutter端Tip消息解析存在Bug

**关键发现**：V9版本Flutter端对Tip消息的解析逻辑存在问题，content字段无法正确获取body中的内容

## 问题原因

V9版本的Flutter端Tip消息(类型10)解析存在Bug，导致content字段无法正确获取消息内容。这是V9版本Flutter端的已知问题，其他端正常。

## 解决方案

1. **方案一（推荐）**：升级到V10版本，该问题已修复
2. **方案二**：使用自定义消息(类型100)替代Tip消息(类型10)
   - 服务端发送自定义消息，将内容放在text字段中
   - Flutter端可以正常解析自定义消息的text字段

## 其他触发场景

