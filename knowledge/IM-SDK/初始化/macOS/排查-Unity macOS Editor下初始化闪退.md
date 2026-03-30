---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: macOS
title: Unity macOS Editor下初始化闪退
root_cause: SDK对新的ARM64架构Unity Editor支持不完善
solution: 使用研发提供的适配包（UNITY_IM_SDK.unitypackage），导入后在初始化时系统会有安全提示，在隐私和安全里面允许即可
customers: ['北京久幺幺']
source: chat_history
tags: ['Unity', 'macOS', 'Editor', '闪退', 'ARM64']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：macOS Unity macOS Editor下初始化闪退

## 问题详情

**现象**：
客户希望在Mac Unity Editor下直接调试，但导入官网package后调用init接口时闪退。

## 排查过程

1. 客户反馈在Mac Unity Editor下调试时调用init闪退
2. 使用M2芯片的Mac
3. 经确认Editor版本较新，之前适配的是较老的Editor版本
**关键发现**：SDK对新的ARM64架构Editor支持不完善

## 问题原因

SDK对新的ARM64架构Unity Editor支持不完善

## 解决方案

使用研发提供的适配包（UNITY_IM_SDK.unitypackage），导入后在初始化时系统会有安全提示，在隐私和安全里面允许即可

## 其他触发场景

（合并时在此处追加）
