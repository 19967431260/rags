---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 小程序
title: 小程序ESM引入发送图片视频报V2NIMError:misuse
root_cause: 未引入V2NIMStorageService云端存储模块
solution: 引入V2NIMStorageService模块，该模块包含上传文件能力，发送多媒体消息需要依赖此模块
customers: ['Helo']
source: chat_history
tags: ['V2NIMError', 'misuse', '小程序', 'ESM', '图片消息', '视频消息']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：小程序 小程序ESM引入发送图片视频报V2NIMError:misuse

## 问题详情

**现象**：
小程序使用ESM方式引入IM SDK时，发送图片和视频消息报错V2NIMError: misuse，文字消息正常。

## 排查过程



## 问题原因

未引入V2NIMStorageService云端存储模块

## 解决方案

引入V2NIMStorageService模块，该模块包含上传文件能力，发送多媒体消息需要依赖此模块

## 其他触发场景

（合并时在此处追加）
