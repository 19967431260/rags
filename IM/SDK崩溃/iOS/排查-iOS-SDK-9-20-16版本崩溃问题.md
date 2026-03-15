---
track_type: 排查类
sub_type: BUG问题
product: IM
feature: SDK崩溃
platform: iOS
title: iOS SDK 9.20.16版本崩溃问题
root_cause: SDK 9.20.16版本存在已知问题
solution: 升级到9.21.0版本，该版本已优化此问题。崩溃和卡顿关系不大，如有卡顿需单独排查。
customers:
- 积木成林
source: chat_history
tags:
- iOS
- 崩溃
- Bugly
- 9.20.16
- 9.21.0
created: '2026-01-07'
updated: '2026-03-15'
---

## 问题：iOS iOS SDK 9.20.16版本崩溃问题

## 问题详情

**现象**：
iOS端Bugly监测到NIM SDK崩溃，版本号：NIMSDK_LITE (9.20.16)。客户反馈使用聊天会很卡。

## 排查过程

1. 客户提供Bugly崩溃日志 2. 云信添加Bugly账号查看详情 3. 分析崩溃堆栈

## 问题原因

SDK 9.20.16版本存在已知问题

## 解决方案

升级到9.21.0版本，该版本已优化此问题。崩溃和卡顿关系不大，如有卡顿需单独排查。
