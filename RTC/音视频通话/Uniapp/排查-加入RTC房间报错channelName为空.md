---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Uniapp
title: 加入RTC房间报错channelName为空
root_cause: 加入房间时未传递channelName字段
solution: 在加入房间接口中传递channelName字段参数
customers: ["顶呱呱科技股份有限公司"]
source: chat_history
tags: ["channelName","加入房间","参数缺失"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Uniapp 加入RTC房间报错channelName为空

## 问题详情

**现象**：
客户在Uniapp平台调用加入RTC房间接口时报错"channelName is empty"，使用的是调试模式。

## 问题原因

加入房间时未传递channelName字段

## 解决方案

在加入房间接口中传递channelName字段参数

## 其他触发场景

