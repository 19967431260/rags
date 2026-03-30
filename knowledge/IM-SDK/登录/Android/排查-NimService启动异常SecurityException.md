---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Android
title: NimService启动异常SecurityException
root_cause: 频繁杀死应用被系统判定为不好进程，进程被系统禁止启动（小米系统限制）
solution: 关闭省电模式，打开自启动权限
customers: ['新视展']
source: chat_history
tags: ['SecurityException', 'NimService', '登录失败', 'process is bad']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Android NimService启动异常SecurityException

## 问题详情

**现象**：
Android端SDK初始化登录时偶现失败，日志显示start NimService error: java.lang.SecurityException: Unable to start service，process is bad。

## 排查过程

1. 客户反馈登录偶现失败
2. 技术支持查看日志发现SecurityException
3. 确认是频繁杀死应用被小米系统判定core进程为不好进程，禁止启动

## 问题原因

频繁杀死应用被系统判定为不好进程，进程被系统禁止启动（小米系统限制）

## 解决方案

关闭省电模式，打开自启动权限

## 其他触发场景

（合并时在此处追加）
