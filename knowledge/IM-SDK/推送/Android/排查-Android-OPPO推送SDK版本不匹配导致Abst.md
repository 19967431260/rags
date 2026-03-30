---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送SDK版本不匹配导致AbstractMethodError崩溃
root_cause: OPPO推送SDK版本不匹配，云信SDK 9.20.17需要配套使用OPPO推送SDK 3.5.1版本，客户当前使用的是3.0.0版本。
solution: 升级OPPO推送SDK至3.5.1版本，与云信SDK 9.20.17配套使用。参考更新日志：https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE
customers: ["FVIP-云信-上海抱朴"]
source: chat_history
tags: ["OPPO推送", "AbstractMethodError", "崩溃", "推送SDK", "3.5.1", "3.0.0"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android OPPO推送SDK版本不匹配导致AbstractMethodError崩溃

## 问题详情

**现象**：
Android应用在使用OPPO手机时出现崩溃，错误为java.lang.AbstractMethodError，涉及com.heytap.msp.push.callback.ICallBackResultService.onRegister方法。

## 排查过程

1. 查看崩溃日志 → 发现AbstractMethodError，涉及OPPO推送SDK的ICallBackResultService.onRegister方法
**关键发现**：客户使用的OPPO推送SDK版本为3.0.0，与云信SDK 9.20.17不兼容

## 问题原因

OPPO推送SDK版本不匹配，云信SDK 9.20.17需要配套使用OPPO推送SDK 3.5.1版本，客户当前使用的是3.0.0版本。

## 解决方案

升级OPPO推送SDK至3.5.1版本，与云信SDK 9.20.17配套使用。参考更新日志：https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE

## 其他触发场景

