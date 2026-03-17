---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 日志配置
platform: 通用
title: Electron端SDK日志级别配置导致崩溃
root_cause: sdkLogLevel配置方式不正确，应使用NIM.V2NIMConst.V2NIMSDKLogLevel枚举值；缺少appDataPath日志路径配置
solution: 1. 正确配置日志级别：sdkLogLevel: NIM.V2NIMConst.V2NIMSDKLogLevel.V2NIM_SDK_LOG_LEVEL_PRO 2. 在init时添加appDataPath参数指定日志路径 3. 引入：const NIM = require('node-nim')
customers: ["圆通"]
source: chat_history
tags: ["Electron","sdkLogLevel","日志配置","appDataPath","V2NIM_SDK_LOG_LEVEL_PRO"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：通用 Electron端SDK日志级别配置导致崩溃

## 问题详情

**现象**：
Electron端设置sdkLogLevel字段后总是崩溃，配置私有化参数后连接超时。

## 排查过程

1. 检查sdkLogLevel配置 → 应使用枚举值
2. 检查连接超时 → 查看日志请求的URL地址
3. 检查日志输出 → 需要配置appDataPath参数

**关键发现**：sdkLogLevel需要使用正确的枚举值，且需配置日志路径

## 问题原因

sdkLogLevel配置方式不正确，应使用NIM.V2NIMConst.V2NIMSDKLogLevel枚举值；缺少appDataPath日志路径配置

## 解决方案

1. 正确配置日志级别：sdkLogLevel: NIM.V2NIMConst.V2NIMSDKLogLevel.V2NIM_SDK_LOG_LEVEL_PRO
2. 在init时添加appDataPath参数指定日志路径
3. 引入：const NIM = require('node-nim')

## 其他触发场景

（暂无）
