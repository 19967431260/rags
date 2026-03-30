---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 屏幕共享
platform: Web
title: Web端屏幕共享默认选择整个屏幕
root_cause: SDK版本过低，forceDisplaySurface参数不支持
solution: 升级RTC SDK到5.6.50及以上版本，使用NERTC.getParameters().forceDisplaySurface = 'monitor'
customers: ["法正智能科技有限公司"]
source: chat_history
tags: ["屏幕共享", "forceDisplaySurface", "整个屏幕", "版本升级"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：Web Web端屏幕共享默认选择整个屏幕

## 问题详情

**现象**：
屏幕共享时默认弹出选择框，希望默认选中整个屏幕。

## 排查过程

1. 尝试使用NERTC.getParameters().forceDisplaySurface = 'monitor'
2. 发现旧版本不支持
3. 升级到5.6.50版本后解决

## 问题原因

SDK版本过低，forceDisplaySurface参数不支持

## 解决方案

升级RTC SDK到5.6.50及以上版本，使用NERTC.getParameters().forceDisplaySurface = 'monitor'

## 其他触发场景
- [Web] Web端屏幕共享默认选择整个屏幕，来源：['法正智能科技有限公司']，2026-03-20

