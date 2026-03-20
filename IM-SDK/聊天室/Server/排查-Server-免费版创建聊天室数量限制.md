---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: Server
title: 免费版创建聊天室数量限制
root_cause: 免费版套餐聊天室数量限制
solution: 更换付费版appkey，免费版有聊天室数量限制
customers: ["智慧树"]
source: chat_history
tags: ["113434", "聊天室", "免费版", "数量限制", "chatroom count limit"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Server 免费版创建聊天室数量限制

## 问题详情

**现象**：
创建IM聊天室报错113434 chatroom count limit exceeded，创建账号成功但创建聊天室失败。

## 排查过程

1. 确认appkey版本
2. 检查聊天室数量限制
**关键发现**：使用的是免费版appkey，免费版创建聊天室数量有限制

## 问题原因

免费版套餐聊天室数量限制

## 解决方案

更换付费版appkey，免费版有聊天室数量限制

## 其他触发场景

