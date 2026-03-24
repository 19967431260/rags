---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 本地消息插入
platform: iOS
title: insertMessageToLocal插入消息时间戳问题
root_cause: iOS的timeIntervalSince1970返回秒级时间戳，而云信消息时间戳使用毫秒级
solution: 将Date().timeIntervalSince1970乘以1000转换为毫秒级时间戳，即Date().timeIntervalSince1970 * 1000。
customers: ['AB Leisure Exponent Inc']
source: chat_history
tags: ['iOS', 'insertMessageToLocal', '时间戳', '排序', '毫秒', 'Date']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：iOS insertMessageToLocal插入消息时间戳问题

## 问题详情

**现象**：
通过ChatRepo.shared.insertMessageToLocal插入本地消息后，再次通过chatRepo.getMessageList取出时，这些本地消息永远显示在列表顶部。客户使用Date().timeIntervalSince1970作为时间戳。

## 排查过程

1. 客户反馈本地消息排序异常 → 技术支持询问时间戳传入方式 → 客户使用Date().timeIntervalSince1970 → 技术支持指出消息时间精确到毫秒 → 客户确认时间位数不对 → 建议乘以1000

## 问题原因

iOS的timeIntervalSince1970返回秒级时间戳，而云信消息时间戳使用毫秒级

## 解决方案

将Date().timeIntervalSince1970乘以1000转换为毫秒级时间戳，即Date().timeIntervalSince1970 * 1000。

## 其他触发场景

（合并时在此处追加）
