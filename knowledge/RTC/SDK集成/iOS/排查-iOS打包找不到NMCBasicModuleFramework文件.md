---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: SDK集成
platform: iOS
title: iOS打包找不到NMCBasicModuleFramework文件
root_cause: NMCBasicModuleFramework文件位于Pods/NERtcSDK文件夹内，客户未在该路径查找。
solution: 在Pods目录下的NERtcSDK文件夹中查找NMCBasicModuleFramework文件，使用otool -l命令处理该文件。
customers: ["江苏盖睿健康"]
source: chat_history
tags: ["NMCBasicModuleFramework", "iOS打包", "otool", "NERtcSDK", "Pods"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS打包找不到NMCBasicModuleFramework文件

## 问题详情

**现象**：
客户使用RTC SDK 5.3以下版本，在打包时提示找不到NMCBasicModuleFramework文件，客户使用otool -l命令检查依赖时无法定位到该文件。

**环境信息**：
- 平台：iOS

## 排查过程

1. 确认SDK版本为5.3以下老版本 → 需要处理NMCBasicModuleFramework
2. 客户反馈pod损坏无法重新集成 → 建议直接定位文件
3. 指导客户在Pods/NERtcSDK文件夹中查找 → 找到目标文件

## 问题原因

NMCBasicModuleFramework文件位于Pods/NERtcSDK文件夹内，客户未在该路径查找。

## 解决方案

在Pods目录下的NERtcSDK文件夹中查找NMCBasicModuleFramework文件，使用otool -l命令处理该文件。

## 其他触发场景

（无）
