---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 日志
platform: Android
title: SDK日志写入路径配置
root_cause: Android 10+需要私有目录权限，非私有目录无法写入
solution: 需要将日志路径配置为应用私有目录，否则无权限写入。
customers: ["一汽奔腾汽车股份有限公司"]
source: chat_history
tags: ["日志","sdkStorageRootPath","私有目录","权限"]
created: 2025-06-27
updated: 2025-06-27
---

## 问题：Android SDK日志写入路径配置

## 问题详情

**现象**：
客户配置了sdkStorageRootPath但日志没有写入对应文件夹。

**环境信息**：
- 平台：Android
- 涉及配置：sdkStorageRootPath

## 问题原因

Android 10+需要私有目录权限，非私有目录无法写入

## 解决方案

需要将日志路径配置为应用私有目录，否则无权限写入。

## 其他触发场景

