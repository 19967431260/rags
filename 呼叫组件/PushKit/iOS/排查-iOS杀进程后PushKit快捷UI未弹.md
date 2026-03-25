---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: PushKit
platform: iOS
title: iOS杀进程后PushKit快捷UI未弹出
root_cause: 杀进程后需要确保在启动方法中完成IM登录才能正常处理PushKit回调
solution: 在didFinishLaunchingWithOptions中调用IM登录方法[[NIMSDK sharedSDK].loginManager autoLogin:loginData]，确保收到PushKit推送时能正确处理
customers: ['北京小刀万维-G1&G2']
source: chat_history
tags: ['PushKit', '快捷UI', '杀进程', 'iOS', '登录']
created: 2025-09-01
updated: 2026-03-25
---

## 问题：iOS iOS杀进程后PushKit快捷UI未弹出

## 问题详情

**现象**：
客户使用PushKit实现来电通知，app在后台时可以弹出快捷UI，但杀进程后无法弹出。

## 解决方案

在didFinishLaunchingWithOptions中调用IM登录方法[[NIMSDK sharedSDK].loginManager autoLogin:loginData]，确保收到PushKit推送时能正确处理
