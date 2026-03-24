---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: 苹果推送payload配置body不显示
root_cause: 客户代码配置问题
solution: 配置NIMPushNotificationDisplayTypeDetail显示详细内容，参考文档：https://doc.yunxin.163.com/messaging/guide/zM4MDQzOTk?platform=iOS
customers: ["VIP云信-东莞市伊洛信息科技有限公司"]
source: chat_history
tags: ["APNs", "推送", "payload", "body", "iOS"]
created: 2025-02-21
updated: 2026-03-20
---

## 问题：iOS 苹果推送payload配置body不显示

## 问题详情

**现象**：
配置苹果推送payload后，推送横幅body一直只显示"您收到一条新消息"

## 排查过程

1. 确认初始化配置 → NIMPushNotificationDisplayTypeDetail
2. 验证配置成功 → updateApnsSetting调用成功
3. 客户自查 → 发现是自身代码问题

## 问题原因

客户代码配置问题

## 解决方案

配置NIMPushNotificationDisplayTypeDetail显示详细内容，参考文档：https://doc.yunxin.163.com/messaging/guide/zM4MDQzOTk?platform=iOS

## 其他触发场景

