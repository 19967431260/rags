---
track_type: 排查类
sub_type: 线上事故
product: RTC
feature: 音视频通话
platform: Android
title: NERTC 5.6.30与libc++_shared库冲突导致崩溃
root_cause: NERTC 5.6.0以上版本的在线配置问题，与libc++_shared库存在冲突
solution: 云信已回滚在线配置，预计影响5.6.0以上版本。如仍有问题可回退到NERTC 4.6.66版本
customers: ['武汉无毁']
source: chat_history
tags: ['NERTC', '崩溃', 'libc++_shared', '5.6.30', '音视频']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Android NERTC 5.6.30与libc++_shared库冲突导致崩溃

## 问题详情

**现象**：
客户应用集成阿里实人认证so库(含libc++_shared)后，使用NERTC 5.6.30版本时发生崩溃。崩溃发生在入会时，回退到NERTC 4.6.66版本无此问题。

## 排查过程

1. 客户提供崩溃日志 → 客服初步查看堆栈
2. 客户指出崩溃位置 → 确认与libc++_shared库冲突
3. 确认版本：NIM 9.12.0 + NERTC 5.6.30
4. 回退到NERTC 4.6.66验证无问题
5. 客服确认是本地配置问题，15点左右已回滚在线配置

## 问题原因

NERTC 5.6.0以上版本的在线配置问题，与libc++_shared库存在冲突

## 解决方案

云信已回滚在线配置，预计影响5.6.0以上版本。如仍有问题可回退到NERTC 4.6.66版本

## 其他触发场景

（合并时在此处追加）
