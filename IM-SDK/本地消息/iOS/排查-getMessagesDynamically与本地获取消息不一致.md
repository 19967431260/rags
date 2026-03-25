---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地消息
platform: iOS
title: getMessagesDynamically与本地获取消息不一致
root_cause: 使用的是searchMessage方法，场景是关键字匹配，只支持文本消息
solution: searchMessage只支持文本消息检索。查询本地历史应使用messagesInSession方法。
customers: ["智联招聘"]
source: chat_history
tags: ["iOS", "本地消息", "searchMessage", "messagesInSession"]
created: 2025-05-12
updated: 2025-03-20
---

## 问题：iOS getMessagesDynamically与本地获取消息不一致

## 问题详情

**现象**：
动态获取消息返回14条，本地获取只返回6条，发现除了文本消息其他类型消息都没返回。

## 排查过程

**关键发现**：使用的是searchMessage方法，场景是关键字匹配，只支持文本消息

## 问题原因

使用的是searchMessage方法，场景是关键字匹配，只支持文本消息

## 解决方案

searchMessage只支持文本消息检索。查询本地历史应使用messagesInSession方法。
