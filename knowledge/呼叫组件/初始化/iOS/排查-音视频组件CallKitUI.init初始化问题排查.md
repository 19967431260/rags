---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 初始化
platform: iOS
title: 音视频组件CallKitUI.init初始化问题排查
root_cause: 初始化逻辑没有服务端上报，需要客户端日志确认
solution: CallKitUI.init初始化逻辑没有服务端上报，需要拉取客户端SDK日志才能确认是否调用到初始化方法。
customers: ['前理增团队-升级多米趣产品-dx']
source: chat_history
tags: ['iOS', '呼叫组件', 'CallKitUI', '初始化', '音视频']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：iOS 音视频组件CallKitUI.init初始化问题排查

## 问题详情

**现象**：
客户反馈用户体现音视频组件初始化失败，无法接听和拨打，需要确认是否有调用初始化方法。

## 排查过程

1. 客户反馈音视频无法接听拨打
2. 询问具体现象
3. 确认初始化失败有弹窗提示
4. 询问代码如何判断失败
5. 说明初始化逻辑没有上报，需要客户端SDK日志

## 问题原因

初始化逻辑没有服务端上报，需要客户端日志确认

## 解决方案

CallKitUI.init初始化逻辑没有服务端上报，需要拉取客户端SDK日志才能确认是否调用到初始化方法。

## 其他触发场景

（合并时在此处追加）
