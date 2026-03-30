---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 隐私合规
platform: Android
title: Android隐私合规用户同意前获取ssid问题
root_cause: SDK版本9.17.1的config方法影响扩大，导致在用户同意隐私协议前就执行了获取ssid的代码
solution: 1. 升级SDK到9.19.10版本（该版本去掉了ssid获取）
customers: ["徐州比邻"]
source: chat_history
tags: ["隐私合规", "ssid", "Android", "9.19.10", "NIMClient.initDelay", "初始化"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android隐私合规用户同意前获取ssid问题

## 问题详情

**现象**：
应用在上架检测时被检测到在用户同意隐私协议之前获取了ssid，违反隐私合规要求。客户当前使用SDK版本9.17.1，采用NIMClient.config+NIMClient.initSdk的初始化方式。

**环境信息**：
- 平台：Android

## 排查过程

1. 客户反馈升级到9.17.1后仍被检测出隐私协议同意前获取ssid的问题
2. 检查客户初始化代码，发现用户在同意隐私协议前就调用了NIMClient.config和NIMClient.initSdk
**关键发现**：config方法在某些版本中扩大了影响范围，导致获取ssid的代码被执行

## 根因分析

SDK版本9.17.1的config方法影响扩大，导致在用户同意隐私协议前就执行了获取ssid的代码

## 解决方案

1. 升级SDK到9.19.10版本（该版本去掉了ssid获取）
2. 修改初始化逻辑：用户同意隐私协议前不调用任何NIM API，在同意回调中调用NIMClient.initDelay接口替代原来的NIMClient.config+NIMClient.initSdk

## 其他触发场景

（无）
