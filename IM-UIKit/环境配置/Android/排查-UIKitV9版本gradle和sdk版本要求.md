---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 环境配置
platform: Android
title: UIKit V9版本gradle和sdk版本要求
root_cause: UIKit需要较新的gradle、sdk和jdk版本
solution: V9版本需要compileSdkVersion 31+、gradle 7+、jdk11。V10需要jdk17。旧项目需要升级构建环境。
customers: ["学考合一（海南）教育科技有限公司"]
source: chat_history
tags: ["gradle","sdk版本","jdk","V9","兼容性"]
created: 2025-05-31
updated: 2025-05-31
---

## 问题：Android UIKit V9版本gradle和sdk版本要求

## 问题详情

**现象**：
客户项目使用较低版本gradle(4.2.1)和sdk(29)，引入UIKit控件报错。

## 排查过程

1. 尝试升级gradle和sdk版本 → 尝试升级
2. 发现V9/V10都需要较高版本 → 确认版本要求
3. V9需要jdk11，V10需要jdk17 → 确认jdk要求
4. compileSdkVersion需要31-34 → 确认sdk版本

**关键发现**：UIKit需要较新的gradle、sdk和jdk版本

## 问题原因

UIKit需要较新的gradle、sdk和jdk版本

## 解决方案

V9版本需要compileSdkVersion 31+、gradle 7+、jdk11。V10需要jdk17。旧项目需要升级构建环境。

## 其他触发场景

