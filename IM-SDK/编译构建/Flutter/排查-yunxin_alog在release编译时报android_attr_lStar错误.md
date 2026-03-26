---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 编译构建
platform: Flutter
title: yunxin_alog在release编译时报android:attr/lStar错误
root_cause: yunxin_alog库需要Android 15(API 35)的资源，项目的compileSdkVersion低于35
solution: 在android/app/build.gradle.kts中设置compileSdk=35；如果仍有错误可能需要清理缓存后重新编译。
customers: ["仁人数字化科技（山东）有限公司"]
source: chat_history
tags: ["yunxin_alog", "release编译", "android:attr/lStar", "compileSdk"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：Flutter yunxin_alog在release编译时报android:attr/lStar错误

## 问题详情

**现象**：
yunxin_alog在release编译时报android:attr/lStar错误。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter on Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
android:attr/lStar错误

## 排查过程

**关键发现**：yunxin_alog库需要Android 15(API 35)的资源，项目的compileSdkVersion低于35

## 问题原因

yunxin_alog库需要Android 15(API 35)的资源，项目的compileSdkVersion低于35

## 解决方案

在android/app/build.gradle.kts中设置compileSdk=35；如果仍有错误可能需要清理缓存后重新编译。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
