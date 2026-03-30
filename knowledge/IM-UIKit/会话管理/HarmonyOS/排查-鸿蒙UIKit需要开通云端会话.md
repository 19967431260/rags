---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-UIKit
feature: 会话管理
platform: HarmonyOS
title: 鸿蒙UIKit需要开通云端会话
root_cause: 鸿蒙UIKit组件对接的是云端会话，客户未开通该功能
solution: 需要开通云端会话功能，老套餐没有自助开通入口需联系技术支持内部申请开通
customers: ['北京久幺幺']
source: chat_history
tags: ['鸿蒙', 'UIKit', '云端会话', 'V10', '会话列表']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙UIKit需要开通云端会话

## 问题详情

**现象**：
客户使用鸿蒙UIKit demo导入后，发现不显示消息会话列表。

## 排查过程

1. 客户反馈鸿蒙UIKit demo不显示会话列表
2. 经确认：鸿蒙是V10版本SDK，UIKit使用的是云端会话功能
3. V9 SDK使用的是本地会话
**关键发现**：老套餐没有自助开通云端会话的入口

## 问题原因

鸿蒙UIKit组件对接的是云端会话，客户未开通该功能

## 解决方案

需要开通云端会话功能，老套餐没有自助开通入口需联系技术支持内部申请开通

## 其他触发场景

（合并时在此处追加）
