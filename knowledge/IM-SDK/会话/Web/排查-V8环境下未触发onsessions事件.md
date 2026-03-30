---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话
platform: Web
title: V8环境下未触发onsessions事件
root_cause: 用户最近7天无新消息，服务端未下发漫游或离线消息，因此未触发onsessions
solution: 现象符合预期。可以调用getLocalSessions查询本地会话列表获取历史会话
customers: ["圆通"]
source: chat_history
tags: ["V8", "onsessions", "会话", "漫游消息"]
created: 2025-05-21
updated: 2025-03-20
---

## 问题：Web V8环境下未触发onsessions事件

## 问题详情

**现象**：
V8环境下特定用户登录后未触发onsessions事件。

## 排查过程

**关键发现**：用户最近7天无新消息，服务端未下发漫游或离线消息，因此未触发onsessions

## 问题原因

用户最近7天无新消息，服务端未下发漫游或离线消息，因此未触发onsessions

## 解决方案

现象符合预期。可以调用getLocalSessions查询本地会话列表获取历史会话
