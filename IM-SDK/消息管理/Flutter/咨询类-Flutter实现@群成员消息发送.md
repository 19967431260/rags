---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息管理
platform: Flutter
title: Flutter实现@群成员消息发送
root_cause: 
solution: 通过消息的serverExtension扩展字段实现@功能：1. 将被@的用户列表封装到serverExtension字段；2. 配置强制推送确保被@用户收到提醒；3. 接收方解析serverExtension判断自己是否被@；4. @所有人可使用特殊标识(如all)表示；5. 在会话列表显示【xxx提及了你】等提示。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['Flutter', '@消息', 'serverExtension', '强制推送', '群消息']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Flutter实现@群成员消息发送

## 问题详情

**现象**：
需要在Flutter中实现@好友发送消息功能，包括@单人和@多人，以及@所有人。

## 排查过程



## 问题原因



## 解决方案

通过消息的serverExtension扩展字段实现@功能：1. 将被@的用户列表封装到serverExtension字段；2. 配置强制推送确保被@用户收到提醒；3. 接收方解析serverExtension判断自己是否被@；4. @所有人可使用特殊标识(如all)表示；5. 在会话列表显示【xxx提及了你】等提示。

## 其他触发场景

（合并时在此处追加）
