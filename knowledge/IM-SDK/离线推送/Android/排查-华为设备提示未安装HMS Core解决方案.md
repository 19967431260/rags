---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Android
title: 华为设备提示未安装HMS Core解决方案
root_cause: 部分华为/荣耀设备未安装华为移动服务框架(HMS Core)，或需要集成荣耀推送SDK
solution: 方案1：集成com.huawei.hms:hmscoreinstaller:6.7.0.300引导用户安装HMS Core；方案2：同时集成荣耀推送SDK com.hihonor.mcs:push:7.0.41.301适配荣耀设备
customers: ['北京圆心医疗']
source: chat_history
tags: ['华为推送', 'HMS Core', '荣耀推送', '离线推送', 'Android']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Android 华为设备提示未安装HMS Core解决方案

## 问题详情

**现象**：
客户集成华为推送SDK后，在部分设备上提示'您的设备未安装最新版本的HMS core'。

## 排查过程

1. 确认问题 → 华为设备提示缺少HMS Core
2. 分析原因 → 部分华为/荣耀设备未安装华为框架
3. 验证方案 → 集成hmscoreinstaller或集成荣耀推送

## 问题原因

部分华为/荣耀设备未安装华为移动服务框架(HMS Core)，或需要集成荣耀推送SDK

## 解决方案

方案1：集成com.huawei.hms:hmscoreinstaller:6.7.0.300引导用户安装HMS Core；方案2：同时集成荣耀推送SDK com.hihonor.mcs:push:7.0.41.301适配荣耀设备

## 其他触发场景

（合并时在此处追加）
