---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: NIMClient.initDelay异步初始化与登录时序问题
root_cause: initDelay是异步初始化，调用IM登录时SDK可能还未完成初始化
solution: 使用NIMClient.getStatus()获取初始化状态或监听初始化状态回调，确保初始化成功后再调用登录接口，参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM
customers: ["景群數位互動有限公司"]
source: chat_history
tags: ["IM-SDK", "Android", "initDelay", "初始化", "异步", "登录"]
created: 2025-02-07
updated: 2026-03-20
---

## 问题：Android NIMClient.initDelay异步初始化与登录时序问题

## 问题详情

**现象**：
Android端调用NIMClient.initDelay进行异步初始化，在启动页自动登录成功后调用IM登录接口，可能出现SDK还未完成初始化就调用登录的情况。

## 排查过程

1. 确认initDelay作用 → 异步初始化方法，用于隐私协议确认步骤
2. 分析时序问题 → 启动页自动登录成功后调用IM登录，可能SDK还在初始化
3. 提供解决方案 → 监听初始化状态后再登录

## 问题原因

initDelay是异步初始化，调用IM登录时SDK可能还未完成初始化

## 解决方案

使用NIMClient.getStatus()获取初始化状态或监听初始化状态回调，确保初始化成功后再调用登录接口，参考文档：https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM

## 其他触发场景
- [Android] NIMClient.initDelay异步初始化与登录时序问题，来源：['景群數位互動有限公司']，2026-03-20
- [Android] NIMClient.initDelay异步初始化与登录时序问题，来源：['景群數位互動有限公司']，2026-03-20

