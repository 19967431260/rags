---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: iOS
title: iOS端subMessages函数查询引用消息返回空
root_cause: 使用方式错误。subMessages是查「子消息列表」的方法，需要传入被引用的消息（第一条消息），返回的是引用过这条消息的列表，而不是通过消息2去查被引用的消息1
solution: 被引用的消息id直接保存在threadOption中，可直接获取，不需要调用subMessages去查询
customers: ["FVIP-云信-上海抱朴"]
source: chat_history
tags: ["iOS", "subMessages", "引用消息", "子消息"]
created: 2025-08-12
updated: 2025-03-25
---

## 问题：iOS subMessages查询引用消息返回空

## 问题详情

**现象**：
iOS端调用subMessages函数去取引用消息，返回数组为空

**复现步骤**：
1. 发送一条带引用的消息（引用自己发出的上一条消息）
2. 调用subMessages函数用该消息去查询
3. 返回空数组

## 排查过程

1. 客服咨询subMessages函数的正确用法 → 确认这是查询「子消息列表」的方法
2. 分析函数参数 → 需要传入被引用的消息（第一条消息），而不是回复消息

**关键发现**：subMessages返回的是引用过这条消息的列表，而不是被引用的消息

## 问题原因

使用方式错误。subMessages是查「子消息列表」的方法，需要传入被引用的消息（第一条消息），返回的是引用过这条消息的列表，而不是通过消息2去查被引用的消息1。

## 解决方案

被引用的消息id直接保存在threadOption中，可直接获取，不需要调用subMessages去查询。

## 其他触发场景

- [iOS] iOS端如何判断消息是否是引用消息，来源：FVIP-云信-上海抱朴，2025-03-25
