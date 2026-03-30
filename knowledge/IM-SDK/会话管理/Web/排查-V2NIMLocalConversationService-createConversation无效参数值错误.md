---
track_type: 排查类
sub_type: 接口使用
product: IM-SDK
feature: 会话管理
platform: Web
title: V2NIMLocalConversationService.createConversation无效参数值错误
root_cause: V10版本的conversationId拼接规则需要按特定格式拼接
solution: V10版本的conversationId拼接规则是：自己的id|会话类型（单聊/群聊）|对方的id（对方userid/群id）。不能直接传对方id，需要按规则拼接。示例：单聊会话id = `myAccount|1|receiverId`，其中会话类型：1=单聊，2=群聊
customers: ["路过山河（北京）旅游发展有限公司"]
source: chat_history
tags: ["IM", "V10", "会话管理", "conversationId", "createConversation", "参数错误"]
created: 2025-05-26
updated: 2025-03-23
---

## 问题：Web V2NIMLocalConversationService.createConversation无效参数值错误

## 问题详情

**现象**：
用户调用createConversation方法创建会话时提示无效参数值。

**环境信息**：
- 平台：Web

## 排查过程

**关键发现**：V10版本的conversationId拼接规则需要按特定格式拼接

## 问题原因

V10版本的conversationId拼接规则需要按特定格式拼接

## 解决方案

V10版本的conversationId拼接规则是：自己的id|会话类型（单聊/群聊）|对方的id（对方userid/群id）。不能直接传对方id，需要按规则拼接。

示例：单聊会话id = `myAccount|1|receiverId`
其中会话类型：1=单聊，2=群聊
