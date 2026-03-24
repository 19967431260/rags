---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 自动登录
platform: HarmonyOS
title: 鸿蒙端自动登录能力及onAccountReady回调使用
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 鸿蒙端自动登录能力及onAccountReady回调使用

## 问题描述

客户咨询鸿蒙V10.8.0版本是否支持自动登录能力，以及如何在登录成功前读取本地数据库

## 解答

V10.8.0版本SDK内部会自动判断自动登录场景，无需单独调用自动登录接口。监听onAccountReady回调，在回调触发后即可调用本地数据库接口（如getConversationList），无需等待登录成功

## 标签

- 自动登录
- onAccountReady
- HarmonyOS
- V10.8.0
- 本地数据库

## 客户

- 顺丰科技

## 会话日期

2025-02-06
