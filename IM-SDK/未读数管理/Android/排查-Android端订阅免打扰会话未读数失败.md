---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 未读数管理
platform: Android
title: Android端订阅免打扰会话未读数失败
root_cause: 注册subscribeUnreadCountByFilter的时机过早，在数据库未打开时就进行了注册，导致订阅失败
solution: 在收到AuthServiceObserver的observeDataReady回调（数据库打开通知）之后再去注册subscribeUnreadCountByFilter；或者在登录成功之后、在viewDidLoad中注册订阅
customers: ["千寻代售APP沟通群"]
source: chat_history
tags: ["subscribeUnreadCountByFilter","isDataReady","AuthServiceObserver","observeDataReady","免打扰"]
created: 2025-08-04
updated: 2026-03-26
---

## 问题：Android Android端订阅免打扰会话未读数失败

## 问题详情

**现象**：
Android端集成SDK，使用subscribeUnreadCountByFilter订阅免打扰会话的未读数，收到报错：isDataReady failed。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户注册subscribeUnreadCountByFilter后收到isDataReady failed报错 → 确认错误信息
2. 检查日志发现注册时机问题：订阅时数据库未打开 → 根因定位
3. SDK要求在收到数据库打开回调之后再注册订阅 → 问题说明

**关键发现**：注册subscribeUnreadCountByFilter的时机过早，在数据库未打开时就进行了注册，导致订阅失败

## 问题原因

注册subscribeUnreadCountByFilter的时机过早，在数据库未打开时就进行了注册，导致订阅失败。

## 解决方案

在收到AuthServiceObserver的observeDataReady回调（数据库打开通知）之后再去注册subscribeUnreadCountByFilter；或者在登录成功之后、在viewDidLoad中注册订阅。

## 其他触发场景

（合并时在此处追加）
