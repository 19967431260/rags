---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: 安卓端自定义消息重发后data为空
root_cause: 客户业务层代码处理问题，非SDK问题
solution: 经客户自查，问题出在业务层代码处理逻辑。建议检查CustomAttachment.parseData的实现，确保重发消息时消息体数据正确传递。
customers: ['广州启倬信息']
source: chat_history
tags: ['自定义消息', '重发', 'data为空', '拉黑', 'Android']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：Android 安卓端自定义消息重发后data为空

## 问题详情

**现象**：
用户A拉黑用户B后，用户A发送自定义消息给用户B出现红点（发送失败）。用户B取消拉黑后，用户A点击红点重发消息，用户B收到的自定义消息data字段为空。iOS发iOS/安卓正常，安卓发安卓/iOS异常。

## 排查过程

1. 确认问题仅在点击红点重发时出现，新发送消息正常
2. 确认版本：iOS 9.7.2，安卓9.7.0
3. 客户排查后发现是自身业务代码问题

## 问题原因

客户业务层代码处理问题，非SDK问题

## 解决方案

经客户自查，问题出在业务层代码处理逻辑。建议检查CustomAttachment.parseData的实现，确保重发消息时消息体数据正确传递。

## 其他触发场景

（合并时在此处追加）
