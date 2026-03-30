---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: iOS集成
platform: iOS
title: Xcode 16.2/iOS 18.3上传App Store报错
root_cause: NMCBasicModuleFramework在5.3.0版本之后已经移除，可能是缓存问题导致旧版本残留
solution: 1. 确认当前使用的SDK版本，如果是5.3以上版本，删除缓存重新pod install
2. 参考官方文档 https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client 中的脚本处理bitcode问题
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# Xcode 16.2/iOS 18.3上传App Store报错

## 问题描述

Xcode升级到16.2，iOS系统升级到18.3后，上传App Store过程中报错，提示NMCBasicModuleFramework包含bitcode

## 问题背景

- 报错信息：Invalid Executable. The executable contains bitcode
- 其他框架已处理好，但找不到NMCBasicModuleFramework.framework

## 根因分析

NMCBasicModuleFramework在5.3.0版本之后已经移除，可能是缓存问题导致旧版本残留

## 解决方案

1. 确认当前使用的SDK版本，如果是5.3以上版本，删除缓存重新pod install
2. 参考官方文档 https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client 中的脚本处理bitcode问题

## 标签

- iOS
- Xcode
- App Store
- bitcode
- NMCBasicModuleFramework

## 客户

- FVIP-云信-江苏盖睿健康

## 会话日期

2025-02-27
