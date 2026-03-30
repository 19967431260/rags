---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "libwebsocket"
platform: "HarmonyOS"
title: "鸿蒙SDK崩溃问题（libwebsocket）"
root_cause: "SDK版本存在已知崩溃问题"
solution: "升级到10.9.50版本，该版本已优化此问题；10.8.25到10.9.50没有特别的兼容变更，可兼容老版本"
customers: ["智联招聘"]
source: "chat_history"
tags: ["鸿蒙", "崩溃", "libwebsocket", "SDK升级"]
created: "2025-09-16"
updated: "2026-03-20"
---

## 问题：HarmonyOS 鸿蒙SDK崩溃问题（libwebsocket）

## 问题详情

**现象**：
鸿蒙SDK出现崩溃，堆栈信息显示崩溃到系统线程，偶现问题，线上版本设备崩溃率占比万分之1

## 排查过程

1. 分析崩溃堆栈 → 崩溃到系统so文件，线程名不是SDK的
2. 确认复现情况 → 偶现，无法本地复现
3. 查看SDK版本 → 当前版本存在已知问题
4. 提供升级方案 → 后续版本已优化
**关键发现**：SDK版本问题，后续版本已修复

## 问题原因

SDK版本存在已知崩溃问题

## 解决方案

升级到10.9.50版本，该版本已优化此问题；10.8.25到10.9.50没有特别的兼容变更，可兼容老版本

## 其他触发场景
