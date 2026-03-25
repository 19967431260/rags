---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS进入后台收不到推送通知
root_cause: 推送证书过期导致无法发送推送通知
solution: 更新iOS推送证书，重新配置推送服务
customers: ["江苏乐筑"]
source: chat_history
tags: ["iOS", "推送", "证书过期", "APNs"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS进入后台收不到推送通知

## 问题详情

**现象**：
客户反馈iOS应用进入后台后收不到推送通知，使用云信SDK版本9.12.1。

**环境信息**：
- 平台：iOS

## 排查过程

1. 获取SDK日志分析 → 按文档路径提取日志
2. 检查推送证书状态 → 发现desk_dis_push推送证书已过期

## 根因分析

推送证书过期导致无法发送推送通知

## 解决方案

更新iOS推送证书，重新配置推送服务

## 其他触发场景

（无）
