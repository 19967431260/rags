---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送SDK版本不兼容导致NoSuchMethodError
root_cause: OPPO推送SDK版本与云信SDK 8.9.121不兼容
solution: 使用OPPO推送SDK 3.4.0版本：com.heytap.msp_3.4.0.aar
customers: ["上海掌鑫聚芯信息科技有限公司"]
source: chat_history
tags: ["OPPO推送", "NoSuchMethodError", "SDK版本", "mix_push"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Android OPPO推送SDK版本不兼容导致NoSuchMethodError

## 问题详情

**现象**：
OPPO推送报错NoSuchMethodError: No static method isSupportPush，云信SDK版本8.9.121。

**排查过程**：
1. 检查日志发现OPPO推送版本不兼容
2. 确认当前SDK版本8.9.121
3. 提供适配的OPPO推送SDK版本

## 问题原因

OPPO推送SDK版本与云信SDK 8.9.121不兼容

## 解决方案

使用OPPO推送SDK 3.4.0版本：com.heytap.msp_3.4.0.aar


## 其他触发场景
- [Android] vivo推送SDK版本不兼容导致NoClassDefFoundError，来源：["上海掌鑫聚芯信息科技有限公司"]，2026-03-20
