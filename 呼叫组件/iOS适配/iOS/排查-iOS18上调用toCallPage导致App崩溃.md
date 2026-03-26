---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: iOS适配
platform: iOS
title: iOS18上调用toCallPage导致App崩溃
root_cause: iOS18系统API变更导致toCallPage调用方式需要适配
solution: 在iOS18上调用toCallPage时需要使用新的API方式，具体参考云信iOS SDK适配文档。
customers: ["成都超林科技有限公司"]
source: chat_history
tags: ["iOS18", "toCallPage", "崩溃", "API适配"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS iOS18上调用toCallPage导致App崩溃

## 问题详情

**现象**：
iOS18上调用toCallPage导致App崩溃。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS 18
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：iOS18系统API变更导致toCallPage调用方式需要适配

## 问题原因

iOS18系统API变更导致toCallPage调用方式需要适配

## 解决方案

在iOS18上调用toCallPage时需要使用新的API方式，具体参考云信iOS SDK适配文档。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
