---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 扩展字段
platform: Web
title: SetExt设置扩展字段Web端解析失败
root_cause: 数据格式包含转义字符，需要业务层处理
solution: 业务上需要处理转义，使用JSON.parse()去掉转义字符
customers: ["湖南腾速科技"]
source: chat_history
tags: ["SetExt", "扩展字段", "JSON", "转义", "Web"]
created: 2025-02-24
updated: 2026-03-20
---

## 问题：Web SetExt设置扩展字段Web端解析失败

## 问题详情

**现象**：
通过SetExt设置扩展字段，Web端获取到的custom数据格式不同导致解析失败。

## 排查过程

1. 查看设置的数据格式 → 包含转义字符
2. 确认处理方式 → 业务上需要处理转义，去掉那些\
3. 建议使用JSON.parse()解析

## 问题原因

数据格式包含转义字符，需要业务层处理

## 解决方案

业务上需要处理转义，使用JSON.parse()去掉转义字符

## 其他触发场景
- [Web] SetExt设置扩展字段Web端解析失败，来源：['湖南腾速科技']，2026-03-20
- [Web] SetExt设置扩展字段Web端解析失败，来源：['湖南腾速科技']，2026-03-20

