---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 好友列表
platform: Android
title: V9 Android getFriends()大部分情况返回空
root_cause: 
solution: 建议在数据同步完成之后再调用getFriends()查询好友列表。如果问题持续，需要复现并记录时间点，提取SDK日志进行分析。日志提取方法：https://faq.yunxin.163.com/#KB0179
customers: ["南京麦豆健康"]
source: chat_history
tags: ["getFriends", "好友列表", "NimUserInfoCache", "数据同步", "V9"]
created: 2026-01-23
updated: 2026-03-15
---

## 问题：Android V9 Android getFriends()大部分情况返回空

## 问题详情

**现象**：
使用V9.19.11 Android SDK，调用NimUserInfoCache.getInstance().getFriends()获取好友列表，大部分情况返回空，偶尔能返回数据。

## 排查过程

1. 确认调用接口 → getFriends()
2. 检查调用时机 → 未确认是否在数据同步完成后调用
3. 需要复现并提供日志 → 等待客户提供SDK日志分析

**关键发现**：可能是数据同步时机问题导致缓存未就绪

## 问题原因

## 解决方案

建议在数据同步完成之后再调用getFriends()查询好友列表。如果问题持续，需要复现并记录时间点，提取SDK日志进行分析。日志提取方法：https://faq.yunxin.163.com/#KB0179

## 其他触发场景

