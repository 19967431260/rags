---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话列表
platform: Uniapp
title: getConversationList调不通
root_cause: 初始化后未调用login方法登录。
solution: 1. 确保初始化后调用login方法登录
2. 监听相关回调确认登录状态
3. 登录成功后再调用getConversationList
4. 建议debugLevel开到debug方便排查问题。
customers: ['云信-安徽省刀锋网络科技有限公司']
source: chat_history
tags: ['getConversationList', '登录', 'Uniapp', '回调']
created: 2025-02-24
updated: 2026-03-23
---

## 问题：Uniapp getConversationList调不通

## 问题详情

**现象**：
调用getConversationList接口无响应。

**环境信息**：
- 平台：Uniapp
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认是否登录
2. 建议打点日志
3. 检查SDK回调
4. 发现未调用login

## 问题原因

初始化后未调用login方法登录。

## 解决方案

1. 确保初始化后调用login方法登录
2. 监听相关回调确认登录状态
3. 登录成功后再调用getConversationList
4. 建议debugLevel开到debug方便排查问题。

## 其他触发场景

（合并时在此处追加：`- [Uniapp] getConversationList调不通，来源：['云信-安徽省刀锋网络科技有限公司']，2026-03-23`）
