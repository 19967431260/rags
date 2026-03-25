---
track_type: 排查类
sub_type: 使用问题
product: 短信
feature: 短信发送
platform: Server
title: 短信发送触发频控限制FAIL_SE
root_cause: 频控导致
solution: 优化频控策略后恢复正常，如触发限制需等待1440分钟（24小时）后才能再次发送
customers: ["广州益乐互动"]
source: chat_history
tags: ["短信", "FAIL_SE", "频控", "频繁发送", "限流"]
created: 2025-05-23
updated: 2025-03-20
---

## 问题：Server 短信发送触发频控限制FAIL_SE

## 问题详情

**现象**：
短信发送返回FAIL_SE错误，没有配置限流但触发频繁发送限制，需要间隔1440分钟后才能再发送。

## 排查过程

**关键发现**：频控导致

## 问题原因

频控导致

## 解决方案

优化频控策略后恢复正常，如触发限制需等待1440分钟（24小时）后才能再次发送
