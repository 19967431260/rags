---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 初始化
platform: iOS
title: iOS V10会话列表空白问题
root_cause: V10版本获取会话列表数据时依赖同步完成标志，该标志在同步完成后赋值。如果登录后未创建会话页面，标识不会被赋值为true。
solution: 建议登录后立即创建会话页面，可以先不跳转但需先创建出来，确保数据同步机制正常工作。
customers: ['杭州泰阿网络']
source: chat_history
tags: ['V10', 'iOS', '会话列表', '空白', '初始化']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：iOS iOS V10会话列表空白问题

## 问题详情

**现象**：
客户初始化tabBar后跳转CustomConversationController出现空白，未初始化时直接跳转正常。

## 排查过程

1. 检查登录状态确认已登录；2. 检查CustomConversationController注册情况；3. 分析发现是数据同步标识问题。

## 问题原因

V10版本获取会话列表数据时依赖同步完成标志，该标志在同步完成后赋值。如果登录后未创建会话页面，标识不会被赋值为true。

## 解决方案

建议登录后立即创建会话页面，可以先不跳转但需先创建出来，确保数据同步机制正常工作。

## 其他触发场景

（合并时在此处追加）
