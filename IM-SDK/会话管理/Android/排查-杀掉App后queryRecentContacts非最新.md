---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Android
title: 杀掉App后queryRecentContacts非最新
root_cause: 数据同步未完成时查询
solution: 监听数据同步状态，等待同步完成后再查询，参考文档监听数据同步状态
customers: ["积木成林"]
source: chat_history
tags: ["queryRecentContacts", "数据同步", "会话列表", "杀进程"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：杀掉App后queryRecentContacts非最新

## 问题详情

**现象**：
用户杀死App后收到消息，再次登录调用queryRecentContacts，第一次查询有概率不是最新的

**环境信息**：
- 平台：Android

## 根因分析

数据同步未完成时查询

## 解决方案

监听数据同步状态，等待同步完成后再查询，参考文档监听数据同步状态

## 其他触发场景

（无）
