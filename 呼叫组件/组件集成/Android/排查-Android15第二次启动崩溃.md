---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 组件集成
platform: Android
title: Android15系统第二次启动崩溃
root_cause: call-ui版本过低,与当前使用的IM SDK版本不兼容,导致在Android15系统上第二次启动时崩溃
solution: 1. 将com.netease.yunxin.kit.call:call-ui升级到2.7.1。2. 将IM相关SDK降级到9.20.15版本(因客户代码适配9.x)。升级指南参考: https://doc.yunxin.163.com/nertccallkit/guide/zUzMDU3Mzc?platform=android
customers: ["成都宝游网络科技有限公司"]
source: chat_history
tags: ["呼叫组件", "call-ui", "Android15", "崩溃", "版本兼容", "2.7.1"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Android Android15系统第二次启动崩溃

## 问题详情

**现象**：
客户集成呼叫组件后,第一次登录正常,第二次打开程序时在Android15系统上崩溃。堆栈显示SDK版本兼容性问题。

**环境信息**：
- 系统版本：Android15

## 排查过程

1. 检查崩溃堆栈 → 发现SDK版本问题
2. 查看项目依赖树 → 确认call-ui和IM SDK版本不匹配

**关键发现**: call-ui版本过低,与IM SDK 10.x不兼容

## 问题原因

call-ui版本过低,与当前使用的IM SDK版本不兼容,导致在Android15系统上第二次启动时崩溃

## 解决方案

1. 将com.netease.yunxin.kit.call:call-ui升级到2.7.1
2. 将IM相关SDK降级到9.20.15版本(因客户代码适配9.x)
3. 升级指南参考: https://doc.yunxin.163.com/nertccallkit/guide/zUzMDU3Mzc?platform=android

## 其他触发场景
