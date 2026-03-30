---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 登录鉴权
platform: Android
title: IM SDK登录后立即logout，登录流程异常如何处理？
root_cause: 登录登出调用时机不当，同一秒内重复操作
solution: 检查登录和登出的调用时机，避免同一秒内即登录又登出且重复登出
customers: ["FVIP-云信-上海抱朴"]
source: chat_history
tags: ["Android", "IM V9", "登录", "logout", "登录流程"]
created: 2025-12-02
updated: 2026-03-23
---

## 问题：Android IM SDK登录后立即logout，登录流程异常如何处理？

## 问题详情

**现象**：
Android IM SDK登录后立即logout，登录流程出现异常。

**环境信息**：
- 平台：Android

## 排查过程

1. 检查登录和登出的调用时机 → 发现同一秒内即登录又登出且重复登出

**关键发现**：登录和登出调用时机不当导致流程异常

## 问题原因

登录和登出的调用时机不当，同一秒内即登录又登出且重复登出，导致登录流程异常。

## 解决方案

检查登录和登出的调用时机，避免同一秒内即登录又登出且重复登出。建议按照最佳实践处理登录流程。

参考文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android

## 其他触发场景

