---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 服务端API
platform: Server
title: IM服务端API调用返回414错误是什么原因？
root_cause: URI过长或Content-Type设置不正确
solution: 检查请求头中Content-Type是否正确设置
customers: ["FVIP云信-成都色差"]
source: chat_history
tags: ["IM V10", "服务端API", "414错误", "Content-Type"]
created: 2025-12-23
updated: 2026-03-23
---

## 问题：IM服务端API调用返回414错误是什么原因？

## 问题详情

**现象**：
调用IM服务端API时返回414错误。

**环境信息**：
- 产品：IM V10
- 平台：Server

## 排查过程

1. 检查请求URI长度 → 确认是否过长
2. 检查请求头Content-Type → 确认是否正确设置

**关键发现**：414错误通常表示URI过长或Content-Type设置不正确

## 问题原因

URI过长或Content-Type设置不正确导致请求失败。

## 解决方案

检查请求头中Content-Type是否正确设置。

## 其他触发场景

