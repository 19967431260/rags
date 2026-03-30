---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Flutter
title: Flutter RTC uid不能为0
root_cause: RTC uid不能为0，会导致加入房间失败
solution: RTC uid必须设置为非0值，通话双方分别设置为不同值（如1和2）
customers: ['VIP云信-北京未来星图']
source: chat_history
tags: ['Flutter', 'RTC', 'uid', '无声音']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Flutter Flutter RTC uid不能为0

## 问题详情

**现象**：
Flutter端RTC音视频通话双方都听不到声音，排查发现uid赋值为0导致。

## 排查过程

1. 客户反馈音视频通话没有声音。
2. 查询后台发现搜不到该房间名称，判断uid可能有问题。
3. 确认客户uid给了0。
4. 建议改为非0值（如1和2）。

## 问题原因

RTC uid不能为0，会导致加入房间失败

## 解决方案

RTC uid必须设置为非0值，通话双方分别设置为不同值（如1和2）

## 其他触发场景

（合并时在此处追加）
