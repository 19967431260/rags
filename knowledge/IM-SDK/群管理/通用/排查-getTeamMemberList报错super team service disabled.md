---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群管理
platform: 通用
title: getTeamMemberList报错super team service disabled
root_cause: 客户使用的是超大群(super team)类型，但该应用未开通超大群功能，默认是高级群
solution: 确认群类型，如使用高级群则使用对应接口；如需使用超大群需先开通功能
customers: ['北京圆心医疗']
source: chat_history
tags: ['getTeamMemberList', 'super team', '超大群', '群类型', 'V2NIM']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：通用 getTeamMemberList报错super team service disabled

## 问题详情

**现象**：
客户调用V2NIMTeamService.getTeamMemberList获取群成员列表时报错'super team service disabled'。

## 排查过程

1. 检查群类型 → 客户conversationId中包含群ID
2. 判断群类型 → 客户使用了超大群(super team)类型，但未开通该功能

## 问题原因

客户使用的是超大群(super team)类型，但该应用未开通超大群功能，默认是高级群

## 解决方案

确认群类型，如使用高级群则使用对应接口；如需使用超大群需先开通功能

## 其他触发场景

（合并时在此处追加）
