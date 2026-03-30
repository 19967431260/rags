---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: HarmonyOS
title: 鸿蒙端消息重发报错V2NIMError unknown error
root_cause: SDK代码问题，在10.7.1版本已修复。
solution: 升级到IM SDK 10.7.1版本，该问题已在该版本修复。
customers: ['联通在线信息科技有限公司']
source: chat_history
tags: ['HarmonyOS', '消息重发', 'V2NIMError', 'SDK版本', '10.7.1']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙端消息重发报错V2NIMError unknown error

## 问题详情

**现象**：
鸿蒙端使用原消息重发时返回报错V2NIMError: unknown error。

## 排查过程

1. 确认重发方式 → 客户直接使用原消息发送
2. 建议设置resend字段为true → 客户反馈接口参数中没有该字段
3. 获取日志分析 → 研发确认是代码问题

## 问题原因

SDK代码问题，在10.7.1版本已修复。

## 解决方案

升级到IM SDK 10.7.1版本，该问题已在该版本修复。

## 其他触发场景

（合并时在此处追加）
