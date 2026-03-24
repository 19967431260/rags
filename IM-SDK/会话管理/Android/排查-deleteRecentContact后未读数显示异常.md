---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Android
title: deleteRecentContact后未读数显示异常
root_cause: sessionReadAck设置为false导致会话未读数没有同步
solution: 将SDKOptions.sessionReadAck设置为true
customers: ['新视展']
source: chat_history
tags: ['deleteRecentContact', '未读数', '会话列表', 'sessionReadAck']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Android deleteRecentContact后未读数显示异常

## 问题详情

**现象**：
用户A发送多条消息给B，B调用deleteRecentContact(LOCAL_AND_REMOTE)移除会话后，A再发消息，B收到会话列表变更，会话中未读数字段显示为前面A发过的总条数而非1。

## 排查过程

1. 客户反馈删除会话后新消息未读数显示异常
2. 技术支持询问是否必现
3. 客户确认必现并提供日志
4. 技术支持询问SDKOptions.sessionReadAck设置
5. 客户确认使用SDKOption.DEFAULT，sessionReadAck为false
6. 技术支持建议改为true再测试

## 问题原因

sessionReadAck设置为false导致会话未读数没有同步

## 解决方案

将SDKOptions.sessionReadAck设置为true

## 其他触发场景

（合并时在此处追加）
