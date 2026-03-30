---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送配置
platform: Android
title: Android偶发性语音发不出：SDK重连中408超时
root_cause: 用户网络波动导致SDK长连接断开，SDK重试期间返回408超时，SDK不会自动重连需业务层手动处理
solution: SDK返回408后不会自动重连，需要在返回408后再次调用login接口重新建立连接；可联系技术支持拉取日志分析。
customers: ["和仁"]
source: chat_history
tags: ["Android", "语音发不出", "408超时", "重连"]
created: 2025-07-09
updated: 2025-07-25
---

## 问题：Android Android偶发性语音发不出：SDK重连中408超时

## 问题详情

**现象**：

## 问题原因

用户网络波动导致SDK长连接断开，SDK重试期间返回408超时，SDK不会自动重连需业务层手动处理

## 解决方案

SDK返回408后不会自动重连，需要在返回408后再次调用login接口重新建立连接；可联系技术支持拉取日志分析。
