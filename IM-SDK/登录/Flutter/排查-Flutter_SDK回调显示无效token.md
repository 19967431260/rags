---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 登录
platform: Flutter
title: Flutter SDK回调显示无效token
root_cause: tokenProvider回调中返回了示例提示字符串，而不是实际的token字符串
solution: 需要将NimCore.instance.loginService.tokenProvider设置为返回实际token的异步函数，而不是返回示例中的提示字符串
customers: ["郑州晨宙信息科技有限公司"]
source: chat_history
tags: ["IM V10","Flutter","动态Token","登录认证"]
created: 2025-05-15
updated: 2025-03-23
---

## 问题：Flutter Flutter SDK回调显示无效token

## 问题详情

**现象**：
客户使用动态token登录时，SDK回调显示无效token。

**环境信息**：
- 平台：Flutter
- 功能：登录

## 排查过程

1. 确认问题现象 → SDK回调显示无效token
2. 检查tokenProvider实现 → 发现返回了示例提示字符串
3. 确认正确实现 → 需要返回实际的token字符串
4. 解决问题 → 修改tokenProvider实现

**关键发现**：tokenProvider回调中返回了示例提示字符串，而不是实际的token字符串

## 问题原因

tokenProvider回调中需要返回实际的token字符串，而不是返回示例中的提示字符串。

## 解决方案

需要将NimCore.instance.loginService.tokenProvider设置为返回实际token的异步函数。

## 其他触发场景

