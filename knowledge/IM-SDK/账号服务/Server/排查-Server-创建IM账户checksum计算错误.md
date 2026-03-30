---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号服务
platform: Server
title: 创建IM账户checksum计算错误
root_cause: checksum计算错误
solution: 检查checksum计算逻辑，确保使用正确的AppSecret和计算方式
customers: ["陕西科丰"]
source: chat_history
tags: ["403", "checksum", "创建账号", "认证失败"]
created: 2025-11-27
updated: 2026-03-20
---

## 问题：Server 创建IM账户checksum计算错误

## 问题详情

**现象**：
创建IM账户返回403 authentication failed，checksum计算错误。

## 排查过程

1. 检查appkey
2. 分析checksum计算
**关键发现**：checksum计算错误

## 问题原因

checksum计算错误

## 解决方案

检查checksum计算逻辑，确保使用正确的AppSecret和计算方式

## 其他触发场景

