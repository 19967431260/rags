---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: FCM推送杀掉进程收不到
root_cause: 管理后台配置的FCM推送证书有问题，导致fcm服务器返回403
solution: 检查管理后台FCM推送证书配置。APP运行时走的是SDK内置消息提醒，不是推送。
customers: ["元拓科技（大连）有限公司"]
source: chat_history
tags: ["FCM","推送","403","证书配置","海外"]
created: 2025-06-16
updated: 2025-06-16
---

## 问题：Android FCM推送杀掉进程收不到

## 问题详情

**现象**：
海外应用使用FCM推送，杀掉进程后收不到推送，但app运行时正常。

## 排查过程

1. 检查FCM推送证书配置 → 检查证书
2. 查看服务器返回日志 → 查看日志
3. 发现fcm服务器返回403错误 → 发现错误码
4. 确认推送证书配置有问题 → 确定问题根因

**关键发现**：管理后台配置的FCM推送证书有问题，导致fcm服务器返回403

## 问题原因

管理后台配置的FCM推送证书有问题，导致fcm服务器返回403

## 解决方案

检查管理后台FCM推送证书配置。APP运行时走的是SDK内置消息提醒，不是推送。

## 其他触发场景

