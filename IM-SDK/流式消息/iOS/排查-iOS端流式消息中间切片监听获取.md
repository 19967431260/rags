---
track_type: 排查类
sub_type: 功能缺失
product: IM-SDK
feature: 流式消息
platform: iOS
title: iOS端流式消息中间切片监听获取
root_cause: 群流式消息功能未开通，需要申请开通该功能
solution: 申请开通群流式消息功能，提供appkey和详细场景（如用户和多个客服的群聊场景）。配置开通后实时生效。
customers: ["智己汽车"]
source: chat_history
tags: ["流式消息","群消息","iOS","onReceiveMessagesModified","功能开通"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：iOS iOS端流式消息中间切片监听获取

## 问题详情

**现象**：
iOS端接收流式消息时，onRecvMessages收到第一个切片，onReceiveMessagesModified收到合并后的消息，但中间的切片无法获取。测试发现只能收到最后完整的消息。

## 排查过程

1. 检查SDK日志和消息id → 发现是群消息
2. 确认群流式消息功能未开通 → 需要申请开通

**关键发现**：群流式消息需要单独申请开通，单聊默认支持

## 问题原因

群流式消息功能未开通，需要申请开通该功能

## 解决方案

申请开通群流式消息功能，提供appkey和详细场景（如用户和多个客服的群聊场景）。配置开通后实时生效。

## 其他触发场景

（暂无）
