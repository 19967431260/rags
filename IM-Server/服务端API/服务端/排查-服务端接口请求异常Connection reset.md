---
track_type: 排查类
sub_type: 使用问题
product: IM-Server
feature: 服务端API
platform: 服务端
title: 服务端接口请求异常Connection reset
root_cause: 
solution: 建议检查客户端是否使用了连接池，检查是否有大量的失效连接被复用。
customers: ["VIP云信-上海来伊份"]
source: chat_history
tags: ["Connection reset", "连接池", "服务端API"]
created: 2026-02-25
updated: 2026-03-15
---

## 问题：服务端 服务端接口请求异常Connection reset

## 问题详情

**现象**：
客户反馈昨晚20点40到21点之间请求云信接口报Connection reset异常。

## 排查过程

检查服务器日志，该时段未见告警和异常。

## 问题原因



## 解决方案

建议检查客户端是否使用了连接池，检查是否有大量的失效连接被复用。
