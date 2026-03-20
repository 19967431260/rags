---
track_type: 排查类
sub_type: 测试问题
product: NERoom
feature: 白板转码
platform: Server
title: 动态转码成功但index.json 404
root_cause: 转码异常导致index.json未生成
solution: 转码优化处理中，属于badcase需要优化
customers: ["智慧树"]
source: chat_history
tags: ["白板", "动态转码", "index.json", "404", "badcase"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Server 动态转码成功但index.json 404

## 问题详情

**现象**：
动态转码成功status:40，但访问index.json提示404，之前也出现过。

## 排查过程

1. 检查转码结果
2. 分析index.json生成
**关键发现**：转码异常，没有正常生成index.json，是badcase

## 问题原因

转码异常导致index.json未生成

## 解决方案

转码优化处理中，属于badcase需要优化

## 其他触发场景

