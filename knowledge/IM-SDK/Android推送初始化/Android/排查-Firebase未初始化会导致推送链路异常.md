---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Android推送初始化
platform: Android
title: Firebase未初始化会导致推送链路异常
root_cause: Firebase 库未在正确进程或初始化时机完成初始化。
solution: 确保在实际使用的进程中初始化 Firebase；常见做法是在 Application.onCreate 中完成初始化，避免因未初始化而被系统拦截。
customers: ["智业互联健康科技"]
source: chat_history
tags: ["Firebase", "Application.onCreate", "子进程", "初始化", "Android"]
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Android Firebase未初始化会导致推送链路异常

## 问题详情

**现象**：
客户在 Android 9.18.1 集成环境中遇到异常/闪退，并结合 FAQ 排查发现问题与 Firebase 初始化有关。

## 排查过程

1. 客户提供异常截图并说明当前版本为 9.18.1。
2. 技术支持判断 Firebase 需要在子进程中正确初始化，否则可能被系统拦截。
3. 随后补充 FAQ，并进一步说明也可在 Application.onCreate 中完成初始化。

**关键发现**：Firebase 初始化缺失或时机不对会导致相关功能异常。

## 问题原因

Firebase 库未在正确进程或初始化时机完成初始化。

## 解决方案

确保在实际使用的进程中初始化 Firebase；常见做法是在 Application.onCreate 中完成初始化，避免因未初始化而被系统拦截。

## 其他触发场景

