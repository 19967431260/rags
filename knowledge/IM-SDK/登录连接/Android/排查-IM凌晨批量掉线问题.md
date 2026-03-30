---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 登录连接
platform: Android
title: IM凌晨批量掉线问题排查
root_cause: 登录参数配置错误，java.lang.IllegalArgumentException: LoginInfo is invalid
solution: 检查登录参数配置，参考官方最佳实践文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android
customers: ["济南时代"]
source: chat_history
tags: ["掉线", "登录失败", "Android", "凌晨", "批量"]
created: 2025-02-25
updated: 2026-03-20
---

## 问题：Android IM凌晨批量掉线问题排查

## 问题详情

**现象**：
客户反馈凌晨12点到1点半期间IM掉线严重，大量用户无法连接，显示正在连接中。

## 排查过程

1. 确认未收到监控异常提醒
2. 收集用户accid和时间段
3. 拉取日志分析
4. 发现部分用户有卸载重装行为导致日志缺失
5. 分析用户登录日志发现LoginInfo is invalid错误
6. 确认是登录参数问题

## 问题原因

登录参数配置错误，java.lang.IllegalArgumentException: LoginInfo is invalid

## 解决方案

检查登录参数配置，参考官方最佳实践文档：https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android

## 其他触发场景

