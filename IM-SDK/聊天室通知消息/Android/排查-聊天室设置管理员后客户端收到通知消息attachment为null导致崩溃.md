---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室通知消息
platform: Android
title: 聊天室设置管理员后客户端收到通知消息attachment为null导致崩溃
root_cause: 设置聊天室管理员后，云信服务器自动发送的通知消息attachment为null，客户端未做判空处理导致崩溃
solution: 客户端判断消息类型，当attachment为null时直接忽略该消息。参考文档：https://doc.yunxin.163.com/messaging/guide/TI1MDE5MzA?platform=android#%E8%81%8A%E5%A4%A9%E5%AE%A4%E9%80%9A%E7%9F%A5%E6%B6%88%E6%81%AF
customers:
  - 淮南东东网络科技有限公司
source: chat_history
tags:
  - 聊天室
  - 通知消息
  - attachment
  - 'null'
  - 崩溃
  - 管理员
created: '2025-06-11'
updated: '2025-03-23'
---

## 问题：Android 聊天室设置管理员后客户端收到通知消息attachment为null导致崩溃

## 问题详情

**现象**：
通过API发送聊天室自定义消息后，客户端收到消息时闪退。原因是设置聊天室管理员后，云信服务器会自动发送一条类型为5的通知消息，该通知消息的attachment为null。客户端在解析消息时，对NIMChatroomNotificationContent类型的消息取notifyExt时因数据为null而崩溃。

**排查过程**：

1. 确认客户端收到类型为5的消息（聊天室通知消息）
2. 发现设置管理员操作会触发云信服务器自动发送通知
3. 定位崩溃原因为attachment为null时未做判空处理

**关键发现**：设置聊天室管理员后，云信服务器自动发送的通知消息attachment为null，客户端未做判空处理导致崩溃

## 问题原因

设置聊天室管理员后，云信服务器自动发送的通知消息attachment为null，客户端未做判空处理导致崩溃

## 解决方案

客户端判断消息类型，当attachment为null时直接忽略该消息。参考文档：https://doc.yunxin.163.com/messaging/guide/TI1MDE5MzA?platform=android#%E8%81%8A%E5%A4%A9%E5%AE%A4%E9%80%9A%E7%9F%A5%E6%B6%88%E6%81%AF
