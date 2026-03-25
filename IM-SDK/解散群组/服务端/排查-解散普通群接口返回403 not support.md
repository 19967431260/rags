---
track_type: 排查类
sub_type: 接口用法咨询
product: IM-SDK
feature: 解散群组
platform: 服务端
title: 解散普通群接口返回403 not support
root_cause: 解散群接口只适用于高级群，不适用于普通群（讨论组）
solution: 普通群（讨论组）不能使用解散群接口，需要使用其他方式处理。
customers: ["上海金桥"]
source: chat_history
tags: ["IM", "解散群组", "403", "普通群", "讨论组"]
created: 2025-05-23
updated: 2025-03-20
---

## 问题：服务端 解散普通群接口返回403 not support

## 问题详情

**现象**：
调用解散群接口返回错误{"code":403,"desc":"not support"}。

## 排查过程

**关键发现**：解散群接口只适用于高级群，不适用于普通群（讨论组）

## 问题原因

解散群接口只适用于高级群，不适用于普通群（讨论组）

## 解决方案

普通群（讨论组）不能使用解散群接口，需要使用其他方式处理。
