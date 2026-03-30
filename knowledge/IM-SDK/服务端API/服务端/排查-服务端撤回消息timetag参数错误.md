---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 服务端撤回消息timetag参数错误
root_cause: timetag参数错误地取了ext扩展字段中的时间戳，应取SDK外层的时间戳
solution: 撤回消息时timetag参数应取SDK外层的msgTimestamp，而非ext扩展字段中的时间戳
customers: ["深圳市镜玩"]
source: chat_history
tags: ["IM-SDK", "消息撤回", "timetag", "414", "服务端API"]
created: 2025-05-14
updated: 2025-03-20
---

## 问题：服务端 服务端撤回消息timetag参数错误

## 问题详情

**现象**：
调用服务端消息撤回接口返回414错误'some param not match message'，原因是timetag参数取值错误。

## 排查过程

**关键发现**：timetag参数错误地取了ext扩展字段中的时间戳，应取SDK外层的时间戳

## 问题原因

timetag参数错误地取了ext扩展字段中的时间戳，应取SDK外层的时间戳

## 解决方案

撤回消息时timetag参数应取SDK外层的msgTimestamp，而非ext扩展字段中的时间戳
