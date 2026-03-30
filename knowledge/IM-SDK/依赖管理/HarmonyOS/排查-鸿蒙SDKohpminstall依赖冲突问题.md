---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 依赖管理
platform: HarmonyOS
title: 鸿蒙SDK ohpm install依赖冲突问题
root_cause: ohpm高版本会校验依赖库冲突，因为nim/har有本地依赖也有远端依赖。
solution: 在顶层oh-package里面override依赖库。官方建议统一第三方库依赖方式。
customers: ["智联招聘"]
source: chat_history
tags: ["鸿蒙", "HarmonyOS", "ohpm", "依赖冲突", "base.har"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：鸿蒙SDK ohpm install依赖冲突问题

## 问题详情

**现象**：
升级鸿蒙SDK到10.8.10时，sync依赖报错：ENOENT: no such file or directory, stat '.../base.har'。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 确认官网仓库存在该包
2. 分析发现ohpm高版本会校验依赖库冲突
3. 因为nim/har有本地依赖也有远端依赖所以失败

## 根因分析

ohpm高版本会校验依赖库冲突，因为nim/har有本地依赖也有远端依赖。

## 解决方案

在顶层oh-package里面override依赖库。官方建议统一第三方库依赖方式。

## 其他触发场景

（无）
