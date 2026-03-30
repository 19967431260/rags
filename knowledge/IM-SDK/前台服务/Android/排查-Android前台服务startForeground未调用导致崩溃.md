---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 前台服务
platform: Android
title: Android前台服务startForeground未调用导致崩溃
root_cause: 前台服务启动后未及时调用startForeground导致系统抛出异常
solution: 配置disableAwake解决前台服务异常。参考FAQ：https://faq.yunxin.163.com/#KB0373
customers: ['全一医疗（珠海）']
source: chat_history
tags: ['Android', '前台服务', 'startForeground', '崩溃', 'disableAwake']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android Android前台服务startForeground未调用导致崩溃

## 问题详情

**现象**：
客户Android应用部分机型报Fatal Exception: android.app.RemoteServiceException: Context.startForegroundService() did not then call Service.startForeground()异常。

## 排查过程

1. 客户反馈部分机型出现前台服务异常
2. 确认SDK版本
3. 提供FAQ链接
4. 建议配置disableAwake

## 问题原因

前台服务启动后未及时调用startForeground导致系统抛出异常

## 解决方案

配置disableAwake解决前台服务异常。参考FAQ：https://faq.yunxin.163.com/#KB0373

## 其他触发场景

（合并时在此处追加）
