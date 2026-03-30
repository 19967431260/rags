---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Android
title: RTC房间异常结束timeout
root_cause: App切后台后被系统限制网络连接
solution: App切后台后需要起前台服务进行保活，避免被系统限制网络导致RTC断开
customers: ['VIP云信-北京汉医健康科技']
source: chat_history
tags: ['RTC', 'timeout', '后台', '保活', 'Android']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Android RTC房间异常结束timeout

## 问题详情

**现象**：
RTC音视频通话房间异常结束，需要查询原因。

## 排查过程

1. 客户提供cid查询。
2. 查询发现reason_str为timeout。
3. 进一步分析是App切到后台后被系统限制网络导致断开。

## 问题原因

App切后台后被系统限制网络连接

## 解决方案

App切后台后需要起前台服务进行保活，避免被系统限制网络导致RTC断开

## 其他触发场景

（合并时在此处追加）
