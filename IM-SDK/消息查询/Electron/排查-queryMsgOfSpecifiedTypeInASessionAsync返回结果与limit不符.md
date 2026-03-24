---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息查询
platform: Electron
title: queryMsgOfSpecifiedTypeInASessionAsync返回结果与limit不符
root_cause: SDK内部实现问题，返回的count字段与实际msglogs数组长度不一致
solution: 以实际msglogs.size为准，业务层做过滤限制。SDK后续版本会优化此问题
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# queryMsgOfSpecifiedTypeInASessionAsync返回结果与limit不符

## 问题描述

调用queryMsgOfSpecifiedTypeInASessionAsync接口查询消息，设置limit_count为100，但返回结果的count_和msglogs_数量不一致

## 问题背景

1. 确认问题复现
2. 分析SDK日志发现返回结果以msglogs为准

## 根因分析

SDK内部实现问题，返回的count字段与实际msglogs数组长度不一致

## 解决方案

以实际msglogs.size为准，业务层做过滤限制。SDK后续版本会优化此问题

## 标签

- 消息查询
- limit
- Electron
- queryMsgOfSpecifiedTypeInASessionAsync

## 客户

- 顺丰科技

## 会话日期

2025-02-20
