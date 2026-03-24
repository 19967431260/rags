---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: iOS
title: fetchTeamMembers回调不执行问题
root_cause: 客户使用NIMSDK V10版本(10.5.1)调用V9的API，存在兼容性问题。NIMKit是老的开源UI库，默认引入V9 SDK，未兼容V10 SDK。
solution: 如果继续使用V9 API，建议集成9.19.4版本。V10对比V9 API完全不同，升级需要全面替换。两套API在本地数据上是同一份。
customers: ['北京云动（会小二）']
source: chat_history
tags: ['IM-SDK', 'fetchTeamMembers', '回调', 'V9', 'V10', '兼容', 'NIMKit']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：iOS fetchTeamMembers回调不执行问题

## 问题详情

**现象**：
客户反馈fetchTeamMembers回调一直不执行，已确认方法被调用且SDK已初始化。

## 排查过程

1. 确认方法被调用 → 客户确认走了方法
2. 确认SDK初始化和登录完成 → 客户确认已完成
3. 测试发现解散的群不回调，正常群没问题
4. 客户提供群ID和账号信息
5. 排查发现客户使用NIMSDK 10.5.1版本调用V9 API
6. 确认V10 SDK调用V9 API存在兼容问题

## 问题原因

客户使用NIMSDK V10版本(10.5.1)调用V9的API，存在兼容性问题。NIMKit是老的开源UI库，默认引入V9 SDK，未兼容V10 SDK。

## 解决方案

如果继续使用V9 API，建议集成9.19.4版本。V10对比V9 API完全不同，升级需要全面替换。两套API在本地数据上是同一份。

## 其他触发场景

（合并时在此处追加）
