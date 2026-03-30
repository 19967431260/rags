---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "用户资料"
platform: "Server"
title: "创建用户时ext字段未生效问题"
root_cause: "create接口的ex字段只在创建账号时生效，已创建的账号无法通过该接口更新扩展字段"
solution: "已创建的账号需使用更新用户资料API (updateUinfo.action) 来更新ex字段，或客户端调用SDK的更新用户资料方法。"
customers: ["杭州秋果计划科技"]
source: "chat_history"
tags: ["IM", "create", "ex", "用户资料", "更新"]
created: "2025-09-02"
updated: "2026-03-20"
---

## 问题：Server 创建用户时ext字段未生效问题

## 问题详情

**现象**：
调用create接口传入ex字段，但客户端收到的消息中该字段为null。账号是4月创建的，现在才设置ex字段。

## 排查过程

1. 确认API调用方式 → 使用create接口传ex
2. 查询账号创建时间 → 2025-04-01创建
3. 确认问题原因 → 只有创建时才能通过create接口设置ex

## 问题原因

create接口的ex字段只在创建账号时生效，已创建的账号无法通过该接口更新扩展字段

## 解决方案

已创建的账号需使用更新用户资料API (updateUinfo.action) 来更新ex字段，或客户端调用SDK的更新用户资料方法。

## 其他触发场景
