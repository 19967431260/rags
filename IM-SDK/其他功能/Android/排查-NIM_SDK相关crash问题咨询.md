---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 其他功能
platform: Android
title: NIM SDK相关crash问题咨询
root_cause: 系统服务BoardServices在进程退出时的异常，不是云信SDK的问题
solution: 这是系统服务退出时的异常，用户应无感知。如果出现不多且没有用户反馈不需要处理
customers: ["FVIP云信-深圳享笑"]
source: chat_history
tags: ["crash", "BoardServices", "系统异常", "9.19.5"]
created: 2025-08-04
updated: 2025-03-25
---

## 问题：NIM SDK相关crash问题咨询

## 问题详情

**现象**：
发现有nimsdk相关的crash，SDK版本9.19.5

## 排查过程

1. 客服让客户提供SDK版本9.19.5 → 客服说去确认
2. 客户回复是bugly那边的原因 → 最近系统库在升级
3. 客服查看日志后确认 → 是系统的BoardServices服务退出，看起来是进程退出时的异常，用户应该无感知
4. 客服说如果出现不多且没有用户反馈不需要处理

**关键发现**：系统服务BoardServices在进程退出时的异常，不是云信SDK的问题

## 问题原因

系统服务BoardServices在进程退出时的异常，不是云信SDK的问题。

## 解决方案

这是系统服务退出时的异常，用户应无感知。如果出现不多且没有用户反馈不需要处理。

## 其他触发场景

- [Android] SDK升级后ANR和卡顿问题，来源：FVIP云信-深圳享笑，2025-03-25
