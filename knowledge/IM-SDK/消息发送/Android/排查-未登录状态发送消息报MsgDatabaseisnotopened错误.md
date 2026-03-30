---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: 未登录状态发送消息报MsgDatabase is not opened错误
root_cause: 未登录状态下调用发送消息接口，SDK数据库未初始化完成
solution: 在sendMessage之前检查登录状态，非LOGINED状态时拦截发送请求，或给用户提示正在重连并提供重发按钮
customers: ["VIP云信-武汉无毁"]
source: chat_history
tags: ["MsgDatabase", "未登录", "发送消息", "Android", "crash", "LOGINED"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：未登录状态发送消息报MsgDatabase is not opened错误

## 问题详情

**现象**：
Android端在断线重连过程中调用sendMessage发送消息时，抛出异常MsgDatabase is not opened. Please login first!，应用出现crash

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈断线重连时发消息报错
2. 确认报错为java.lang.IllegalStateException
3. 建议在非LOGINED状态拦截发消息操作
4. 建议给用户提示正在重连，并暴露重发按钮

## 根因分析

未登录状态下调用发送消息接口，SDK数据库未初始化完成

## 解决方案

在sendMessage之前检查登录状态，非LOGINED状态时拦截发送请求，或给用户提示正在重连并提供重发按钮

## 其他触发场景

（无）
