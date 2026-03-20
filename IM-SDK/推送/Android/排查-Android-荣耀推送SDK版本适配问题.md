---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: 荣耀推送SDK版本适配问题
root_cause: 华为和荣耀推送分家，荣耀手机需要单独集成荣耀推送SDK
solution: 1. 集成荣耀推送SDK
2. 通过checkSupportHonorPush判断荣耀手机
3. 返回true时不执行华为推送初始化
customers: ["上海掌鑫聚芯信息科技有限公司"]
source: chat_history
tags: ["荣耀推送", "华为推送", "907135003", "Android"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Android 荣耀推送SDK版本适配问题

## 问题详情

**现象**：
荣耀手机收不到推送，日志显示错误907135003: client api invalid。华为和荣耀推送在新版本上分家。

**排查过程**：
1. 检查日志发现荣耀推送报错907135003
2. 确认华为和荣耀推送已分家
3. 需要单独集成荣耀推送SDK

## 问题原因

华为和荣耀推送分家，荣耀手机需要单独集成荣耀推送SDK

## 解决方案

1. 集成荣耀推送SDK
2. 通过checkSupportHonorPush判断荣耀手机
3. 返回true时不执行华为推送初始化
