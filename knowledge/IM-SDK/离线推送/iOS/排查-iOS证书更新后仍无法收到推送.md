---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "离线推送"
platform: "iOS"
title: "iOS证书更新后仍无法收到推送"
root_cause: "应用未调用updateApnsToken上报token，可能系统回调未触发"
solution: "检查didRegisterForRemoteNotificationsWithDeviceToken回调实现，确保调用updateApnsToken"
customers: ["广州还行"]
source: "chat_history"
tags: ["iOS推送", "updateApnsToken", "token上报", "证书"]
created: "2025-09-16"
updated: "2026-03-20"
---

## 问题：iOS iOS证书更新后仍无法收到推送

## 问题详情

**现象**：
客户重新配置iOS证书后仍无法收到推送通知。

## 排查过程

1. 技术人员查询服务器发现没有token上报
2. 客户登录设备供技术人员拉取日志
3. 分析日志发现未调用updateApnsToken接口
4. 确认系统didRegisterForRemoteNotificationsWithDeviceToken方法未触发

## 问题原因

应用未调用updateApnsToken上报token，可能系统回调未触发

## 解决方案

检查didRegisterForRemoteNotificationsWithDeviceToken回调实现，确保调用updateApnsToken

## 其他触发场景
