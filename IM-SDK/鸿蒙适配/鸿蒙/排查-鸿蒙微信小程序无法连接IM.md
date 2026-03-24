---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 鸿蒙适配
platform: 鸿蒙
title: 鸿蒙微信小程序无法连接IM
root_cause: 鸿蒙的微信小程序websocket有兼容问题，鸿蒙上缺失wx.connectSocket API，无法建立长连接。
solution: 建议客户先使用鸿蒙App访问。这是微信和鸿蒙那边的兼容工作，云信只能确认最新进展。腾讯IM官方提供的小程序demo在鸿蒙上也无法建立websocket连接。
customers: ["智联招聘"]
source: chat_history
tags: ["鸿蒙", "小程序", "websocket", "connectSocket"]
created: 2025-02-21
updated: 2025-03-20
---

## 问题：鸿蒙 鸿蒙微信小程序无法连接IM

## 问题详情

**现象**：
鸿蒙系统上的微信小程序无法正常连接IM，怀疑syncdone没有执行。

**环境信息**：
- 平台：鸿蒙
- 应用：微信小程序

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取关键排查步骤，无则省略）

**关键发现**：（从会话提取关键发现，无则省略）

## 问题原因

鸿蒙的微信小程序websocket有兼容问题，鸿蒙上缺失wx.connectSocket API，无法建立长连接。

## 解决方案

建议客户先使用鸿蒙App访问。这是微信和鸿蒙那边的兼容工作，云信只能确认最新进展。腾讯IM官方提供的小程序demo在鸿蒙上也无法建立websocket连接。

## 其他触发场景
