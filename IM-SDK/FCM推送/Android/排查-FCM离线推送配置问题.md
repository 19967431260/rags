---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: FCM推送
platform: Android
title: FCM离线推送配置问题
root_cause: 控制台未开启FCM推送优先，走到了vivo推送
solution: 在控制台开启FCM推送优先即可。配置路径：控制台 > 应用 > 推送配置 > 开启FCM推送优先。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# FCM离线推送配置问题

## 问题描述

Android端接入FCM离线推送，控制台日志显示未成功

## 问题背景

- nimSdkVersion = 8.9.12650
- firebase-messaging:23.0.0
- 登录成功后开启离线推送，但控制台显示未成功

## 根因分析

控制台未开启FCM推送优先，走到了vivo推送

## 解决方案

在控制台开启FCM推送优先即可。配置路径：控制台 > 应用 > 推送配置 > 开启FCM推送优先。

## 标签

- Android
- FCM
- 离线推送
- 推送配置

## 客户

- FVIP云信-时间在线-gj

## 会话日期

2025-02-12
