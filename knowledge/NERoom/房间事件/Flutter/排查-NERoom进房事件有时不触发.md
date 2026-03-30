---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间事件
platform: Flutter
title: NERoom进房事件有时不触发
root_cause: 切换账号时未调用NERoomKit.instance.authService.logout()，导致roomkit内部IM保留上一次账号信息
solution: 切换账号时调用NERoomKit.instance.authService.logout()，重新登录后再调用login
customers: ['河南新秀金文化传媒']
source: chat_history
tags: ['进房事件', '切换账号', 'logout', '事件监听', 'Flutter']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Flutter NERoom进房事件有时不触发

## 问题详情

**现象**：
监听进房事件有时能收到有时收不到，只有RTC事件没有NERoom和聊天室事件。

## 排查过程

1. 检查IM控制台配置
2. 确认是否切换账号
3. 检查是否logout

## 问题原因

切换账号时未调用NERoomKit.instance.authService.logout()，导致roomkit内部IM保留上一次账号信息

## 解决方案

切换账号时调用NERoomKit.instance.authService.logout()，重新登录后再调用login

## 其他触发场景

（合并时在此处追加）
