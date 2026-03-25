---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间管理
platform: 微信小程序
title: 小程序加入房间返回401 ws connect timeout
root_cause: 建连前的请求较慢或小程序卡线程，导致websocket建连时机延后，连接时房间已关闭
solution: 建议切换网络、重启手机和小程序再试，如问题频繁需要提供小程序日志进一步分析
customers: ["海南恒志互联网生活服务平台有限公司"]
source: chat_history
tags: ["401", "websocket", "timeout", "小程序", "加入房间"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：小程序加入房间返回401 ws connect timeout

## 问题详情

**现象**：
客户反馈小程序端加入房间失败，返回错误code: 401, reason: ws connect timeout。房间号YX736058709553186228。

**环境信息**：
- 平台：微信小程序

## 排查过程

1. 查询服务器状态 → 服务器无异常
2. 检查房间状态 → 查询websocket建连时的房间状态
3. 发现问题 → 真正websocket建连时房间已被关闭
4. 分析原因 → 建连前请求较慢或小程序卡线程导致建连时机延后

## 问题原因

建连前的请求较慢或小程序卡线程，导致websocket建连时机延后，连接时房间已关闭

## 解决方案

建议切换网络、重启手机和小程序再试，如问题频繁需要提供小程序日志进一步分析

## 其他触发场景

（无）
