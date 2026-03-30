---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 集成编译
platform: Android
title: Android端libc++_shared.so库冲突解决方案
root_cause: 多个第三方库引入同名libc++_shared.so导致冲突，不能直接移除ALOG库
solution: 在build.gradle中使用exclude排除alog库的so文件：
```gradle
exclude group: 'com.netease.yunxin', module: 'alog'
```
或采用pickFirst策略保留一份so文件
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# Android端libc++_shared.so库冲突解决方案

## 问题描述

客户在使用IM V9 9.7.0版本UIKit时，遇到alog库中的libc++_shared.so与项目引入的其他库同名冲突，排除alog库后出现闪退问题

## 问题背景

1. 客户尝试排除alog库解决so冲突 → 出现闪退
2. 确认不能简单移除ALOG库，因为呼叫组件依赖该库
3. 建议采用Android Gradle的exclude方案处理so冲突

## 根因分析

多个第三方库引入同名libc++_shared.so导致冲突，不能直接移除ALOG库

## 解决方案

在build.gradle中使用exclude排除alog库的so文件：
```gradle
exclude group: 'com.netease.yunxin', module: 'alog'
```
或采用pickFirst策略保留一份so文件

## 标签

- libc++_shared.so
- so冲突
- alog
- exclude
- Android
- IM V9

## 客户

- 星网锐捷

## 会话日期

2025-02-06
