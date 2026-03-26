---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息管理
platform: Android
title: 多端添加observeReceiveMessage互不影响：支持多个监听器
root_cause: 多端（Android+Flutter）同时添加了消息接收监听，担心相互影响
solution: 多端添加observeReceiveMessage监听不会相互影响，SDK支持多个监听器同时工作
customers: ["杭州微蚁"]
source: chat_history
tags: ["observeReceiveMessage", "多端", "Flutter", "Android", "监听"]
created: 2025-07-04
updated: 2026-03-25
---

## 问题：多端添加observeReceiveMessage互不影响：支持多个监听器

## 问题原因

多端（Android+Flutter）同时添加了消息接收监听，担心相互影响

## 解决方案

多端添加observeReceiveMessage监听不会相互影响，SDK支持多个监听器同时工作
