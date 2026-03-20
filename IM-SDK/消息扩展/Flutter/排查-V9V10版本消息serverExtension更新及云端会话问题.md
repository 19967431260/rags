---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息扩展
platform: Flutter
title: V9/V10版本消息serverExtension更新及云端会话问题
root_cause: V9不支持更新消息serverExtension，V10需要开通云端会话
solution: 1. V9只能更新本地扩展，V10支持更新serverExtension；2. 开通云端会话功能；3. 海外数据中心配置serverConfig；4. 接收方需通知发送方修改消息
customers: ["武汉石屋网络科技有限公司"]
source: chat_history
tags: ["V9", "V10", "serverExtension", "云端会话", "Flutter"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Flutter V9/V10版本消息serverExtension更新及云端会话问题

## 问题详情

**现象**：
客户咨询Flutter V9版本更新消息serverExtension问题，以及V10版本云端会话、消息已读状态、消息存储等相关问题。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. V9无法更新消息serverExtension
2. V10云端会话未开通导致报错191001
3. 海外数据中心需配置serverConfig
4. 接收方无法修改消息扩展

**关键发现**：

## 问题原因

V9不支持更新消息serverExtension，V10需要开通云端会话

## 解决方案

1. V9只能更新本地扩展，V10支持更新serverExtension；2. 开通云端会话功能；3. 海外数据中心配置serverConfig；4. 接收方需通知发送方修改消息

## 其他触发场景

