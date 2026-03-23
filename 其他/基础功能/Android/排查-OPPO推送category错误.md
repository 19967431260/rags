---
track_type: 排查类
sub_type: 客户环境问题
product: 其他
feature: 基础功能
platform: Android
title: OPPO推送category错误
root_cause: OPPO推送category参数错误，使用了不被允许的category值
solution: 检查OPPO推送category配置，使用OPPO官方支持的category值
customers:
  - 上海烯牛信息技术有限公司
source: chat_history
tags:
  - OPPO推送
  - category错误
  - 离线推送
  - code:67
created: '2025-06-11'
updated: '2026-03-23'
---

## 问题：Android OPPO推送category错误

## 问题详情

**现象**：
OPPO收不到离线消息，返回错误code:67, message:"category error"

**环境信息**：
- 平台：Android
- 推送通道：OPPO
- category设置：subscribe
- 时间：2025-06-11

## 排查过程

1. 检查推送响应 → 返回{"code":67,"message":"category error"}
2. 确认错误来源 → OPPO服务器返回的错误
3. 分析问题 → category参数设置不正确

**关键发现**：OPPO推送category参数错误

## 问题原因

OPPO推送使用了不被允许的category值（subscribe），导致推送失败

## 解决方案

1. 检查OPPO推送category配置
2. 使用OPPO官方支持的category值
3. 参考OPPO推送文档配置正确的category参数
4. 确保channel_id和category匹配
