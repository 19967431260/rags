---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 推送
platform: iOS
title: TestFlight应用推送收不到
root_cause: 证书名称配置错误，应该是"证书dis_apns_p12"而不是"dis_apns_p12"
solution: 检查控制台配置的证书名称与代码初始化的名称是否一致。TestFlight和App Store可能需要配置不同的证书。
customers: ["青岛上啥班"]
source: chat_history
tags: ["iOS", "TestFlight", "推送", "证书", "dis_apns_p12"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：TestFlight应用推送收不到

## 问题详情

**现象**：
TestFlight下载的应用早上能收到推送，中午开始收不到，App Store版本正常。

**环境信息**：
- 平台：iOS

## 排查过程

1. 客户反馈TestFlight应用推送突然失效
2. 提供接收方accid和时间点查询
3. 查询发现dis_apns_p12证书不存在
4. 客户检查证书名称发现配置错误

## 根因分析

证书名称配置错误，应该是"证书dis_apns_p12"而不是"dis_apns_p12"

## 解决方案

检查控制台配置的证书名称与代码初始化的名称是否一致。TestFlight和App Store可能需要配置不同的证书。

## 其他触发场景

（无）
