---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息列表
platform: iOS
title: iOS端getMessageList首次调用卡顿
root_cause: SDK版本较低，存在性能问题
solution: 将NIMSDK_LITE升级到10.7.0版本，该版本已优化此问题。使用special版本可指定NIMSDK_LITE到最新版本。
customers: ['AB Leisure Exponent Inc']
source: chat_history
tags: ['iOS', 'getMessageList', '卡顿', 'NIMSDK_LITE', '10.7.0', '性能优化']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：iOS iOS端getMessageList首次调用卡顿

## 问题详情

**现象**：
iOS端调用chatRepo.getMessageList(option: opt)接口时，首次调用会卡住主线程好几秒，即使在子线程调用也无法解决。使用版本：NEChatKit 10.4.1、NIMSDK_LITE 10.5.0。

## 排查过程



## 问题原因

SDK版本较低，存在性能问题

## 解决方案

将NIMSDK_LITE升级到10.7.0版本，该版本已优化此问题。使用special版本可指定NIMSDK_LITE到最新版本。

## 其他触发场景

（合并时在此处追加）
