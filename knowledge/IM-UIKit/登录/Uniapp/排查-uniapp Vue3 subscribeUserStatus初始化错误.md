---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 登录
platform: Uniapp
title: uniapp Vue3 subscribeUserStatus初始化错误
root_cause: subscribeUserStatus的执行时机早于其初始化，导致JavaScript ReferenceError。
solution: 将subscribeUserStatus调用移至connectWatch之前执行，即可解决初始化顺序问题。
customers: ["武汉毅麦信息科技有限公司"]
source: chat_history
tags: ["subscribeUserStatus","初始化","Uniapp","Vue3","ReferenceError"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：Uniapp uniapp Vue3 subscribeUserStatus初始化错误

## 问题详情

**现象**：
客户在uniapp Vue3中使用UIKit时遇到JavaScript错误：Encountered an uncaught exception... ReferenceError: Cannot access 'subscribeUserStatus' before initialization

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服研发确认是UIKit demo代码问题，将subscribeUserStatus换到connectWatch前面执行后问题解决 → 代码顺序问题

**关键发现**：subscribeUserStatus的执行时机早于其初始化，导致JavaScript ReferenceError。

## 问题原因

subscribeUserStatus的执行时机早于其初始化，导致JavaScript ReferenceError。

## 解决方案

将subscribeUserStatus调用移至connectWatch之前执行，即可解决初始化顺序问题。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
