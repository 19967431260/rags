---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: Android 15小米手机登录失败问题
root_cause: 小米手机默认会限制子进程的频繁启动，V9 SDK使用子进程机制。
solution: V9方案：让用户手动开启应用自启动、关闭省电模式。V10方案：升级V10 SDK，已重构无子进程设计。
customers: ['中讯邮电']
source: chat_history
tags: ['登录失败', 'Android 15', '小米', '子进程', 'V9', 'V10']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Android Android 15小米手机登录失败问题

## 问题详情

**现象**：
在安卓15的小米手机上，很容易出现登录失败的情况，影响用户体验。

## 排查过程



## 问题原因

小米手机默认会限制子进程的频繁启动，V9 SDK使用子进程机制。

## 解决方案

V9方案：让用户手动开启应用自启动、关闭省电模式。V10方案：升级V10 SDK，已重构无子进程设计。

## 其他触发场景

（合并时在此处追加）
