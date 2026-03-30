---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 数据库
platform: HarmonyOS
title: 鸿蒙SDK数据库SQL警告问题
root_cause: 华为SQL接口内部问题，只是warning级别，不影响正常使用。
solution: 1. 该warning不影响SDK正常使用；2. 建议升级到最新的鸿蒙SDK版本10.8.10提升整体稳定性；3. 1.4.0是beta版本，已不建议继续使用。
customers: ["智联招聘"]
source: chat_history
tags: ["鸿蒙", "HarmonyOS", "SQL警告", "nim_msg.db", "1.4.0-beta"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：鸿蒙SDK数据库SQL警告问题

## 问题详情

**现象**：
华为鸿蒙平台监控到SQL底层报警：WARNING(28) double-quoted string literal。SDK版本1.4.0-beta，nim_msg.db存在异常数据上报。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 确认使用的是华为提供的接口，没有自己写SQL语句
2. 该日志是华为自己的问题，只是一个warning
3. 确认不影响SDK正常使用

## 根因分析

华为SQL接口内部问题，只是warning级别，不影响正常使用。

## 解决方案

1. 该warning不影响SDK正常使用；2. 建议升级到最新的鸿蒙SDK版本10.8.10提升整体稳定性；3. 1.4.0是beta版本，已不建议继续使用。

## 其他触发场景

（无）
