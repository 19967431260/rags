---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: iOS
title: iOS图片消息SDK解析失败
root_cause: NERoom版本兼容性问题
solution: 更新nim_core到1.8.3，netease_roomkit到9.19.4
customers: ["河南新秀金文化传媒"]
source: chat_history
tags: ["图片消息", "iOS", "解析失败", "版本", "NERoom"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：iOS iOS图片消息SDK解析失败

## 问题详情

**现象**：
安卓发送图片消息，iOS收到但SDK解析失败导致无法显示。

## 排查过程

1. 获取iOS SDK日志
2. 确认发送方为安卓
3. 排查NERoom版本问题
4. 建议更新IM SDK版本到9.19.4

## 问题原因

NERoom版本兼容性问题

## 解决方案

更新nim_core到1.8.3，netease_roomkit到9.19.4

## 其他触发场景
- [iOS] iOS图片消息SDK解析失败，来源：['河南新秀金文化传媒']，2026-03-20
- [iOS] iOS图片消息SDK解析失败，来源：['河南新秀金文化传媒']，2026-03-20

