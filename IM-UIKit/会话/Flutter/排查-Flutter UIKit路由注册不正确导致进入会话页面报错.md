---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话
platform: Flutter
title: Flutter UIKit路由注册不正确导致进入会话页面报错
root_cause: initPlugins()没有放在return MaterialApp之前执行；或者routes注册位置不对导致页面路由未生效。
solution: 1. 在return MaterialApp之前执行initPlugins()，包含ChatKitClient.init()、TeamKitClient.init()、ConversationKitClient.init()、ContactKitClient.init()、SearchKitClient.init()；\n2. 在MaterialApp的routes中注册：routes: IMKitRouter.instance.routes\n3. 确认没有重复注册路由。
customers: ["杭州云汽配配科技有限公司"]
source: chat_history
tags: ["Flutter","UIKit","路由","ChatPage","Navigator","注册"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：Flutter Flutter UIKit路由注册不正确导致进入会话页面报错

## 问题详情

**现象**：
客户Flutter端注册了UIKit的会话列表页面能正常进入，但单聊页面（ChatPage）跳转时报错"没有找到这个路径"。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服排查：检查routes是否在根Widget下注册 → 排查路由
2. 是否注册了多次导致覆盖 → 重复注册问题

**关键发现**：initPlugins()没有放在return MaterialApp之前执行；或者routes注册位置不对导致页面路由未生效。

## 问题原因

initPlugins()没有放在return MaterialApp之前执行；或者routes注册位置不对导致页面路由未生效。

## 解决方案

1. 在return MaterialApp之前执行initPlugins()，包含ChatKitClient.init()、TeamKitClient.init()、ConversationKitClient.init()、ContactKitClient.init()、SearchKitClient.init()；
2. 在MaterialApp的routes中注册：routes: IMKitRouter.instance.routes
3. 确认没有重复注册路由。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
