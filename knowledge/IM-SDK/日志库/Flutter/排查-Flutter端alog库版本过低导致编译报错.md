---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 日志库
platform: Flutter
title: Flutter端alog库版本过低导致编译报错
root_cause: Flutter项目中alog库依赖版本过低，与新版SDK不兼容
solution: 将alog库依赖升级至api 'com.netease.yunxin.kit:alog:1.1.1'即可解决编译报错
customers: ["四创科技有限公司"]
source: chat_history
tags: ["Flutter","alog","编译报错","依赖版本"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：Flutter Flutter端alog库版本过低导致编译报错

## 问题详情

**现象**：
Flutter版本集成IM SDK编译时报错，错误信息涉及log库依赖版本过低。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：Flutter项目中alog库依赖版本过低，与新版SDK不兼容

## 问题原因

Flutter项目中alog库依赖版本过低，与新版SDK不兼容。

## 解决方案

将alog库依赖升级至api 'com.netease.yunxin.kit:alog:1.1.1'即可解决编译报错。

## 其他触发场景

（合并时在此处追加）
