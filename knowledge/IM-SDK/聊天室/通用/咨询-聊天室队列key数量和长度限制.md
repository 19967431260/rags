---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 聊天室
platform: 通用
title: 聊天室队列key数量和长度限制
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 聊天室队列key数量和长度限制

## 问题描述

客户咨询聊天室队列单条消息的key数量和字符限制

## 解答

聊天室队列默认100个key，最大支持1000个key。单value限制4096字符，总量不限制。但建议不要存储过大，否则列出所有元素时数据量太大会导致处理慢、卡UI。

## 标签

- 聊天室
- 队列
- key限制
- 长度限制

## 客户

- FVIP云信-深圳富旅奇缘

## 会话日期

2025-02-17
