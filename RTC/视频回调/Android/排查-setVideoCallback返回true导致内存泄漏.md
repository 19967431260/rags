---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频回调
platform: Android
title: setVideoCallback返回true导致内存泄漏
root_cause: 使用Camera2+I420格式时存在内存泄漏
solution: 切换为Camera1+NV21格式。加入房间前调用setParameter设置KEY_VIDEO_CAMERA_TYPE为1使用Camera1，然后setLocalVideoConfig设置colorFormat为NV21。
customers: ["福建天创信息科技有限公司"]
source: chat_history
tags: ["RTC", "setVideoCallback", "内存泄漏", "Camera1", "NV21"]
created: 2026-02-27
updated: 2026-03-17
---

## 问题：Android setVideoCallback返回true导致内存泄漏

## 问题详情

**现象**：
调用setVideoCallback并返回true后，内存持续增长无法回收，最终导致应用闪退。返回false时内存平稳。

## 排查过程

1. 检查回调处理代码 → 回调中未做任何处理直接返回
2. 测试返回false → 内存平稳无增长
3. 测试返回true → 内存持续增长，手动GC无法回收

**关键发现**：返回true时SDK内部存在内存泄漏

## 问题原因

使用Camera2+I420格式时存在内存泄漏

## 解决方案

切换为Camera1+NV21格式。加入房间前调用setParameter设置KEY_VIDEO_CAMERA_TYPE为1使用Camera1，然后setLocalVideoConfig设置colorFormat为NV21。

## 其他触发场景
