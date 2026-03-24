---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Android
title: RTC查询用户网络信号质量
root_cause: 用户网络环境不佳，上下行丢包
solution: 通过后台数据查询用户网络质量，可关注上行/下行丢包率指标
customers: ['VIP云信-北京汉医健康科技']
source: chat_history
tags: ['RTC', '网络质量', '丢包', 'Android']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Android RTC查询用户网络信号质量

## 问题详情

**现象**：
需要查询特定用户在进入RTC房间时的网络信号质量情况。

## 排查过程

1. 客户提供cid和uid。
2. 查询上报数据发现该用户在房间内最后一分钟网络情况不太好，上下行都有丢包。

## 问题原因

用户网络环境不佳，上下行丢包

## 解决方案

通过后台数据查询用户网络质量，可关注上行/下行丢包率指标

## 其他触发场景

（合并时在此处追加）
