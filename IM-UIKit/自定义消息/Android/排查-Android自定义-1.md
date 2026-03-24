---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 自定义消息
platform: Android
title: Android自定义消息ViewHolder实现
root_cause: 自定义消息type与SDK内置type冲突，或ViewHolder实现问题
solution: 1. 自定义消息type使用1000以上数字避免冲突
2. 通过MessageHelper.isReceivedMessage(messageBean)判断消息方向
3. 在setUserInfo方法中控制头像显示/隐藏
customers: ["江西闪招信息技术有限公司"]
source: chat_history
tags: ["自定义消息", "ViewHolder", "Android", "UIKit", "未知消息体"]
created: 2025-02-10
updated: 2026-03-20
---

## 问题：Android Android自定义消息ViewHolder实现

## 问题详情

**现象**：
客户按文档接入自定义消息，但显示未知消息体。需要实现发送方和接收方不同UI样式。

## 排查过程

1. 检查addViewToMessageContainer实现，参考ChatRichTextMessageViewHolder
2. 确认FindJobViewHolder的super里的viewType与addCustomAttach保持一致
3. 检查parent参数和是否绑定到父布局
4. 建议将type改为1000以上避免与SDK内置type冲突

## 问题原因

自定义消息type与SDK内置type冲突，或ViewHolder实现问题

## 解决方案

1. 自定义消息type使用1000以上数字避免冲突
2. 通过MessageHelper.isReceivedMessage(messageBean)判断消息方向
3. 在setUserInfo方法中控制头像显示/隐藏

## 其他触发场景

