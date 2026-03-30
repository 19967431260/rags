---
track_type: 排查类
sub_type: 客户环境问题
product: IM
feature: 消息收发
platform: Android
title: Android端消息发送失败-网络连接正常但消息发不出
root_cause: 需要客户端日志进一步分析具体原因
solution: 1.拉取Android端日志分析具体错误 2.检查消息发送接口调用是否正确 3.检查是否有网络代理或防火墙限制
customers: ["智联招聘"]
source: chat_history
tags: ["Android", "消息发送失败", "客户端日志"]
created: 2026-01-15
updated: 2026-03-15
---


## 问题：Android Android端消息发送失败-网络连接正常但消息发不出

## 问题详情

Android端用户反馈消息发送失败，显示发送中状态但一直发不出去。iOS端正常。网络连接正常，其他功能正常。

## 排查过程

1.检查网络连接状态 → 正常
2.检查登录状态 → 正常
3.建议拉取客户端日志分析

## 问题原因

需要客户端日志进一步分析具体原因

## 解决方案

1.拉取Android端日志分析具体错误 2.检查消息发送接口调用是否正确 3.检查是否有网络代理或防火墙限制
