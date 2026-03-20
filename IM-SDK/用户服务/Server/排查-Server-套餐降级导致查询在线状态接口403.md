---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 用户服务
platform: Server
title: 套餐降级导致查询在线状态接口403
root_cause: 套餐降级导致旗舰版功能被关闭
solution: 特殊申请开通该接口权限，或升级回旗舰版
customers: ["触手"]
source: chat_history
tags: ["403", "userOnlineStatus", "套餐降级", "旗舰版", "高级版"]
created: 2025-11-25
updated: 2026-03-20
---

## 问题：Server 套餐降级导致查询在线状态接口403

## 问题详情

**现象**：
IM账号从专业版降级到高级版后，调用userOnlineStatus.action接口返回403，导致业务异常用户被下线。

## 排查过程

1. 确认接口调用情况
2. 检查套餐功能差异
**关键发现**：userOnlineStatus接口是旗舰版才有的功能，降级后该功能被关闭

## 问题原因

套餐降级导致旗舰版功能被关闭

## 解决方案

特殊申请开通该接口权限，或升级回旗舰版

## 其他触发场景

