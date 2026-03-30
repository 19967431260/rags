---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Web
title: uniapp微信小程序分包后NIM实例序列化报错
root_cause: nim实例继承自EventEmitter3对象，包含循环引用，无法被JSON序列化。Vue组件的data会被序列化，导致报错。
solution: 不要在vue组件的data里挂载nim实例，推荐将nim实例挂载到vuex的store中。
customers:
- 111医药馆
source: chat_history
tags:
- uniapp
- 微信小程序
- 分包
- 序列化
- EventEmitter3
created: '2026-01-30'
updated: '2026-03-15'
---

## 问题：Web uniapp微信小程序分包后NIM实例序列化报错

## 问题详情

**现象**：
uniapp开发微信小程序使用分包，引用NIM_Web_NIM_miniapp.js后，在IM初始化时报错：Converting circular structure to JSON。

## 排查过程

**关键发现**：nim实例挂载在vue组件的data中，导致序列化失败。

## 问题原因

nim实例继承自EventEmitter3对象，包含循环引用，无法被JSON序列化。Vue组件的data会被序列化，导致报错。

## 解决方案

不要在vue组件的data里挂载nim实例，推荐将nim实例挂载到vuex的store中。
