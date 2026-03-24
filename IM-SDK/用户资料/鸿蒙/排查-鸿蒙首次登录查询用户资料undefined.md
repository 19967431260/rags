---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: 鸿蒙
title: 鸿蒙首次登录查询用户资料undefined
root_cause: 本地数据同步有延迟，首次登录本地数据尚未同步完成
solution: 先从getUserList获取本地数据，获取不到时调用getUserListFromCloud从云端获取
customers: ["圆通"]
source: chat_history
tags: ["鸿蒙","userService","getUserList","数据同步"]
created: 2025-02-19
updated: 2025-03-20
---

## 问题：鸿蒙 鸿蒙首次登录查询用户资料undefined

## 问题详情

**现象**：
第一次登录使用userService查询用户资料返回undefined，第二次才能查询到。

## 排查过程

1. 确认在数据同步完成后调用 → 确认时机
2. 发现本地数据同步需要时间 → 定位延迟
3. 改为先从getUserList获取，获取不到再尝试getUserListFromCloud → 提供方案

**关键发现**：本地数据同步有延迟，首次登录本地数据尚未同步完成

## 问题原因

本地数据同步有延迟，首次登录本地数据尚未同步完成。

## 解决方案

先从getUserList获取本地数据，获取不到时调用getUserListFromCloud从云端获取。

## 其他触发场景

