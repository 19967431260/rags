---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 未读数
platform: Web
title: Web UIKit V10获取未读数始终为0
root_cause: 默认使用本地会话，未开启云端会话
solution: 使用window.__xkit_store__.store.localConversationStore.totalUnreadCount获取未读数。如需使用云端会话需要开启相应配置。
customers: ["山东智链云创科技发展有限公司"]
source: chat_history
tags: ["未读数", "Web", "UIKit", "V10", "localConversationStore"]
created: 2025-05-01
updated: 2025-03-20
---

## 问题：Web Web UIKit V10获取未读数始终为0

## 问题详情

**现象**：
使用localConversationStore.totalUnreadCount获取未读数，但数据对不上始终是0。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Web

## 排查过程

1. 确认SDK版本为10.7和10.8.30
2. 排查发现conversationstore是undefined
3. 确认默认使用了本地会话而非云端会话
4. 提供正确的获取方式

## 问题原因

默认使用本地会话，未开启云端会话

## 解决方案

使用window.__xkit_store__.store.localConversationStore.totalUnreadCount获取未读数。如需使用云端会话需要开启相应配置。

## 其他触发场景

