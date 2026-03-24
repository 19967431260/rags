---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: UI刷新
platform: HarmonyOS
title: 鸿蒙UIKit消息删除后UI不刷新
root_cause: 并发刷新问题，SDK消息回调与业务刷新操作冲突
solution: 使用setTimeout延迟1秒再刷新，或将操作分开延迟执行
customers: ["台州浩瀚网络"]
source: chat_history
tags: ["HarmonyOS", "UIKit", "UI刷新", "deleteMessage", "并发"]
created: 2025-02-07
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙UIKit消息删除后UI不刷新

## 问题详情

**现象**：
调用deleteMessage和insertMessage后UI不刷新，偶现问题，与业务代码中发送服务器消息的时序有关

**环境信息**：
- 平台：HarmonyOS
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 测试场景1：不调用业务接口，直接调用SDK刷新方法 → UI正常刷新
2. 测试场景2：调用业务接口但不发送云信消息 → UI正常刷新
3. 测试场景3：调用业务接口并发送云信消息后 → UI不刷新

**关键发现**：问题与并发刷新有关，收到消息时也会触发刷新

## 问题原因

并发刷新问题，SDK消息回调与业务刷新操作冲突

## 解决方案

使用setTimeout延迟1秒再刷新，或将操作分开延迟执行

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
