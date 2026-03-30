---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 消息接收
platform: Android
title: Android收不到消息Push binder dead
root_cause: push进程崩溃或被系统杀死
solution: push进程崩溃导致，建议抓取logcat日志进一步分析原因
customers: ["深圳市家家顺-乐有家"]
source: chat_history
tags: ["Android", "收不到消息", "Push binder dead", "push进程"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android收不到消息Push binder dead

## 问题详情

**现象**：
Android端在17:25-17:45期间收不到消息，查不到聊天记录，日志显示Push binder dead。

**环境信息**：
- 平台：Android

## 排查过程

1. 分析SDK日志
2. 查找Push binder dead错误
3. 确认push进程状态

## 根因分析

push进程崩溃或被系统杀死

## 解决方案

push进程崩溃导致，建议抓取logcat日志进一步分析原因

## 其他触发场景

（无）
