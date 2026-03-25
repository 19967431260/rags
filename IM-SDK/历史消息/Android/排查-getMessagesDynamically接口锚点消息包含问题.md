---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息
platform: Android
title: getMessagesDynamically接口锚点消息包含问题
root_cause: SDK接口实现问题，getMessagesDynamically接口返回了不应包含的锚点消息
solution: SDK内部根据本地数据库自增id去重。如果消息对象不包含getMessageId，去重逻辑不会生效。建议使用queryMessageListByUuidBlock接口查出来的对象作为锚点。
customers: ["罗克佳华"]
source: chat_history
tags: ["getMessagesDynamically","锚点消息","消息去重","queryMessageListByUuidBlock"]
created: 2025-05-28
updated: 2025-03-20
---

## 问题：Android getMessagesDynamically接口锚点消息包含问题

## 问题详情

**现象**：
调用getMessagesDynamically接口查询历史消息，接口定义不包含锚点消息，但实际返回结果包含了锚点消息。

**复现步骤**：
1. 搜索一条消息
2. 点击后查询到三条数据
3. 断点发现getMessagesDynamically返回结果包含了锚点消息

**环境信息**：
- SDK 版本：IM V10
- 平台：Android

## 排查过程

1. 客户反馈搜索一条消息，点击后查询到三条数据
2. 断点发现getMessagesDynamically返回结果包含了锚点消息
3. 与接口定义不符（定义不包含锚点）

**关键发现**：SDK内部根据本地数据库自增id去重，如果消息对象不包含getMessageId，去重逻辑不会生效

## 问题原因

SDK接口实现问题，getMessagesDynamically接口返回了不应包含的锚点消息

## 解决方案

SDK内部根据本地数据库自增id去重。如果消息对象不包含getMessageId，去重逻辑不会生效。建议使用queryMessageListByUuidBlock接口查出来的对象作为锚点。

问题已提给研发确认修复。

## 其他触发场景

