---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 互动直播
platform: iOS
title: addLiveStreamTask缺少taskId参数报错
root_cause: addLiveStreamTask接口的taskId参数是必传的，客户未传递导致参数校验失败。
solution: addLiveStreamTask必须传入taskId参数，值为全局唯一的字符串（如UUID），不需要后台生成，客户端自行生成即可。
customers: ["FVIP云信-上海功途教育"]
source: chat_history
tags: ["addLiveStreamTask", "taskId", "参数错误", "30003"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：iOS addLiveStreamTask缺少taskId参数报错

## 问题详情

**现象**：
addLiveStreamTask调用时未传taskId参数，导致接口报错。

## 排查过程

1. 检查日志 → 发现addLiveStreamTask参数错误：invalid param
2. 对比文档 → 客户未传taskId参数，误以为可以不传
**关键发现**：taskId是必传参数

## 问题原因

addLiveStreamTask接口的taskId参数是必传的，客户未传递导致参数校验失败。

## 解决方案

addLiveStreamTask必须传入taskId参数，值为全局唯一的字符串（如UUID），不需要后台生成，客户端自行生成即可。

## 其他触发场景

