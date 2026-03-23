---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: SDK体积
platform: iOS
title: iOS NERtcSDK 4.6.22版本打包体积过大
root_cause: 4.6.22版本未去除bitcode，在新Xcode上打包时体积异常增大
solution: 升级到NERtcSDK 5.8.20版本，该版本已去除bitcode，打包增量约30MB。推荐组合：pod 'NERtcCallKit/NOS_Special', '2.5.2' + pod 'NIMSDK_LITE', '9.20.10' + pod 'NERtcSDK', '5.8.20'
customers:
  - 深圳闯游星科技有限公司
source: chat_history
tags:
  - iOS
  - RTC
  - SDK体积
  - bitcode
  - 4.6.22
  - 5.8.20
created: '2025-06-06'
updated: '2025-03-23'
---

## 问题：iOS iOS NERtcSDK 4.6.22版本打包体积过大

## 问题详情

**现象**：
集成NERtcSDK 4.6.22版本后，iOS App打包后IPA体积增加约80MB，其中NERtcSDK.framework约135MB，导致整体IPA接近200MB。

**排查过程**：

1. 确认4.x版本包含多个架构，上架时只需arm64
2. 发现新Xcode bitcode兼容问题导致4.6.22版本打包体积大
3. 建议升级到5.8.20版本（已去除bitcode）
4. 验证5.8.20版本打包增量约30MB

**关键发现**：4.6.22版本未去除bitcode，在新Xcode上打包时体积异常增大

## 问题原因

4.6.22版本未去除bitcode，在新Xcode上打包时体积异常增大

## 解决方案

升级到NERtcSDK 5.8.20版本，该版本已去除bitcode，打包增量约30MB。推荐组合：pod 'NERtcCallKit/NOS_Special', '2.5.2' + pod 'NIMSDK_LITE', '9.20.10' + pod 'NERtcSDK', '5.8.20'
