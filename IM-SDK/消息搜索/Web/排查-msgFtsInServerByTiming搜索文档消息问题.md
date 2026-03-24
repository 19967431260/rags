---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息搜索
platform: Web
title: msgFtsInServerByTiming搜索文档消息问题
root_cause: 搜索接口默认limit为10条，当搜索关键词较普遍时，前面10条结果可能都是文本消息，导致文档消息被截断。
solution: 1. 增加limit参数值（最大50或100）；2. 或限制消息类型为file进行搜索；3. 或提前查询时间范围，缩小搜索区间。
customers: ['深圳联友-企业协同']
source: chat_history
tags: ['搜索', '文档', 'msgFtsInServerByTiming', 'limit', 'Web']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Web msgFtsInServerByTiming搜索文档消息问题

## 问题详情

**现象**：
客户使用msgFtsInServerByTiming接口搜索聊天记录正常，但搜索文档消息无法找到历史文件。

## 排查过程

1. 对比新旧接口入参；2. 分析搜索结果，发现返回10条消息上限导致；3. 验证关键词匹配情况。

## 问题原因

搜索接口默认limit为10条，当搜索关键词较普遍时，前面10条结果可能都是文本消息，导致文档消息被截断。

## 解决方案

1. 增加limit参数值（最大50或100）；2. 或限制消息类型为file进行搜索；3. 或提前查询时间范围，缩小搜索区间。

## 其他触发场景

（合并时在此处追加）
