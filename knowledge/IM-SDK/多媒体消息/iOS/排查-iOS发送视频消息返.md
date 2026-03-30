---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 多媒体消息
platform: iOS
title: iOS发送视频消息返回NIMLocalErrorCodeInvalidMedia错误
root_cause: 文件路径传递错误，将文件路径字符传成了URL格式
solution: 确保传递正确的本地文件路径，不要传入URL格式
customers: ["杭州奇艺网络"]
source: chat_history
tags: ["IM-SDK", "视频消息", "NIMLocalErrorCodeInvalidMedia", "iOS"]
created: 2025-02-13
updated: 2026-03-20
---

## 问题：iOS iOS发送视频消息返回NIMLocalErrorCodeInvalidMedia错误

## 问题详情

**现象**：
IM发送视频消息时出现NIMLocalErrorCodeInvalidMedia错误，提示多媒体文件异常。

## 排查过程

（从会话记录提取）

## 问题原因

文件路径传递错误，将文件路径字符传成了URL格式

## 解决方案

确保传递正确的本地文件路径，不要传入URL格式

## 其他触发场景
- [iOS] iOS发送视频消息返回NIMLocalErrorCodeInvalidMedia错误，来源：['杭州奇艺网络']，2026-03-20
- [iOS] iOS发送视频消息返回NIMLocalErrorCodeInvalidMedia错误，来源：['杭州奇艺网络']，2026-03-20

