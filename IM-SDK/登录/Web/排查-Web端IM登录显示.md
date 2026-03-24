---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Web
title: Web端IM登录显示断开连接
root_cause: 实例未正确销毁，导致重复登录互踢
solution: 确保正确销毁实例后再登录，或在控制台开启多端登录配置
customers: ["河南新秀金文化传媒"]
source: chat_history
tags: ["登录", "断开", "Web", "实例销毁", "多端登录"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：Web Web端IM登录显示断开连接

## 问题详情

**现象**：
其他端未登录情况下，Web登录显示断开连接。

## 排查过程

1. 检查日志发现有多端登录通知
2. 确认实例未销毁导致重复登录
3. 建议检查销毁逻辑

## 问题原因

实例未正确销毁，导致重复登录互踢

## 解决方案

确保正确销毁实例后再登录，或在控制台开启多端登录配置

## 其他触发场景

