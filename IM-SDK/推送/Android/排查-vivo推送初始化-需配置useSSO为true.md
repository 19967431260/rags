---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: Vivo推送初始化：需将useSSO参数配置为true
root_cause: Vivo推送需要初始化，云信SDK内部做了初始化，但如果隐私授权在SDK初始化之后才获取，需将useSSO参数调整为true
solution: 将useSSO参数调整为true；版本vivo_pushSDK_v3.0.0.7_488.aar可解决；如果仍不行可能是隐私授权获取时机问题，需在SDK初始化之前获取隐私授权
customers: ["广州市巴图鲁信息科技"]
source: chat_history
tags: ["vivo推送", "useSSO", "初始化", "Android"]
created: 2025-07-17
updated: 2025-07-25
---

## 问题：Vivo推送初始化：需将useSSO参数配置为true

## 问题原因

Vivo推送需要初始化，云信SDK内部做了初始化，但如果隐私授权在SDK初始化之后才获取，需将useSSO参数调整为true

## 解决方案

将useSSO参数调整为true；版本vivo_pushSDK_v3.0.0.7_488.aar可解决；如果仍不行可能是隐私授权获取时机问题，需在SDK初始化之前获取隐私授权
