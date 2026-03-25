---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "自定义消息"
platform: "iOS"
title: "自定义消息attachment状态更新后encode/decode不一致"
root_cause: "发送消息时会触发消息的encode/decode过程，如果直接发送已经被修改过的消息对象，可能导致encode时使用的是修改后的数据，但SDK内部处理过程中又触发了decode，使用的是缓存或原始数据，导致状态不一致。"
solution: "发送消息时不要直接发送已存在的消息对象，建议重新构建一个新的消息对象来发送。内容可以复用原消息的内容，但要重新给新消息对象赋值一遍，避免发送过程中消息对象有修改导致encode/decode数据不一致。"
customers: ["FVIP-深圳秀蛋"]
source: "chat_history"
tags: ["自定义消息", "attachment", "encode", "decode", "status", "saveMessage", "sendMessage", "iOS"]
created: "2025-09-26"
updated: "2026-03-20"
---

## 问题：iOS 自定义消息attachment状态更新后encode/decode不一致

## 问题详情

**现象**：
客户实现自定义图片消息，在saveMessage后修改attachment的status字段，但发送时发现decode出来的status仍是旧值。

## 排查过程

1. 检查客户代码逻辑：saveMessage插入本地消息(status=2发送中) → 上传图片成功 → 修改status=0 → delete本地消息 → sendMessage发送
2. 发现sendMessage时会触发decodeAttachment，此时status仍为2
3. 排查发现客户直接发送了已修改过的msg对象
4. 建议重新构建消息对象后问题解决

## 问题原因

发送消息时会触发消息的encode/decode过程，如果直接发送已经被修改过的消息对象，可能导致encode时使用的是修改后的数据，但SDK内部处理过程中又触发了decode，使用的是缓存或原始数据，导致状态不一致。

## 解决方案

发送消息时不要直接发送已存在的消息对象，建议重新构建一个新的消息对象来发送。内容可以复用原消息的内容，但要重新给新消息对象赋值一遍，避免发送过程中消息对象有修改导致encode/decode数据不一致。

## 其他触发场景
