---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Android
title: 请求服务器API接口时间戳不符错误
root_cause: 本地时间戳与服务器时间戳差距过大
solution: 检查本地设备时间与服务器时间是否同步，确保时间戳误差在允许范围内
customers: ["无锡农商"]
source: chat_history
tags: ["Android", "时间戳", "API", "错误"]
created: 2025-05-23
updated: 2025-03-20
---

## 问题：Android 请求服务器API接口时间戳不符错误

## 问题详情

**现象**：
安卓SDK请求服务器API接口时提示时间戳不符错误。

## 排查过程

**关键发现**：本地时间戳与服务器时间戳差距过大

## 问题原因

本地时间戳与服务器时间戳差距过大

## 解决方案

检查本地设备时间与服务器时间是否同步，确保时间戳误差在允许范围内
