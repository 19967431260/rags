---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 基础功能
platform: HarmonyOS
title: SDK版本升级咨询
root_cause: ""
solution: "版本都是向下兼容的，直接升级到最新版本即可"
customers: ["SVIPS云信"]
source: chat_history
tags: []
created: 2025-06-04
updated: 2025-03-23
---

## 问题：HarmonyOS SDK版本升级咨询

## 问题详情

**现象**：
客户测试3小时正常，希望确定正常后再出9.16版本复现确认。担心新版本跨度太大有其他未知问题。

**环境信息**：
- 当前测试版本：新版本
- 目标版本：9.16

## 排查过程

1. 新版本测试3小时 → 正常
2. 客户要求出9.16版本确认原因

## 问题原因

客户担心版本跨度大存在未知风险

## 解决方案

版本都是向下兼容的，不维护历史版本，直接升级到最新版本即可。每个版本都会做历史功能覆盖测试。

## 其他触发场景

