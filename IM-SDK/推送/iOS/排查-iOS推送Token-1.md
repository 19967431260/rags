---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS推送Token获取异常问题
root_cause: iOS端推送token获取或传递异常，导致token为全0。
solution: 检查iOS端推送token的获取方式和传递给云信的方式，确保正确获取APNs deviceToken并正确传递给SDK。
customers: ["小牛看房"]
source: chat_history
tags: ["iOS", "推送", "APNs", "token", "证书"]
created: 2025-02-24
updated: 2026-03-20
---

## 问题：iOS iOS推送Token获取异常问题

## 问题详情

**现象**：
客户iOS端证书配置正常但收不到推送，检查发现推送token为全0字符串。

## 排查过程

1. 客户反馈证书配置正常但收不到推送
2. 检查SDK日志发现推送token异常
3. 确认token为0000000000000000000000000000000000000000000000000000000000000000

## 问题原因

iOS端推送token获取或传递异常，导致token为全0。

## 解决方案

检查iOS端推送token的获取方式和传递给云信的方式，确保正确获取APNs deviceToken并正确传递给SDK。

## 其他触发场景

