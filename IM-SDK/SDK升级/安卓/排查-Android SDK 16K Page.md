---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK升级
platform: 安卓
title: Android SDK 16K Page Size对齐问题
root_cause: 9.15.0及之前版本的SDK未适配Android 16K Page Size要求
solution: 升级到9.20.15版本；所有com.netease.nimlib:xxx依赖需保持相同版本
customers: ['广州浪花']
source: chat_history
tags: ['16K', 'Page Size', 'SDK升级', '9.20.15', 'so对齐']
created: 2025-09-23
updated: 2026-03-25
---

## 问题：安卓 Android SDK 16K Page Size对齐问题

## 问题详情

**现象**：
Google检测9.15.0版本的so库有两个没有做16K对齐，需要升级适配版本解决。

## 解决方案

升级到9.20.15版本；所有com.netease.nimlib:xxx依赖需保持相同版本
