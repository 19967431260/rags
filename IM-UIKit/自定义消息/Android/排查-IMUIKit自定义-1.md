---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 自定义消息
platform: Android
title: IM UIKit自定义消息解析显示[未知消息体]
root_cause: 自定义消息ViewHolder中类型判断逻辑有误。
solution: 1. 使用ChatKitClient.addCustomAttach和addCustomViewHolder注册自定义消息
2. 注册时机要在ChatKitClient.init(context)之后
3. 参考ChatStickerViewHolder实现
4. 检查ViewHolder中类型判断逻辑
customers: ["广州元沣"]
source: chat_history
tags: ["IM-UIKit", "自定义消息", "ViewHolder", "Android", "ChatKitClient"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：Android IM UIKit自定义消息解析显示[未知消息体]

## 问题详情

**现象**：
客户使用IM UIKit V9自定义消息，发送成功但解析未生效，显示[未知消息体]。

## 排查过程

1. 客户反馈自定义消息显示异常
2. 检查CustomerSampleAttachment实现
3. 发现传字符串方式不正确
4. 检查注册时机
5. 建议调整到ChatKitClient.init后注册
6. 最终发现ViewHolder中类型判断问题

## 问题原因

自定义消息ViewHolder中类型判断逻辑有误。

## 解决方案

1. 使用ChatKitClient.addCustomAttach和addCustomViewHolder注册自定义消息
2. 注册时机要在ChatKitClient.init(context)之后
3. 参考ChatStickerViewHolder实现
4. 检查ViewHolder中类型判断逻辑

## 其他触发场景

