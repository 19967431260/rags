---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 批量消息
platform: 服务端
title: sendBatchMsg接口报错from is empty
root_cause: 接口参数名错误，批量消息接口使用fromAccid而非from
solution: 使用正确的参数名fromAccid代替from；检查Content-Type设置
customers: ['广州浪花']
source: chat_history
tags: ['414', 'from is empty', 'sendBatchMsg', '批量消息', 'fromAccid']
created: 2025-09-18
updated: 2026-03-25
---

## 问题：服务端 sendBatchMsg接口报错from is empty

## 问题详情

**现象**：
调用sendBatchMsg.action接口发送批量消息时返回错误code:414, desc:from is empty，但请求中已传入from参数。

## 解决方案

使用正确的参数名fromAccid代替from；检查Content-Type设置
