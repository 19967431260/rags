---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 云端录制
platform: Server
title: 测试环境录制回调未收到
root_cause: 
solution: 服务端抄送正常，建议客户检查测试环境回调接收服务
customers: ["浙江惠瀜"]
source: chat_history
tags: ["RTC", "录制", "回调", "测试环境"]
created: 2025-11-22
updated: 2026-03-20
---

## 问题：Server 测试环境录制回调未收到

## 问题详情

**现象**：
测试环境房间号57796054026292没有收到录制回调。

## 排查过程

1. 检查回调请求记录
2. 确认HTTP响应码
**关键发现**：服务端有请求记录，返回HTTP 200

## 问题原因

暂无根因分析

## 解决方案

服务端抄送正常，建议客户检查测试环境回调接收服务

## 其他触发场景

