---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 初始化
platform: 安卓
title: 同一APP配置多套appkey动态初始化方案
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 同一APP配置多套appkey动态初始化方案

## 问题描述

客户需要在同一个APP中根据不同医院配置初始化不同的appkey，但init方法需要在进程启动时调用，此时还未获取到配置

## 解答

IM SDK支持延迟设置appkey：
1. 进程启动时调用NIMClient.init()，SDKOptions.appkey可以不设置
2. 登录时通过loginInfo传入appkey，登录设置的appkey优先级最高，会覆盖初始化时的配置

这样就可以根据获取到的医院配置动态设置不同的appkey。

## 标签

- 初始化
- appkey
- 动态配置
- 登录
- 多租户

## 客户

- ISV云信-和仁

## 会话日期

2025-02-27
