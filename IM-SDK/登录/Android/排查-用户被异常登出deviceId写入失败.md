---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: 用户被异常登出deviceId写入失败
root_cause: SDK生成的deviceId无法写入设备缓存，导致重连后被识别为新设备而踢出
solution: 建议用户卸载重装应用，让SDK重新生成deviceId并写入缓存。
customers: ["深圳富旅奇缘"]
source: chat_history
tags: ["登录", "deviceId", "被踢", "缓存", "多端登录"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：用户被异常登出deviceId写入失败

## 问题详情

**现象**：
用户没有多端登录，但被挤下线。

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈用户被异常登出
2. 提供accid和appkey查询
3. 分析发现SDK生成的deviceId无法写入设备缓存
4. 导致设备重连后被踢

## 根因分析

SDK生成的deviceId无法写入设备缓存，导致重连后被识别为新设备而踢出

## 解决方案

建议用户卸载重装应用，让SDK重新生成deviceId并写入缓存。

## 其他触发场景

（无）
