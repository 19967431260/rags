---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 聊天室
platform: Android
title: 聊天室sendMessage返回code=7问题
root_cause: code=7是客户业务层自己定义的toast提示，非云信SDK错误码
solution: 检查业务层代码，确认什么情况下会抛出code=7的提示
customers: ['杭州飓风网络有限公司']
source: chat_history
tags: ['聊天室', 'sendMessage', 'code=7', '错误码']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Android 聊天室sendMessage返回code=7问题

## 问题详情

**现象**：
客户调用NIMChatRoomSDK.getChatRoomService().sendMessage发送图片时，返回错误码code=7。

## 排查过程

1. 检查错误码定义 → 云信无此错误码
2. 确认是业务层toast提示

## 问题原因

code=7是客户业务层自己定义的toast提示，非云信SDK错误码

## 解决方案

检查业务层代码，确认什么情况下会抛出code=7的提示

## 其他触发场景

（合并时在此处追加）
