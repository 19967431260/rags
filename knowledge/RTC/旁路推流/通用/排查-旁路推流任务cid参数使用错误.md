---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 旁路推流
platform: 通用
title: 旁路推流任务cid参数使用错误
root_cause: 创建旁路推流任务接口的cid参数需要使用RTC房间的channelId，而非直播频道的cid
solution: 使用加入RTC房间时onJoinChannel回调返回的channelId作为cid参数
customers: ["顶呱呱科技股份有限公司"]
source: chat_history
tags: ["旁路推流","cid","channelId"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：通用 旁路推流任务cid参数使用错误

## 问题详情

**现象**：
客户在创建旁路推流任务时，错误地使用了直播频道的cid，导致推流失败。

## 问题原因

创建旁路推流任务接口的cid参数需要使用RTC房间的channelId，而非直播频道的cid

## 解决方案

使用加入RTC房间时onJoinChannel回调返回的channelId作为cid参数

## 其他触发场景

