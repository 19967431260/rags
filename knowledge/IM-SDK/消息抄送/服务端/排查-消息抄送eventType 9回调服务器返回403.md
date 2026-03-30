---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息抄送
platform: 服务端
title: 消息抄送eventType 9回调服务器返回403
root_cause: 服务器返回403，响应体大小超过限制(512-1024)
solution: 检查服务器响应体大小，确保不超过抄送接口限制
customers: ["广州网络科技"]
source: chat_history
tags: ["消息抄送", "eventType 9", "403", "回调", "response size"]
created: 2025-05-29
updated: 2025-03-20
---

## 问题：服务端 消息抄送eventType 9回调服务器返回403

## 问题详情

**现象**：
客户反馈进出房通知的消息抄送(eventType 9)不发送了，经排查发现是服务器返回403错误。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 确认监听回调类型为eventType 9
2. 检查服务器返回 → 发现返回403错误，response.size.exceed=512-1024
3. 客户自行找到问题原因

## 问题原因

服务器返回403，响应体大小超过限制(512-1024)

## 解决方案

检查服务器响应体大小，确保不超过抄送接口限制

## 其他触发场景

