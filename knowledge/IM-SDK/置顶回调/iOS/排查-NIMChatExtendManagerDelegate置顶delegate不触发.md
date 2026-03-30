---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 置顶回调
platform: iOS
title: NIMChatExtendManagerDelegate置顶delegate不触发
root_cause: 置顶delegate只在多端登录时触发，单端操作时置顶方法本身有回调。
solution: 置顶delegate仅多端登录场景触发，单端置顶操作在置顶方法回调中处理UI即可，需业务层本地处理。
customers: ['无锡枇杷园餐饮管理有限公司']
source: chat_history
tags: ['置顶', 'delegate', '多端登录', 'iOS', 'ChatExtendManager']
created: 2025-02-28
updated: 2026-03-23
---

## 问题：iOS NIMChatExtendManagerDelegate置顶delegate不触发

## 问题详情

**现象**：
客户反馈NIMChatExtendManagerDelegate的置顶delegate方法不走。

**环境信息**：
- 平台：iOS
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

置顶delegate只在多端登录时触发，单端操作时置顶方法本身有回调。

## 解决方案

置顶delegate仅多端登录场景触发，单端置顶操作在置顶方法回调中处理UI即可，需业务层本地处理。

## 其他触发场景

（合并时在此处追加：`- [iOS] NIMChatExtendManagerDelegate置顶delegate不触发，来源：['无锡枇杷园餐饮管理有限公司']，2026-03-23`）
