---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: FCM推送404 unregistered原因分析
root_cause: 推送token失效，设备每次安装后deviceid变化导致token失效
solution: token失效是正常现象，建议剔除404错误统计。用户重新登录应用后会自动上报最新token
customers: ["VIP云信-武汉量子千寻科技有限公司"]
source: chat_history
tags: ["FCM", "404", "unregistered", "推送", "token失效"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：FCM推送404 unregistered原因分析

## 问题详情

**现象**：
FCM推送大量返回404 unregistered错误，成功率低

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈FCM推送成功率仅8%
2. 分析发现大量404 unregistered错误
3. 确认是推送token失效导致
4. 原因包括用户卸载、重装、token变动等

## 根因分析

推送token失效，设备每次安装后deviceid变化导致token失效

## 解决方案

token失效是正常现象，建议剔除404错误统计。用户重新登录应用后会自动上报最新token

## 其他触发场景

（无）
