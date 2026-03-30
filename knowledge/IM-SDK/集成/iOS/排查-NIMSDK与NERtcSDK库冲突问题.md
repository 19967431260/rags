---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: iOS
title: NIMSDK与NERtcSDK库冲突问题
root_cause: NIMSDK pod已包含nimavchat、nimsdk、nmc等库，本地又重复引入
solution: 使用pod 'NIMSDK', '9.19.10'集成即可，不需要再本地引入NIMSDK相关库；NERtcSDK可单独本地集成
customers: ["深圳市家家顺-乐有家"]
source: chat_history
tags: ["iOS", "库冲突", "NERtcSDK", "pod", "xcframework"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：NIMSDK与NERtcSDK库冲突问题

## 问题详情

**现象**：
客户同时集成NIMSDK和NERtcSDK 5.5.2时，出现库重复冲突，报错有冲突的framework。

**环境信息**：
- 平台：iOS

## 排查过程

1. 检查项目中的本地库
2. 确认pod集成方式
3. 分析冲突的库文件

## 根因分析

NIMSDK pod已包含nimavchat、nimsdk、nmc等库，本地又重复引入

## 解决方案

使用pod 'NIMSDK', '9.19.10'集成即可，不需要再本地引入NIMSDK相关库；NERtcSDK可单独本地集成

## 其他触发场景

（无）
