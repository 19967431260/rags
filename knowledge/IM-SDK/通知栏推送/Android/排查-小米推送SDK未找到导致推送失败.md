---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: 小米推送SDK未找到导致推送失败
root_cause: 在vivo设备上测试小米推送功能，小米推送只在小米设备上生效
solution: 小米推送只在小米设备上生效，需要在小米设备上测试。vivo设备需要配置vivo推送。
customers: ["福州市玄星网络科技有限公司"]
source: chat_history
tags: ["小米推送","Android","设备兼容","推送失败"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Android 小米推送SDK未找到导致推送失败

## 问题详情

**现象**：
Android端日志显示"Xiao Mi push sdk find"和"framework not support, puthType=5"。客户使用Flutter集成，小米推送SDK版本MiPush_SDK_Client_6_0_1-C_3rd，NIM SDK版本10.9.4+3。测试设备为vivo手机。

## 排查过程

1. 检查日志 → 发现"Xiao Mi push sdk find"和"framework not support"错误
2. 检查APK内小米SDK → 已包含小米SDK
3. 检查测试设备 → 发现是vivo设备

**关键发现**：在vivo设备上测试小米推送

## 问题原因

在vivo设备上测试小米推送功能，小米推送只在小米设备上生效

## 解决方案

小米推送只在小米设备上生效，需要在小米设备上测试。vivo设备需要配置vivo推送。

## 其他触发场景

