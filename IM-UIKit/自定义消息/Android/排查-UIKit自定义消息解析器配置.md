---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 自定义消息
platform: Android
title: UIKit自定义消息解析器配置
root_cause: 需要实现自定义消息解析器，且后台发送的自定义消息attachment结构需要正确。
solution: 1. 实现自定义消息解析器；2. 确保后台发送的自定义消息attachment结构正确，能成功反序列化。
customers: ["广州元沣智能科技有限公司"]
source: chat_history
tags: ["IM-UIKit", "自定义消息", "Android", "解析器", "attachment"]
created: 2025-06-25
updated: 2025-03-23
---

## 问题：Android UIKit自定义消息解析器配置

## 问题详情

**现象**：
Android端UIKit接收到后台发送的自定义消息，message.getAttachment()为空，无法解析。

## 排查过程

1. 确认消息类型 → 是自定义消息
2. 检查attachment → 为空
3. 分析原因 → 需要实现自定义消息解析器
4. 检查attachment结构 → 可能结构不对未反序列化成功

**关键发现**：需要实现自定义消息解析器，且后台发送的自定义消息attachment结构需要正确

## 问题原因

需要实现自定义消息解析器，且后台发送的自定义消息attachment结构需要正确。

## 解决方案

1. 实现自定义消息解析器；2. 确保后台发送的自定义消息attachment结构正确，能成功反序列化。

## 其他触发场景

