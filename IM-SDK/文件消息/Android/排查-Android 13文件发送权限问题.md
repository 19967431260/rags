---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 文件消息
platform: Android
title: Android 13文件发送权限问题
root_cause: Android 13权限模型变更，需要使用细分的媒体权限（READ_MEDIA_AUDIO/IMAGES/VIDEO）替代READ_EXTERNAL_STORAGE
solution: Android 13及以上申请READ_MEDIA_AUDIO/IMAGES/VIDEO权限；如需访问非媒体文件，申请MANAGE_EXTERNAL_STORAGE权限
customers: ['北京校企脉文化科技有限公司']
source: chat_history
tags: ['Android 13', '文件发送', '权限', 'READ_MEDIA']
created: 2025-02-19
updated: 2026-03-23
---

## 问题：Android Android 13文件发送权限问题

## 问题详情

**现象**：
Android端发送文件消息没有成功，在Android 13系统上文件读写权限申请失败。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查发送返回 → 返回code 200表示发送成功
2. 检查文件路径 → 确认文件是否存在
3. 关键发现：Android 13（API 33）对媒体文件权限进行了细化，需要使用READ_MEDIA_AUDIO/IMAGES/VIDEO替代旧版权限

## 问题原因

Android 13权限模型变更，需要使用细分的媒体权限（READ_MEDIA_AUDIO/IMAGES/VIDEO）替代READ_EXTERNAL_STORAGE

## 解决方案

Android 13及以上申请READ_MEDIA_AUDIO/IMAGES/VIDEO权限；如需访问非媒体文件，申请MANAGE_EXTERNAL_STORAGE权限

## 其他触发场景

（合并时在此处追加：`- [Android] Android 13文件发送权限问题，来源：['北京校企脉文化科技有限公司']，2026-03-23`）
