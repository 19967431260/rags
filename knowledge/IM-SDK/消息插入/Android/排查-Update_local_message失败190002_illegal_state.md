---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息插入
platform: Android
title: Update local message失败190002 illegal state
root_cause: Update local message失败190002 illegal state是因为消息状态不合法
solution: 确认消息状态是否允许更新，消息必须处于可更新状态才能调用更新接口。
customers: ["河南瓜虫网络科技有限公司"]
source: chat_history
tags: ["Update local message", "190002", "illegal state", "Android"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：Android Update local message失败190002 illegal state

## 问题详情

**现象**：
Update local message失败190002 illegal state。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
错误码190002：illegal state

## 排查过程

**关键发现**：Update local message失败190002 illegal state是因为消息状态不合法

## 问题原因

Update local message失败190002 illegal state是因为消息状态不合法

## 解决方案

确认消息状态是否允许更新，消息必须处于可更新状态才能调用更新接口。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
