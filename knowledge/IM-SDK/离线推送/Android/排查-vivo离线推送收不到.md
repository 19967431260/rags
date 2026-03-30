---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: vivo离线推送收不到
root_cause: 需到vivo推送平台查询具体失败原因。
solution: 根据日志中的token(regid)和taskId到vivo推送平台查询推送状态和失败原因。
customers: ["杭州东方网升"]
source: chat_history
tags: ["vivo", "离线推送", "收不到", "推送平台"]
created: 2025-06-24
updated: 2026-03-23
---

## 问题：Android vivo离线推送收不到

## 问题详情

**现象**：
客户反馈vivo手机离线收不到推送通知，但服务器调用推送接口成功。

**环境信息**：
- 平台：vivo Android

**相关日志**：
- VIVO_PUSH_SUCCESS，推送请求成功

## 排查过程

1. 检查SDK日志：VIVO_PUSH_SUCCESS，推送请求成功
2. 提供regid和taskId给客户到vivo平台查询
3. 确认服务器侧调用正常

**关键发现**：需到vivo推送平台查询具体失败原因。

## 问题原因

需到vivo推送平台查询具体失败原因。

## 解决方案

根据日志中的token(regid)和taskId到vivo推送平台查询推送状态和失败原因。

## 其他触发场景

