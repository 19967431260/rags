---
track_type: 排查类
sub_type: 功能异常
product: IM-UIKit
feature: 本地消息搜索
platform: HarmonyOS
title: not implemented
root_cause: 缺少@nimsdk/search库依赖
solution: 需要添加@nimsdk/search库依赖并执行ohpm install
customers: ["SVIP+云信-北京久幺幺"]
source: chat_history
tags: ["鸿蒙", "本地搜索", "search", "Method not implemented"]
created: 2025-12-15
updated: 2026-03-23
---

## 问题：鸿蒙本地消息搜索报错-Method not implemented

## 问题详情

**现象**：
鸿蒙平台调用searchLocalMessages报错：`V2NIMSearchServiceStub: Method 'search' not implemented`

**环境信息**：
- 产品：IM-UIKit
- 功能：本地消息搜索
- 平台：鸿蒙

## 排查过程

1. 确认错误是search库未引入
2. 建议添加@nimsdk/search库
3. 客户添加依赖后仍报错

**关键发现**：缺少@nimsdk/search库依赖

## 问题原因

缺少@nimsdk/search库依赖。

## 解决方案

需要添加@nimsdk/search库依赖并执行ohpm install。

## 其他触发场景

