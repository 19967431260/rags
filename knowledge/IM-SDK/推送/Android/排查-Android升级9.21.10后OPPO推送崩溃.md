---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: Android升级9.21.10后OPPO推送崩溃
root_cause: 云信SDK 9.21.10需要升级OPPO推送SDK版本以保持兼容性
solution: 升级OPPO推送SDK到3.5.1或3.5.2版本。云信SDK版本必须对齐，其他厂商推送版本要求参考9.16.3文档，稍高几个小版本（大版本不变）一般没问题。
customers: ["智己汽车"]
source: chat_history
tags: ["Android","OPPO推送","9.21.10","AbstractMethodError","版本兼容"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：Android Android升级9.21.10后OPPO推送崩溃

## 问题详情

**现象**：
Android从9.13.0升级到9.21.10后运行报错：java.lang.AbstractMethodError: abstract method "void com.heytap.msp.push.callback.ICallBackResultService.onRegister(int, java.lang.String)"

**环境信息**：
- SDK 版本：9.21.10

**相关日志**：
java.lang.AbstractMethodError: abstract method "void com.heytap.msp.push.callback.ICallBackResultService.onRegister(int, java.lang.String)"

## 排查过程

1. 检查依赖版本 → basesdk、chatroom、push、lucene都已升级到9.21.10
2. 分析错误堆栈 → OPPO推送SDK版本不兼容

**关键发现**：升级云信SDK后需要同步升级OPPO推送SDK版本

## 问题原因

云信SDK 9.21.10需要升级OPPO推送SDK版本以保持兼容性

## 解决方案

升级OPPO推送SDK到3.5.1或3.5.2版本。云信SDK版本必须对齐，其他厂商推送版本要求参考9.16.3文档，稍高几个小版本（大版本不变）一般没问题。

## 其他触发场景

（暂无）
