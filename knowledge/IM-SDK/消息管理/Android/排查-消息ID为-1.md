---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息管理
platform: Android
title: Android获取消息时ID为-1表示消息未入库
root_cause: 消息ID为-1说明该消息尚未入库，messageId字段尚未被SDK赋值
solution: 以uuid为准，不要使用messageId作为消息标识；messageId为-1的消息表示还未完成入库流程
customers: ["时间在线"]
source: chat_history
tags: ["Android", "messageId", "uuid", "消息ID"]
created: 2025-07-21
updated: 2025-07-25
---

## 问题：Android 获取消息时 ID 为 -1 表示消息未入库

## 问题详情

**现象**：
客户获取聊天内容时，发现个别消息ID是-1，服务端能查到但本地显示异常。

## 排查过程

1. 客户提供截图，显示消息ID为-1
2. 技术支持确认：这应该是还没有入库
3. 建议以uuid为准，不要使用messageId

**关键发现**：messageId为-1说明消息尚未完成入库，SDK的消息入库是异步的。

## 问题原因

消息ID为-1表示该消息还未入库，messageId字段尚未被SDK赋值。使用messageId作为唯一标识不可靠。

## 解决方案

1. 以uuid作为消息唯一标识，不要依赖messageId
2. messageId为-1的消息表示还未完成入库流程，属正常现象，待SDK完成入库后messageId会被正确赋值
