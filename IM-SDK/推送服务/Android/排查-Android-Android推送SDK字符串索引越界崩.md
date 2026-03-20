---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 推送服务
platform: Android
title: Android推送SDK字符串索引越界崩溃
root_cause: 
solution: 同上一个崩溃问题，升级SDK版本解决
customers: ["智联招聘"]
source: chat_history
tags: ["Android", "崩溃", "StringIndexOutOfBoundsException", "推送"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Android Android推送SDK字符串索引越界崩溃

## 问题详情

**现象**：
客户反馈另一个崩溃：java.lang.StringIndexOutOfBoundsException String index out of range: -2，堆栈涉及com.netease.nimlib.push.net.e和com.netease.nimlib.push.b.c。

## 排查过程



## 问题原因

暂无根因分析

## 解决方案

同上一个崩溃问题，升级SDK版本解决

## 其他触发场景

