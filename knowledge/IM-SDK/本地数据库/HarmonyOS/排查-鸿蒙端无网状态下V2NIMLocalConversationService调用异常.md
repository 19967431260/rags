---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地数据库
platform: HarmonyOS
title: 鸿蒙端无网状态下V2NIMLocalConversationService调用异常
root_cause: 重复调用logout导致SDK内部维护的状态异常，进而导致数据库打开失败
solution: 避免在初始化过程中进行重试操作，不要多次调用登出。如无特殊需求，不需要多次调用logout。已提供修复包：NIMSDK-Harmony-SDK-10.8.0-20250206-17:10:35-b9a07e60.tar.gz
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 鸿蒙端无网状态下V2NIMLocalConversationService调用异常

## 问题描述

无网状态下自动登录，onAccountReady已回调，但调用V2NIMLocalConversationService.getConversationList报错，提示非法状态

## 问题背景

1. 确认onAccountReady回调已完成
2. 排查发现无网状态下数据库打开失败
3. 分析日志发现可能是重复logout导致SDK内部状态异常

## 根因分析

重复调用logout导致SDK内部维护的状态异常，进而导致数据库打开失败

## 解决方案

避免在初始化过程中进行重试操作，不要多次调用登出。如无特殊需求，不需要多次调用logout。已提供修复包：NIMSDK-Harmony-SDK-10.8.0-20250206-17:10:35-b9a07e60.tar.gz

## 标签

- 无网状态
- 数据库打开失败
- 重复logout
- HarmonyOS
- 自动登录

## 客户

- 顺丰科技

## 会话日期

2025-02-06
