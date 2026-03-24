---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Web
title: Web端如何删除会话使下次初始化不下发
root_cause: 客户使用的不是最新代码
solution: 使用deleteLocalSession删除会话并同时删除漫游消息，确保使用最新版本SDK代码
customers: ["VIP云信-上海太屋"]
source: chat_history
tags: ["deleteLocalSession", "会话删除", "漫游消息", "Web SDK"]
created: 2025-02-26
updated: 2026-03-20
---

## 问题：Web Web端如何删除会话使下次初始化不下发

## 问题详情

**现象**：
客户使用Web SDK，希望删除会话后下次初始化时onSessions回调不再下发该会话。尝试使用deleteLocalSession但会话仍然存在。

## 排查过程

1. 客户询问删除会话方法 → 客服建议使用deleteLocalSession并同时删除漫游消息
2. 客户反馈删除后下次登录会话仍存在 → 客服要求提供deleteLocalSession日志和下次登录日志
3. 客户确认是最新代码问题 → 问题解决

## 问题原因

客户使用的不是最新代码

## 解决方案

使用deleteLocalSession删除会话并同时删除漫游消息，确保使用最新版本SDK代码

## 其他触发场景

