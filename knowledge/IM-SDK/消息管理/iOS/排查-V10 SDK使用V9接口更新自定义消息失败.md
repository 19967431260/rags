---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "消息管理"
platform: "iOS"
title: "V10 SDK使用V9接口更新自定义消息失败"
root_cause: "V10 SDK虽然兼容V9接口，但在消息对象处理上与V9存在差异。客户业务逻辑中先saveMessage插入本地消息，然后修改attachment后再sendMessage，这个过程中消息对象被多次修改，导致发送时触发的encodeAttachment使用的是旧数据。"
solution: "发送消息时不要直接发送已有的消息对象，建议重新构建一个新的消息对象来发送，内容可以复用原消息的内容，但要重新给新消息对象赋值一遍，避免发送过程中消息对象有修改导致状态不一致。"
customers: ["FVIP-深圳秀蛋"]
source: "chat_history"
tags: ["V10", "V9", "updateMessage", "自定义消息", "saveMessage", "sendMessage", "iOS"]
created: "2025-09-25"
updated: "2026-03-20"
---

## 问题：iOS V10 SDK使用V9接口更新自定义消息失败

## 问题详情

**现象**：
客户使用V10 SDK但调用V9的updateMessage接口更新自定义消息时失败，同样的代码在V9 SDK上正常运行。

## 排查过程

1. 确认客户当前SDK版本为V10，使用V9的API
2. 客户尝试将NIMMessage转为V2NIMMessage但无法直接转换
3. 排查日志发现sendMessage调用前存在多次saveMessage操作
4. 最终发现客户业务逻辑中消息对象被多次修改导致状态不一致

## 问题原因

V10 SDK虽然兼容V9接口，但在消息对象处理上与V9存在差异。客户业务逻辑中先saveMessage插入本地消息，然后修改attachment后再sendMessage，这个过程中消息对象被多次修改，导致发送时触发的encodeAttachment使用的是旧数据。

## 解决方案

发送消息时不要直接发送已有的消息对象，建议重新构建一个新的消息对象来发送，内容可以复用原消息的内容，但要重新给新消息对象赋值一遍，避免发送过程中消息对象有修改导致状态不一致。

## 其他触发场景
