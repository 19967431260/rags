---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: V9发送消息报错414 check checksum error
root_cause: 登录使用的appkey与发送消息时SDK配置的appkey不一致
solution: 确保登录和发送消息使用同一个appkey。检查初始化SDK时配置的appkey与登录时使用的appkey是否一致。
customers: ["湖南惠农"]
source: chat_history
tags: ["414", "checksum error", "appkey", "V9"]
created: 2026-01-13
updated: 2026-03-15
---

## 问题：Android V9发送消息报错414 check checksum error

## 问题详情

**现象**：
Android V9 SDK发送消息时报错414 check checksum error，但登录成功。

## 排查过程

1. 检查报错信息 → 414 check checksum error
2. 确认登录状态 → 登录成功
3. 检查appkey配置 → 发现使用了错误的appkey

**关键发现**：登录和发送消息使用了不同的appkey

## 问题原因

登录使用的appkey与发送消息时SDK配置的appkey不一致

## 解决方案

确保登录和发送消息使用同一个appkey。检查初始化SDK时配置的appkey与登录时使用的appkey是否一致。

## 其他触发场景

