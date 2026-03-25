---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Electron
title: V10会话列表lastMessage不是最新消息
root_cause: 服务端发送消息时未设置updateSession参数，SDK默认值处理不符合预期
solution: 服务端发送消息时指定updateSession为true，或升级到10.8.10版本修复该问题
customers: ["深圳联友"]
source: chat_history
tags: ["getConversationList", "lastMessage", "conversationChanged", "服务端消息", "updateSession"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：V10会话列表lastMessage不是最新消息

## 问题详情

**现象**：
通过localConversationService.getConversationList查询到的会话，最后一条消息不是最新的，清除未读数后触发的conversationChanged回调中lastMessage也不对

**环境信息**：
- 平台：Electron

## 排查过程

1. 确认复现流程 → 点开会话窗口 → 清除未读数 → 收到conversationChanged回调
2. 分析消息来源 → 最后一条消息是服务端发送的自定义消息
3. 检查消息配置 → 发现服务端发送消息时未设置updateSession参数
4. 确认默认值问题 → SDK默认值不符合预期，未设置时应默认更新会话最后一条消息

## 根因分析

服务端发送消息时未设置updateSession参数，SDK默认值处理不符合预期

## 解决方案

服务端发送消息时指定updateSession为true，或升级到10.8.10版本修复该问题

## 其他触发场景

（无）
