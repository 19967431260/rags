---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息扩展字段
platform: iOS
title: 消息发送失败报错参数错误ext超限
root_cause: 消息扩展字段(ext)超过限制，默认限制3072字节
solution: 可在控制台调整消息扩展字段大小限制
customers: ["深圳市镜玩-觅伊"]
source: chat_history
tags: ["消息扩展","ext","参数错误","414","大小限制"]
created: 2025-02-19
updated: 2025-03-20
---

## 问题：iOS 消息发送失败报错参数错误ext超限

## 问题详情

**现象**：
iOS端发送礼物消息失败，报错Error Domain=NIMRemoteErrorDomain Code=414 "参数错误"。消息包含较大的giftSetData扩展信息。

**复现步骤**：
1. 构造包含大扩展字段的消息
2. 发送消息
3. 返回414错误

## 排查过程

1. 获取SDK日志 → 获取详细日志
2. 分析发现ext exceed limit, limit 3072 → 确认超限

**关键发现**：ext字段超过3072字节限制

## 问题原因

消息扩展字段(ext)超过限制，默认限制3072字节。

## 解决方案

可在控制台调整消息扩展字段大小限制。

## 其他触发场景

