---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK升级
platform: Android
title: 升级SDK到9.17.2及以上版本导致应用启动崩溃
root_cause: SDK在9.17.2版本将okhttp依赖升级到4.10.0，与客户应用环境存在兼容性冲突。
solution: 在build.gradle中添加依赖强制策略，将okhttp版本降级到3.4.1：configurations.all { resolutionStrategy { resolutionStrategy.force 'com.squareup.okhttp3:okhttp:3.4.1' } }。需要测试登录和文件消息发送功能确保正常。
customers: ["可思达地信息科技"]
source: chat_history
tags: ["崩溃", "SDK升级", "okhttp", "依赖冲突", "9.17.2"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Android 升级SDK到9.17.2及以上版本导致应用启动崩溃

## 问题详情

**现象**：
客户升级SDK版本时发现，从9.17.1升级到9.17.2及以上版本后，应用启动时直接崩溃，无法进入首页。必现。

**环境信息**：
- SDK 版本：9.17.2+
- 系统版本 / 设备：Android平台

**相关日志**：
崩溃信息被应用自身的CrashHandler捕获，进程通过SIG:9信号正常退出。

## 排查过程

1. 检查SDK版本差异 → 确认9.17.1及之前版本正常，9.17.2开始崩溃
2. 检查依赖更新 → 确认nim_base和chatroom都已同步升级
3. 分析崩溃日志 → 发现崩溃信息被应用自身的CrashHandler捕获，无明确堆栈
4. 排查依赖冲突 → 发现SDK在9.17.2版本升级了okhttp从3.x到4.10.0
5. 测试依赖版本 → 强制使用okhttp 3.4.1后应用恢复正常

**关键发现**：SDK在9.17.2版本将okhttp依赖从3.x升级到4.10.0，与客户应用存在兼容性问题。

## 问题原因

SDK在9.17.2版本将okhttp依赖升级到4.10.0，与客户应用环境存在兼容性冲突。

## 解决方案

在build.gradle中添加依赖强制策略，将okhttp版本降级到3.4.1：configurations.all { resolutionStrategy { resolutionStrategy.force 'com.squareup.okhttp3:okhttp:3.4.1' } }。需要测试登录和文件消息发送功能确保正常。

## 其他触发场景

（暂无）
