---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 音视频通话1.0
platform: Windows
title: Windows音视频通话秒拒时收不到拒绝回调
root_cause: 秒拒情况下，被拒通知先于发起呼叫结果通知到达，导致SDK内部状态异常，无法触发拒绝回调。
solution: 1. 避免秒拒场景，延迟500ms后再拒绝
2. 服务端已修复该时序问题
3. 客户端做好异常处理，设置呼叫超时机制
customers: ["深圳千舸智联"]
source: chat_history
tags: ["音视频1.0", "秒拒", "kNIMVideoChatSessionTypeCalleeAckNotify", "回调丢失", "Windows"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Windows Windows音视频通话秒拒时收不到拒绝回调

## 问题详情

**现象**：
客户在使用Windows IM SDK音视频通话1.0时，发起呼叫成功（收到kNIMVideoChatSessionTypeStartRes回调），但对方秒拒时，有一定概率收不到kNIMVideoChatSessionTypeCalleeAckNotify拒绝回调。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认问题现象 → 发起呼叫成功，但对方拒绝回调收不到
2. 分析日志 → 服务端协议已下发拒绝通知
3. 测试不同场景 → 手动拒绝正常，秒拒有问题
4. 分析时序 → 发现发起呼叫的response code晚于被拒绝的通知
5. 定位根因 → 秒拒情况下，被拒通知先于发起结果通知到达
**关键发现**：秒拒时，kNIMVideoChatSessionTypeCalleeAckNotify回调因时序问题无法触发

**关键发现**：

## 问题原因

秒拒情况下，被拒通知先于发起呼叫结果通知到达，导致SDK内部状态异常，无法触发拒绝回调。

## 解决方案

1. 避免秒拒场景，延迟500ms后再拒绝
2. 服务端已修复该时序问题
3. 客户端做好异常处理，设置呼叫超时机制

## 其他触发场景

