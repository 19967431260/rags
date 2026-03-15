---
track_type: 排查类
sub_type: 集成问题
product: NERtcCallUIKit
feature: 依赖管理
platform: iOS
title: NERtcCallUIKit本地源码集成时NECommonKit版本冲突
root_cause: NERtcCallUIKit.podspec中依赖的NERtcCallKit未指定为NOS_Special子模块，导致引入了NOS子模块，与其他组件的NECommonKit版本不一致
solution: 修改NERtcCallUIKit.podspec文件，将NERtcCallKit依赖改为NERtcCallKit/NOS_Special。删除Podfile.lock后重新pod install。
customers: ["VIP云信-深圳市天启航空科技有限公司"]
source: chat_history
tags: ["NERtcCallUIKit", "NECommonKit", "版本冲突", "NOS_Special", "podspec"]
created: 2026-02-09
updated: 2026-03-15
---

## 问题：iOS NERtcCallUIKit本地源码集成时NECommonKit版本冲突

## 问题详情

**现象**：
使用本地源码集成NERtcCallUIKit时，CocoaPods报错NECommonKit版本冲突。NERtcCallKit/NOS依赖9.7.4版本，而NEChatKit依赖9.7.5版本。

## 排查过程



## 问题原因

NERtcCallUIKit.podspec中依赖的NERtcCallKit未指定为NOS_Special子模块，导致引入了NOS子模块，与其他组件的NECommonKit版本不一致

## 解决方案

修改NERtcCallUIKit.podspec文件，将NERtcCallKit依赖改为NERtcCallKit/NOS_Special。删除Podfile.lock后重新pod install。
