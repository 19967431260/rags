---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 系统通知
platform: iOS
title: fetchSystemNotifications查询系统通知无数据
root_cause: fetchSystemNotifications仅查询本地数据库，系统通知只下发一次，卸载重装后丢失
solution: 系统通知只支持本地查询，无法从远端拉取；卸载重装后历史系统通知无法恢复
customers: ["VIP云信-上海来伊份"]
source: chat_history
tags: ["fetchSystemNotifications", "系统通知", "TeamApply", "iOS", "本地查询"]
created: 2025-02-07
updated: 2026-03-20
---

## 问题：iOS fetchSystemNotifications查询系统通知无数据

## 问题详情

**现象**：
调用fetchSystemNotifications查询NIMSystemNotificationTypeTeamApply类型的系统通知，返回空数组

## 排查过程

1. 确认方法只从本地取数据 → 非服务端查询
2. 确认系统通知只下发一次 → 卸载重装后无法同步

## 问题原因

fetchSystemNotifications仅查询本地数据库，系统通知只下发一次，卸载重装后丢失

## 解决方案

系统通知只支持本地查询，无法从远端拉取；卸载重装后历史系统通知无法恢复

## 其他触发场景

