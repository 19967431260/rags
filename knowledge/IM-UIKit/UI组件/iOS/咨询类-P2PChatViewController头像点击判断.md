---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-UIKit
feature: UI组件
platform: iOS
title: P2PChatViewController头像点击判断
root_cause: 
solution: 使用model?.message?.isSelf判断点击的是否为自己发送的消息。
customers: ['厦门嘉运恒泰']
source: chat_history
tags: ['iOS', 'UIKit', '头像', 'isSelf', '判断']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：P2PChatViewController头像点击判断

## 问题详情

**现象**：
客户重写didTapAvatarView方法后需要判断点击的是不是自己。

## 排查过程



## 问题原因



## 解决方案

使用model?.message?.isSelf判断点击的是否为自己发送的消息。

## 其他触发场景

（合并时在此处追加）
