---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: 通用
title: getLocalSessions获取会话数量不完整
root_cause: ""
solution: getLocalSessions是获取本地会话，需要确认服务端拉会话使用的接口。本地会话数量取决于客户端是否完整同步了服务端会话数据。
customers: ["重庆汇博"]
source: chat_history
tags: ["getLocalSessions","会话列表","本地会话","数据同步"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：通用 getLocalSessions获取会话数量不完整

## 问题详情

**现象**：
账号hr3217191使用getLocalSessions只能获取到36个会话，但服务端同步的数据显示有更多会话。导致客户端获取到的未读人数只有4个，但后端同步到的未读超过4个人。

## 解决方案

getLocalSessions是获取本地会话，需要确认服务端拉会话使用的接口。本地会话数量取决于客户端是否完整同步了服务端会话数据。

## 其他触发场景

