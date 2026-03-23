---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 基础功能
platform: Android
title: Android音频采样率和声道配置
root_cause: ""
solution: "确认onAudioFrameDidRecord回调，研发查看采样率和声道配置"
customers: ["云信"]
source: chat_history
tags: ["token","消息"]
created: 2025-06-04
updated: 2025-03-23
---

## 问题：Android音频采样率和声道配置

## 问题详情

**现象**：
客户需要16k-单声道-16位深的音频格式，咨询setAudioFrameObserver是否可以设置。

**环境信息**：
- 平台：Android
- 需求：16k采样率、单声道、16位深

## 排查过程

1. 确认回调方法 → onAudioFrameDidRecord
2. 研发确认 → 查看采样率和声道是否有办法单独配置
3. JDK版本 → lib-module-1.0.0.jar使用JDK11，客户需要1.8

## 问题原因

需要确认SDK是否支持单独配置音频采样率和声道

## 解决方案

1. 确认使用onAudioFrameDidRecord回调获取数据
2. 研发查看是否支持采样率和声道单独配置
3. 打包时配置compileOptions使用Java 1.8

## 其他触发场景

