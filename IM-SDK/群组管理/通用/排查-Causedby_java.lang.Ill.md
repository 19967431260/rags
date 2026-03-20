---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: 通用
title: Causedby:java.lang.Ill
root_cause: ""
solution: "本地测试必现的吗，这个报错是还没初始化调用SDK的接口返回的"
customers: ["SVIP+Melvo+云信-项目对接群"]
source: chat_history
tags: ["云信", "SDK", "技术支持"]
created: 2025-01-22
updated: 2026-03-20
---

## 问题：通用 Causedby:java.lang.Ill

## 问题详情

**现象**：
Caused by: java.lang.IllegalStateException: SDK not initialized or invoked in wrong process!
麻烦看下这个问题修改应用权限后，回到应用就崩溃，提示sdk未初始化@网易云信-王硕

## 排查过程

1. 根据会话信息确认问题触发路径并复核关键配置。

## 问题原因

会话中未提供更细根因。

## 解决方案

本地测试必现的吗，这个报错是还没初始化调用SDK的接口返回的
