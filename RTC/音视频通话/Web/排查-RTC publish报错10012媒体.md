---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Web
title: RTC publish报错10012媒体mediasoup模块缺失
root_cause: 麦克风、摄像头或屏幕共享开启时有权限确认框，用户一直不点击，然后执行了leave()，之后点击确认出现SDK异常
solution: 升级SDK到最新版本5.8.29，新版本已优化处理该场景
customers: ['北京汉医健康科技']
source: chat_history
tags: ['RTC', '10012', 'mediasoup', 'iOS', '权限']
created: 2025-09-08
updated: 2026-03-25
---

## 问题：Web RTC publish报错10012媒体mediasoup模块缺失

## 问题详情

**现象**：
Web SDK 5.8.16在小程序内H5运行时，publish()报错：{code_:10012, message_:'publish() 媒体mediasoup模块缺失'}，浏览器为iOS 18.5微信内置浏览器。

## 解决方案

升级SDK到最新版本5.8.29，新版本已优化处理该场景
