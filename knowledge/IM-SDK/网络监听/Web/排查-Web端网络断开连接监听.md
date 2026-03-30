---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 网络监听
platform: Web
title: Web端网络断开连接监听
root_cause: 客户代码逻辑问题
solution: SDK默认会自动重连，willReconnect、disconnect等事件在断网时会正常触发
customers: ['广州欢牛']
source: chat_history
tags: ['网络监听', 'willReconnect', 'disconnect', '自动重连', 'Web']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Web Web端网络断开连接监听

## 问题详情

**现象**：
客户需要监听网络断开和重连事件，但断网后相关回调未执行。

## 排查过程

1. 客户提供代码截图
2. 本地测试验证正常
3. 提供录屏演示正常回调

## 问题原因

客户代码逻辑问题

## 解决方案

SDK默认会自动重连，willReconnect、disconnect等事件在断网时会正常触发

## 其他触发场景

（合并时在此处追加）
