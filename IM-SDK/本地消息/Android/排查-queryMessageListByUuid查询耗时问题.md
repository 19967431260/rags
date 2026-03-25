---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 本地消息
platform: Android
title: queryMessageListByUuid查询耗时问题
root_cause: SDK底层查询耗时正常（2ms），总耗时300ms是上层业务逻辑导致
solution: SDK底层查询耗时约2ms，异步方法几十ms符合预期。建议检查上层业务逻辑是否存在耗时操作。
customers: ["深圳享笑"]
source: chat_history
tags: ["queryMessageListByUuid", "耗时", "本地消息", "性能"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：queryMessageListByUuid查询耗时问题

## 问题详情

**现象**：
根据uuid查询历史消息耗时约300ms，咨询是否是预期内。

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈queryMessageListByUuid耗时300ms
2. 客户一次只查一条
3. 分析SDK日志发现底层耗时仅2ms
4. 建议客户检查上层逻辑

## 根因分析

SDK底层查询耗时正常（2ms），总耗时300ms是上层业务逻辑导致

## 解决方案

SDK底层查询耗时约2ms，异步方法几十ms符合预期。建议检查上层业务逻辑是否存在耗时操作。

## 其他触发场景

（无）
