---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: GB28181
platform: 服务端
title: 开启直播接口调用gslb失败返回800
root_cause: 同一个摄像头反复开播触发临界case
solution: 研发排查中，建议避免同一摄像头频繁开播
customers: ["政采云"]
source: chat_history
tags: ["RTC", "GB28181", "startStream", "gslb"]
created: 2025-02-18
updated: 2025-03-20
---

## 问题：服务端 开启直播接口调用gslb失败返回800

## 问题详情

**现象**：
调用app/gb28181/startStream接口返回code:800，message:调用gslb接口失败。

**环境信息**：
- 平台：服务端
- 接口：app/gb28181/startStream

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取关键排查步骤，无则省略）

**关键发现**：（从会话提取关键发现，无则省略）

## 问题原因

同一个摄像头反复开播触发临界case。

## 解决方案

研发排查中，建议避免同一摄像头频繁开播。

## 其他触发场景
