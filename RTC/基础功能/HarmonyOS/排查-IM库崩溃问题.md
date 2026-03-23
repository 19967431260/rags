---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 基础功能
platform: HarmonyOS
title: IM库崩溃问题排查
root_cause: ""
solution: "提供带符号的库进行复现，确认问题原因"
customers: ["SVIPS云信"]
source: chat_history
tags: []
created: 2025-06-04
updated: 2025-03-23
---

## 问题：HarmonyOS IM库崩溃问题排查

## 问题详情

**现象**：
客户请求研发重编一个带调试信息的IM库用于复现崩溃问题。

**环境信息**：
- 平台：HarmonyOS
- 问题必现

## 排查过程

1. 客户提供带符号的库 → 直接替换所有.so文件
2. 测试复现 → 需要多挂一段时间观察

## 问题原因

待研发确认具体崩溃原因

## 解决方案

1. 提供带符号的库给客户替换
2. 长时间挂机测试观察
3. 如正常则升级到最新版本

## 其他触发场景

