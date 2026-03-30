---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: 安卓端查询已撤回消息content为null
root_cause: revokeMessage成功后，服务器会自动删除云端消息，本地查询时content为null
solution: revokeMessage成功后，服务器会自动删除云端消息。本地调用deleteChattingHistory不会触发云端删除，但服务端会自动删除已撤回的消息
customers: ["FVIP-云信-上海抱朴"]
source: chat_history
tags: ["Android", "消息撤回", "queryThreadTalkHistory", "content"]
created: 2025-08-13
updated: 2025-03-25
---

## 问题：安卓端查询已撤回消息content为null

## 问题详情

**现象**：
调用queryThreadTalkHistory查询已撤回的纯文本类型消息，content为null

**复现步骤**：
1. 发送一条消息
2. 调用revokeMessage撤回消息
3. 调用deleteChattingHistory删除本地记录
4. 调用queryThreadTalkHistory查询
5. 返回的消息msgType=0，content=null

## 排查过程

1. 客服咨询为何撤回消息查询时content为null → 确认是服务端自动删除云端消息
2. 分析deleteChattingHistory行为 → 本地删除不会触发云端删除

**关键发现**：revokeMessage成功后，服务器会自动删除云端消息

## 问题原因

revokeMessage成功后，服务器会自动删除云端消息。本地调用deleteChattingHistory不会触发云端删除，但服务端会自动删除已撤回的消息。

## 解决方案

revokeMessage成功后，服务器会自动删除云端消息。本地调用deleteChattingHistory不会触发云端删除，但服务端会自动删除已撤回的消息。

## 其他触发场景

- [Android] 安卓端查询已撤回消息content为null，来源：FVIP-云信-上海抱朴，2025-03-25
