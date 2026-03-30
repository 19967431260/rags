---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 音视频通话
platform: Android
title: 安卓呼叫组件onCallConnected回调丢失
root_cause: 客户在joinChannel之后、onUserJoin之前添加了音视频监听，且业务层存在重复初始化NERtc的情况，导致呼叫组件无法获取音视频监听事件。
solution: 避免在joinChannel和onUserJoin之间添加音视频监听，检查业务层是否有重复调用NERtcEx.getInstance().init的情况。按照呼叫组件官方使用方式集成。
customers: ["北京平直方大科贸有限公司"]
source: chat_history
tags: ["呼叫组件", "onCallConnected", "回调", "重复初始化", "NERtc"]
created: 2025-02-26
updated: 2026-03-20
---

## 问题：Android 安卓呼叫组件onCallConnected回调丢失

## 问题详情

**现象**：
安卓之间拨打视频通话后，只有一方能收到onCallConnected回调，主叫被叫都可能收不到。客户业务层添加了音视频监听。

## 排查过程

1. 检查日志发现joinChannel后onUserJoin前添加了监听\n2. 发现客户业务层重复初始化导致监听重复注册\n3. 定位到NERtcEx.getInstance().init被多次调用

## 问题原因

客户在joinChannel之后、onUserJoin之前添加了音视频监听，且业务层存在重复初始化NERtc的情况，导致呼叫组件无法获取音视频监听事件。

## 解决方案

避免在joinChannel和onUserJoin之间添加音视频监听，检查业务层是否有重复调用NERtcEx.getInstance().init的情况。按照呼叫组件官方使用方式集成。

## 其他触发场景
- [Android] 安卓呼叫组件onCallConnected回调丢失，来源：['北京平直方大科贸有限公司']，2026-03-20
- [Android] 安卓呼叫组件onCallConnected回调丢失，来源：['北京平直方大科贸有限公司']，2026-03-20

