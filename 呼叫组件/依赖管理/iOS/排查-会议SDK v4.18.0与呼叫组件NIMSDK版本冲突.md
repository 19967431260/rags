---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 依赖管理
platform: iOS
title: 会议SDK v4.18.0与呼叫组件NIMSDK版本冲突
root_cause: 组件的NIMSDK版本和会议依赖的NIMSDK版本冲突。
solution: 使用NOS_Special版本指定NIMSDK版本：pod 'NERtcCallKit/NOS_Special', '3.6.0'、pod 'NERtcCallUIKit/NOS_Special', '3.6.0'、pod 'NIMSDK_LITE', '10.9.42'。本地源码引用时修改podspec中的依赖为NERtcCallKit/NOS_Special。
customers: ["成都新势界"]
source: chat_history
tags: ["版本冲突","NIMSDK","NOS_Special","依赖管理"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：iOS 会议SDK v4.18.0与呼叫组件NIMSDK版本冲突

## 问题详情

**现象**：
从会议SDK v4.17.0更新到v4.18.0后出现编译错误，提示NIMSDK版本冲突。呼叫组件依赖的NIMSDK版本与会议SDK依赖的NIMSDK版本不一致导致。

## 问题原因

组件的NIMSDK版本和会议依赖的NIMSDK版本冲突。

## 解决方案

使用NOS_Special版本指定NIMSDK版本：pod 'NERtcCallKit/NOS_Special', '3.6.0'、pod 'NERtcCallUIKit/NOS_Special', '3.6.0'、pod 'NIMSDK_LITE', '10.9.42'。本地源码引用时修改podspec中的依赖为NERtcCallKit/NOS_Special。

## 其他触发场景

