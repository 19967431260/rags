---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 连接管理
platform: 服务端
title: IM发送消息提示socket状态不对错误
root_cause: IM掉线，一般是用户网络波动导致
solution: 检查客户端网络连接状态，重新登录IM
customers: ["杭州灰豚科技"]
source: chat_history
tags: ["IM-SDK", "socket", "Error_Connection_Socket_State_not_Match", "掉线"]
created: 2025-02-19
updated: 2026-03-20
---

## 问题：服务端 IM发送消息提示socket状态不对错误

## 问题详情

**现象**：
部分用户发送消息提示socket状态不对，错误信息：Error_Connection_Socket_State_not_Match，sendMsg not connected or not login。

## 排查过程

1. 确认服务器状态正常，无发布行为
2. 检查服务器监控指标
3. 确认用户网络状况

## 问题原因

IM掉线，一般是用户网络波动导致

## 解决方案

检查客户端网络连接状态，重新登录IM

## 其他触发场景
- [服务端] IM发送消息提示socket状态不对错误，来源：['杭州灰豚科技']，2026-03-20
- [服务端] IM发送消息提示socket状态不对错误，来源：['杭州灰豚科技']，2026-03-20

