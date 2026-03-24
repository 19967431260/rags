---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 微信小程序
platform: 微信小程序
title: 微信鸿蒙版小程序云信IM连接失败
root_cause: 微信对鸿蒙系统的兼容尚未完全做好，云信SDK只是调用微信小程序的API，底层兼容问题由微信决定
solution: 当前鸿蒙版微信无法正常使用云信IM功能。建议使用原生APP开发作为替代方案。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 微信鸿蒙版小程序云信IM连接失败

## 问题描述

在微信鸿蒙版小程序中使用云信IM SDK时出现连接失败的问题

## 问题背景

- 微信版本：v1.0.3
- 鸿蒙版本：HarmonyOS Next 5.0.0.126
- 设备：华为Mate 60 Pro

## 根因分析

微信对鸿蒙系统的兼容尚未完全做好，云信SDK只是调用微信小程序的API，底层兼容问题由微信决定

## 解决方案

当前鸿蒙版微信无法正常使用云信IM功能。建议使用原生APP开发作为替代方案。

## 标签

- 鸿蒙
- 微信小程序
- 连接失败
- 兼容性问题

## 客户

- FVIP-云信-上海抱朴

## 会话日期

2025-02-24
