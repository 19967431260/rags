---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 群组管理
platform: 通用
title: fetchTeamMembers频繁调用触发限流
root_cause: 业务层在群成员变化时主动调用fetchTeamMembers，高并发场景（1000人同时入群）触发限流
solution: 付费提升限流阈值到60秒1000次，费用4500元/月；或业务层优化调用频率
customers: ["VIP云信-上海来伊份"]
source: chat_history
tags: ["fetchTeamMembers", "限流", "QPS", "群成员", "高并发"]
created: 2025-02-05
updated: 2026-03-20
---

## 问题：通用 fetchTeamMembers频繁调用触发限流

## 问题详情

**现象**：
查询群成员信息时频繁报错，群成员数波动（2000→1800），用户未注册云信导致加群失败

## 排查过程

1. 查看日志发现fetchTeamMembers调用频繁 → 确认是业务层主动拉取
2. 确认限流策略 → 60秒60次
3. 评估提升QPS → 确定无法调整，需业务层优化
4. 临时提升限流 → 付费调整到60秒1000次（4500元/月）

## 问题原因

业务层在群成员变化时主动调用fetchTeamMembers，高并发场景（1000人同时入群）触发限流

## 解决方案

付费提升限流阈值到60秒1000次，费用4500元/月；或业务层优化调用频率

## 其他触发场景

