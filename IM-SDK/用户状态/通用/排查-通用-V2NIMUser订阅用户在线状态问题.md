---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 用户状态
platform: 通用
title: V2NIMUser订阅用户在线状态问题
root_cause: 
solution: 订阅时会有一次回调，将被订阅者状态回调给订阅者。用户默认设为离线状态，有登录调用时改为在线。
customers: ["上海近屿智能科技有限公司"]
source: chat_history
tags: ["V2NIMUser", "用户状态", "订阅", "在线状态"]
created: 2025-11-03
updated: 2026-03-20
---

## 问题：通用 V2NIMUser订阅用户在线状态问题

## 问题详情

**现象**：
客户咨询如何主动查询用户登录状态，A登录时订阅B，无法判断B是否在线。

**排查过程**：


## 问题原因



## 解决方案

订阅时会有一次回调，将被订阅者状态回调给订阅者。用户默认设为离线状态，有登录调用时改为在线。
