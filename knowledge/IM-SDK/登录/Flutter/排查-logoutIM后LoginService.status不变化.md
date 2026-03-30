---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Flutter
title: logoutIM后LoginService.status不变化
root_cause: 监听LoginService.loginStatus的方式不正确，应使用正确的监听回调方式
solution: 使用getIt<LoginService>().loginStatus?.listen((status) {})方式监听登录状态变化
customers: ["优合集团有限公司"]
source: chat_history
tags: ["Flutter", "logoutIM", "LoginService", "登录状态"]
created: 2025-06-23
updated: 2026-03-23
---

## 问题：Flutter logoutIM后LoginService.status不变化

## 问题详情

**现象**：
调用退出登录logoutIM()后，LoginService.status状态没有发生变化，但logoutIM()返回成功。

**环境信息**：
- SDK版本：nim_core:1.8.3
- 平台：Android/Flutter

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认SDK版本(nim_core:1.8.3)和平台(Android/Flutter)
2. 检查监听代码写法 → 发现监听方式不正确

**关键发现**：监听LoginService.loginStatus的方式不正确，应使用正确的监听回调方式

## 问题原因

监听LoginService.loginStatus的方式不正确，应使用正确的监听回调方式

## 解决方案

使用getIt<LoginService>().loginStatus?.listen((status) {})方式监听登录状态变化

## 其他触发场景

