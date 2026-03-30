---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 登录服务
platform: Android
title: 小米系统杀死子进程导致登录异常
root_cause: 小米系统bug，短时间内频繁打开关闭app时触发
solution: 已知系统bug，已反馈给小米公司，等待后续版本更新修复。临时方案：过一会再打开app就正常
customers: ["111医药馆"]
source: chat_history
tags: ["小米", "登录", "AbstractMethodError", "子进程", "process is bad", "SecurityException"]
created: 2025-11-27
updated: 2026-03-20
---

## 问题：Android 小米系统杀死子进程导致登录异常

## 问题详情

**现象**：
使用NIMClient.getService(AuthService::class.java).login进行登录时偶尔报错AbstractMethodError，偶尔未响应。

## 排查过程

1. 分析日志
2. 确认错误原因
**关键发现**：小米系统认为子进程是坏进程直接杀死，导致后续登录异常，错误信息process is bad

## 问题原因

小米系统bug，短时间内频繁打开关闭app时触发

## 解决方案

已知系统bug，已反馈给小米公司，等待后续版本更新修复。临时方案：过一会再打开app就正常

## 其他触发场景

