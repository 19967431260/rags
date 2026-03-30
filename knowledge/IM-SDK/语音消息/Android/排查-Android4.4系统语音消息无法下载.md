---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Android
title: Android 4.4系统语音消息无法下载
root_cause: Android 4.4系统已不被支持（新版本SDK最低要求API 21），网络访问受限导致语音消息下载失败
solution: Android 4.4不再兼容；最低Android API版本需升级至21；如需在低版本Android上下载语音，可尝试将语音URL中https替换为http后用okhttp3下载
customers: ["上海互说"]
source: chat_history
tags: ["Android", "4.4", "语音下载", "SDK版本", "API 21", "okhttp3"]
created: 2025-07-08
updated: 2025-07-25
---

## 问题：Android 4.4系统语音消息无法下载

## 问题详情

**现象**：
部分Android 4.4设备语音消息无法下载，SDK版本6.5.0，问题出现在江苏镇江、山东济南、甘肃等地区。同网络下手机和电脑浏览器可正常访问语音链接。

**环境信息**：
- SDK版本：6.5.0
- Android版本：4.4
- 问题区域：江苏镇江、山东济南、甘肃等地

## 排查过程

1. 排查域名解析问题，未发现异常
2. 确认纯5G网络下问题依旧，为设备网络环境限制
3. 确认为Android 4.4系统版本过低
4. 确认2023年起新版本SDK整体不再支持Android 4.4

**关键发现**：Android 4.4系统已不被支持，新版SDK整体不支持该版本；最低Android API版本需升级至21。

## 问题原因

Android 4.4系统版本过低，已被官方废弃支持。新版本SDK不再兼容，导致网络访问受限、语音消息下载失败。

## 解决方案

1. Android 4.4不再兼容，新版SDK整体不支持
2. 最低Android API版本需升级至21（原19）
3. 如需在低版本Android上下载语音，可尝试：用okhttp3将语音URL中https替换为http后下载
4. 长期方案：升级客户端Android最低系统版本要求
