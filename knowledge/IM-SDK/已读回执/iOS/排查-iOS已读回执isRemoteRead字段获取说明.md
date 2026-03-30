---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 已读回执
platform: iOS
title: iOS已读回执isRemoteRead字段获取说明
root_cause: isRemoteRead等字段在debug打印时不展示但实际存在；markAllMessagesReadInSession只清理本地未读数，不会发送已读回执给对方
solution: 1. 通过SDK接口获取message实例后直接获取isRemoteRead字段
2. markAllMessagesReadInSession仅清理本地未读，sendMessageReceipt才是发送已读回执给对方
3. 对方收到已读回执后，消息的isRemoteRead才会变为YES
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# iOS已读回执isRemoteRead字段获取说明

## 问题描述

iOS端使用已读回执功能，但查询发送出去的message消息体中找不到isRemoteRead字段

## 问题背景

1. 确认消息重新获取方式
2. 排查发现部分字段在debug时不展示但实际存在
3. 区分markAllMessagesReadInSession和sendMessageReceipt的区别

## 根因分析

isRemoteRead等字段在debug打印时不展示但实际存在；markAllMessagesReadInSession只清理本地未读数，不会发送已读回执给对方

## 解决方案

1. 通过SDK接口获取message实例后直接获取isRemoteRead字段
2. markAllMessagesReadInSession仅清理本地未读，sendMessageReceipt才是发送已读回执给对方
3. 对方收到已读回执后，消息的isRemoteRead才会变为YES

## 标签

- 已读回执
- isRemoteRead
- iOS
- markAllMessagesReadInSession
- sendMessageReceipt

## 客户

- 积木成林

## 会话日期

2025-02-20
