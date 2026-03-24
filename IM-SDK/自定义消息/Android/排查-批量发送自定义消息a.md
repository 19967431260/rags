---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 自定义消息
platform: Android
title: 批量发送自定义消息attachment type为0
root_cause: 客户端没有正确解析自定义消息，未走到自定义解析器
solution: 安卓端需要实现自定义消息解析器（MsgAttachmentParser），如果attachment为空说明没有解析成功
customers: ["即客"]
source: chat_history
tags: ["自定义消息", "attachment", "type", "批量发送", "解析器"]
created: 2025-02-07
updated: 2026-03-20
---

## 问题：Android 批量发送自定义消息attachment type为0

## 问题详情

**现象**：
使用批量发送点对点普通消息接口发送自定义消息，客户端收到的attachment的type为0，但body中已定义type字段。

## 排查过程

1. 检查body传参 → 写法看起来没问题
2. 检查客户端解析 → 需要确认是否走到自定义解析器
3. 分析 → 安卓端需要通过自定义解析器解析attachment

## 问题原因

客户端没有正确解析自定义消息，未走到自定义解析器

## 解决方案

安卓端需要实现自定义消息解析器（MsgAttachmentParser），如果attachment为空说明没有解析成功

## 其他触发场景
- [Android] 批量发送自定义消息attachment type为0，来源：['即客']，2026-03-20
- [Android] 批量发送自定义消息attachment type为0，来源：['即客']，2026-03-20

