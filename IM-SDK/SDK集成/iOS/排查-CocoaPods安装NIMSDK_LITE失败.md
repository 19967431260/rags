---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: SDK集成
platform: iOS
title: CocoaPods安装NIMSDK_LITE失败
root_cause: CocoaPods下载网络问题。
solution: 可直接访问SDK下载地址：https://yx-web-nosdn.netease.im/im/sdk/ios/NIM_iOS_SDK_IM_v9.16.6_ee9dab6bc8.zip
customers: ["初晴/核芯"]
source: chat_history
tags: ["CocoaPods", "NIMSDK_LITE", "安装失败", "iOS", "网络问题"]
created: 2025-02-25
updated: 2025-03-20
---

## 问题：iOS CocoaPods安装NIMSDK_LITE失败

## 问题详情

**现象**：
使用pod 'NIMSDK_LITE', '~> 9.16.6'安装失败，报错HTTP/2 stream was not closed cleanly: INTERNAL_ERROR。

**环境信息**：
- 平台：iOS
- 安装方式：CocoaPods
- SDK版本：9.16.6

**相关日志**：
HTTP/2 stream was not closed cleanly: INTERNAL_ERROR

## 排查过程

1. 初步判断 → 怀疑网络问题，建议挂梯子
2. 客户尝试 → 已挂梯子仍失败
3. 建议直接下载 → 提供SDK直链下载地址

**关键发现**：CocoaPods下载网络问题

## 问题原因

CocoaPods下载网络问题。

## 解决方案

可直接访问SDK下载地址：https://yx-web-nosdn.netease.im/im/sdk/ios/NIM_iOS_SDK_IM_v9.16.6_ee9dab6bc8.zip

## 其他触发场景
