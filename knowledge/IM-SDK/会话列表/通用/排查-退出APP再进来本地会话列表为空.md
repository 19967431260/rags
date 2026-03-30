---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: 通用
title: 退出APP再进来本地会话列表为空
root_cause: 控制台消息漫游配置未正确开启。
solution: 在控制台开启消息漫游配置，或在代码中设置消息漫游。
customers: ["成都鲸沃科技有限公司"]
source: chat_history
tags: ["会话列表","V2NIMLocalConversationService","消息漫游","本地会话"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：通用 退出APP再进来本地会话列表为空

## 问题详情

**现象**：
发送消息后退出APP再进来，调用V2NIMLocalConversationService.getConversationList获取本地会话列表为空。客户使用标准版，已开启消息漫游。

## 排查过程

1. 确认使用的是本地会话接口而非云端会话接口 → 确认使用V2NIMLocalConversationService
2. 检查appkey和消息漫游配置 → 发现控制台配置问题
3. 确认消息是否存历史 → 消息未正确存储

**关键发现**：控制台消息漫游配置问题

## 问题原因

控制台消息漫游配置未正确开启。

## 解决方案

在控制台开启消息漫游配置，或在代码中设置消息漫游。

## 其他触发场景

