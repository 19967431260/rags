---
track_type: 排查类
sub_type: 疑似BUG
product: IM-SDK
feature: 消息发送
platform: Android
title: V9文本消息body为空的异常情况
root_cause: 疑似客户端发送消息时text字段异常为空，导致回调中body字段不存在。具体原因待进一步日志分析。
solution: 1. 业务侧在sendMessage回调或observeMsgStatus中调用NIMMessage.getContent()打印日志，确认SDK返回的content是否有值；2. 如果SDK返回的content也是空，需要往前检查发送逻辑；3. 临时方案：业务侧拦截body为空的消息并提示用户。
customers: ["深圳享笑"]
source: chat_history
tags: ["body", "text", "第三方回调", "消息发送", "V9"]
created: 2026-01-20
updated: 2026-03-15
---

## 问题：Android V9文本消息body为空的异常情况

## 问题详情

**现象**：
Android V8.9.130 SDK发送文本消息时，第三方回调收到的消息没有body字段，但业务侧发送前记录的文本内容是"好"。极少出现，1年内仅1例。

## 排查过程

1. 检查第三方回调数据 → 发现body字段不存在
2. 确认消息来源 → 安卓客户端V8.9.130
3. 确认SDK机制 → 只有text传空时body才不带
4. 对比业务记录 → 业务侧记录的是"好"

**关键发现**：SDK的text为空时body不带，但业务侧有记录文本，可能是发送过程中text丢失

## 问题原因

疑似客户端发送消息时text字段异常为空，导致回调中body字段不存在。具体原因待进一步日志分析。

## 解决方案

1. 业务侧在sendMessage回调或observeMsgStatus中调用NIMMessage.getContent()打印日志，确认SDK返回的content是否有值；2. 如果SDK返回的content也是空，需要往前检查发送逻辑；3. 临时方案：业务侧拦截body为空的消息并提示用户。

## 其他触发场景

- [Android] V9文本消息body为空的异常情况，来源：['深圳享笑']，2026-03-15
