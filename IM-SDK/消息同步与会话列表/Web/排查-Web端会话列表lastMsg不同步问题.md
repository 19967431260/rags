---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息同步与会话列表
platform: Web
title: Web端会话列表lastMsg不同步问题
root_cause: 可能是进入聊天页面时调用获取历史消息的时间参数不对，没有拉到最新的消息；或者是SDK版本问题
solution: 1. 确保在onsyncdone监听触发后才获取会话列表\n2. 进入聊天页面时调用nim.getHistoryMsgs获取历史消息\n3. 升级到SDK 9.19.13以上版本\n4. 检查获取会话列表的时机和参数
customers: ["江苏乐筑"]
source: chat_history
tags: ["Web", "lastMsg", "消息同步", "onsyncdone", "getHistoryMsgs"]
created: 2025-06-13
updated: 2025-03-23
---

## 问题：Web Web端会话列表lastMsg不同步问题

## 问题详情

**现象**：
Web端IM SDK在消息同步完成后获取会话列表，但session的lastMsg不是最新消息。现象：后台停留在消息页时前台发消息能及时收到；后台离开消息页面，前台发消息后未读数增加，但后台再打开消息页面看不到最新消息，未读数依然存在。

## 排查过程

1. 检查是否在onsyncdone监听触发后才获取会话，确保消息同步完成才获取会话
2. 检查进入聊天页面时是否调用nim.getHistoryMsgs获取历史消息
3. 检查SDK版本，建议升级到9.19.13以上版本测试
4. 对比发送方和接收方的日志，确认消息id和获取时机

**关键发现**：可能是进入聊天页面时调用获取历史消息的时间参数不对，没有拉到最新的消息；或者是SDK版本问题

## 问题原因

可能是进入聊天页面时调用获取历史消息的时间参数不对，没有拉到最新的消息；或者是SDK版本问题

## 解决方案

1. 确保在onsyncdone监听触发后才获取会话列表
2. 进入聊天页面时调用nim.getHistoryMsgs获取历史消息
3. 升级到SDK 9.19.13以上版本
4. 检查获取会话列表的时机和参数

## 其他触发场景

