---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息发送
platform: Android
title: Android端发送消息JSON解析崩溃
root_cause: 发送消息时JSON中某字段传入了字符串"null"而非省略或传整型，SDK解析类型不匹配导致崩溃。
solution: 将该字段改为整型值或不包含该字段（SDK会自动补默认值），不要传字符串"null"。
customers: ["浙江闪铸集团有限公司", "珠海市纽带信息服务有限公司"]
source: chat_history
tags: ["JSON解析", "崩溃", "sendMessage", "Android"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：Android Android端发送消息JSON解析崩溃

## 问题详情

**现象**：
客户在Android端发送消息时崩溃，传入的JSON中某字段值为字符串"null"导致SDK解析失败。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供堆栈截图 → 支持判断为JSON解析问题
2. 支持要求客户提供完整传入消息JSON数据 → 获取完整数据
3. 支持发现字段值为字符串"null"而非省略该字段 → 定位根因
4. 支持建议将该字段改为整型或直接省略 → 提供解决方案

**关键发现**：JSON字段传入字符串"null"而非省略或传整型，SDK解析类型不匹配导致崩溃

## 问题原因

发送消息时JSON中某字段传入了字符串"null"而非省略或传整型，SDK解析类型不匹配导致崩溃。

## 解决方案

将该字段改为整型值或不包含该字段（SDK会自动补默认值），不要传字符串"null"。

## 其他触发场景

- [Android] Android端发送消息JSON解析崩溃，来源：珠海市纽带信息服务有限公司，2026-03-26
