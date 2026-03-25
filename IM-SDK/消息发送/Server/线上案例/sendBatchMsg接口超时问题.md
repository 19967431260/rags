---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 消息发送
platform: Server
title: sendBatchMsg接口超时问题
root_cause: 服务器有台机器延迟有波动，导致业务请求RT波动。
solution: 确认到有台机器延迟有波动，在20:50已恢复，可后续观察。
customers: ["杭州知聊"]
source: chat_history
tags: ["sendBatchMsg", "超时", "批量发送", "服务端API"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：sendBatchMsg接口超时问题

## 问题详情

**现象**：
sendBatchMsg批量发送消息接口出现超时情况，从20:02开始间歇性出现。

**环境信息**：
- 平台：服务端

## 排查过程

1. 确认问题时间点和现象
2. 后台排查发现有台机器延迟有波动
3. 导致业务请求RT有波动或增加

## 根因分析

服务器有台机器延迟有波动，导致业务请求RT波动。

## 解决方案

确认到有台机器延迟有波动，在20:50已恢复，可后续观察。

## 其他触发场景

（无）
