---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: iOS
platform: iOS
title: 上传商店bitcode报错
root_cause: 使用的SDK版本包含bitcode，需要升级到无bitcode版本
solution: 升级以下版本去除bitcode：
customers: ["青岛上啥班"]
source: chat_history
tags: ["iOS", "bitcode", "上传商店", "NERtcCallKit", "NIMSDK"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：上传商店bitcode报错

## 问题详情

**现象**：
上传App Store时遇到bitcode相关报错。

**环境信息**：
- 平台：iOS

## 排查过程

1. 客户反馈上传商店报错
2. 提供文档链接去除bitcode
3. 客户执行脚本后仍有报错
4. 建议升级相关库版本

## 根因分析

使用的SDK版本包含bitcode，需要升级到无bitcode版本

## 解决方案

升级以下版本去除bitcode：
pod 'NIMSDK', '9.19.11'
pod 'NERtcCallKit', '2.5.2'
pod 'NERtcSDK', '5.8.5'
如找不到新版本，执行pod repo update后再试。

## 其他触发场景

（无）
