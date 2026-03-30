---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 登录
platform: Flutter
title: Flutter iOS平台无法拉取NIMSDK_LITE
root_cause: 本地spec仓库未更新，找不到兼容版本
solution: 执行pod install --repo-update更新本地spec仓库后再尝试安装
customers: ["郑州鸾翔凤集文化传媒有限公司"]
source: chat_history
tags: ["IM V9/V10","Flutter","iOS","CocoaPods"]
created: 2025-05-19
updated: 2025-03-23
---

## 问题：Flutter Flutter iOS平台无法拉取NIMSDK_LITE

## 问题详情

**现象**：
客户在iOS平台执行pod install时，报错CocoaPods could not find compatible versions for pod NIMSDK_LITE/FCS。

**环境信息**：
- 平台：Flutter iOS
- 功能：IM SDK集成

## 排查过程

1. 确认错误信息 → CocoaPods could not find compatible versions
2. 分析原因 → 本地spec仓库未更新
3. 确认解决方案 → 更新本地spec仓库

**关键发现**：本地spec仓库未更新，找不到兼容版本

## 问题原因

本地spec仓库未更新，找不到兼容版本。

## 解决方案

执行pod install --repo-update更新本地spec仓库后再尝试安装。

## 其他触发场景

