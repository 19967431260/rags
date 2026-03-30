---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 崩溃
platform: Android
title: Android端OOM崩溃升级SDK版本修复
root_cause: IM SDK 9.19.14版本存在OOM崩溃问题。
solution: 升级到IM SDK 9.20.15版本，该版本已修复OOM崩溃问题。
customers: ["YOOY语音"]
source: chat_history
tags: ["OOM","崩溃","9.20.15","Android"]
created: 2025-08-29
updated: 2026-03-26
---

## 问题：Android Android端OOM崩溃升级SDK版本修复

## 问题详情

**现象**：
Android端出现OOM（Out of Memory）崩溃，SDK版本9.19.14。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 收集崩溃堆栈和SDK版本 → 确认OOM崩溃
2. 联系研发分析 → 问题确认
3. 确认OOM问题在9.20.15版本修复 → 修复版本

**关键发现**：IM SDK 9.19.14版本存在OOM崩溃问题。

## 问题原因

IM SDK 9.19.14版本存在OOM崩溃问题。

## 解决方案

升级到IM SDK 9.20.15版本，该版本已修复OOM崩溃问题。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
