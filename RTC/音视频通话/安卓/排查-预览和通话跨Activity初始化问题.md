---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: 安卓
title: 预览和通话跨Activity初始化问题
root_cause: 不同Activity页面使用了不同的callback实例，初始化只能传一个callback
solution: 确保跨Activity使用同一个callback实例，或重新初始化SDK
customers: ["中讯邮电咨询设计院"]
source: chat_history
tags: ["RTC","callback","跨Activity","onUserJoin"]
created: 2025-02-13
updated: 2025-03-20
---

## 问题：安卓 预览和通话跨Activity初始化问题

## 问题详情

**现象**：
预览前初始化音视频SDK，关闭预览后在另一个Activity进行通话，收不到远端加入房间的回调。

## 排查过程

1. 确认加入的是同一房间 → 排除房间问题
2. 检查日志发现onUserJoin已触发但客户端未收到回调 → 确认回调已触发
3. 排查发现不同页面使用了不同的callback实例 → 定位问题
4. 初始化只能传一个callback实例 → 确认限制

**关键发现**：不同Activity页面使用了不同的callback实例

## 问题原因

不同Activity页面使用了不同的callback实例，初始化只能传一个callback。

## 解决方案

确保跨Activity使用同一个callback实例，或重新初始化SDK。

## 其他触发场景

