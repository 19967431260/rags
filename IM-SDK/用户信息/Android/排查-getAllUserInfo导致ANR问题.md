---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户信息
platform: Android
title: getAllUserInfo导致ANR问题
root_cause: 本地用户信息较多时，getAllUserInfo一次性加载所有数据导致主线程阻塞。
solution: 优化方案：1) 调整线程处理；2) 懒加载不一次性加载所有用户信息。
customers: ["临沂华升云网络科技有限公司"]
source: chat_history
tags: ["ANR", "getAllUserInfo", "用户信息", "性能优化", "懒加载"]
created: 2025-06-20
updated: 2025-03-23
---

## 问题：Android getAllUserInfo导致ANR问题

## 问题详情

**现象**：
客户反馈友盟上出现ANR崩溃，与getAllUserInfo方法相关。

## 排查过程

1. 日志分析 → 确认是getAllUserInfo引起的
2. 原因定位 → 本地用户信息较多时耗时操作
3. 优化建议 → 调整线程或懒加载，不一次性加载所有用户信息

**关键发现**：本地用户信息较多时，getAllUserInfo一次性加载所有数据导致主线程阻塞

## 问题原因

本地用户信息较多时，getAllUserInfo一次性加载所有数据导致主线程阻塞。

## 解决方案

优化方案：1) 调整线程处理；2) 懒加载不一次性加载所有用户信息。

## 其他触发场景

