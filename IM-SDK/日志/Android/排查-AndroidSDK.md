---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 日志
platform: Android
title: Android SDK日志路径配置
root_cause: SDKOptions未正确配置sdkStorageRootPath
solution: 在IMKitClient.init时配置SDKOptions.sdkStorageRootPath，建议写法：context.getExternalCacheDir().getCanonicalPath() + "/nim"
customers: ["江西闪招信息技术有限公司"]
source: chat_history
tags: ["日志", "SDKOptions", "Android", "路径配置"]
created: 2025-02-15
updated: 2026-03-20
---

## 问题：Android Android SDK日志路径配置

## 问题详情

**现象**：
客户无法找到IM SDK日志文件。

## 排查过程

1. 检查SDKOptions的sdkStorageRootPath配置
2. 确认日志写入外部存储路径
3. 日志路径：/Android/data/包名/cache/nim/

## 问题原因

SDKOptions未正确配置sdkStorageRootPath

## 解决方案

在IMKitClient.init时配置SDKOptions.sdkStorageRootPath，建议写法：context.getExternalCacheDir().getCanonicalPath() + "/nim"

## 其他触发场景
- [Android] Android SDK日志路径配置，来源：['江西闪招信息技术有限公司']，2026-03-20
- [Android] Android SDK日志路径配置，来源：['江西闪招信息技术有限公司']，2026-03-20

