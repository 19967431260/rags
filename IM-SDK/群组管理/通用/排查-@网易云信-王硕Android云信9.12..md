---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 通用
title: @网易云信-王硕Android云信9.12.
root_cause: ""
solution: "sqlcipher升级了，用4.5.4版本"
customers: ["技术｜网易云信｜网易智企&深圳尚米"]
source: chat_history
tags: ["login", "云信", "SDK", "技术支持"]
created: 2024-12-31
updated: 2026-03-20
---

## 问题：通用 @网易云信-王硕Android云信9.12.

## 问题详情

**现象**：
@网易云信-王硕  Android云信9.12.0版本更新到9.19.4之后，已经登陆成功之后，查询queryTeamList()报异常onException()    java.lang.IllegalStateException: Cache is not ready. Please login first!

## 排查过程

1. 根据会话信息确认问题触发路径并复核关键配置。

## 问题原因

会话中未提供更细根因。

## 解决方案

sqlcipher升级了，用4.5.4版本
