---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Electron SDK
platform: Electron
title: V10 Electron conversationId构建错误
root_cause: V10会话ID格式为：用户账号|会话类型|聊天对象账号，会话类型1为单聊、2为群聊。客户混淆了会话类型。
solution: 使用V2NIMConversationIdUtil工具类创建conversationId，单聊类型值为1，群聊类型值为2。格式：accountId|conversationType|targetAccountId。
customers: ['深圳联友-企业协同']
source: chat_history
tags: ['V10', 'Electron', 'conversationId', '查询', '单聊']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Electron V10 Electron conversationId构建错误

## 问题详情

**现象**：
客户使用V10 Electron SDK查询消息列表时，单聊查询无响应或报错invalid parameter。

## 排查过程

1. 检查conversationId格式；2. 发现使用'2'表示群组类型，但单聊应使用'1'；3. 确认V10会话ID格式与V9不同。

## 问题原因

V10会话ID格式为：用户账号|会话类型|聊天对象账号，会话类型1为单聊、2为群聊。客户混淆了会话类型。

## 解决方案

使用V2NIMConversationIdUtil工具类创建conversationId，单聊类型值为1，群聊类型值为2。格式：accountId|conversationType|targetAccountId。

## 其他触发场景

（合并时在此处追加）
