---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 超大群
platform: Flutter
title: 查询超大群信息返回code=803
root_cause: 群不存在或已被删除
solution: 803错误表示群不存在，检查群号是否正确或群是否已被删除
customers: ["COOLSHOW PTE.LTD."]
source: chat_history
tags: ["超大群", "803", "queryTeam", "群不存在"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：查询超大群信息返回code=803

## 问题详情

**现象**：
调用NimCore.instance.superTeamService.queryTeam返回code=803

**环境信息**：
- 平台：Flutter

## 排查过程

1. 确认群号 → 14241756\n2. 检查群是否存在 → 803表示群不存在\n3. 确认群类型 → 客户使用的是超大群\n4. 检查调用方式 → 使用superTeamService正确

## 根因分析

群不存在或已被删除

## 解决方案

803错误表示群不存在，检查群号是否正确或群是否已被删除

## 其他触发场景

（无）
