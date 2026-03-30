---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Server
title: sendBatchMsg接口返回416 query too fast
root_cause: 客户在21秒内调用sendBatchMsg接口120次，已达到接口限频阈值
solution: 降低sendBatchMsg接口调用频率，或将批量消息分批发送以避免触发120次/分钟限频
customers: ["广州数九"]
source: chat_history
tags: ["416","sendBatchMsg","限频","query too fast"]
created: 2025-08-08
updated: 2025-08-08
---

## 问题：Server sendBatchMsg接口返回416 query too fast

## 问题详情

**现象**：
客户调用sendBatchMsg接口批量发消息，返回416错误码（query too fast）。发送方认为请求未超过120次/分钟限制。

**复现步骤**：
（无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：复现时间：2025-08-07 19:27:58，接口：https://api-outsea.netease.im/nimserver/msg/sendBatchMsg.action

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 技术支持查询日志 → 19:27:37.305至19:27:58.641之间已有120次调用同一个接口
2. 确认为客户端在短时间内高频调用导致触发限频

**关键发现**：客户在21秒内调用sendBatchMsg接口120次，已达到接口限频阈值。

## 问题原因

客户在21秒内调用sendBatchMsg接口120次，已达到接口限频阈值。

## 解决方案

降低sendBatchMsg接口调用频率，或将批量消息分批发送以避免触发120次/分钟限频。

## 其他触发场景

（合并时在此处追加）
