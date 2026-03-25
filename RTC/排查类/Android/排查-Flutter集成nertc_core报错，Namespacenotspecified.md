---
track_type: 排查类
sub_type: 环境问题排查
product: RTC
feature: 排查类
platform: Android
title: Flutter集成nertc_core报错，Namespace not specified
root_cause: 客户环境问题
solution: 在较新版本的Android Gradle Plugin中，需要在build.gradle文件中明确指定namespace。可以在项目级的build.gradle文件中添加：subprojects {
customers: ["郑州白喵星网络科技有限公司"]
source: chat_history
tags: []
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Flutter集成nertc_core报错，Namespace not specified

## 问题详情

**现象**：
Flutter集成nertc_core报错，Namespace not specified

**环境信息**：
- 平台：安卓
- 产品：音视频2.0

## 解决方案

在较新版本的Android Gradle Plugin中，需要在build.gradle文件中明确指定namespace。可以在项目级的build.gradle文件中添加：subprojects { if (project.name == "nertc_core"){ project.afterEvaluate { android{ namespace = "com.netease.nertcflutter" } } } }。或者参考最佳实践：https://github.com/netease-im/G2-API-Examples/tree/main/flutter/nertc_api_example

## 其他触发场景

（无）
