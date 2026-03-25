---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 第三方回调
platform: Android
title: sendMessage返回403错误
root_cause: 第三方回调时客户服务器拒绝了消息发送
solution: 检查第三方回调服务器是否正确处理回调请求。可通过服务端API发消息绕过第三方回调。
customers: ["北京宝宝树"]
source: chat_history
tags: ["403", "sendMessage", "第三方回调", "Android"]
created: 2025-05-07
updated: 2025-03-20
---

## 问题：Android sendMessage返回403错误

## 问题详情

**现象**：
Android端调用NIMClient.getService(MsgService.class).sendMessage发送消息返回403错误。

## 排查过程

**关键发现**：第三方回调时客户服务器拒绝了消息发送

## 问题原因

第三方回调时客户服务器拒绝了消息发送

## 解决方案

检查第三方回调服务器是否正确处理回调请求。可通过服务端API发消息绕过第三方回调。
