---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务器API推送
platform: Android
title: 服务器API下发P2P消息不触发推送通知
root_cause: ''
solution: 服务器API请求下发的消息默认就能触发通知栏，前提是：1. app本身在后台；2. setChattingAccount两个参数均为NONE。
customers:
  - 深圳对娱信息技术有限公司
source: chat_history
tags:
  - 服务器API
  - P2P消息
  - 推送通知
  - setChattingAccount
created: '2025-06-23'
updated: '2025-03-23'
---

## 问题：Android 服务器API下发P2P消息不触发推送通知

## 问题详情

**现象**：
通过服务器API下发的P2P消息（如招呼消息）没有触发推送通知，用户收不到通知栏提示。

## 解决方案

服务器API请求下发的消息默认就能触发通知栏，前提是：1. app本身在后台；2. setChattingAccount两个参数均为NONE。
