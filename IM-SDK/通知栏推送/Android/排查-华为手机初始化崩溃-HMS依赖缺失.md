---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 通知栏推送
platform: Android
title: 华为手机初始化崩溃-HMS依赖缺失
root_cause: 海外版本未集成华为HMS推送SDK依赖包
solution: 在build.gradle中添加华为HMS推送依赖：implementation 'com.huawei.hms:push:x.x.x.xxx'，或在海外版本中通过MixPushConfig禁用华为推送
customers: ["VIP云信-武汉梦匠科技有限公司"]
source: chat_history
tags: ["华为推送", "NoClassDefFoundError", "HmsInstanceId", "HMS依赖", "海外版本"]
created: 2026-02-09
updated: 2026-03-15
---

## 问题：Android 华为手机初始化崩溃-HMS依赖缺失

## 问题详情

**现象**：
海外版本在华为手机初始化时崩溃，报错：java.lang.NoClassDefFoundError: Failed resolution of: Lcom/huawei/hms/aaid/HmsInstanceId。ClassNotFoundException显示在DexPathList中找不到该类。

## 排查过程

1. 检查崩溃堆栈 → HWPush初始化时找不到HmsInstanceId类
2. 确认ClassNotFoundException → 华为HMS SDK依赖缺失
**关键发现**：海外版本缺少华为HMS推送依赖

## 问题原因

海外版本未集成华为HMS推送SDK依赖包

## 解决方案

在build.gradle中添加华为HMS推送依赖：implementation 'com.huawei.hms:push:x.x.x.xxx'，或在海外版本中通过MixPushConfig禁用华为推送
