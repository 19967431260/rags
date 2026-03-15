---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 在线状态
platform: Uniapp
title: 用户在线状态显示undefined或全部离线
root_cause: 未开启在线状态订阅配置
solution: 在控制台开启在线状态订阅功能，重新登录后生效。
customers: ["合肥九邑信息科技有限公司"]
source: chat_history
tags: ["在线状态", "订阅", "配置", "控制台"]
created: 2026-02-13
updated: 2026-03-16
---

## 问题：Uniapp 用户在线状态显示undefined或全部离线

## 问题详情

**现象**：
客户端查询用户在线状态时，状态字段打印为undefined，所有用户显示为离线状态。必现。

## 排查过程

1. 检查在线状态配置 → 未开启

**关键发现**：需要开启在线状态订阅功能

## 问题原因

未开启在线状态订阅配置

## 解决方案

在控制台开启在线状态订阅功能，重新登录后生效。

## 其他触发场景

