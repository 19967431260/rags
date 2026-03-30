---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 推送服务
platform: Android
title: Android推送SDK空指针崩溃
root_cause: push sdk下的线程安全问题，2024年9月引入
solution: 升级到最新版本9.20.17；如不使用离线推送，push包可以不用集成
customers: ["智联招聘"]
source: chat_history
tags: ["Android", "崩溃", "NullPointerException", "推送", "NetworkKeeper", "9.19.11"]
created: 2025-11-24
updated: 2026-03-20
---

## 问题：Android Android推送SDK空指针崩溃

## 问题详情

**现象**：
客户反馈Android崩溃：java.lang.NullPointerException Attempt to invoke virtual method 'void java.util.Timer.schedule(java.util.TimerTask, long)' on a null object reference，堆栈在com.netease.nimlib.push.b.c.b(NetworkKeeper.java)。客户表示App已不使用云信推送。

## 排查过程

1. 确认SDK版本为9.19.11
2. 分析问题引入时间
3. 排查RTC集成影响
**关键发现**：该问题是2024年9月份引入的线程安全问题，与RTC无关

## 问题原因

push sdk下的线程安全问题，2024年9月引入

## 解决方案

升级到最新版本9.20.17；如不使用离线推送，push包可以不用集成

## 其他触发场景

