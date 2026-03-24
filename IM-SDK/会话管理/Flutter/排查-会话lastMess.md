---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Flutter
title: 会话lastMessageContent未更新
root_cause: session对象没有及时更新
solution: 需要更新session对象，确保获取到最新的会话信息
customers: ["南宁小清柠"]
source: chat_history
tags: ["lastMessageContent", "会话", "Flutter", "数据更新"]
created: 2025-02-25
updated: 2026-03-20
---

## 问题：Flutter 会话lastMessageContent未更新

## 问题详情

**现象**：
查询会话的lastMessageContent没有取到最新的消息内容，详情页获取历史消息显示有2条。

## 排查过程

（从会话记录提取）

## 问题原因

session对象没有及时更新

## 解决方案

需要更新session对象，确保获取到最新的会话信息

## 其他触发场景
- [Flutter] 会话lastMessageContent未更新，来源：['南宁小清柠']，2026-03-20
- [Flutter] 会话lastMessageContent未更新，来源：['南宁小清柠']，2026-03-20

