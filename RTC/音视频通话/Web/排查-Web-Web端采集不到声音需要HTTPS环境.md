---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: Web
title: Web端采集不到声音需要HTTPS环境
root_cause: Web端使用HTTP协议访问，浏览器限制无法获取麦克风设备权限，需要使用HTTPS或localhost。
solution: Web端开发需使用HTTPS协议或localhost访问，才能正常获取麦克风等设备权限。
customers: ["FVIP云信-上海功途教育"]
source: chat_history
tags: ["Web", "HTTPS", "采集", "麦克风", "设备权限"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Web Web端采集不到声音需要HTTPS环境

## 问题详情

**现象**：
Web端通过join成功加入房间，但采集不到声音。

## 排查过程

1. 检查console日志 → 发现权限访问报错
2. 确认访问协议 → 客户使用HTTP本地开发
**关键发现**：浏览器要求HTTPS或localhost才能访问设备权限

## 问题原因

Web端使用HTTP协议访问，浏览器限制无法获取麦克风设备权限，需要使用HTTPS或localhost。

## 解决方案

Web端开发需使用HTTPS协议或localhost访问，才能正常获取麦克风等设备权限。

## 其他触发场景

