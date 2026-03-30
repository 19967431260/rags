---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: V10迁移
platform: iOS
title: IM V10登录后获取登录信息为空
root_cause: V10 SDK需要使用V10的接口获取登录信息，混用V9接口会返回空
solution: V10使用v2LoginService获取登录信息：[[[NIMSDK sharedSDK] v2LoginService] getLoginUser]和[[[NIMSDK sharedSDK] v2LoginService] getLoginStatus]。V9和V10接口不要混用
customers: ['VIP云信-高途预见塔塔项目']
source: chat_history
tags: ['V10', 'currentAccount', 'isLogined', 'v2LoginService', 'iOS']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：iOS IM V10登录后获取登录信息为空

## 问题详情

**现象**：
iOS使用V10登录成功（静态token登录）后，获取[NIMSDK sharedSDK].loginManager.currentAccount为空，isLogined为nil

## 排查过程

1. 确认登录成功 → 走了success回调
2. 检查调用方式 → 使用V10登录但用V9方法获取登录信息
3. 确认混用问题 → V10需要使用V10的接口

## 问题原因

V10 SDK需要使用V10的接口获取登录信息，混用V9接口会返回空

## 解决方案

V10使用v2LoginService获取登录信息：[[[NIMSDK sharedSDK] v2LoginService] getLoginUser]和[[[NIMSDK sharedSDK] v2LoginService] getLoginStatus]。V9和V10接口不要混用

## 其他触发场景

（合并时在此处追加）
