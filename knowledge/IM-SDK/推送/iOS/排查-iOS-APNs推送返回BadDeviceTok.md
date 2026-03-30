---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: APNs推送返回BadDeviceToken错误
root_cause: APNs证书配置问题导致BadDeviceToken错误
solution: 参考云信文档排查BadDeviceToken问题：https://doc.yunxin.163.com/campass/concept/DcyNzIyODQ
customers: ["xhsp"]
source: chat_history
tags: ["APNs", "推送", "BadDeviceToken", "iOS"]
created: 2025-11-13
updated: 2026-03-20
---

## 问题：iOS APNs推送返回BadDeviceToken错误

## 问题详情

**现象**：
客户配置APNs推送证书后，客户端上传了deviceToken，但发送文本消息没有推送。

**排查过程**：
1. 检查服务端推送日志
2. 发现APNs返回错误：rejectionReason='BadDeviceToken'
3. 判断为证书或环境配置问题

## 问题原因

APNs证书配置问题导致BadDeviceToken错误

## 解决方案

参考云信文档排查BadDeviceToken问题：https://doc.yunxin.163.com/campass/concept/DcyNzIyODQ
