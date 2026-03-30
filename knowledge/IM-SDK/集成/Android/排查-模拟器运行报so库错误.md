---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: Android
title: 模拟器运行报so库错误
root_cause: NDK配置了x86架构，但SDK可能不支持或模拟器架构不匹配
solution: NDK配置中去掉x86架构配置
customers: ["西安未来国际信息股份有限公司"]
source: chat_history
tags: ["模拟器","so库","NDK","x86"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Android 模拟器运行报so库错误

## 问题详情

**现象**：
在Android模拟器上运行时报so库相关错误

## 问题原因

NDK配置了x86架构，但SDK可能不支持或模拟器架构不匹配

## 解决方案

NDK配置中去掉x86架构配置

## 其他触发场景

