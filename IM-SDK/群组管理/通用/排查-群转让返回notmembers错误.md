---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 通用
title: 群转让返回not members错误
root_cause: 群转让时指定的用户必须是群成员
solution: 群转让时newowner必须是群成员，检查accid是否正确
customers: ["COOLSHOW PTE.LTD."]
source: chat_history
tags: ["群转让", "not members", "414", "群成员"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：群转让返回not members错误

## 问题详情

**现象**：
调用群转让接口返回414错误，desc为not members

**环境信息**：
- 平台：通用

## 排查过程

1. 检查错误信息 → not members\n2. 确认群成员 → 发现指定的newowner不在群成员中

## 根因分析

群转让时指定的用户必须是群成员

## 解决方案

群转让时newowner必须是群成员，检查accid是否正确

## 其他触发场景

（无）
