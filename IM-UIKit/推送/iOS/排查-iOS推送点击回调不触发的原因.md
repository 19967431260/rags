---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 推送
platform: iOS
title: iOS推送点击回调不触发的原因
root_cause: iOS推送点击回调需要正确配置UNUserNotificationCenter委托
solution: 确保正确设置UNUserNotificationCenter的委托，并在委托方法中处理推送点击事件。
customers: ["武汉市渺寇午科技有限公司"]
source: chat_history
tags: ["iOS", "推送", "点击回调", "UNUserNotificationCenter"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS iOS推送点击回调不触发的原因

## 问题详情

**现象**：
iOS推送点击回调不触发。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：iOS推送点击回调需要正确配置UNUserNotificationCenter委托

## 问题原因

iOS推送点击回调需要正确配置UNUserNotificationCenter委托

## 解决方案

确保正确设置UNUserNotificationCenter的委托，并在委托方法中处理推送点击事件。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
