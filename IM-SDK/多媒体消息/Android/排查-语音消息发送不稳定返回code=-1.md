---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 多媒体消息
platform: Android
title: 语音消息发送不稳定返回code=-1
root_cause: 服务端配置问题导致语音/图片上传不稳定。
solution: 针对appkey进行服务端配置优化，优化后测试验证。
customers: ["YOOY语音"]
source: chat_history
tags: ["code=-1", "语音发送失败", "发送不稳定", "upload-sg.chatnos.com"]
created: 2025-06-26
updated: 2025-03-23
---

## 问题：Android 语音消息发送不稳定返回code=-1

## 问题详情

**现象**：
用户登录成功但发送语音消息返回code=-1，文本消息可正常发送，语音和图片容易失败，现象不稳定（一会行一会不行）。

## 排查过程

1. 确认问题现象 → 发送文本成功(code=200)，语音失败(code=-1)
2. 分析回调状态 → observeMsgStatus返回fail
3. 请求ping测试 → upload-sg.chatnos.com
4. 网络测试结果 → 延迟正常
5. 配置优化 → 针对appkey做配置优化

**关键发现**：服务端配置问题导致语音/图片上传不稳定

## 问题原因

服务端配置问题导致语音/图片上传不稳定。

## 解决方案

针对appkey进行服务端配置优化，优化后测试验证。

## 其他触发场景

