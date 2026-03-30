---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 服务端
title: 群邀请模式inviteMode与创建时邀请的区别
root_cause: 创建群时附带的邀请和创建成功后邀请的时机不同，inviteMode控制的是创建后的邀请行为
solution: 创建群时的附带邀请不受inviteMode限制，创建后的邀请需要遵循inviteMode设置（如需要对方同意）
customers: ["VIP云信-上海有浩信息科技有限公"]
source: chat_history
tags: ["inviteMode", "群邀请", "服务端API", "群管理"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：服务端 群邀请模式inviteMode与创建时邀请的区别

## 问题详情

**现象**：
服务端API创建群后，通过APP拉人进群时提示成功但实际未加入，咨询inviteMode配置问题

## 排查过程

1. 确认群inviteMode设置 → 发现需要被邀请者同意
2. 对比创建群时附带邀请 vs 创建成功后邀请 → 两个邀请时机不同

## 问题原因

创建群时附带的邀请和创建成功后邀请的时机不同，inviteMode控制的是创建后的邀请行为

## 解决方案

创建群时的附带邀请不受inviteMode限制，创建后的邀请需要遵循inviteMode设置（如需要对方同意）

## 其他触发场景

