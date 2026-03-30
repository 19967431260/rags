---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话列表
platform: Web
title: Web端ConversationContainer初始化时数据尚未加载导致不显示
root_cause: 组件初始化时NIM实例尚未完成数据同步，ConversationContainer创建时拿到的是空数据，之后即使数据到达，组件也没有收到更新通知
solution: 使用store方式管理会话数据：在视图组件创建之前先确保NIM实例完成初始化和数据同步，或者在组件mount时主动从store获取最新数据触发重新渲染。避免在数据未就绪时过早创建视图组件。
customers: ["西安云海信息技术有限责任"]
source: chat_history
tags: ["ConversationContainer","React","视图初始化","store","会话列表","Web"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：Web Web端ConversationContainer初始化时数据尚未加载导致不显示

## 问题详情

**现象**：
Web端使用React集成云信SDK，登录成功并获取到会话列表数据，但ConversationContainer组件不显示任何内容，empty视图也不显示。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Web
- 其他：React集成

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服排查确认是时序问题：视图组件先创建完成，然后nim才获取到会话列表数据 → 定位到时序问题
2. 导致ConversationContainer没有被通知到数据更新 → 确认根因

**关键发现**：组件初始化时NIM实例尚未完成数据同步，ConversationContainer创建时拿到的是空数据

## 问题原因

组件初始化时NIM实例尚未完成数据同步，ConversationContainer创建时拿到的是空数据，之后即使数据到达，组件也没有收到更新通知

## 解决方案

使用store方式管理会话数据：
1. 在视图组件创建之前先确保NIM实例完成初始化和数据同步
2. 或者在组件mount时主动从store获取最新数据触发重新渲染
3. 避免在数据未就绪时过早创建视图组件

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
