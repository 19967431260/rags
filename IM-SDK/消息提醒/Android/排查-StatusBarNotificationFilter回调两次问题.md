---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "消息提醒"
platform: "Android"
title: "StatusBarNotificationFilter回调两次问题"
root_cause: "旧版本SDK存在该问题，V9.20.15已优化"
solution: "升级到V9.20.15，或兼容处理两次回调的情况；推送库需要对应升级"
customers: ["北京耘想科技"]
source: "chat_history"
tags: ["StatusBarNotificationFilter", "回调", "Android", "V9.20.15"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：Android StatusBarNotificationFilter回调两次问题

## 问题详情

**现象**：
客户发现群里接收一个消息时，StatusBarNotificationFilter回调会执行两次。

## 排查过程

1. 客户提供消息ID和日志 → 49f7fee4e528499b9138fd2fa2d5bddb
2. 技术支持分析 → 日志看只有一次
3. 客户提供截图 → 确实回调两次
4. 研发分析 → 确认该版本会执行两次，后面已优化
5. 提供优化版本 → V9.20.15
6. 说明升级影响 → API不影响，但推送库要升级

## 问题原因

旧版本SDK存在该问题，V9.20.15已优化

## 解决方案

升级到V9.20.15，或兼容处理两次回调的情况；推送库需要对应升级

## 其他触发场景
