---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 超大群
platform: Flutter
title: 超大群消息撤回失败code=414
root_cause: 使用了单聊消息的撤回接口撤回超大群消息
solution: 超大群消息撤回需要使用SuperTeamService.revokeMessage，Flutter SDK需使用底层SDK方法，type传superTeamDeleteMsg
customers: ["COOLSHOW PTE.LTD."]
source: chat_history
tags: ["超大群", "消息撤回", "414", "SuperTeamService"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：超大群消息撤回失败code=414

## 问题详情

**现象**：
调用revokeMessage撤回超大群消息返回414错误

**环境信息**：
- 平台：Flutter

## 排查过程

1. 确认消息为自己发送 → 是\n2. 检查撤回API → 使用了单聊消息撤回接口\n3. 确认SDK支持 → Flutter SDK SuperTeamService没有revoke方法\n4. 提供解决方案 → 使用superTeamDeleteMsg类型撤回

## 根因分析

使用了单聊消息的撤回接口撤回超大群消息

## 解决方案

超大群消息撤回需要使用SuperTeamService.revokeMessage，Flutter SDK需使用底层SDK方法，type传superTeamDeleteMsg

## 其他触发场景

（无）
