---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 群组管理
platform: Server
title: 服务端创建群组返回414错误，custom字段长度限制
root_cause: custom字段长度超过1024字符限制
solution: 缩减custom字段内容，该限制无法扩容
customers: ["ISV云信-上海金桥"]
source: chat_history
tags: ["IM V10", "创建群组", "414错误", "custom字段", "长度限制"]
created: 2025-12-02
updated: 2026-03-23
---

## 问题：服务端创建群组返回414错误，custom字段长度限制

## 问题详情

**现象**：
服务端创建群组接口返回414错误。

**环境信息**：
- 产品：IM V10
- 平台：Server
- 接口：team/create

## 排查过程

1. 检查请求参数 → 发现custom字段长度过长
2. 确认字段限制 → custom字段长度限制为1024字符

**关键发现**：custom字段长度超过1024字符限制

## 问题原因

custom字段长度超过1024字符限制，导致返回414错误。

## 解决方案

缩减custom字段内容。该限制无法扩容。

## 其他触发场景

