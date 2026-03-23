---
track_type: 排查类
sub_type: 崩溃
product: 呼叫组件
feature: 音视频通话
platform: Android
title: 通话接通时双端闪退-AbstractMethodError
root_cause: 呼叫组件版本与RTC SDK版本不兼容，旧版本缺少onUserJoined方法的实现
solution: 升级呼叫组件到最新版本（call-ui:2.5.1），如无法升级compileSdk到31，可使用1.6.4版本
customers: ["ISV云信-龙软科技-音视频私有化"]
source: chat_history
tags: ["闪退", "AbstractMethodError", "版本不兼容", "呼叫组件", "onUserJoined"]
created: 2025-12-09
updated: 2026-03-23
---

## 问题：通话接通时双端闪退-AbstractMethodError

## 问题详情

**现象**：
使用呼叫组件进行音视频通话，接收端点击接收时两端都闪退。错误：`java.lang.AbstractMethodError: abstract method onUserJoined`

**环境信息**：
- 产品：呼叫组件
- 功能：音视频通话
- 平台：Android

## 排查过程

1. 获取闪退日志
2. 发现AbstractMethodError，onUserJoined方法未实现
3. 确认callkit版本和RTC SDK版本不兼容（2年前的旧版本）
4. 建议升级到最新版本

**关键发现**：呼叫组件版本与RTC SDK版本不兼容

## 问题原因

呼叫组件版本与RTC SDK版本不兼容，旧版本缺少onUserJoined方法的实现。

## 解决方案

升级呼叫组件到最新版本（call-ui:2.5.1），如无法升级compileSdk到31，可使用1.6.4版本。

## 其他触发场景

