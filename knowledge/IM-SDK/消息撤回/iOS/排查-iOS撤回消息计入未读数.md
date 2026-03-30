---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息撤回
platform: iOS
title: iOS撤回消息计入未读数
root_cause: 
solution: 撤回时有参数设置是否计入未读，参考FAQ文档KB0025
customers: ["北京久幺幺"]
source: chat_history
tags: ["消息撤回", "未读数", "iOS", "NIMRecentSession"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS撤回消息计入未读数

## 问题详情

**现象**：
收到对方撤回消息后NIMRecentSession.unreadCount会变成2，期望为1

**环境信息**：
- 平台：iOS

## 解决方案

撤回时有参数设置是否计入未读，参考FAQ文档KB0025

## 其他触发场景

（无）
