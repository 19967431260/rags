---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地存储
platform: Web
title: 无法连接到IMDB
root_cause: SDK版本较低，存在DB兼容性问题
solution: 升级SDK到9.19.10版本，已优化IndexDB兼容性
customers: ['智己']
source: chat_history
tags: ['IndexDB', 'Web', '连接失败', 'SDK升级']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Web 无法连接到IMDB

## 问题详情

**现象**：
Web端提示连不到IMDB，IndexDB连接失败

## 排查过程

1. 确认浏览器支持DB → 客户确认一直正常使用
2. 建议升级SDK → 当前版本较低，已优化很多DB打不开的情况

## 问题原因

SDK版本较低，存在DB兼容性问题

## 解决方案

升级SDK到9.19.10版本，已优化IndexDB兼容性

## 其他触发场景

（合并时在此处追加）
