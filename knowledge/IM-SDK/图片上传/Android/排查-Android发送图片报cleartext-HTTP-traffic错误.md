---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 图片上传
platform: Android
title: Android发送图片报cleartext HTTP traffic错误
root_cause: Android 9+默认禁止明文HTTP传输，需要在项目配置中允许或配置HTTPS
solution: 检查项目网络安全配置(network_security_config.xml)，添加允许明文传输的配置或使用HTTPS。
customers: ["VIP云信-重庆汇博"]
source: chat_history
tags: ["cleartext HTTP", "Android 9+", "明文传输", "图片上传"]
created: 2025-11-26
updated: 2026-03-20
---

## 问题：Android Android发送图片报cleartext HTTP traffic错误

## 问题详情

**现象**：
Android发送图片时报错：java.io.IOException: cleartext HTTP traffic to wannos.127.net not permitted

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认SDK版本 → 8.9.115
2. 检查手机时间 → 准确
3. 客户自查 → 项目配置问题
**关键发现**：项目网络安全配置问题

**关键发现**：

## 问题原因

Android 9+默认禁止明文HTTP传输，需要在项目配置中允许或配置HTTPS

## 解决方案

检查项目网络安全配置(network_security_config.xml)，添加允许明文传输的配置或使用HTTPS。

## 其他触发场景

