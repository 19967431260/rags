---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息查询
platform: Windows
title: getMessageListByIds无法查询已撤回消息
root_cause: V10接口设计限制，默认过滤已撤回消息
solution: 使用撤回通知中的消息内容，或通过其他方式缓存被撤回消息
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["消息查询", "撤回消息", "getMessageListByIds", "V10"]
created: 2025-10-31
updated: 2026-03-20
---

## 问题：Windows getMessageListByIds无法查询已撤回消息

## 问题详情

**现象**：
使用getMessageListByIds接口查询被撤回的消息，返回结果为空。V9版本的QueryMsgByIDAysnc可以查到。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认查询的消息类型 → 被撤回的消息
2. 对比V9和V10接口差异
**关键发现**：V10 getMessageListByIds不支持查询已删除/已撤回消息

**关键发现**：

## 问题原因

V10接口设计限制，默认过滤已撤回消息

## 解决方案

使用撤回通知中的消息内容，或通过其他方式缓存被撤回消息

## 其他触发场景

