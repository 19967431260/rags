---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 厂商推送
platform: Android
title: 华为HMS推送初始化报ClassNotFoundException
root_cause: ""
solution: 客户自行找到原因解决（未在聊天记录中说明具体解决方案，可能是缺少HMS SDK依赖或需要在海外版本中禁用华为推送配置）
customers: ["武汉梦匠科技有限公司"]
source: chat_history
tags: ["ClassNotFoundException", "HmsInstanceId", "华为推送", "HMS", "海外版本"]
created: 2026-02-09
updated: 2026-03-17
---

## 问题：Android 华为HMS推送初始化报ClassNotFoundException

## 问题详情

**现象**：
海外版本应用在华为手机初始化云信SDK时崩溃，报错：java.lang.NoClassDefFoundError: Failed resolution of: Lcom/huawei/hms/aaid/HmsInstanceId。错误发生在HWPush初始化时找不到华为HMS相关类。

**环境信息**：
- 平台：Android
- 场景：海外版本

**相关日志**：
java.lang.NoClassDefFoundError: Failed resolution of: Lcom/huawei/hms/aaid/HmsInstanceId

## 排查过程

客户自行排查并解决

## 问题原因



## 解决方案

客户自行找到原因解决（未在聊天记录中说明具体解决方案，可能是缺少HMS SDK依赖或需要在海外版本中禁用华为推送配置）

## 其他触发场景
