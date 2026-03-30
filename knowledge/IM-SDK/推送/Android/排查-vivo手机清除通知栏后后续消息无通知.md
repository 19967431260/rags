---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: vivo手机清除通知栏后后续消息无通知
root_cause: Google FCM推送token失效，返回404错误，导致推送失败
solution: FCM返回404表示应用实例已从FCM取消注册，所使用的令牌不再有效，需要使用新令牌重新获取。建议检查Firebase token更新机制，确保token有效。
customers: ["时间在线"]
source: chat_history
tags: ["vivo", "推送", "FCM", "404", "token失效", "通知栏"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：vivo手机清除通知栏后后续消息无通知

## 问题详情

**现象**：
vivo手机应用后台情况下，通知栏能正常收到云信消息通知，但在系统通知栏清除一次后，后续发送的消息就没有通知显示了。

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈vivo手机清除通知后后续消息无推送
2. 客户提供消息ID和日志
3. 分析日志发现Google FCM返回404错误
4. 确认是推送token失效导致

## 根因分析

Google FCM推送token失效，返回404错误，导致推送失败

## 解决方案

FCM返回404表示应用实例已从FCM取消注册，所使用的令牌不再有效，需要使用新令牌重新获取。建议检查Firebase token更新机制，确保token有效。

## 其他触发场景

（无）
