---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: Windows
title: Windows聊天室回调重复注册问题
root_cause: 离开聊天室时只调用Exit没有注销回调注册，导致再次进入后回调重复触发。
solution: 离开聊天室时注销回调注册：nim_chatroom::ChatRoom::RegEnterCb(nullptr); nim_chatroom::ChatRoom::RegSendMsgAckCb(nullptr); nim_chatroom::ChatRoom::RegReceiveMsgCb(nullptr);
customers: ['深圳市合渝网络技术对接群']
source: chat_history
tags: ['Windows', '聊天室', '回调', '重复', 'Exit', 'RegEnterCb']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：Windows Windows聊天室回调重复注册问题

## 问题详情

**现象**：
Windows端客户进入聊天室时注册了消息回调，离开房间只调用Exit，再次进入后会收到重复的消息。

## 排查过程

1. 客户询问进入房间注册的消息回调，离开房间是否需要注销
2. 技术支持回复可以注销
3. 客户说明目前只调用了Exit，离开再进入后会收到重复消息
4. 询问对应注销API
5. 提供注销回调的API：RegEnterCb(nullptr)、RegSendMsgAckCb(nullptr)、RegReceiveMsgCb(nullptr)

## 问题原因

离开聊天室时只调用Exit没有注销回调注册，导致再次进入后回调重复触发。

## 解决方案

离开聊天室时注销回调注册：nim_chatroom::ChatRoom::RegEnterCb(nullptr); nim_chatroom::ChatRoom::RegSendMsgAckCb(nullptr); nim_chatroom::ChatRoom::RegReceiveMsgCb(nullptr);

## 其他触发场景

（合并时在此处追加）
