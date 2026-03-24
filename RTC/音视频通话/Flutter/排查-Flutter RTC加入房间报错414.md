---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: Flutter
title: Flutter RTC加入房间报错414
root_cause: 未传递token参数导致加入房间失败
solution: 调用joinChannel时确保传入有效的token参数
customers: ['VIP云信-北京未来星图']
source: chat_history
tags: ['414', 'Flutter', 'RTC', '加入房间', 'token']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Flutter Flutter RTC加入房间报错414

## 问题详情

**现象**：
Flutter端使用RTC加入音视频房间时返回414错误码，无法成功进入房间。

## 排查过程

1. 客户提供channelName后查询后台数据，发现result 414，表示加入房间失败。
2. 建议客户参考文档KB0394排查常见原因。
3. 客户反馈发现是没有传token导致。

## 问题原因

未传递token参数导致加入房间失败

## 解决方案

调用joinChannel时确保传入有效的token参数

## 其他触发场景

（合并时在此处追加）
