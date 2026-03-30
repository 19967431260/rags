---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: Android子进程ANR不影响主进程
root_cause: 断网检测断开连接时，有线程正在做登录操作卡在InetAddress.getAllByName系统方法上，两个过程竞争同一个锁导致阻塞
solution: 通过SDKOptions.disablePush(true)关闭云信推送功能，该配置不会调用厂商推送的关闭方法，只关闭云信自己的推送逻辑
customers: ["智联招聘"]
source: chat_history
tags: ["Android", "ANR", "9.20.17", "子进程", "push", "disablePush"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Android 子进程ANR不影响主进程

## 问题详情

**现象**：
Android端IM SDK 9.20.17版本出现ANR，堆栈显示在子进程pin.social:core中，涉及InetAddress.getAllByName系统方法阻塞。客户未使用云信push功能。ANR发生在子进程，用户无感知。

**环境信息**：
- SDK 版本：9.20.17
- 进程：子进程 pin.social:core

## 排查过程

1. 收集ANR堆栈和SDK版本 → 9.20.17
2. 分析ANR进程 → 发生在子进程，用户无感知
3. 分析根因 → 断网时断开连接与登录操作竞争同一个锁，登录卡在系统方法上

**关键发现**：ANR发生在子进程，概率很小，不影响用户UI操作

## 问题原因

断网检测断开连接时，有线程正在做登录操作卡在InetAddress.getAllByName系统方法上，两个过程竞争同一个锁导致阻塞

## 解决方案

通过SDKOptions.disablePush(true)关闭云信推送功能，该配置不会调用厂商推送的关闭方法，只关闭云信自己的推送逻辑

## 其他触发场景

（暂无）
