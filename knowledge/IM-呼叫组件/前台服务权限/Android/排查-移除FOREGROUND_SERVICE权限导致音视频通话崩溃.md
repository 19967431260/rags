---
track_type: 排查类
sub_type: 使用问题
product: IM-呼叫组件
feature: 前台服务权限
platform: Android
title: 移除FOREGROUND_SERVICE权限导致音视频通话崩溃
root_cause: 呼叫组件默认使用前台服务保持通话稳定性，移除权限后无法启动前台服务导致崩溃。
solution: 在NimSDKOptionConfig中配置：
```kotlin
val config = NimSDKOptionConfig()
config.enableForegroundService = false
```
不启动前台服务，避免权限依赖。
customers: ["VIP云信-去狮城科技"]
source: chat_history
tags: ["FOREGROUND_SERVICE", "音视频通话", "谷歌审核", "enableForegroundService", "权限崩溃"]
created: 2026-02-13
updated: 2026-03-15
---

## 问题：Android 移除FOREGROUND_SERVICE权限导致音视频通话崩溃

## 问题详情

**现象**：
谷歌应用商店审核时要求移除FOREGROUND_SERVICE相关权限（MICROPHONE、CAMERA），但移除后调起音频通话会崩溃，提示权限被拒。

## 排查过程

1. 移除manifest权限 → 通话崩溃
2. 设置disableAwake=true → 无效
3. 配置enableForegroundService=false → 崩溃解决

## 问题原因

呼叫组件默认使用前台服务保持通话稳定性，移除权限后无法启动前台服务导致崩溃。

## 解决方案

在NimSDKOptionConfig中配置：
```kotlin
val config = NimSDKOptionConfig()
config.enableForegroundService = false
```
不启动前台服务，避免权限依赖。
