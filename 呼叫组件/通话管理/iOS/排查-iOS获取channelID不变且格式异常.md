---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 通话管理
platform: iOS
title: iOS获取channelID不变且格式异常
root_cause: NERtcCallUIKit源码中channelId赋值错误。
solution: 需要等待SDK修复更新，预计年后排期修复。
customers: ['VIP云信-上海万达信息-健康云项目']
source: chat_history
tags: ['channelID', 'iOS', 'BUG', '赋值错误']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：iOS iOS获取channelID不变且格式异常

## 问题详情

**现象**：
iOS每次获取的channelID一直不变，而且和安卓格式不一样。

## 排查过程

1. 确认使用的版本是从git下载的源码
2. 排查发现是代码中赋值错误，把其他值赋给了channelId

## 问题原因

NERtcCallUIKit源码中channelId赋值错误。

## 解决方案

需要等待SDK修复更新，预计年后排期修复。

## 其他触发场景

（合并时在此处追加）
