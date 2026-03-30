---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 崩溃修复
platform: Windows
title: Windows端SDK WebSocket崩溃
root_cause: websocket连接问题
solution: 升级到最新版本10.9.53，该问题已优化修复
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["Windows", "崩溃", "websocket", "升级"]
created: 2025-10-31
updated: 2026-03-20
---

## 问题：Windows Windows端SDK WebSocket崩溃

## 问题详情

**现象**：
Windows端IM SDK出现崩溃，与websocket相关。客户提供了dmp文件。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析崩溃日志 → 确认是websocket问题
2. 对比之前问题 → 确认是不同问题
**关键发现**：websocket崩溃，主干已修复

**关键发现**：

## 问题原因

websocket连接问题

## 解决方案

升级到最新版本10.9.53，该问题已优化修复

## 其他触发场景

