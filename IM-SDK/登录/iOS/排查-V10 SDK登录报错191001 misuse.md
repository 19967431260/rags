---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: iOS
title: V10 SDK登录报错191001 misuse
root_cause: V9和V10 SDK混用导致，需要在配置中开启V10兼容模式。
solution: 在配置中将对应字段设置为true开启V10兼容模式，确保项目完全使用V10 SDK。
customers: ['凯旋出海']
source: chat_history
tags: ['191001', 'misuse', 'V10', '登录', '混用']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：iOS V10 SDK登录报错191001 misuse

## 问题详情

**现象**：
新项目使用V10 SDK登录时报错code=191001, desc=misuse，使用login:token:option:success:failure:接口。

## 排查过程

1. 客户反馈登录报错191001 → 技术支持询问是否V9和V10混用
2. 客户提供SDK日志 → 技术支持分析确认是V9和V10版本混用导致
3. 指导客户在配置中开启V10兼容模式

## 问题原因

V9和V10 SDK混用导致，需要在配置中开启V10兼容模式。

## 解决方案

在配置中将对应字段设置为true开启V10兼容模式，确保项目完全使用V10 SDK。

## 其他触发场景

（合并时在此处追加）
