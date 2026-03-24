---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地存储
platform: Web
title: getLocalMsgs查询不到最新消息问题
root_cause: 可能是客户端时间与服务器时间有时差，或未正确配置db参数
solution: 检查getLocalMsgs的end参数设置，确认初始化时db参数未设置为false，可直接检查db库确认数据是否存在。
customers: ['搜狐']
source: chat_history
tags: ['getLocalMsgs', '本地消息', '时间戳', 'Web', '查询']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Web getLocalMsgs查询不到最新消息问题

## 问题详情

**现象**：
客户反馈web端会话列表能看到最后一条消息，但进入会话从本地获取的消息却不是最新的。

## 排查过程

1. 客户反馈getLocalMsgs拿不到最新消息
2. 询问end参数是否主动赋值
3. 怀疑客户端时间与服务器时间有时差
4. 建议检查db库中是否真的不存在
5. 询问获取未读数初始化时是否把db参数设置为false

## 问题原因

可能是客户端时间与服务器时间有时差，或未正确配置db参数

## 解决方案

检查getLocalMsgs的end参数设置，确认初始化时db参数未设置为false，可直接检查db库确认数据是否存在。

## 其他触发场景

（合并时在此处追加）
