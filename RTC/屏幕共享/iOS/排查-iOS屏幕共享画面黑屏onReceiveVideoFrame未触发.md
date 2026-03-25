---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 屏幕共享
platform: iOS
title: iOS屏幕共享画面黑屏onReceiveVideoFrame未触发
root_cause: 屏幕共享Extension配置不完整，缺少系统级屏幕共享授权
solution: 参考Demo配置完整的屏幕共享Extension，确保AppGroup、Broadcast Upload Extension配置正确，添加NEScreenShareHostDelegate代理
customers: ["成都华西数字医疗"]
source: chat_history
tags: ["iOS", "屏幕共享", "黑屏", "onReceiveVideoFrame", "Extension"]
created: 2025-05-08
updated: 2025-03-20
---

## 问题：iOS iOS屏幕共享画面黑屏onReceiveVideoFrame未触发

## 问题详情

**现象**：
客户反馈startScreenCapture返回0，setupLocalSubStreamVideoCanvas后画面黑屏，onReceiveVideoFrame未触发。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 检查屏幕共享Extension配置
2. 确认AppGroup配置正确
3. 检查NEScreenShareHostDelegate代理是否添加
4. 确认弹出系统屏幕共享授权弹窗

## 问题原因

屏幕共享Extension配置不完整，缺少系统级屏幕共享授权

## 解决方案

参考Demo配置完整的屏幕共享Extension，确保AppGroup、Broadcast Upload Extension配置正确，添加NEScreenShareHostDelegate代理

## 其他触发场景

