---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: 安卓Push消息延迟问题
root_cause: 
solution: 详见正文。
customers: ["智慧丘比特"]
source: chat_history
tags: ["Push延迟", "厂商推送", "安卓", "taskId"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

用户反馈安卓Push延迟严重，新消息跨天才收到，早上8点发的消息下午2点才收到。

## 排查过程

1. 客户反馈Push延迟 → 确认是APNs还是厂商推送
2. 确认是安卓厂商推送 → 查询日志显示正常时间推给厂商
3. 提供taskId给厂商查询

## 根因分析

厂商推送延迟

## 解决方案

云信正常时间推送给厂商，延迟需联系厂商查询，可提供taskId作为推送唯一ID
