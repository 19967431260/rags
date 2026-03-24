---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Android
title: 小米推送注册失败Invalid package name错误
root_cause: 应用包名与小米开放平台注册的应用包名不一致
solution: 1. 检查小米开放平台注册的应用包名是否与当前应用包名一致\n2. 如不一致，需要在小米开放平台重新配置正确的包名\n3. 或修改应用包名与小米平台注册的一致
customers: ['湖北宏鑫康隆科技有限公司']
source: chat_history
tags: ['小米推送', '22022', 'Invalid package name', '离线推送', '包名']
created: 2025-01-18
updated: 2026-03-23
---

## 问题：Android 小米推送注册失败Invalid package name错误

## 问题详情

**现象**：
小米推送注册时返回错误码22022，提示Invalid package name:com.xmcy.confide。这是小米推送SDK校验包名失败导致的，通常是因为应用包名与小米开放平台注册的应用包名不一致。

## 排查过程

1. 查看日志发现小米推送注册失败\n2. 错误码：22022，原因：Invalid package name\n3. 确认包名com.xmcy.confide与小米开放平台配置不匹配

## 问题原因

应用包名与小米开放平台注册的应用包名不一致

## 解决方案

1. 检查小米开放平台注册的应用包名是否与当前应用包名一致\n2. 如不一致，需要在小米开放平台重新配置正确的包名\n3. 或修改应用包名与小米平台注册的一致

## 其他触发场景

（合并时在此处追加）
