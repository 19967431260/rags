---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 呼叫组件
platform: Uniapp
title: Uniapp离线好友添加邀请收不到
root_cause: 呼叫组件初始化顺序问题：nimCallKit.initConfig和nimCallKit.login在nim.connect()之前执行，导致离线系统通知被原生层接收，uniapp层登录后无法获取
solution: 将nimCallKit.initConfig和nimCallKit.login调用放在nim.connect()的.then回调中执行，确保IM登录完成后再初始化呼叫组件
customers: ["湖南梦话灵境网络科技有限公司"]
source: chat_history
tags: ["离线通知", "好友添加", "呼叫组件", "Uniapp", "初始化顺序"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：Uniapp Uniapp离线好友添加邀请收不到

## 问题详情

**现象**：
客户在使用Uniapp开发时，获取验证消息列表时无法获取到离线的添加好友邀请。现象：用户A添加用户B为好友时，B处于离线状态，B登录后没有收到好友添加消息。

## 排查过程

1. 检查呼叫组件初始化登录时机 → 发现客户在IM登录之前就初始化了呼叫组件
**关键发现**：呼叫组件原生层也有IM登录逻辑，先登录会导致离线系统通知下发到原生层，uniapp IM层再登录就收不到这个离线通知了，因为离线只下发一次

## 问题原因

呼叫组件初始化顺序问题：nimCallKit.initConfig和nimCallKit.login在nim.connect()之前执行，导致离线系统通知被原生层接收，uniapp层登录后无法获取

## 解决方案

将nimCallKit.initConfig和nimCallKit.login调用放在nim.connect()的.then回调中执行，确保IM登录完成后再初始化呼叫组件

## 其他触发场景
- [Uniapp] Uniapp离线好友添加邀请收不到，来源：['湖南梦话灵境网络科技有限公司']，2026-03-20
- [Uniapp] Uniapp离线好友添加邀请收不到，来源：['湖南梦话灵境网络科技有限公司']，2026-03-20

