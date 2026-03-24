---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: Android
title: enterChatRoomEx返回404错误
root_cause: 聊天室不存在或状态为关闭
solution: 确认聊天室ID存在且状态为开启，如关闭需调用服务端API开启
customers: ['景群數位互動有限公司']
source: chat_history
tags: ['enterChatRoomEx', '404', '聊天室', '加入失败']
created: 2025-01-01
updated: 2026-03-23
---

## 问题：Android enterChatRoomEx返回404错误

## 问题详情

**现象**：
调用NIMClient.getService(ChatRoomService.class).enterChatRoomEx(data, 1)返回onFailed，code是404

## 排查过程



## 问题原因

聊天室不存在或状态为关闭

## 解决方案

确认聊天室ID存在且状态为开启，如关闭需调用服务端API开启

## 其他触发场景

（合并时在此处追加）
