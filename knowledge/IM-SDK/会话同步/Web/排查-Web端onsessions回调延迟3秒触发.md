---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话同步
platform: Web
title: Web端onsessions回调延迟3秒触发
root_cause: 服务器同步需要时间，群列表数量较多（1074个）导致同步耗时增加。
solution: 服务器同步需要时间，不是卡顿。需要同步的数据越多，耗时相应增加。群列表数量多会影响同步时间。
customers: ['圆通']
source: chat_history
tags: ['会话同步', 'onsessions', 'Web', '延迟']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Web Web端onsessions回调延迟3秒触发

## 问题详情

**现象**：
客户反馈onsessions回调需要3秒多才触发，询问是否正常。

## 排查过程

1. 确认会话数量（30多个）
2. 检查群列表数量（1074个）
3. 分析同步耗时原因

## 问题原因

服务器同步需要时间，群列表数量较多（1074个）导致同步耗时增加。

## 解决方案

服务器同步需要时间，不是卡顿。需要同步的数据越多，耗时相应增加。群列表数量多会影响同步时间。

## 其他触发场景

（合并时在此处追加）
