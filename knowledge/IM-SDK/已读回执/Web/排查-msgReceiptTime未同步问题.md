---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 已读回执
platform: Web
title: msgReceiptTime未同步问题
root_cause: 只有收到对方发送的已读回执后，才会更新msgReceiptTime时间戳
solution: 收到对方已读回执后自动更新msgReceiptTime，使用msgReceiptTime字段即可
customers: ["圆通"]
source: chat_history
tags: ["msgReceiptTime","已读回执","时间戳"]
created: 2025-02-17
updated: 2025-03-20
---

## 问题：Web msgReceiptTime未同步问题

## 问题详情

**现象**：
session对象中msgReceiptTime字段部分会话没有值。

## 排查过程

1. 查看日志发现服务器只同步了部分会话的已读回执时间戳 → 确认现象
2. 确认需要收到对方发的已读回执才会更新时间戳 → 定位机制

**关键发现**：只有收到对方发送的已读回执后，才会更新msgReceiptTime时间戳

## 问题原因

只有收到对方发送的已读回执后，才会更新msgReceiptTime时间戳。

## 解决方案

收到对方已读回执后自动更新msgReceiptTime，使用msgReceiptTime字段即可。

## 其他触发场景

