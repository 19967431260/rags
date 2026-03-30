---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: iOS
title: iOS最近会话lastMessage参数缺失问题
root_cause: 从数据库取会话时，lastMessage不保证是全的，很多内容没有存入会话数据库
solution: 参数缺失时，根据消息ID调用接口查询完整消息实例：https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS
customers: ['积木成林']
source: chat_history
tags: ['lastMessage', 'messageSubType', 'NIMRecentSession', 'iOS', '会话']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：iOS iOS最近会话lastMessage参数缺失问题

## 问题详情

**现象**：
客户反馈iOS端NIMRecentSession中的lastMessage的messageSubType值会变动，收到消息时内容是2，重新运行后查询被清空，删除App重装后又恢复正常。

## 排查过程

1. 客户反馈lastMessage的messageSubType值不稳定
2. 经分析：会话中的lastMessage在同步到新消息时（有内存缓存）是全的
3. 但只从数据库取会话时，lastMessage不保证是全的，很多内容没有去往会话的数据库存
**关键发现**：内存缓存和数据库查询返回的lastMessage完整性不一致

## 问题原因

从数据库取会话时，lastMessage不保证是全的，很多内容没有存入会话数据库

## 解决方案

参数缺失时，根据消息ID调用接口查询完整消息实例：https://doc.yunxin.163.com/messaging/guide/DYzOTY1NDc?platform=iOS

## 其他触发场景

（合并时在此处追加）
