---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: iOS
title: Unity SDK iOS端崩溃问题
root_cause: iOS静态库与其他SDK存在符号冲突导致崩溃
solution: 使用动态库版本替代静态库，或排查工程中其他SDK的符号冲突
customers: ['北京久幺幺']
source: chat_history
tags: ['Unity', 'iOS', '崩溃', '静态库', '动态库']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：iOS Unity SDK iOS端崩溃问题

## 问题详情

**现象**：
客户集成NIM Unity版本在iOS设备上运行时遇到崩溃问题，日志显示curl_perform相关错误，发生在登录时。

## 排查过程

1. 客户反馈Unity SDK在iOS上必现崩溃
2. SDK版本2.6.0，Unity版本2021.3.41f1c1
3. 研发提供测试包将iOS下静态库改成动态库后问题消失
4. 排查发现客户工程中还接入了声网SDK
**关键发现**：静态库与工程中其他SDK（声网）可能存在符号冲突

## 问题原因

iOS静态库与其他SDK存在符号冲突导致崩溃

## 解决方案

使用动态库版本替代静态库，或排查工程中其他SDK的符号冲突

## 其他触发场景

（合并时在此处追加）
