---
track_type: 排查类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息管理
platform: 服务端
title: querySessionMsg接口查询不到消息
root_cause: 分页查询参数使用不正确，excludeMsgid是过滤消息ID而非分页起始位置
solution: 使用最后一次查询消息的时间戳作为下次查询的起始时间，配合limit参数实现分页
customers: ["北京云朵课堂"]
source: chat_history
tags: ["querySessionMsg", "分页查询", "消息查询", "时间戳"]
created: 2025-05-27
updated: 2025-03-20
---

## 问题：服务端 querySessionMsg接口查询不到消息

## 问题详情

**现象**：
通过三方回调收集的日志显示消息存在，但调用querySessionMsg接口查询不到该消息。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 确认消息存在 → 服务端可以查询到
2. 检查查询参数 → 发现分页方式理解有误
3. 说明分页逻辑 → 使用最后一次查询消息的时间戳作为下次查询的起始时间

## 问题原因

分页查询参数使用不正确，excludeMsgid是过滤消息ID而非分页起始位置

## 解决方案

使用最后一次查询消息的时间戳作为下次查询的起始时间，配合limit参数实现分页

## 其他触发场景

