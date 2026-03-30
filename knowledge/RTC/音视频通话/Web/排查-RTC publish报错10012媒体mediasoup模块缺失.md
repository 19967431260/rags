---
track_type: "排查类"
sub_type: "使用问题"
product: "RTC"
feature: "音视频通话"
platform: "Web"
title: "RTC publish报错10012媒体mediasoup模块缺失"
root_cause: "麦克风、摄像头或屏幕共享开启时有权限确认框，用户一直不点击，然后执行了leave()，之后点击确认出现SDK异常"
solution: "升级SDK到最新版本5.8.29，新版本已优化处理该场景"
customers: ["北京汉医健康科技"]
source: "chat_history"
tags: ["RTC", "10012", "mediasoup", "iOS", "权限"]
created: "2025-09-08"
updated: "2026-03-20"
---

## 问题：Web RTC publish报错10012媒体mediasoup模块缺失

## 问题详情

**现象**：
Web SDK 5.8.16在小程序内H5运行时，publish()报错：{code_:10012, message_:'publish() 媒体mediasoup模块缺失'}，浏览器为iOS 18.5微信内置浏览器。

## 排查过程

1. 询问浏览器版本 → iOS 18.5微信内置浏览器
2. 客户提供日志 → 技术支持分析
3. 查看房间信息 → 发现医生PC端一直在房间内，有视频流上行
4. 分析API调用 → 发现是麦克风/摄像头权限确认框用户未点击就执行leave()导致的异常
5. 确认SDK版本问题

## 问题原因

麦克风、摄像头或屏幕共享开启时有权限确认框，用户一直不点击，然后执行了leave()，之后点击确认出现SDK异常

## 解决方案

升级SDK到最新版本5.8.29，新版本已优化处理该场景

## 其他触发场景
