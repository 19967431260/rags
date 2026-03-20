---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: Web
title: IM V10聊天室独立登录需实现linkProvider
root_cause: IM V10聊天室SDK独立登录时，如果不先登录NIM主SDK，需要实现linkProvider参数返回聊天室服务器地址。
solution: 在enter参数中实现linkProvider函数，返回聊天室服务器地址列表，如：["chatwl02.yunxinfw.com:443"]。
customers: ["FVIP云信-北京淘金者-牛股王"]
source: chat_history
tags: ["IM V10", "聊天室", "linkProvider", "enter", "独立登录"]
created: 2025-11-18
updated: 2026-03-20
---

## 问题：Web IM V10聊天室独立登录需实现linkProvider

## 问题详情

**现象**：
客户使用IM V10版本聊天室SDK，在不登录NIM主SDK的情况下直接enter登录聊天室报错。

## 排查过程

1. 确认错误现象 → 调用getInstance后enter登录报错
2. 分析原因 → 客户未登录NIM主SDK，需要独立登录聊天室
**关键发现**：独立登录聊天室需要实现linkProvider返回聊天室地址

## 问题原因

IM V10聊天室SDK独立登录时，如果不先登录NIM主SDK，需要实现linkProvider参数返回聊天室服务器地址。

## 解决方案

在enter参数中实现linkProvider函数，返回聊天室服务器地址列表，如：["chatwl02.yunxinfw.com:443"]。

## 其他触发场景

