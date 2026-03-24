---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 事件订阅
platform: Android
title: EventSubscribeService注册事件报错invalid params
root_cause: EventSubscribeRequest为空或未设置publishers字段
solution: 检查registerEventSubscribe方法调用时传入的EventSubscribeRequest是否为空，是否设置了publishers字段
customers: ["南宁小清柠"]
source: chat_history
tags: ["EventSubscribeService", "registerEventSubscribe", "invalid params", "Android", "事件订阅"]
created: 2025-02-28
updated: 2026-03-20
---

## 问题：Android EventSubscribeService注册事件报错invalid params

## 问题详情

**现象**：
Android端调用EventSubscribeService#registerEventSubscribe时报错java.lang.IllegalArgumentException: invalid params!

## 排查过程

（从会话记录提取）

## 问题原因

EventSubscribeRequest为空或未设置publishers字段

## 解决方案

检查registerEventSubscribe方法调用时传入的EventSubscribeRequest是否为空，是否设置了publishers字段

## 其他触发场景
- [Android] EventSubscribeService注册事件报错invalid params，来源：['南宁小清柠']，2026-03-20
- [Android] EventSubscribeService注册事件报错invalid params，来源：['南宁小清柠']，2026-03-20

