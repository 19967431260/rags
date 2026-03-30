---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 已读回执
platform: Flutter
title: Flutter自定义消息已读状态显示
root_cause: 接管发送消息逻辑后未设置messageAck参数
solution: 设置messageAck为true开启已读回执
customers: ['四川珩安科技有限公司']
source: chat_history
tags: ['Flutter', '自定义消息', '已读回执', 'messageAck']
created: 2025-02-12
updated: 2026-03-23
---

## 问题：Flutter Flutter自定义消息已读状态显示

## 问题详情

**现象**：
发送的自定义消息不显示已读状态，文本消息正常

**环境信息**：
- 平台：Flutter
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈自定义消息没有已读状态
2. 检查代码发现接管了发送消息逻辑
3. 需要设置messageAck参数为true

## 问题原因

接管发送消息逻辑后未设置messageAck参数

## 解决方案

设置messageAck为true开启已读回执

## 其他触发场景

（合并时在此处追加：`- [Flutter] Flutter自定义消息已读状态显示，来源：['四川珩安科技有限公司']，2026-03-23`）
