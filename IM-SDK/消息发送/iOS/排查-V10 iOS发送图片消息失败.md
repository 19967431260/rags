---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息发送
platform: iOS
title: V10 iOS发送图片消息失败
root_cause: 图片消息参数设置问题，sceneName和宽高参数需要正确设置。
solution: 参考官方示例代码设置图片消息参数：imagePath（沙盒路径）、name（图片名）、sceneName（@""）、width/height（200）。
customers: ["杭州跨客技术服务有限公司"]
source: chat_history
tags: ["图片消息", "iOS", "V10", "createImageMessage", "发送失败"]
created: 2025-05-16
updated: 2025-03-20
---

## 问题：iOS V10 iOS发送图片消息失败

## 问题详情

**现象**：
iOS使用V10 SDK发送视频和语音消息成功，但发送图片消息报错。使用V2NIMMessageCreator createImageMessage方法。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 客户反馈发送图片失败，视频语音正常 → 技术支持建议检查sceneName参数
2. 客户尝试传nil和空字符串都失败 → 技术支持提供示例代码
3. 建议对比官方示例代码排查

## 问题原因

图片消息参数设置问题，sceneName和宽高参数需要正确设置。

## 解决方案

参考官方示例代码设置图片消息参数：imagePath（沙盒路径）、name（图片名）、sceneName（@""）、width/height（200）。

## 其他触发场景

