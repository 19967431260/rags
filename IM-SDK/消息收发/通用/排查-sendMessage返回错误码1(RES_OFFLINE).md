---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息收发
platform: 通用
title: sendMessage返回错误码1(RES_OFFLINE)
root_cause: IM未登录或已离线，无法执行发送消息操作
solution: 错误码1表示RES_OFFLINE，当前未在线无法操作。检查IM登录状态，确保已登录后再发送消息
customers:
  - 爱追光
source: chat_history
tags:
  - IM
  - sendMessage
  - 错误码1
  - RES_OFFLINE
created: '2025-06-23'
updated: '2025-03-23'
---

## 问题：通用 sendMessage返回错误码1(RES_OFFLINE)

## 问题详情

**现象**：
调用sendMessage接口onFailed回调，错误码为1。客户不清楚错误含义。

## 问题原因

IM未登录或已离线，无法执行发送消息操作

## 解决方案

错误码1表示RES_OFFLINE，当前未在线无法操作。检查IM登录状态，确保已登录后再发送消息
