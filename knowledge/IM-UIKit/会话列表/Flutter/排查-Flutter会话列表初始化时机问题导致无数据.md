---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话列表
platform: Flutter
title: Flutter会话列表初始化时机问题导致无数据
root_cause: 时机问题，SDK登录完成同步数据后再加载页面，ConversationRepo.onSyncFinished监听不会触发
solution: 在ConversationViewModel初始化时主动调用获取会话列表数据。反馈给研发，后续版本会修复。
customers: ["南京芷间科技有限公司"]
source: chat_history
tags: ["Flutter", "会话列表", "时机", "初始化", "UIKit"]
created: 2025-05-23
updated: 2025-03-20
---

## 问题：Flutter Flutter会话列表初始化时机问题导致无数据

## 问题详情

**现象**：
APP启动时就登录了云信，然后再打开页面，但会话列表没有数据。ConversationViewModel的_init()里的监听不触发。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Flutter

## 排查过程

1. 确认传了enableV2CloudConversation: true
2. 查看SDK日志确认登录后同步了云端会话列表
3. 发现是时机问题，如果SDK登录完成同步数据后再加载页面，监听不会触发
4. 需要在页面初始化时主动调用获取数据

## 问题原因

时机问题，SDK登录完成同步数据后再加载页面，ConversationRepo.onSyncFinished监听不会触发

## 解决方案

在ConversationViewModel初始化时主动调用获取会话列表数据。反馈给研发，后续版本会修复。

## 其他触发场景

